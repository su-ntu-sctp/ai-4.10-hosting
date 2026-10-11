# Lesson 4.10: Hosting Options - Manual Hosting

## Learning Objectives

By the end of this lesson, you will be able to:
1. **Identify** different hosting options for both codebase and database
2. **Compare** and contrast different hosting platforms
3. **Select** the appropriate hosting platform based on project requirements
4. **Distinguish** between PaaS, IaaS, and container hosting
5. **Deploy** a containerized application and a PostgreSQL database to Railway, starting from a Docker Hub image

---

## Prerequisites

Before starting this lesson, you should have:
- Completed Lesson 4.9 (CI/CD Tools)
- Understanding of Docker and containerization
- Familiarity with Docker Hub (pushing and pulling images)
- Basic knowledge of CI/CD pipelines
- Completed Lesson 4.6 (Docker Compose) - today you deploy that version of devops-demo with PostgreSQL
- Docker running on your computer and a Docker Hub account

---

## Introduction

**Key Questions:**
- Where can you host your application?
- What are the different types of hosting platforms?
- How do you choose the right hosting platform?
- What about databases?

In this lesson, we'll explore different hosting options and you'll deploy your **devops-demo** application and a PostgreSQL database to Railway yourself, starting from a Docker Hub image. In Lesson 4.12, you'll deploy to Railway again - this time directly from GitHub - and automate the process.

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
| **Railway** | PaaS | Rapid prototyping | $5 one-time trial credit (30 days), then $1 free credit/month ongoing | PostgreSQL (paid) | Easy |
| **Render** | PaaS | Web apps, APIs | 750 hours/month | PostgreSQL (free, 30 days) | Easy |
| **Fly.io** | Container | Edge computing | No free tier for new accounts (removed 2024) | PostgreSQL (paid) | Medium |
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
- New accounts get a one-time $5 trial credit, no credit card required to start
- No cold starts (always-on)
- Great for learning and prototyping

**❌ Cons:**
- The $5 trial credit is one-time (valid 30 days or until spent), not a recurring monthly amount
- After the trial, the ongoing Free plan only includes $1 of credit per month
- More expensive than Render if your project outgrows the Free plan's limits (1 replica, 0.5GB RAM)
- Trial database/volume data is deleted 30 days after the trial credit expires unless you upgrade

**Free Tier Details:**
- **Trial (new accounts):** One-time $5 credit, valid for 30 days or until spent, whichever comes first. No credit card required to start.
- **After the Trial:** Railway automatically moves your account to the ongoing **Free plan** — $0/month subscription with $1 of free credit per month (does not roll over)
- **Database:** Counts against your Trial/Free plan credit
- **App hosting:** Counts against your Trial/Free plan credit
- **Note:** Great for learning — the Trial comfortably covers your first 1-2 weeks of experimentation, and the Free plan afterward keeps a small always-on app running at no ongoing cost, just with tighter resource limits (1 replica, 0.5GB RAM, 1 vCPU)

**Best Use Cases:**
- Student projects and learning (our use case!)
- Quick prototypes
- Hackathon projects
- Short-term demos
- Testing deployment workflows

**Pricing:**
- Trial: Free (one-time $5 credit, 30 days)
- Free plan (ongoing, automatic after trial): $0/month, $1 credit/month included
- Hobby plan (optional upgrade for more resources): $5/month minimum subscription, includes $5 usage credit
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
- **PostgreSQL:** Free for 30 days, then a 14-day grace period before the database and its data are deleted (changed from 90 days in May 2024)
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
- True always-on (no sleeping)

**❌ Cons:**
- Steeper learning curve
- Configuration more complex
- Database costs extra ($2/month minimum)
- Requires credit card
- Less beginner-friendly
- **Fly.io removed its free tier for new signups in 2024** — new accounts get only a short trial before billing starts; the free VMs described below now apply only to legacy accounts created before the change

