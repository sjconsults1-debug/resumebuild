# Deployment Guide

## Prerequisites
- Node.js installed
- Vercel CLI installed (`npm install -g vercel`)
- Git repository set up

## Deployment Steps

1. **Prepare for deployment**:
   ```bash
   npm run deploy
   ```

2. **Deploy to Vercel**:
   ```bash
   vercel --prod --yes
   ```

## Troubleshooting

### "Specified input file ./css/tailwind.css does not exist" Error

This error occurs when the Vercel build process cannot find the Tailwind CSS input file. To fix this:

1. Ensure `css/tailwind.css` exists with the following content:
   ```css
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
   ```

2. Make sure the file is committed to your Git repository:
   ```bash
   git add css/tailwind.css
   git commit -m "Add tailwind.css for build process"
   git push origin main
   ```

3. Redeploy to Vercel

## Build Process

The deployment process:
1. Runs `npm run build:css-only` to generate `css/main.css` from `css/tailwind.css`
2. Commits the generated files to the repository
3. Deploys to Vercel

## Environment Variables

Make sure to set the following environment variables in Vercel:
- `MONGODB_URI` - Your MongoDB connection string
- `JWT_SECRET` - Your JWT secret key
- `NODE_ENV` - Set to "production"