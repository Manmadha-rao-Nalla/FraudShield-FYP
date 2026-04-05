# FraudShield - AI Transaction Analyzer

A modern fraud detection system powered by Claude AI, trained on the PaySim mobile money dataset. Deployed on Vercel with serverless backend.

## Features

- Real-time transaction fraud detection
- AI-powered analysis using Claude Sonnet
- Beautiful, responsive UI with live computed features
- Transaction history logging
- Risk probability gauge with detailed analysis

## Deployment to Vercel

### Prerequisites

- Node.js 16+ installed
- Git account with GitHub
- Vercel account
- Anthropic API key (Claude)

### Step 1: Set Up Git Repository

```bash
cd fraud-detector-vercel
git init
git add .
git commit -m "Initial commit: FraudShield deployment"
```

Push to GitHub:
1. Create a new repository on GitHub
2. Add remote: `git remote add origin https://github.com/USERNAME/REPO_NAME.git`
3. Push: `git branch -M main && git push -u origin main`

### Step 2: Deploy to Vercel

**Option A: Using Vercel CLI**

```bash
npm install -g vercel
vercel login
vercel
```

**Option B: Using Vercel Dashboard**

1. Go to https://vercel.com
2. Click "New Project"
3. Import your GitHub repository
4. Vercel auto-detects the configuration

### Step 3: Configure Environment Variables

In Vercel Dashboard:

1. Go to your project settings
2. Navigate to "Environment Variables"
3. Add variable:
   - Name: `ANTHROPIC_API_KEY`
   - Value: `sk-ant-...` (your Anthropic API key)
4. Click "Save"

### Step 4: Deploy

```bash
vercel --prod
```

Your app is now live at the Vercel URL!

## Local Development

Install dependencies:
```bash
npm install
```

Run locally:
```bash
npm run dev
```

Access at: `http://localhost:3000`

## API Endpoint

**POST** `/api/analyze`

Request body:
```json
{
  "prompt": "Your fraud detection prompt..."
}
```

Response:
```json
{
  "probability": 0.25,
  "verdict": "LEGIT",
  "confidence": "HIGH",
  "flags": [...],
  "analysis": "..."
}
```

## Project Structure

```
fraud-detector-vercel/
├── api/
│   └── analyze.js          # Claude API wrapper
├── public/
│   └── index.html          # Frontend application
├── package.json            # Dependencies
├── vercel.json             # Deployment config
└── .gitignore              # Git ignore rules
```

## Security Notes

- API key is stored securely in Vercel Environment Variables
- Frontend makes requests to Vercel Functions, not directly to Claude
- All API calls are server-side, protecting your credentials

## Troubleshooting

**"API key not configured"**
- Verify `ANTHROPIC_API_KEY` is set in Vercel Environment Variables
- Redeploy after adding the environment variable

**CORS errors**
- Requests should be to `/api/analyze`, not directly to Anthropic
- Check frontend code is using correct endpoint

**Deployment fails**
- Ensure `package.json` and `vercel.json` are valid JSON
- Check for syntax errors: `node -c filename.js`

## License

MIT
