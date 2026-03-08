# 🚀 Deployment Guide - Sai Priya Portfolio

Complete guide to deploy your portfolio to various platforms.

---

## 📋 Pre-Deployment Checklist

Before deploying, ensure:
- [ ] ✅ Resume PDF added as `saipriya_resume.pdf`
- [ ] ✅ All personalized information updated in `index.html`
- [ ] ✅ Tested locally in multiple browsers
- [ ] ✅ All links working (LinkedIn, GitHub, email)
- [ ] ✅ Mobile responsiveness tested
- [ ] ✅ Dark mode working correctly
- [ ] ✅ No console errors

---

## Option 1: Vercel (Recommended) ⭐

**Why Vercel?**
- Free hosting with SSL
- Automatic deployments from Git
- Fast CDN
- Preview deployments
- Zero configuration needed

### Step-by-Step:

1. **Install Vercel CLI**
```bash
npm install -g vercel
```

2. **Navigate to Portfolio Directory**
```bash
cd /home/saipriya/portfolio
```

3. **Login to Vercel**
```bash
vercel login
```

4. **Deploy**
```bash
vercel
```

5. **Follow Prompts**
```
? Set up and deploy "~/portfolio"? [Y/n] Y
? Which scope do you want to deploy to? Sai Priya Gorrela
? Link to existing project? [y/N] N
? What's your project's name? portfolio
? In which directory is your code located? ./
```

6. **Your Site is Live!**
- Vercel will provide a URL like: `https://portfolio-xyz.vercel.app`
- Production deployment: `vercel --prod`

### Custom Domain (Optional)
1. Go to Vercel dashboard
2. Select your project
3. Go to Settings → Domains
4. Add your custom domain
5. Update DNS records as instructed

---

## Option 2: Netlify

**Why Netlify?**
- Drag and drop deployment
- Free SSL certificates
- Continuous deployment
- Form handling (if needed)

### Step-by-Step:

1. **Prepare Files**
```bash
cd /home/saipriya/portfolio
# Ensure all files are in the portfolio folder
ls -la
# Should show: index.html, styles.css, script.js, saipriya_resume.pdf
```

