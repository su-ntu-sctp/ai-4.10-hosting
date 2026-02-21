# Assignment (Optional)

## Brief

Analyze different hosting platforms and make informed deployment decisions based on project requirements and constraints.

1. **Hosting Platform Comparison Matrix**
   - Create a detailed comparison table for the four hosting platforms covered: Railway, Render, Fly.io, and Heroku
   - For each platform, document:
     - **Type:** PaaS, IaaS, or Container hosting
     - **Free tier details:** What's included, limitations, expiration
     - **Database options:** What databases are available, costs
     - **Setup difficulty:** Easy, medium, or hard with brief explanation
     - **Cold starts:** Yes or No, and impact on user experience
     - **Best use cases:** List 2-3 specific scenarios where this platform excels
     - **Credit card requirement:** Yes or No
     - **Estimated monthly cost:** For a small app with database
   - Create a visual table or matrix format
   - Example:
```
     | Feature | Railway | Render | Fly.io | Heroku |
     |---------|---------|--------|--------|--------|
     | Type | PaaS | PaaS | Container | PaaS |
     | Free Tier | $5 credit/month | 750 hrs/month | 3 VMs | None |
     | ...     | ... | ... | ... | ... |
```
   - Add a concluding paragraph (3-4 sentences) recommending which platform is best for student learning projects and why

2. **Platform Selection for Real-World Scenarios**
   - Analyze and write recommendations for FOUR different scenarios below
   - For each scenario, provide:
     - Recommended hosting platform (Railway, Render, Fly.io, or other)
     - 3-4 specific reasons supporting your choice
     - Cost estimate (monthly)
     - 1-2 potential challenges or considerations
     - Brief explanation (1-2 sentences) why the other platforms would NOT be suitable
   
   **Scenario A - Learning Project:**
   - You're a student building a Spring Boot REST API with PostgreSQL
   - Need to demonstrate it to professors for grading
   - Project runs for 2 weeks during semester
   - Budget: $0 preferred, maximum $5
   - No prior deployment experience
   
   **Scenario B - Startup MVP:**
   - Building a minimum viable product for a new SaaS idea
   - Node.js backend with Redis cache and PostgreSQL
   - Need to show to potential investors
   - Expecting 100-500 users initially
   - Budget: $30/month
   - Must be reliable and always-on
   
   **Scenario C - Global Mobile App Backend:**
   - Backend API for mobile app
   - Users spread across USA, Europe, and Asia
   - Need fast response times globally
   - React Native frontend, Spring Boot backend
   - Expecting 5,000-10,000 daily active users
   - Budget: $100/month
   - Can handle medium DevOps complexity
   
   **Scenario D - Corporate Internal Tool:**
   - Internal employee directory and management system
   - 200 employees using daily during business hours
   - Java Spring Boot with PostgreSQL
   - Must comply with data privacy regulations
   - Company IT budget: $300/month
   - Requires high reliability and security

## Submission (Optional)

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.

## References
- Java: https://docs.oracle.com/javase/
- Spring Boot: https://docs.spring.io/spring-boot/docs/current/reference/html/
- PostgreSQL: https://www.postgresql.org/docs/
- OWASP: https://cheatsheetseries.owasp.org/