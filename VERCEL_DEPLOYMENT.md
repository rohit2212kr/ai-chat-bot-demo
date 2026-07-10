# Deploy Frontend to Vercel - Step by Step

Your backend is ready at: **http://ai-chat-bot-demo.onrender.com**

Now let's deploy the frontend!

## Step-by-Step Instructions

### 1. Go to Vercel
Visit: **https://vercel.com/new**

### 2. Import Your GitHub Repository
- Click **"Add New..." → "Project"** or **"Import Git Repository"**
- Search for: `rohit2212kr/ai-chat-bot-demo`
- Click **"Import"**

### 3. Configure the Project

#### Framework Settings:
- **Framework Preset**: Select `Vite` (should auto-detect)
- **Root Directory**: Click **"Edit"** → Enter `client` → Click **"Continue"**

#### Build Settings:
- **Build Command**: `npm run build` (should be auto-filled)
- **Output Directory**: `dist` (should be auto-filled)
- **Install Command**: `npm install` (should be auto-filled)

### 4. Add Environment Variable

Click **"Environment Variables"** section:

**Add this variable:**
- **Name (Key)**: `VITE_API_BASE_URL`
- **Value**: `http://ai-chat-bot-demo.onrender.com/api`
- Click **"Add"**

⚠️ **Important**: Make sure to include `/api` at the end of the URL!

### 5. Deploy
- Click **"Deploy"** button
- Wait 1-2 minutes for deployment to complete
- You'll see a success screen with your live URL

### 6. Test Your Application
1. Click on the deployed URL (e.g., `https://ai-chat-bot-demo-xxx.vercel.app`)
2. Click on the chat widget button
3. Type a message and press Enter
4. Verify the AI responds correctly

## Troubleshooting

### If the chat doesn't work:
1. Open browser developer console (F12)
2. Check for any error messages
3. Verify the API URL is correct in Vercel environment variables
4. Make sure your Render backend is running (visit the backend URL directly)

### Common Issues:

**"Failed to fetch" error:**
- Check if `VITE_API_BASE_URL` is set correctly in Vercel
- Verify your Render backend is awake (free tier sleeps after inactivity)

**CORS errors:**
- Go back to Render dashboard
- Update `CLIENT_URL` environment variable with your Vercel URL
- Example: `https://ai-chat-bot-demo-xxx.vercel.app`

## After Deployment

### Update Backend CORS (Recommended)
1. Go to Render Dashboard: https://dashboard.render.com
2. Click on your backend service: `ai-chat-bot-demo`
3. Go to **"Environment"** tab
4. Edit the `CLIENT_URL` variable
5. Change from `*` to your Vercel URL: `https://YOUR-VERCEL-URL.vercel.app`
6. Save (will auto-redeploy in ~1-2 minutes)

This improves security by only allowing requests from your frontend.

## 🎉 Congratulations!

Your AI Chatbot is now live:
- **Frontend**: https://[your-vercel-url].vercel.app
- **Backend**: http://ai-chat-bot-demo.onrender.com

Both will auto-deploy when you push changes to GitHub!