2. **Deploy via Drag & Drop**
   - Go to [netlify.com](https://netlify.com)
   - Sign up/login
   - Drag the entire `portfolio` folder to the deploy area
   - Wait a few seconds
   - Your site is live!

### Custom Domain (Optional)
1. Go to Site Settings → Domain Management
2. Add custom domain
3. Configure DNS according to Netlify instructions

---

## Option 3: GitHub Pages

**Why GitHub Pages?**
- Free hosting
- Version control
- Custom domain support
- Community standard

### Step-by-Step:

1. **Initialize Git Repository**
```bash
cd /home/saipriya/portfolio
git init
git add .
git commit -m "Initial portfolio commit"
```

2. **Create GitHub Repository**
   - Go to github.com
   - Create new repository named `portfolio`
   - Don't initialize with README

3. **Push to GitHub**
```bash
git remote add origin https://github.com/saipriya1729/portfolio.git
git branch -M main
git push -u origin main
```

4. **Enable GitHub Pages**
   - Go to repository Settings
   - Scroll to "Pages" section
   - Source: Deploy from a branch
   - Branch: `main` / `root`
   - Save

5. **Your Site is Live!**
   - URL: `https://saipriya1729.github.io/portfolio/`

### Custom Domain (Optional)
1. Add a `CNAME` file with your custom domain
2. Update DNS records at your domain provider
3. Enable custom domain in GitHub Pages settings

---

## Option 4: AWS S3 + CloudFront

**Why AWS?**
- Maximum control
- High scalability
- Low cost (Free Tier eligible)
- Learn AWS skills

### Step-by-Step:

1. **Create S3 Bucket**
   - Go to AWS Console → S3
   - Create bucket: `saipriya-portfolio`
   - Region: Choose closest to you
   - Uncheck "Block all public access"
   - Enable static website hosting

2. **Upload Files**
```bash
# Install AWS CLI
pip install awscli

# Configure credentials
aws configure

# Sync files
aws s3 sync /home/saipriya/portfolio s3://saipriya-portfolio --acl public-read
```

3. **Set Bucket Policy**
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::saipriya-portfolio/*"
    }
  ]
}
```

4. **Set Up CloudFront (Optional but recommended)**
   - Create CloudFront distribution
   - Origin: S3 bucket
   - Default root object: `index.html`
   - Add custom SSL certificate

---

## Option 5: Firebase Hosting

**Why Firebase?**
- Free SSL
- Fast CDN
- Easy deployment
- Google infrastructure

### Step-by-Step:

1. **Install Firebase CLI**
```bash
npm install -g firebase-tools
```

2. **Initialize Firebase**
```bash
cd /home/saipriya/portfolio
firebase init hosting
```

3. **Configure firebase.json**
```json
{
  "hosting": {
    "public": ".",
    "ignore": ["firebase.json", "**/.*", "**/node_modules/**"],
    "rewrites": [
      {
        "source": "**",
        "destination": "/index.html"
      }
    ]
  }
}
```

4. **Deploy**
```bash
firebase deploy
```

---

## 🔧 Post-Deployment Steps

### 1. Verify Deployment
- Check all pages load correctly
- Test all links (LinkedIn, GitHub, email)
- Verify resume download works
- Test on mobile devices
- Test dark mode toggle

### 2. Update LinkedIn
- Add portfolio URL to your LinkedIn profile
- Featured section → Website
- About section → Portfolio link

### 3. Update Resume
- Add portfolio URL to your resume
- Place it near your contact information

### 4. Update GitHub Profile
- Add portfolio to GitHub profile README
- Pin portfolio repository

### 5. Share (Optional)
- Share on Twitter/X
- Post in relevant communities
- Add to email signature

---

## 📊 Monitor Your Portfolio

### Add Analytics (Optional)

**Google Analytics:**
1. Create account at analytics.google.com
2. Get tracking ID
3. Add before closing `</head>` in index.html:
```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

**Plausible Analytics (Privacy-friendly):**
```html
<script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script>
```

---

## 🔄 Continuous Deployment

### Automatic Deployments from Git

**Vercel:**
- Connect GitHub repository to Vercel
- Automatic deployment on every push to main branch

**Netlify:**
- Connect GitHub repository to Netlify
- Automatic deployment on every push

**GitHub Actions (GitHub Pages):**
- Already automatic when pushing to main branch

---

## 🛡️ Security Best Practices

1. **HTTPS Only**
   - All recommended platforms provide free SSL
   - Ensure all links use `https://`

2. **Security Headers**
   - Already included in `vercel.json`
   - For other platforms, configure via their dashboard

3. **No Sensitive Data**
   - Don't commit API keys
   - Don't include passwords in code

4. **Keep Dependencies Updated**
   - Regularly update deployment tools
   - Check for security advisories

---

## 📱 Testing Checklist

After deployment, test:

- [ ] ✅ Homepage loads correctly
- [ ] ✅ All sections scroll smoothly
- [ ] ✅ Dark mode toggle works
- [ ] ✅ All navigation links work
- [ ] ✅ Resume download works
- [ ] ✅ Email link opens mail client
- [ ] ✅ LinkedIn link opens correct profile
- [ ] ✅ GitHub link opens correct profile
- [ ] ✅ Mobile responsive (test on phone)
- [ ] ✅ Desktop (1920x1080)
- [ ] ✅ Tablet (768x1024)
- [ ] ✅ Small laptop (1366x768)
- [ ] ✅ No console errors
- [ ] ✅ Fast loading (< 3 seconds)

---

## 🆘 Troubleshooting

### Issue: Resume not downloading
**Solution:**
- Ensure `saipriya_resume.pdf` exists in portfolio directory
- Check file name matches exactly (case-sensitive)
- Verify file permissions

### Issue: Dark mode not persisting
**Solution:**
- Check browser localStorage is enabled
- Clear browser cache and try again
- Check for JavaScript errors in console

### Issue: Fonts not loading
**Solution:**
- Check internet connection (fonts load from Google)
- Verify Google Fonts link in HTML
- Clear browser cache

### Issue: Slow loading
**Solution:**
- Optimize resume PDF (reduce file size)
- Minimize external dependencies
- Check network tab for bottlenecks

### Issue: Mobile menu not working
**Solution:**
- Check JavaScript is loading
- Verify hamburger menu click events
- Test in different mobile browsers

---

## 📞 Support

If you encounter issues:
1. Check browser console for errors
2. Verify all files are uploaded
3. Compare with local version
4. Check platform status pages
5. Contact platform support if needed

---

## 🎉 Success!

Your portfolio is now live! Share it with the world:

**Example Update:**
```
🚀 Just launched my new portfolio website!

Check out my work as a Backend Software Engineer II:
🔗 [Your Portfolio URL]

Highlights:
• 60% performance improvement
• 50% faster API response times
• Built systems processing 1000+ daily deliveries

#BackendEngineer #RubyOnRails #SoftwareEngineering
```

**Good luck with your job search! 🎯**
