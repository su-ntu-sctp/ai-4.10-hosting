# Lesson 10: Hosting Options - Manual Hosting

## Learning Objectives

By the end of this lesson, you will be able to:
1. Explore different hosting options for both codebase and database
2. Compare and contrast different hosting platforms
3. Understand when to use which hosting platform based on requirements
4. Recognize the differences between PaaS, IaaS, and container hosting

---

## Prerequisites

Before starting this lesson, you should have:
- Completed Lesson 9 (Tool Exploration)
- Understanding of Docker and containerization
- Familiarity with web applications
- Basic knowledge of databases

---

## Introduction

In Lesson 9, you learned about different CI/CD tools. Now your application is built, tested, and packaged as a Docker image. But where do you run it?

**Key Questions:**
- Where can you host your application?
- What are the different types of hosting platforms?
- How do you choose the right hosting platform?
- What about databases?

In this lesson, we'll explore different hosting options and understand how to deploy applications manually before automating the process in Lesson 12.

---

## Part 1 - Understanding Application Hosting

### What is Hosting?

**Hosting** means running your application on a server that's accessible over the internet.

**What you need to host:**
1. **Your application code** (the backend/frontend)
2. **Your database** (PostgreSQL, MySQL, etc.)
3. **Static files** (images, CSS, JS - if any)

### Types of Hosting

#### 1. Platform as a Service (PaaS)

**What it is:**
- You provide the code/Docker image
- Platform handles infrastructure, scaling, monitoring
- Easiest but less control

**Examples:**
- Render, Heroku, Railway

**Best for:**
- Small to medium applications
- Quick deployment
- Teams wanting minimal DevOps work

---

#### 2. Infrastructure as a Service (IaaS)

**What it is:**
- You get virtual machines (VMs)
- You install everything yourself (OS, Docker, database, etc.)
- Most control but most work

**Examples:**
- AWS EC2, Google Compute Engine, Azure VMs

**Best for:**
- Large enterprises
- Custom infrastructure needs
- Teams with DevOps expertise

---

#### 3. Container Hosting

**What it is:**
- Specialized for Docker containers
- You provide Docker image
- Platform runs containers at scale

**Examples:**
- Fly.io, Google Cloud Run, AWS ECS

**Best for:**
- Containerized applications
- Microservices
- Applications needing auto-scaling

---

### Hosting Your Code vs Database

**Option 1: All-in-One Platform**
- Host code AND database on same platform
- Example: Render (app + PostgreSQL database)
- ✅ Simple, one platform to manage
- ❌ Vendor lock-in

**Option 2: Separate Platforms**
- Host code on one platform (Render)
- Host database on another (AWS RDS, Supabase)
- ✅ Best tool for each job
- ❌ More complex to manage

**Option 3: Self-Hosted Database**
- Host code on cloud platform
- Run database on your own server
- ✅ Full control over data
- ❌ You manage backups, security, scaling

**For this course:** We'll use all-in-one platforms (Render) for simplicity.

---

## Part 2 - Comparing Hosting Platforms

Let's compare four popular hosting platforms for containerized applications:

### Platform Overview

| Platform | Type | Best For | Free Tier | Database Included | Difficulty |
|----------|------|----------|-----------|-------------------|------------|
| **Render** | PaaS | Web apps, APIs | 750 hours/month | PostgreSQL (free) | Easy |
| **Railway** | PaaS | Rapid prototyping | $5 credit/month | PostgreSQL (paid) | Easy |
| **Fly.io** | Container | Edge computing | 3 VMs free | PostgreSQL (paid) | Medium |
| **Heroku** | PaaS | Legacy/established apps | None (paid only) | PostgreSQL (paid) | Easy |

---

### Detailed Comparison

#### 1. Render (Recommended for This Course)

**✅ Pros:**
- Generous free tier (750 hours/month for web services)
- Free PostgreSQL database included
- Easy Docker deployment
- Auto-deploy from GitHub/GitLab
- Free SSL certificates
- Good documentation
- No credit card required for free tier

**❌ Cons:**
- Free tier apps "sleep" after 15 minutes of inactivity
- Cold starts take 30-60 seconds
- Limited to 512MB RAM on free tier
- Slower than paid tiers

**Free Tier Details:**
- **Web Service:** 750 hours/month
- **PostgreSQL:** 90 days free, then expires (need to recreate)
- **Bandwidth:** 100GB/month
- **Builds:** Unlimited

