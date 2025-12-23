Week 1 Graduation: Day 7 (Mini Project)
You have successfully simulated the core mechanic of modern AI apps (RAG) using nothing but English. That brings us to Day 7: The Architecture Summarizer Project.

This is your final exam for Week 1. We are going to consolidate everything—Roles, JSON, Few-Shot, and Chaining—into one "Golden Prompt" that you will automate next week.

The Goal: Create a robust "Prompt Template" that can reliably extract architectural details from any messy text, not just the one we used on Day 5.

The Task:

Design a "Master Prompt" that takes raw text as input and outputs a clean JSON summary.

Test it against 3 different "Messy Inputs" (provided below).

Document the results in your GitHub repo.

Phase 1: The "Master Prompt"
Draft a prompt that uses Role (System Architect), Instruction (Extract specific fields), and Format (JSON).

Tip: Use the "Few-Shot" technique if the model struggles.

Phase 2: The Stress Test (Your Inputs)
Run your Master Prompt against these three scenarios.

Input A (The "Executive Panic"):

"We need to launch the new loyalty app by Friday! It's currently hosted on AWS EC2 t2.micro instances, but traffic is spiking. We're using RDS for the database. Marketing wants to add a recommendation engine using Python, but the current backend is Node.js. Also, ensure it's GDPR compliant because we have users in France."

Input B (The "Legacy Grunt"):

"Hey, looking at the old inventory system. It's running on a mainframe, believe it or not. DB2 database. We need to scrape the data and put it into Snowflake for analytics. The connection needs to happen overnight via batch processing. No real-time requirements, but security is tight—no cloud ingress allowed."

Input C (The "Startup Pivot"):

"We're ditching the mobile app and going Web-only using Vercel. We need to migrate our Firestore data to Supabase (PostgreSQL). We expect 500 users day one. Low latency is key. We also need to integrate Stripe for payments."

Phase 3: The Deliverable
Create a new file in your GitHub repo: project_1_summarizer.md.

Paste your Master Prompt.

Paste the JSON Output you got for Input A, B, and C.

(Optional) Add a "Reflection" section: Did one input fail? How did you tweak the prompt to fix it?

Once you submit this to GitHub, you have officially completed Week 1. You will have a portfolio showing you can engineer prompts for AWS, Mainframes, and Modern Web stacks.

Ready to get to work? Let me know if you want me to critique your "Master Prompt" before you run the tests!

Input A prompt:
Okay, here's the first Day 7 exercise. It's using a R-T-C-F framework
**Prompt**
Role: Act as a System Architect
Task: Extract architectural details
Context: A company executive told me, "We need to launch the new loyalty app by Friday! It's currently hosted on AWS EC2 t2.micro instances, but traffic is spiking. We're using RDS for the database. Marketing wants to add a recommendation engine using Python, but the current backend is Node.js. Also, ensure it's GDPR compliant because we have users in France."
Format: JSON

Input A results:
{
  "project_scope": {
    "app_type": "Loyalty App",
    "launch_deadline": "Friday",
    "current_status": "Traffic spiking on existing infrastructure"
  },
  "current_infrastructure": {
    "cloud_provider": "AWS",
    "compute_resources": "EC2 t2.micro instances",
    "database": "RDS",
    "backend_framework": "Node.js"
  },
  "new_requirements": {
    "feature": "Recommendation Engine",
    "required_language": "Python",
    "integration_challenge": "Node.js backend with Python service"
  },
  "compliance_and_security": {
    "requirement": "GDPR Compliance",
    "target_demographic": "Users in France"
  }
}

Moving on to Input B from the Day 7 exercises
**Prompt** 
Role: Act as a System Architect
Task: Extract architectural details
Context: Got an email from a guy supporting an legacy app, "Hey, looking at the old inventory system. It's running on a mainframe, believe it or not. DB2 database. We need to scrape the data and put it into Snowflake for analytics. The connection needs to happen overnight via batch processing. No real-time requirements, but security is tight—no cloud ingress allowed."
Format: JSON
 {
  "source_system": {
    "type": "Legacy Inventory System",
    "infrastructure": "Mainframe",
    "database": "DB2"
  },
  "target_system": {
    "platform": "Snowflake",
    "purpose": "Analytics"
  },
  "integration_strategy": {
    "method": "Batch processing (Data scraping)",
    "frequency": "Overnight",
    "latency_sensitivity": "None (No real-time requirements)"
  },
  "security_constraints": {
    "network_restriction": "No cloud ingress allowed",
    "implication": "Connection must be initiated outbound from the mainframe environment"
  }
}

Moving on to Input C from the Day 7 exercises
**Prompt** 
Role: Act as a System Architect
Task: Extract architectural details
Context: Got a phone call of the IT director of our startup company, "We're ditching the mobile app and going Web-only using Vercel. We need to migrate our Firestore data to Supabase (PostgreSQL). We expect 500 users day one. Low latency is key. We also need to integrate Stripe for payments."
Format: JSON

{
  "client_architecture": {
    "platform_shift": "Mobile App to Web-only",
    "hosting_provider": "Vercel"
  },
  "data_migration": {
    "source_database": "Firestore (NoSQL)",
    "target_database": "Supabase (PostgreSQL)",
    "migration_type": "NoSQL to Relational (SQL)"
  },
  "performance_requirements": {
    "initial_load": "500 users (Day 1)",
    "priority": "Low latency"
  },
  "integrations": {
    "payment_gateway": "Stripe"
  }
}

Reflections:
JSON output doesn't seem to be particularly useful, but I suppose it could be used as input in an AI Agent. I was surprised it was able to parse the data so intelligently.


