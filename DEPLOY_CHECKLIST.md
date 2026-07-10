# Deployment Checklist

## ✅ Pre-Deployment Checklist

- [ ] Gemini API key ready
- [ ] GitHub account created
- [ ] Render account created (https://render.com)
- [ ] Vercel account created (https://vercel.com)

## 📦 Step 1: Push to GitHub

```bash
cd d:\FSD\ai-chatbot-demo
git init
git add .
git commit -m "Initial commit - AI Chatbot Demo"
```

Then on GitHub:
1. Create new repository: https://github.com/new
2. Copy the commands shown and run:
```bash
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git
git branch -M main
git push -u origin main
```

- [ ] Repository created on GitHub
- [ ] Code pushed to GitHub

## 🔧 Step 2: Deploy Backend on Render

1. Go to https://dashboard.render.com
2. Click "New +" → "Web Service"
3. Connect GitHub repository
4. Settings:
   - Root Directory: `server`
   - Build Command: `npm install`
   - Start Command: `npm start`
5. Environment Variables:
   - `GEMINI_API_KEY` = (your key)
   - `PORT` = `3000`
   - `CLIENT_URL` = (leave empty for now, update after Vercel)

- [ ] Backend deployed on Render
- [ ] Backend URL copied: _______________________

## 🌐 Step 3: Deploy Frontend on Vercel

1. Go to https://vercel.com/new
2. Import your GitHub repository
3. Settings:
   - Root Directory: `client`
   - Framework: Vite
   - Build Command: `npm run build`
   - Output Directory: `dist`
4. Environment Variable:
   - `VITE_API_BASE_URL` = `https://YOUR-RENDER-URL.onrender.com/api`

- [ ] Frontend deployed on Vercel
- [ ] Frontend URL: _______________________

## 🔄 Step 4: Update Backend CORS

1. Go back to Render dashboard
2. Click your backend service
3. Go to "Environment" tab
4. Update `CLIENT_URL` variable:
   - Value: `https://YOUR-VERCEL-URL.vercel.app`
5. Save (will auto-redeploy)

- [ ] CORS updated with Vercel URL
- [ ] Backend redeployed

## 🧪 Step 5: Test Your Deployed App

1. Open your Vercel URL
2. Click the chat widget
3. Send a test message
4. Verify the AI responds

- [ ] Chat widget opens
- [ ] Messages send successfully
- [ ] AI responds correctly
- [ ] Voice input works (if needed)

## 🎉 Done!

Your app is now live:
- Frontend: https://_______.vercel.app
- Backend: https://_______.onrender.com

## 📝 Notes

- First request may be slow on Render free tier (cold start ~30s)
- Both platforms auto-deploy when you push to GitHub
- Update environment variables without redeploying in dashboard
