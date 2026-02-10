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
- Railway, Render, Heroku

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
- Example: Railway (app + PostgreSQL database)
- ✅ Simple, one platform to manage
- ❌ Vendor lock-in

**Option 2: Separate Platforms**
- Host code on one platform (Railway)
- Host database on another (AWS RDS, Supabase)
- ✅ Best tool for each job
- ❌ More complex to manage

**Option 3: Self-Hosted Database**
- Host code on cloud platform
- Run database on your own server
- ✅ Full control over data
- ❌ You manage backups, security, scaling

**For this course:** We'll use all-in-one platforms (Railway) for simplicity.

---

## Part 2 - Comparing Hosting Platforms

Let's compare four popular hosting platforms for containerized applications:

### Platform Overview

| Platform | Type | Best For | Free Tier | Database Included | Difficulty |
|----------|------|----------|-----------|-------------------|------------|
| **Railway** | PaaS | Rapid prototyping | $5 credit/month | PostgreSQL (paid) | Easy |
| **Render** | PaaS | Web apps, APIs | 750 hours/month | PostgreSQL (free) | Easy |
| **Fly.io** | Container | Edge computing | 3 VMs free | PostgreSQL (paid) | Medium |
| **Heroku** | PaaS | Legacy/established apps | None (paid only) | PostgreSQL (paid) | Easy |

---

### Detailed Comparison

#### 1. Railway (Recommended for This Course)

**✅ Pros:**
- Extremely easy to use - simplest deployment experience
- Deploy from GitHub or Docker Hub with one click
- Built-in database templates
- Beautiful dashboard and real-time logs
- Fast deployments (typically under 2 minutes)
- $5 free credit every month
- No cold starts (always-on)
- Great for learning and prototyping

**❌ Cons:**
- $5 credit runs out after 5-10 days with app + database
- Requires credit card even for free tier
- More expensive than Render for long-term paid plans
- Less generous free tier for production use

**Free Tier Details:**
- **Credit:** $5/month (resets monthly)
- **Database:** Counts against $5 credit (~$1-2/month)
- **App hosting:** Counts against $5 credit
- **Note:** Perfect for learning and short-term projects

**Best Use Cases:**
- Student projects and learning (our use case!)
- Quick prototypes
- Hackathon projects
- Short-term demos
- Testing deployment workflows

**Pricing:**
- Pay-as-you-go after $5 credit
- Typically $10-20/month for app + database
- Pro plan: $20/month with additional features

---

#### 2. Render

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
- Port configuration can be tricky for beginners

**Free Tier Details:**
- **Web Service:** 750 hours/month
- **PostgreSQL:** 90 days free, then expires (need to recreate)
- **Bandwidth:** 100GB/month
- **Builds:** Unlimited

**Best Use Cases:**
- Long-term student projects
- Small web applications
- APIs with moderate traffic
- Apps that can tolerate cold starts

**Pricing:**
- Starter: $7/month (always-on, no cold starts)
- Standard: $25/month (more resources)

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

**Many developers moved to Railway and Render when Heroku removed free tier!**

---

### Quick Comparison Table

| Feature | Railway | Render | Fly.io | Heroku |
|---------|---------|--------|--------|--------|
| **Setup Time** | 2 minutes | 10 minutes | 15 minutes | 10 minutes |
| **Free Database** | No (paid) | Yes (PostgreSQL) | No | No |
| **Credit Card Required** | Yes | No | Yes | Yes |
| **Cold Starts** | No | Yes (free tier) | No | N/A |
| **Always-On (Free)** | Yes ($5 credit) | No | Yes | No free tier |
| **Best For** | Learning, prototypes | Small apps | Production apps | Enterprise |
| **Learning Curve** | Very Easy | Easy | Medium | Easy |
| **Monthly Cost (Free)** | $0 (5-10 days) | $0 | $0 (no DB) | N/A |

---

## Part 3 - Deploying to Railway (Demo)

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
- ✅ Dockerfile (multi-stage build with correct base images)
- ✅ Docker image on Docker Hub: `username/hello-cicd-app:latest`

**Important: Verify Dockerfile is correct**

Your Dockerfile should look like this (with JDK, not JRE):

```dockerfile
# Build stage
FROM eclipse-temurin:21-jdk-alpine AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN apk add --no-cache maven
RUN mvn clean package -DskipTests

# Runtime stage - USE JDK (NOT JRE)
FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
CMD ["java", "-jar", "app.jar"]
```

**Why JDK instead of JRE?**
- JRE can cause compatibility issues on some platforms
- JDK works reliably everywhere
- Slightly larger image (~50MB) but guaranteed to work

