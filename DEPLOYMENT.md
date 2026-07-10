# Deployment Guide

This guide will help you deploy the AI Chatbot Demo project with the backend on Render and frontend on Vercel.

## Prerequisites

- GitHub account
- Render account (free tier available at https://render.com)
- Vercel account (free tier available at https://vercel.com)
- Gemini API key (get from https://aistudio.google.com/apikey)

## Step 1: Push to GitHub

1. Initialize git repository (if not already done):
   ```bash
   cd d:\FSD\ai-chatbot-demo
   git init
   git add .
   git commit -m "Initial commit - AI Chatbot Demo"
   ```

2. Create a new repository on GitHub (https://github.com/new)
   - Name it something like `ai-chatbot-demo`
   - Don't initialize with README (we already have one)

3. Push to GitHub:
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/ai-chatbot-demo.git
   git branch -M main
   git push -u origin main
   ```

## Step 2: Deploy Backend to Render

1. Go to https://dashboard.render.com and sign in
2. Click "New +" → "Web Service"
3. Connect your GitHub repository
4. Configure the service:
   - **Name**: `ai-chatbot-backend` (or any name you prefer)
   - **Region**: Choose closest to your users
   - **Root Directory**: `server`
   - **Environment**: `Node`
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
   - **Instance Type**: Free (or paid if needed)

5. Add Environment Variables:
   - Click "Advanced" or scroll to "Environment Variables"
   - Add the following:
     - `GEMINI_API_KEY`: Your Gemini API key
     - `PORT`: `3000`

6. Click "Create Web Service"
7. Wait for deployment to complete (usually 2-3 minutes)
8. **Copy your backend URL** (e.g., `https://ai-chatbot-backend-xxxx.onrender.com`)

## Step 3: Deploy Frontend to Vercel

1. Go to https://vercel.com and sign in
2. Click "Add New..." → "Project"
3. Import your GitHub repository
4. Configure the project:
   - **Framework Preset**: Vite
   - **Root Directory**: `client`
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`

5. Add Environment Variables:
   - Click "Environment Variables"
   - Add: `VITE_API_BASE_URL`
   - Value: `https://your-render-backend-url.onrender.com/api`
     (Replace with your actual Render backend URL from Step 2)

6. Click "Deploy"
7. Wait for deployment to complete (usually 1-2 minutes)
8. Your frontend will be live at `https://your-project-name.vercel.app`

## Step 4: Update CORS Settings (Important!)

After deploying, you need to update the backend to allow requests from your Vercel frontend:

1. Update `server/src/app.js` to include your Vercel URL in CORS settings
2. Push changes to GitHub
3. Render will automatically redeploy

## Troubleshooting

### Frontend can't connect to backend
- Check that `VITE_API_BASE_URL` in Vercel matches your Render backend URL
- Verify CORS is configured correctly in backend
- Check Render logs for errors

### Backend errors
- Check Render logs (Dashboard → Your Service → Logs)
- Verify `GEMINI_API_KEY` is set correctly in Render environment variables

### Build failures
- Check the build logs in Render/Vercel
- Ensure all dependencies are in package.json
- Verify Node.js version compatibility

## Post-Deployment

- Test the deployed application thoroughly
- Monitor Render logs for any issues
- Consider adding a custom domain (available in Vercel settings)
- Set up automatic deployments from GitHub (default in both platforms)

## Notes

- **Free tier limitations**:
  - Render free tier: May spin down with inactivity (takes ~30s to wake up)
  - Vercel free tier: 100GB bandwidth, unlimited deployments
- Both platforms support automatic deployments when you push to GitHub
- Environment variables can be updated without redeploying code