**Best Use Cases:**
- Student projects and learning
- Small web applications
- APIs with moderate traffic
- Apps that can tolerate cold starts

**Pricing (if you upgrade):**
- Starter: $7/month (always-on, no cold starts)
- Standard: $25/month (more resources)

---

#### 2. Railway

**✅ Pros:**
- Very easy to use (similar to Heroku)
- Deploy from GitHub with one click
- Built-in database templates
- Nice dashboard and logs
- Fast deployments
- $5 free credit every month

**❌ Cons:**
- $5 credit runs out quickly with database
- Requires credit card even for free tier
- More expensive than Render for paid plans
- Less generous free tier

**Free Tier Details:**
- **Credit:** $5/month (resets monthly)
- **Database:** Counts against $5 credit
- **Note:** $5 lasts ~5-10 days with app + database

**Best Use Cases:**
- Quick prototypes
- Hackathon projects
- Short-term demos

**Pricing:**
- Pay-as-you-go after $5 credit
- Typically $10-20/month for app + database

---

#### 3. Fly.io

**✅ Pros:**
- Apps run close to users (edge computing)
- Fast performance globally
- Good for microservices
- Powerful CLI tool
- Free tier includes 3 VMs
- True always-on (no sleeping)

**❌ Cons:**
- Steeper learning curve
- Configuration more complex
- Database costs extra ($2/month minimum)
- Requires credit card
- Less beginner-friendly

**Free Tier Details:**
- **VMs:** Up to 3 shared-cpu-1x (256MB RAM each)
- **Bandwidth:** 160GB outbound
- **Storage:** 3GB persistent volume
- **Database:** NOT included (costs extra)

**Best Use Cases:**
- Global applications
- Microservices architecture
- Apps needing low latency
- Teams comfortable with CLI

**Pricing:**
- Database: $2-10/month
- Additional VMs: $2-7/month

---

#### 4. Heroku (Reference Only - No Free Tier)

**✅ Pros:**
- Most mature PaaS (15+ years)
- Huge ecosystem of add-ons
- Excellent documentation
- Very reliable
- Used by many companies

**❌ Cons:**
- **No free tier** (removed in 2022)
- Most expensive option
- Basic plan: $5-7/month per app
- Database: $5+/month

**Why mention it?**
- You'll see it in many tutorials and job descriptions
- Good to know it exists
- Understanding alternatives is important

**Pricing:**
- Basic App: $7/month
- PostgreSQL: $5/month (mini plan)
- Total: ~$12/month minimum

**Many developers moved to Render when Heroku removed free tier!**

---

### Quick Comparison Table

| Feature | Render | Railway | Fly.io | Heroku |
|---------|--------|---------|--------|--------|
| **Setup Time** | 10 minutes | 5 minutes | 15 minutes | 10 minutes |
| **Free Database** | Yes (PostgreSQL) | No | No | No |
| **Credit Card Required** | No | Yes | Yes | Yes |
| **Cold Starts** | Yes (free tier) | No | No | N/A |
| **Always-On (Free)** | No | Yes ($5 credit) | Yes | No free tier |
| **Best For** | Learning, small apps | Prototypes | Production apps | Enterprise |
| **Learning Curve** | Easy | Easy | Medium | Easy |
| **Monthly Cost (Free)** | $0 | $0 (5-10 days) | $0 (no DB) | N/A |

---

## Part 3 - Deploying to Render (Demo)

**Note:** This is an **instructor-led demonstration**. You will observe the deployment process, not do it yourself today.

**Why observation-only?**
- You haven't learned Continuous Deployment (CD) yet
- Manual deployment is for understanding the process
- In Lesson 12, you'll deploy properly using automated CI/CD pipelines
- Today's focus: Understanding hosting platform options and comparison
- Lesson 12's focus: Hands-on automated deployment of your devops-demo project

### Demo Application

We'll use the same **hello-cicd-app** from Lesson 9:
- Simple Spring Boot application
- One `/hello` endpoint
- Already containerized (Dockerfile exists)
- Docker image on Docker Hub

---

### Step 1: Prepare the Application

**What we already have from Lesson 9:**
- ✅ Spring Boot app with `/hello` endpoint
- ✅ Dockerfile (multi-stage build)
- ✅ Docker image on Docker Hub: `username/hello-cicd-app:latest`

**No changes needed!** We'll use the existing Docker image.