---

### Step 2: Create a Railway Account

**Instructor will demonstrate:**

1. Go to [https://railway.app](https://railway.app)
2. Click **"Login"** or **"Start a New Project"**
3. Sign up with **GitHub** (recommended) - easiest authentication
4. **Requires credit card** (but won't charge unless you exceed $5 credit)
5. Verify email if prompted

**Dashboard Overview:**
- Projects: Collections of related services
- Services: Individual applications or databases
- Clean, modern interface
- Real-time deployment logs

---

### Step 3: Deploy from Docker Hub

**Railway supports multiple deployment methods:**
- From GitHub repository (with Dockerfile)
- From Docker Hub (pre-built image) ← We'll use this
- From Docker registry
- From templates

**We'll use Docker Hub method** (fastest for demo).

**Instructor will demonstrate:**

**3.1: Start New Project**

1. Click **"Start a New Project"** (or "New Project")
2. Select **"Deploy from Docker Image"**

**3.2: Enter Docker Image**

3. In the dialog, enter:
   ```
   sanjela/hello-cicd-app:latest
   ```
   (Replace `sanjela` with actual Docker Hub username)

4. Click **"Deploy"**

**What happens now:**
- Railway pulls the Docker image from Docker Hub
- Starts the container
- Deployment completes in ~30-60 seconds!

---

### Step 4: Claim Project and Generate Domain

**4.1: Claim the Project**

After deployment starts, you'll see a warning:
> "This is a temporary project and will be deleted in 24 hours"

1. Click **"Claim Project"** button (top right)
2. Your project is now permanent (won't be deleted)

**4.2: Generate Public Domain**

To access your app from the internet:

1. Click on the **hello-cicd-app** service (in the project view)
2. Click **"Settings"** tab at the top
3. Scroll down to **"Networking"** section
4. Under **"Public Networking"**, click **"Generate Domain"**
5. In the dialog:
   - **Port:** Enter `8080` (Spring Boot default port)
   - Click **"Generate Domain"** button

Railway assigns a URL like:
```
https://hello-cicd-app-production.up.railway.app
```

**Your app is now live!**

---

### Step 5: Watch Deployment Progress

**Railway deployment is FAST:**

**You'll see logs in real-time:**
```
==> Pulling image sanjela/hello-cicd-app:latest
==> Image pulled successfully
==> Starting container...
==> Container started

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::

Started HelloCicdAppApplication in 2.962 seconds
Tomcat started on port 8080
```

**Deployment complete!** Total time: ~1-2 minutes

---

### Step 6: Test the Application

**Instructor will demonstrate:**

1. **Copy the Railway URL** (from Settings → Networking)
2. **Add `/hello` to the URL:**
   ```
   https://hello-cicd-app-production.up.railway.app/hello
   ```

3. **Open in browser or use curl:**
   ```bash
   curl https://hello-cicd-app-production.up.railway.app/hello
   ```

4. **You should see:**
   ```
   Hello from GitLab CI/CD Demo!
   ```

**Success!** The application is now running on Railway. ✅

---

### Step 7: Understanding Railway Features

**Logs (Real-time):**
- Click "Deployments" tab to see all deployments
- Click any deployment to see logs
- Beautiful, color-coded output
- Real-time streaming (no refresh needed)

**Metrics:**
- CPU usage
- Memory usage
- Network traffic
- All visible in dashboard

**Settings:**
- Environment variables
- Custom domains
- Volume (persistent storage)
- Deploy triggers

**Variables:**
- Add environment variables for database URLs, API keys, etc.
- Easy key-value interface
- Changes trigger redeployment

**Deployments:**
- See history of all deployments
- Rollback to previous versions
- View logs for each deployment

---

### Step 8: Important Notes About Railway

**Always-On (No Cold Starts):**
- Railway apps don't sleep
- Fast response times even after inactivity
- Great user experience

**$5 Monthly Credit:**
- Free tier gives $5/month credit
- Resets on the 1st of each month
- With just this app: credit lasts ~10-15 days
- With app + database: credit lasts ~5-7 days
- **Perfect for learning and testing!**

**Usage Monitoring:**
- Check usage in project settings
- See how much credit remains
- Estimate how long it will last

**After Credit Runs Out:**
- Services automatically pause
- No charges to your card (unless you opt in)
- Can restart next month when credit resets
- Or add payment method for pay-as-you-go

---

### Step 9: Troubleshooting

**Issue 1: "Deployment failed" or "Crashed"**

**Cause:** Application not starting properly

**Solution:**
1. Click on deployment → View logs
2. Look for errors in startup logs
3. Common issues:
   - Wrong port (Railway auto-detects from EXPOSE in Dockerfile)
   - Missing dependencies
   - Java version mismatch

**Issue 2: Can't access app via URL**

**Cause:** Domain not generated or wrong port configured

**Solution:**
1. Go to Settings → Networking
2. Ensure "Public Networking" section shows a domain
3. Verify port is set to `8080`
4. Try regenerating domain if needed

**Issue 3: "Image not found" error**

**Cause:** Docker image name is incorrect or image doesn't exist on Docker Hub

**Solution:**
1. Verify image exists on Docker Hub (visit hub.docker.com)
2. Check image name format: `username/image:tag`
3. Ensure image is public (not private)
4. Image URL format is just `username/image:latest` (no `docker.io/` prefix needed)

---

## Part 4 - Hosting Databases

### Database Hosting Options

**Option 1: Same Platform as Code**
- Railway provides PostgreSQL, MySQL, MongoDB, Redis templates
- Automatically connects to your app
- ✅ Simple, one dashboard
- ✅ Fast internal networking
- ❌ Counts against your $5 credit

**Option 2: Specialized Database Services**
- **Supabase:** Free PostgreSQL (500MB, always-on)
- **PlanetScale:** Free MySQL (5GB)
- **MongoDB Atlas:** Free MongoDB (512MB)
- ✅ Database stays online even if app pauses
- ✅ Free tier doesn't expire quickly
- ❌ Need to manage connection strings
- ❌ External networking (slightly slower)

**Option 3: Cloud Provider Databases**
- **AWS RDS:** PostgreSQL, MySQL (no free tier)
- **Google Cloud SQL:** PostgreSQL, MySQL (no free tier)
- **Azure Database:** PostgreSQL, MySQL (no free tier)
- ✅ Production-grade, scalable
- ❌ Expensive, complex

---

### Railway Database Demo (Quick Overview)

**Instructor will demonstrate:**

1. **In your project, click "New"**
2. **Select "Database" → "Add PostgreSQL"**

Railway automatically:
- Creates PostgreSQL database
- Generates connection string
- Makes it available as environment variables
- Sets up internal networking

**3. Database is ready immediately!**

**Connection details** available as environment variables:
```
DATABASE_URL=postgresql://postgres:password@postgres.railway.internal:5432/railway
PGHOST=postgres.railway.internal
PGPORT=5432
PGUSER=postgres
PGPASSWORD=<generated-password>
PGDATABASE=railway
```

**4. Use in your app:**

In Spring Boot `application.properties`:
```properties
spring.datasource.url=${DATABASE_URL}
```

Railway automatically injects these variables into your app!

**Note:** Database costs ~$1-2/month from your $5 credit.

---

### Connecting App to Database

**Railway makes this incredibly simple:**

1. **Add database to same project**
2. **Railway automatically injects environment variables**
3. **App can immediately access database**

**No manual configuration needed!** Internal networking is automatic.

**In application.properties:**
```properties
spring.datasource.url=${DATABASE_URL}
spring.jpa.hibernate.ddl-auto=update
```

**That's it!** Railway handles the rest.

**We'll do this in Lesson 12 with devops-demo project!**

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
- Okay with occasional downtime
- Want to learn deployment

**Question:** Which platform should you use?

<details>
<summary>Suggested Answer</summary>

**Best Choice:** Railway

**Reasons:**
1. Extremely simple deployment - great for learning
2. $5/month credit covers learning period (5-10 days)
3. No cold starts - always responsive
4. Beautiful dashboard for monitoring
5. Easy database integration
6. Can restart next month when credit resets

**Alternative:** Render (if you need longer than 10 days on free tier)

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
1. Fastest deployment - literally 2 minutes from Docker image
2. $5/month credit perfect for 48 hours
3. Easy to add Redis and PostgreSQL templates
4. No cold starts during demo
5. Clean, impressive dashboard to show judges
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
3. No cold starts
4. $20-30/month budget covers app + database
5. Better performance for viral traffic
6. Scales well as users grow

**Why not Railway:** Railway is US-only, not ideal for global users

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

**Best Choice:** AWS (IaaS) or Heroku

**Reasons:**
1. Budget allows enterprise solutions
2. AWS: Full control for security/compliance
3. Heroku: Reliable, mature, many add-ons
4. Free tiers not suitable for 500 users
5. Need production-grade reliability
6. Company can afford best solution

**Why not Railway/Render:** Not designed for enterprise-scale applications with strict compliance needs

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
- Monitor usage in dashboard
- Optimize app if needed

**5. Database Migrations:**
- Plan how to run migrations
- Some platforms auto-run on deploy
- Others need manual trigger

---

### Common Deployment Issues

**Issue 1: App doesn't start**
- Check logs for errors
- Verify environment variables are set
- Ensure port is correct (Railway auto-detects from Dockerfile EXPOSE)

**Issue 2: Database connection fails**
- Verify DATABASE_URL is correct
- Check that database and app are in same project
- Ensure database is running

**Issue 3: Image keeps rebuilding**
- Railway caches Docker images
- Force rebuild if needed in settings
- Check Docker Hub for updated image

**Issue 4: App runs locally but not on platform**
- Check Java/Node version compatibility
- Verify all dependencies are in pom.xml/package.json
- Review build logs for errors

---

## Summary

### What You Learned

1. ✅ Different types of hosting (PaaS, IaaS, Container)
2. ✅ Comparison of Railway, Render, Fly.io, and Heroku
3. ✅ How to deploy a Docker image to Railway (hands-on demo)
4. ✅ Database hosting options
5. ✅ When to use which platform based on requirements

### Key Takeaways

**1. Choose platforms based on needs:**
- Learning/Quick prototypes → Railway (easiest, fastest)
- Long-term student projects → Render (longer free tier)
- Production apps → Fly.io (global performance)
- Enterprise → AWS/Azure/Google Cloud (full control)

**2. Free tiers have trade-offs:**
- Railway: $5 credit (5-10 days), no cold starts
- Render: Longer duration but cold starts
- Fly.io: Always-on but no database included
- Choose based on your priorities

**3. Start simple, scale later:**
- Begin with all-in-one platforms (Railway)
- Move to specialized services as you grow
- Don't over-engineer early

**4. Manual deployment teaches concepts:**
- In Lesson 12, we'll automate this with CI/CD
- Understanding manual process helps debug automation
- Railway's simplicity makes learning easier

---

## Next Steps

**In Lesson 12 (Continuous Deployment):**
- Automate deployment using CircleCI
- Deploy the full **devops-demo project** (with database)
- Set up automatic deployments on code push
- Use Docker Compose for local development
- Deploy to Railway with PostgreSQL

**For now:**
- Explore Railway dashboard on your own
- Try creating a free account
- Read Railway documentation
- Think about your own projects

---

## Additional Resources

### Platform Documentation
- [Railway Docs](https://docs.railway.app/) - Complete documentation
- [Render Docs](https://render.com/docs) - Alternative platform
- [Fly.io Docs](https://fly.io/docs/) - Advanced deployment
- [Heroku Docs](https://devcenter.heroku.com/) - Historical reference

### Database Services
- [Supabase](https://supabase.com/) - Free PostgreSQL
- [PlanetScale](https://planetscale.com/) - Free MySQL
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) - Free MongoDB

### Comparison Articles
- [Heroku Alternatives 2024](https://dev.to/render/heroku-alternatives-in-2024-2g5a)
- [Railway vs Render vs Fly.io](https://www.reddit.com/r/webdev/comments/10k5gxz/render_vs_railway_vs_flyio/)
- [Best PaaS for Students](https://dev.to/search?q=best%20paas%20for%20students)

### Video Tutorials
- [Deploy to Railway Tutorial](https://www.youtube.com/results?search_query=deploy+to+railway+tutorial)
- [Docker Deployment Guide](https://www.youtube.com/results?search_query=docker+deployment+guide)
- [Railway vs Render Comparison](https://www.youtube.com/results?search_query=railway+vs+render)

---

## Glossary

**PaaS (Platform as a Service):** Cloud platform where you deploy code and the platform manages infrastructure

**IaaS (Infrastructure as a Service):** Cloud platform where you rent virtual machines and manage everything yourself

**Cold Start:** Delay when a sleeping free-tier app wakes up on first request (Railway doesn't have this!)

**Health Check:** Endpoint that platforms ping to verify app is running (e.g., `/health`)

**Environment Variable:** Configuration value stored outside code (e.g., database URL, API keys)

**SSL Certificate:** Security certificate for HTTPS (automatically provided by Railway)

**Region:** Geographic location where app runs (affects latency)

**Edge Computing:** Running apps close to users globally for low latency

**Internal Networking:** Private network connection between services in same project (faster, more secure)

---

**End of Lesson 10**

**Great job!** You now understand different hosting platforms and how to deploy applications manually. Railway's simplicity made this much easier! In Lesson 12, you'll automate this process with Continuous Deployment!