**Free Tier Details (legacy accounts only — see note above):**
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
|---------|----------|--------------|---------|--------------|
| **Setup Time** | 2 minutes | 10 minutes | 15 minutes | 10 minutes |
| **Free Database** | No (paid) | Yes (PostgreSQL) | No | No |
| **Credit Card Required** | No | No | Yes | Yes |
| **Cold Starts** | No | Yes (free tier) | No | N/A |
| **Always-On (Free)** | Yes (Trial, then ongoing Free plan) | No | N/A (no free tier for new accounts) | No free tier |
| **Best For** | Learning, prototypes | Small apps | Production apps | Enterprise |
| **Learning Curve** | Very Easy | Easy | Medium | Easy |
| **Monthly Cost (Free)** | $0 (Trial 30 days, then $1 credit/mo ongoing) | $0 | N/A (no free tier for new signups) | N/A |

---

### 🏃 Activity 1 — Platform Matching Discussion (10 min)

Based on what you've just read, discuss the following with a partner:

1. A solo developer wants to deploy a Spring Boot app over a weekend to show a client. They have no budget. Which platform would you recommend and why?
2. A startup has 5,000 users across Asia and Europe and needs fast response times globally. Which platform makes the most sense?
3. Looking at the comparison table — why do you think Heroku lost so many users when they removed their free tier in 2022?

> **Key takeaway:** Free tiers are great for learning but always understand the limitations before committing to a platform.

---

## Part 3 - Hands-On: Deploy devops-demo to Railway from Docker Hub

In Parts 3 and 4, **you** will deploy your own **devops-demo** application to Railway from a Docker image on Docker Hub, then connect it to a PostgreSQL database hosted on Railway.

### Two Ways to Deploy to Railway

Railway can deploy your app in two ways. You will practise both in this module:

| | Deploy from Docker Hub (today, Lesson 4.10) | Deploy from GitHub (Lesson 4.12) |
|---|---|---|
| **What Railway uses** | A ready-made image on Docker Hub | Your source code and `Dockerfile` on GitHub |
| **Who builds the image** | You (or a CI pipeline), before deploying | Railway builds it from your `Dockerfile` |
| **How it updates** | Redeploy when a new image is pushed | Redeploys automatically on every push |

> **Why both?** Your **module assignment** asks you to deploy to Railway, so it pays to know both ways. Today you deploy a pre-built image from Docker Hub. In **Lesson 4.12**, you will deploy to Railway again, but this time **directly from GitHub**.

```
Your computer                 Docker Hub                            Railway
docker build + push  ───►  YOUR_USERNAME/devops-demo:4.6.3  ───►  devops-demo service  ───►  Public URL
                                                                        │
                                                                   PostgreSQL (Part 4)
```

---

### Step 1: Build and Push the devops-demo Image

We'll use the version of devops-demo from **Lesson 4.6 (Docker Compose)** - tag `v4.6.3`. This version:
- Connects to **PostgreSQL** using environment variables (`SPRING_DATASOURCE_URL`, `SPRING_DATASOURCE_USERNAME`, `SPRING_DATASOURCE_PASSWORD`)
- Has a **multi-stage Dockerfile** that builds the JAR inside Docker - no `mvn` needed on your computer

For Windows users, use the WSL terminal only. For macOS users, use your preferred terminal.

**1.1: Download the project**

```sh
cd ~
cd playground
curl -L -O https://github.com/aie-devops/devops-demo/archive/refs/tags/v4.6.3.zip
unzip v4.6.3.zip
cd devops-demo-4.6.3
```

**1.2: Build and push the image** (replace `YOUR_DOCKERHUB_USERNAME`)

```sh
docker login
docker build --platform linux/amd64 -t YOUR_DOCKERHUB_USERNAME/devops-demo:4.6.3 .
docker push YOUR_DOCKERHUB_USERNAME/devops-demo:4.6.3
```

The build takes a few minutes the first time while Maven downloads dependencies.

