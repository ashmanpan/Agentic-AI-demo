# Cisco Foresight Agent UI - AWS Amplify Deployment Guide

## Overview
This is an AI-powered network diagnostics demo that uses multi-agent collaboration to troubleshoot various network issues. The application features intelligent prompt matching using both keyword analysis and LLM integration.

## Prerequisites
- AWS Account
- GitHub repository containing this code
- (Optional) OpenAI API key for enhanced prompt matching

## Deployment Steps

### 1. Push Code to GitHub
```bash
git init
git add .
git commit -m "Initial commit - Cisco Foresight Agent UI"
git branch -M main
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main
```

### 2. Deploy to AWS Amplify

1. **Log in to AWS Console** and navigate to AWS Amplify

2. **Create New App**
   - Click "New app" → "Host web app"
   - Choose "GitHub" as your repository service
   - Authorize AWS Amplify to access your GitHub account

3. **Connect Repository**
   - Select your repository and branch (main)
   - Check "Connecting a monorepo? Pick a folder" if needed

4. **Configure Build Settings**
   - Amplify should auto-detect the `amplify.yml` file
   - Review the build settings (no changes needed for static HTML)

5. **Deploy**
   - Click "Save and deploy"
   - Wait for deployment to complete (usually 2-3 minutes)

### 3. Access Your App
- Once deployed, you'll get a URL like: `https://main.d1234abcd.amplifyapp.com`
- Click the URL to access your application

### 4. (Optional) Configure Custom Domain
1. In Amplify Console, go to "Domain management"
2. Click "Add domain"
3. Follow the instructions to configure your custom domain

### 5. (Optional) Add OpenAI API Key Securely

**Option A: Environment Variables (Recommended for production)**
1. In Amplify Console, go to "Environment variables"
2. Add variable: `VITE_OPENAI_API_KEY` = `your-api-key`
3. Modify the code to read from environment variables

**Option B: Direct in HTML (Development only)**
1. Edit `cisco_foresight_agent_hybrid.html`
2. Find line: `const OPENAI_API_KEY = '';`
3. Add your API key: `const OPENAI_API_KEY = 'sk-...';`
4. **Warning**: Never commit API keys to GitHub

## Features
- **Hybrid Search**: Keyword matching with LLM fallback
- **Multiple Scenarios**: 
  - Packet Loss Investigation
  - SR-PCE Path Optimization
  - Router Upgrade Assessment
  - Application Access Troubleshooting
  - Security Breach Response
  - SD-WAN Performance Optimization
  - Capacity Planning Analysis
- **Real-time Agent Visualization**: See how different network agents collaborate

## Local Development
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js (if you have http-server installed)
npx http-server
```
Then open http://localhost:8000/cisco_foresight_agent_hybrid.html

## Continuous Deployment
Any push to the main branch will automatically trigger a new deployment in Amplify.

## Troubleshooting

### Deployment Fails
- Check the Amplify build logs
- Ensure `amplify.yml` is in the root directory
- Verify all files are committed to GitHub

### Application Not Loading
- Check browser console for errors
- Ensure all file paths are relative
- Verify no CORS issues with external resources

### OpenAI Integration Not Working
- Check API key is correctly set
- Monitor browser console for API errors
- Ensure you have API credits available

## Cost Considerations
- AWS Amplify Free Tier: 1000 build minutes/month, 15GB served/month
- OpenAI API: Usage-based pricing for LLM matching feature

## Support
For issues or questions about:
- AWS Amplify: Check AWS documentation
- OpenAI integration: Review OpenAI API documentation
- Application bugs: Check browser console logs