---

### Step 2: Create a Render Account

**Instructor will demonstrate:**

1. Go to [https://render.com](https://render.com)
2. Click **"Get Started for Free"**
3. Sign up with GitHub or Email
4. No credit card required!
5. Verify email address

**Dashboard Overview:**
- Services: Your deployed applications
- Databases: PostgreSQL instances
- Static Sites: For frontend apps
- Environment Groups: Shared environment variables

---

### Step 3: Deploy from Docker Hub

**Render supports multiple deployment methods:**
- From GitHub/GitLab repository (with Dockerfile)
- From Docker Hub (pre-built image)
- From Docker registry

**We'll use Docker Hub method** (fastest for demo).

**Instructor will demonstrate:**

1. **Click "New +" → "Web Service"**

2. **Choose "Deploy an existing image from a registry"**

3. **Enter Docker image details:**
   ```
   Image URL: docker.io/username/hello-cicd-app:latest
   ```
   (Replace `username` with actual Docker Hub username)

4. **Configure the service:**
   - **Name:** `hello-cicd-demo`
   - **Region:** Choose closest to you (e.g., Singapore, Frankfurt, Oregon)
   - **Instance Type:** Free
   - **Environment Variables:** None needed for this simple app

5. **Advanced Settings:**
   - **Port:** `8080` (Spring Boot default)
   - **Health Check Path:** `/hello` (optional but recommended)

6. **Click "Create Web Service"**

---

### Step 4: Watch Deployment Progress

**Render will now:**
1. Pull the Docker image from Docker Hub
2. Start the container
3. Expose it on a public URL
4. Assign SSL certificate (HTTPS)

**Deployment takes 2-3 minutes.**

**You'll see logs:**
```
==> Pulling image from docker.io/username/hello-cicd-app:latest
==> Image pulled successfully
==> Starting service
==> Health check passed
==> Your service is live 🎉
```

**Render provides a URL:**
```
https://hello-cicd-demo.onrender.com
```

---

### Step 5: Test the Application

**Instructor will demonstrate:**

1. **Open the Render URL in browser:**
   ```
   https://hello-cicd-demo.onrender.com/hello
   ```

2. **You should see:**
   ```
   Hello from GitLab CI/CD Demo!
   ```

3. **Success!** The application is now running on Render.

---

### Step 6: Understanding Render Features

**Logs:**
- Click "Logs" tab to see application output
- Real-time logs (like `docker logs`)
- Useful for debugging

**Metrics:**
- CPU usage
- Memory usage
- Request count
- Response times

**Settings:**
- Environment variables
- Auto-deploy on Docker Hub updates
- Health checks
- Custom domains

**Shell Access:**
- Click "Shell" to access container
- Run commands inside the running container
- Useful for debugging

---

### Step 7: Important Notes About Free Tier

**Cold Starts:**
- Free tier services "sleep" after 15 minutes of inactivity
- First request after sleep takes 30-60 seconds to wake up
- Subsequent requests are fast

**How to avoid cold starts?**
- Upgrade to paid plan ($7/month)
- Or: Keep app awake with a ping service (external)

**Why does Render do this?**
- Saves resources
- Prevents abuse of free tier
- Encourages users to upgrade for production apps

---

## Part 4 - Hosting Databases

### Database Hosting Options

**Option 1: Same Platform as Code**
- Render provides free PostgreSQL database
- Automatically connects to your app
- ✅ Simple, one dashboard
- ❌ Both sleep together on free tier

**Option 2: Specialized Database Services**
- **Supabase:** Free PostgreSQL (500MB, always-on)
- **ElephantSQL:** Free PostgreSQL (20MB, deprecated soon)
- **PlanetScale:** Free MySQL (5GB)
- **MongoDB Atlas:** Free MongoDB (512MB)
- ✅ Database stays online even if app sleeps
- ❌ Need to manage connection strings

**Option 3: Cloud Provider Databases**
- **AWS RDS:** PostgreSQL, MySQL (no free tier)
- **Google Cloud SQL:** PostgreSQL, MySQL (no free tier)
- **Azure Database:** PostgreSQL, MySQL (no free tier)
- ✅ Production-grade, scalable
- ❌ Expensive, complex

---

### Render Database Demo (Quick Overview)

**Instructor will demonstrate:**

1. **Click "New +" → "PostgreSQL"**

2. **Configure database:**
   - **Name:** `hello-db`
   - **Database:** `hellodb`
   - **User:** `hello_user`
   - **Region:** Same as your app
   - **Plan:** Free

3. **Click "Create Database"**

4. **Render provides connection details:**
   ```
   Internal Database URL: postgresql://hello_user:password@dpg-xxxxx/hellodb
   External Database URL: postgresql://hello_user:password@oregon-postgres.render.com/hellodb
   ```

5. **Use Internal URL** if app is on same Render account (faster, no internet)

**Note:** Free database expires after 90 days. You'll need to recreate it (or upgrade to paid).

---

### Connecting App to Database

**Add environment variable to your app:**

1. Go to your web service → "Environment"
2. Add variable:
   ```
   Key: DATABASE_URL
   Value: <Internal Database URL from database>
   ```
3. Save changes
4. App auto-redeploys with new environment variable

**In Spring Boot application:**
```properties
spring.datasource.url=${DATABASE_URL}
```

**We'll do this in future lessons with devops-demo project!**

---

## Part 5 - Hands-On Activity: Platform Selection

**Time:** 15 minutes  
**Format:** Small groups (3-4 students)

### Instructions

You will receive 4 hosting scenario cards. For each scenario:
1. Read the requirements
2. Discuss which hosting platform fits best
3. Justify your choice with 2-3 reasons

---

### Scenario 1: Student Portfolio Project

**Project:** Personal portfolio website with blog  
**Tech Stack:** React frontend, Spring Boot backend, PostgreSQL  
**Requirements:**
- Learning project (not production)
- Budget: $0
- Need both app and database
- Okay with cold starts
- Want to learn deployment

**Question:** Which platform should you use?

<details>
<summary>Suggested Answer</summary>

**Best Choice:** Render

**Reasons:**
1. Free tier includes both app and PostgreSQL database
2. No credit card required
3. Easy to learn and use
4. Perfect for student projects
5. Cold starts acceptable for portfolio site
6. Can upgrade later if project grows

</details>

---

### Scenario 2: Weekend Hackathon

**Project:** AI chatbot for event  
**Tech Stack:** Python backend, Redis cache, PostgreSQL  
**Requirements:**
- Need to deploy in 2 days
- Show to judges (one weekend)
- Budget: $10
- Speed of deployment more important than cost
- Needs to be online 48 hours only

**Question:** Which platform should you use?

<details>
<summary>Suggested Answer</summary>

**Best Choice:** Railway

**Reasons:**
1. Fastest deployment (one-click from GitHub)
2. $5/month credit is enough for 48 hours
3. Easy to add Redis and PostgreSQL templates
4. No cold starts with paid credit
5. Clean dashboard to show judges
6. Can delete after hackathon

</details>

---

### Scenario 3: Side Project Going Viral

**Project:** URL shortener app  
**Tech Stack:** Node.js backend, Redis, PostgreSQL  
**Requirements:**
- Started as hobby, now has 10,000 users
- Users in USA, Europe, Asia
- Need fast response times globally
- Budget: $20-30/month
- Can handle some DevOps complexity

**Question:** Which platform should you use?

<details>
<summary>Suggested Answer</summary>

**Best Choice:** Fly.io

**Reasons:**
1. Edge computing = fast globally
2. Can deploy to multiple regions
3. No cold starts even on free tier
4. $20-30/month budget covers app + database
5. Better performance for viral traffic
6. Scales well as users grow

</details>

---

### Scenario 4: Corporate Application

**Project:** Internal employee management system  
**Tech Stack:** Java Spring Boot, PostgreSQL, Redis  
**Requirements:**
- 500 employees using daily
- Must be reliable (no downtime)
- Company has IT budget ($200/month)
- Needs to integrate with existing systems
- Security and compliance important
- Team has DevOps engineer

**Question:** Which platform should you use?

<details>
<summary>Suggested Answer</summary>

**Best Choice:** Heroku or AWS (IaaS)

**Reasons:**
1. Budget allows paid solutions
2. Heroku: Reliable, mature, many add-ons
3. AWS: Full control for security/compliance
4. Free tiers not suitable for 500 users
5. Need production-grade reliability
6. Company can afford best solution

**Alternative:** Could also use Render paid tier ($25-50/month) if simpler needs.

</details>

---

## Part 6 - Deployment Best Practices

### Before Deploying to Production

**1. Environment Variables:**
- Never hardcode secrets in code
- Use environment variables for:
  - Database URLs
  - API keys
  - Secret tokens
- Example: `DATABASE_URL`, `JWT_SECRET`

**2. Health Checks:**
- Add a `/health` endpoint
- Returns 200 OK if app is healthy
- Platforms use this to verify app is running

**3. Logging:**
- Log to stdout/stderr (not files)
- Platforms capture these logs
- Makes debugging easier

**4. Resource Limits:**
- Understand platform limits (RAM, CPU)
- Optimize app to fit free tier
- Monitor usage in dashboard

**5. Database Migrations:**
- Plan how to run migrations
- Some platforms auto-run on deploy
- Others need manual trigger

---

### Common Deployment Issues

**Issue 1: App doesn't start**
- Check logs for errors
- Verify environment variables are set
- Ensure port is correct (Render uses `PORT` env variable)

**Issue 2: Database connection fails**
- Verify DATABASE_URL is correct
- Check firewall rules
- Ensure database is in same region

**Issue 3: Slow response times**
- Cold starts on free tier (expected)
- Upgrade to paid tier
- Or: Optimize code

**Issue 4: App runs locally but not on platform**
- Check Java/Node version compatibility
- Verify all dependencies are in pom.xml/package.json
- Review build logs for errors

---

## Summary

### What You Learned

1. ✅ Different types of hosting (PaaS, IaaS, Container)
2. ✅ Comparison of Render, Railway, Fly.io, and Heroku
3. ✅ How to deploy a Docker image to Render
4. ✅ Database hosting options
5. ✅ When to use which platform based on requirements

### Key Takeaways

**1. Choose platforms based on needs:**
- Learning/Student projects → Render (free)
- Quick prototypes → Railway ($5 credit)
- Production apps → Fly.io or Heroku
- Enterprise → AWS/Azure/Google Cloud

**2. Free tiers have trade-offs:**
- Cold starts
- Limited resources
- Time/credit limits
- Good for learning, not production

**3. Start simple, scale later:**
- Begin with all-in-one platforms (Render)
- Move to specialized services as you grow
- Don't over-engineer early

**4. Manual deployment teaches concepts:**
- In Lesson 12, we'll automate this with CI/CD
- Understanding manual process helps debug automation

---

## Next Steps

**In Lesson 12 (Continuous Deployment):**
- Automate deployment using CircleCI
- Deploy the full **devops-demo project** (with database)
- Set up automatic deployments on code push
- Use Docker Compose for local development
- Deploy to Render with PostgreSQL

**For now:**
- Explore Render dashboard on your own
- Try creating a free account
- Read Render documentation
- Think about your own projects

---

## Additional Resources

### Platform Documentation
- [Render Docs](https://render.com/docs)
- [Railway Docs](https://docs.railway.app/)
- [Fly.io Docs](https://fly.io/docs/)
- [Heroku Docs](https://devcenter.heroku.com/)

### Database Services
- [Supabase](https://supabase.com/) - Free PostgreSQL
- [PlanetScale](https://planetscale.com/) - Free MySQL
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) - Free MongoDB

### Comparison Articles
- [Heroku Alternatives 2024](https://dev.to/render/heroku-alternatives-in-2024-2g5a)
- [Render vs Railway vs Fly.io](https://www.reddit.com/r/webdev/comments/10k5gxz/render_vs_railway_vs_flyio/)

### Video Tutorials
- [Deploy Spring Boot to Render](https://www.youtube.com/results?search_query=deploy+spring+boot+to+render)
- [Docker Deployment Guide](https://www.youtube.com/results?search_query=docker+deployment+guide)

---

## Glossary

**PaaS (Platform as a Service):** Cloud platform where you deploy code and the platform manages infrastructure

**IaaS (Infrastructure as a Service):** Cloud platform where you rent virtual machines and manage everything yourself

**Cold Start:** Delay when a sleeping free-tier app wakes up on first request

**Health Check:** Endpoint that platforms ping to verify app is running (e.g., `/health`)

**Environment Variable:** Configuration value stored outside code (e.g., database URL, API keys)

**SSL Certificate:** Security certificate for HTTPS (Render provides free)

**Region:** Geographic location where app runs (affects latency)

**Edge Computing:** Running apps close to users globally for low latency

---

**End of Lesson 10**

**Great job!** You now understand different hosting platforms and how to deploy applications manually. In Lesson 12, you'll automate this process with Continuous Deployment!