> **Why `--platform linux/amd64`?** Railway runs on `linux/amd64` servers. If you build on an Apple Silicon Mac (M1/M2/M3/M4) without this flag, the image is built for ARM and will crash on Railway with `exec format error`. On Apple Silicon, this build is slower because Docker emulates `amd64`.

> **Why the tag `4.6.3` and not `latest`?** Your `latest` tag holds the image your CI pipeline published in Lesson 4.7 / 4.9 (no database). Using a separate tag keeps the two images apart.

**1.3: Check Docker Hub**

1. Go to [https://hub.docker.com](https://hub.docker.com) and open your `devops-demo` repository
2. Check that the `4.6.3` tag is there
3. Check that the repository is **Public** (Railway can't pull private images without extra setup)

---

### Step 2: Create a Railway Account

1. Go to [https://railway.app](https://railway.app)
2. Click **"Login"** or **"Start a New Project"**
3. Sign up with **GitHub** (recommended)
4. Verify your email if prompted

**Dashboard Overview:**
- **Projects:** Collections of related services (your app and its database live in one project)
- **Services:** Individual applications or databases
- **Deployment logs:** Shown in real time

> Keep this account - you will use it again in Lesson 4.12 and for your module assignment.

---

### Step 3: Deploy from Docker Hub

**3.1: Start a New Project**

1. Click **"Start a New Project"** (or "New Project")
2. Select **"Deploy from Docker Image"**

**3.2: Enter Your Docker Image**

3. In the dialog, enter your image name:
   ```
   YOUR_DOCKERHUB_USERNAME/devops-demo:4.6.3
   ```
   (No `docker.io/` prefix needed)

4. Click **"Deploy"**

Railway pulls your image from Docker Hub and starts the container.

---

### Step 4: Claim the Project and Generate a Domain

**4.1: Claim the Project**

If you see a warning that the project is temporary and will be deleted, click **"Claim Project"** (top right) to make it permanent.

**4.2: Generate a Public Domain**

1. Click the **devops-demo** service in the project view
2. Click the **"Settings"** tab
3. Scroll down to the **"Networking"** section
4. Under **"Public Networking"**, click **"Generate Domain"**
5. In the dialog:
   - **Port:** Enter `8080` (Spring Boot default port)
   - Click **"Generate Domain"**

Railway assigns a URL like:
```
https://devops-demo-production.up.railway.app
```

---

### Step 5: Read the Deployment Logs - Expect a Crash!

Click the **"Deployments"** tab, then click the latest deployment to see its logs.

**This deployment will crash - and that's expected.** Look for an error like this in the logs:

```
Could not resolve placeholder 'SPRING_DATASOURCE_URL' in value "${SPRING_DATASOURCE_URL}"
```

**Why?** This version of devops-demo needs a PostgreSQL database. In Lesson 4.6, Docker Compose gave the app its database settings through environment variables. On Railway, nothing has set `SPRING_DATASOURCE_URL` yet, so the app can't start.

> **Reading the logs is the first step of every deployment fix.** You'll give the app a database in Part 4.

---

### Step 6: Explore Railway's Features

While your app waits for its database, explore your service:

**Deployments:**
- History of every deployment, each with its own logs
- Redeploy or roll back to a previous version

**Variables:**
- Environment variables for database URLs, API keys and other settings
- Changing a variable triggers a new deployment (you'll use this in Part 4)

**Metrics:**
- CPU, memory and network usage

**Settings:**
- Source image, networking (domains), and deploy settings

---

### Step 7: Troubleshooting

**Issue 1: `exec format error` in the logs**

**Cause:** The image was built for ARM (Apple Silicon Mac) instead of `linux/amd64`

**Solution:** Rebuild with `docker build --platform linux/amd64 ...`, push again (Step 1.2), then click **"Redeploy"** in Railway.

**Issue 2: "Image not found" error**

**Cause:** The image name or tag is incorrect, or the image isn't on Docker Hub

**Solution:**
1. Check the image and the `4.6.3` tag exist on [Docker Hub](https://hub.docker.com)
2. Check the name format: `username/devops-demo:4.6.3`
3. Make sure the repository is **Public**
4. Don't add a `docker.io/` prefix

**Issue 3: Can't access the app via the URL**

**Cause:** The app isn't running yet, the domain isn't generated, or the port is wrong

**Solution:**
1. Until you finish Part 4, the app crashes - this is expected
2. Go to **Settings → Networking** and check a domain exists with port `8080`

---

## Part 4 - Hosting Databases

### Database Hosting Options

**Option 1: Same Platform as Your App**
- Railway, Render and similar platforms can host PostgreSQL, MySQL, MongoDB and Redis next to your app
- ✅ Simple - one dashboard, one project
- ✅ Fast, private networking between app and database

**Option 2: Specialized Database Services**
- Managed database providers, e.g. **Supabase** (PostgreSQL), **MongoDB Atlas** (MongoDB)
- ✅ Database is managed separately from where the app runs
- ❌ You manage connection strings across two providers
- ❌ Traffic goes over the public internet (slightly slower)

**Option 3: Cloud Provider Databases**
- **AWS RDS**, **Google Cloud SQL**, **Azure Database** (PostgreSQL, MySQL)
- ✅ Production-grade, highly scalable
- ❌ More complex to set up and run

---

### Hands-On: Add PostgreSQL to Your Railway Project

You'll now give devops-demo the database it needs, in the **same Railway project**.

```
Railway project
┌──────────────────────────────────────────────────────────┐
│                                                          │
│   devops-demo  ───── private network ─────►  Postgres    │
│   (Docker Hub image)                         (database)  │
│                                                          │
└──────────────────────────────────────────────────────────┘
        ▲
   Public URL (/hello)
```

---

### Step 1: Add a PostgreSQL Database

1. In your project, click **"New"** (or **"+ Create"**)
2. Select **"Database"** → **"Add PostgreSQL"**

Railway creates a new **Postgres** service in your project. It's ready in less than a minute.

---

### Step 2: Look at the Database Variables

1. Click the **Postgres** service
2. Open the **"Variables"** tab

Railway created the connection details as variables, including:

| Variable | Example value |
|---|---|
| `PGHOST` | `postgres.railway.internal` |
| `PGPORT` | `5432` |
| `PGUSER` | `postgres` |
| `PGPASSWORD` | `<generated-password>` |
| `PGDATABASE` | `railway` |
| `DATABASE_URL` | `postgresql://postgres:<password>@postgres.railway.internal:5432/railway` |

> **Important:** `DATABASE_URL` is **not** in the format Spring Boot needs. Spring Boot needs a **JDBC URL** that starts with `jdbc:postgresql://` and has no username or password in it. So we build our own URL from the individual variables in the next step.

---

### Step 3: Connect devops-demo to the Database

Give devops-demo the same three environment variables Docker Compose gave it in Lesson 4.6 - this time pointing at Railway's database.

1. Click the **devops-demo** service
2. Open the **"Variables"** tab
3. Click **"New Variable"** and add each of these (copy them exactly):

| Variable | Value |
|---|---|
| `SPRING_DATASOURCE_URL` | `jdbc:postgresql://${{Postgres.PGHOST}}:${{Postgres.PGPORT}}/${{Postgres.PGDATABASE}}` |
| `SPRING_DATASOURCE_USERNAME` | `${{Postgres.PGUSER}}` |
| `SPRING_DATASOURCE_PASSWORD` | `${{Postgres.PGPASSWORD}}` |

**What is `${{Postgres.PGHOST}}`?** It's a **reference variable**. Railway replaces it with the value of `PGHOST` from the service called **Postgres**. If Railway rotates the password or you rename the database, your app picks up the new values automatically. No passwords are copied by hand.

**Compare with Lesson 4.6:**

| | Docker Compose (Lesson 4.6) | Railway (today) |
|---|---|---|
| Database host | `db` (service name) | `postgres.railway.internal` (private network) |
| Where variables live | `environment:` in `compose.yaml` | **Variables** tab of the service |
| Password | Written in `compose.yaml` | Generated by Railway and referenced |

---

### Step 4: Deploy and Check the Logs

1. If Railway shows a banner with your pending changes, click **"Deploy"** (or **"Apply changes"**). Otherwise, the new variables trigger a deployment automatically.
2. Open the **"Deployments"** tab and click the new deployment
3. This time the logs should show the app connecting to the database and starting:

```
HikariPool-1 - Starting...
HikariPool-1 - Added connection org.postgresql.jdbc.PgConnection@...
HikariPool-1 - Start completed.
Tomcat started on port 8080 (http) with context path '/'
Started DevopsDemoApplication in 6.1 seconds
```

`HikariPool-1 - Start completed` means Spring Boot connected to your Railway PostgreSQL database. ✅

---

### Step 5: Test Your Application

1. Copy your Railway URL (from **Settings → Networking**)
2. Add `/hello` to the end of it and open it in your browser, or use curl:
   ```bash
   curl https://YOUR-RAILWAY-URL.up.railway.app/hello
   ```
3. You should see:
   ```
   DevOps demo - now on Docker Hub!
   ```

**Success!** Your devops-demo app and its PostgreSQL database are both running on Railway. 🎉

---

### Step 6: Troubleshooting

**Issue 1: `'url' must start with "jdbc"`**

**Cause:** `SPRING_DATASOURCE_URL` is set to `DATABASE_URL` (or another `postgresql://...` URL)

**Solution:** Use the JDBC URL from Step 3: `jdbc:postgresql://${{Postgres.PGHOST}}:${{Postgres.PGPORT}}/${{Postgres.PGDATABASE}}`

**Issue 2: `UnknownHostException: postgres.railway.internal` or "Connection refused"**

**Cause:** The app can't reach the database over the private network

**Solution:**
1. Check the app and the database are in the **same project** (and the same environment)
2. Check the database service is called **Postgres** - the name in `${{Postgres.PGHOST}}` must match the service name exactly
3. Check the Postgres service is running (green), then redeploy devops-demo

**Issue 3: `password authentication failed for user "postgres"`**

**Cause:** The username or password variable is wrong

**Solution:** Check `SPRING_DATASOURCE_USERNAME` is `${{Postgres.PGUSER}}` and `SPRING_DATASOURCE_PASSWORD` is `${{Postgres.PGPASSWORD}}` - no extra spaces or quotes.

**Issue 4: Still `Could not resolve placeholder 'SPRING_DATASOURCE_URL'`**

**Cause:** The variables were added to the wrong service, or the changes weren't deployed

**Solution:** Add the variables to the **devops-demo** service (not Postgres), then deploy the changes.

---

### Clean Up (Optional)

Running services use your Railway usage allowance. Once you've finished testing, you can delete this project from **Project Settings → Danger → Delete Project**. In **Lesson 4.12**, you'll deploy devops-demo to Railway again - this time directly from GitHub.

---

## Part 5 - Hands-On Activity: Platform Selection

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
2. The one-time $5 trial credit covers the initial learning period (5-10 days), and the ongoing Free plan afterward keeps a small app running at no cost
3. No cold starts - always responsive
4. Beautiful dashboard for monitoring
5. Easy database integration
6. Automatically continues on the Free plan after the trial - no manual restart needed

**Alternative:** Render (if you need a database that stays free for longer than 30 days without a grace-period upgrade)

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
2. The one-time $5 trial credit is more than enough for a 48-hour hackathon
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
4. $20-30/month budget covers app + database (note: Fly.io no longer offers a free tier for new accounts, so this budget goes entirely toward paid usage from day one)
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
- Verify the JDBC URL (`SPRING_DATASOURCE_URL`) starts with `jdbc:postgresql://`
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