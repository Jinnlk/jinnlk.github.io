# About Jinn Khen Lim

Jinn (Jinnson) Khen Lim is a Computer Science & Data Science student at UC Berkeley (dual B.A., with an Economics emphasis), graduating May 2026. He builds data systems that think — from pipelines and warehouses to ML models and AI-powered analytics. Based in Berkeley, CA.

He grew up in Fresno, CA and came to Berkeley chasing something he couldn't yet name. What he found was a deep love for systems — how data flows, transforms, and connects into something greater than its parts. He gets real joy when a pipeline runs clean, when a model surfaces an insight no one saw coming, when everything just works.

What drives him even more than the craft is the people it serves. Coming from a community that wasn't always represented in tech, he knows how much it matters to have someone in the room who gets it. Mentoring and opening doors for people from underrepresented backgrounds in Silicon Valley is something he actively builds toward.

Currently: wrapping up senior year at UC Berkeley, graduating May 2026. Actively looking for full-time roles in data engineering, analytics engineering, and AI/ML. Open to teams building things that matter.

## Interests / a little more

Interests: specialty coffee, travel, fashion, games & socials, AI/ML, volleyball.

Three years as a barista shaped how he thinks about precision and craft — whether dialing in an espresso or debugging a dbt model, small details compound. He loves travel, finding great coffee shops in new cities, and putting together intentional, considered outfits. Outside work he gravitates toward group games, community events, and building things with people in mind.

## Tech stack

Python, SQL, dbt, Airflow, Redshift, Spark, AWS, GCP/Azure, Databricks, BigQuery, Fivetran, LangChain, PyTorch, Scikit-learn, Docker, Kafka.

# Professional Experience

## Envoy — Data Engineer (Jun 2025 – Feb 2026, San Francisco, CA)
- Consolidated 180+ legacy dbt models into 120 standardized models using CTEs, window functions, and incremental strategies (~30% runtime improvement); rebuilt stakeholder dashboards enabling BI migration from Looker to Omni Analytics, saving ~$500K annually.
- Led vendor migrations (Estuary to Fivetran; Chargebee) with end-to-end QA ensuring finance-grade accuracy; reduced vendor spend ~$15K and onboarded Jira, Chorus.ai, and Databricks AI-based customer enrichment datasets as new pipeline sources.
- Upgraded Airflow 2.x to 3.0 and dbt Core to Fusion with Cosmos DAGs, private-link networking, and GitHub Actions CI/CD; cut dbt compile times 40–50% and established a scalable AI-ready deployment framework for prod.
- Built a Claude-powered SQL documentation system covering 1,600+ models and a production LLM observability agent (LangChain, ECS/Fargate, Lambda) that triages dbt/Airflow failures and automates Jira and Slack alerting.
- Tags: dbt, Airflow, Fivetran, LangChain, AWS ECS, CI/CD, Databricks, Omni Analytics.

## Qlay Technologies — Machine Learning Engineer Intern (Jun 2024 – Aug 2024, Remote)
- Fine-tuned a production speech evaluation model using Whisper and Wav2Vec 2.0 with phoneme extraction via Librosa and Epitran to score English proficiency from speech WAV files.
- Deployed a REST API with Django Rest Framework for real-time inference; containerized with Docker and persisted model state in PostgreSQL.
- Tags: Whisper, Wav2Vec 2.0, PyTorch, Django, Docker, PostgreSQL.

## Honda Research Institute — AI / ML Intern (Jan 2024 – May 2024, San Jose, CA)
- Engineered V2X telematics features (GPS, speed, trajectory) with Scikit-Learn; applied K-Means to segment 2,700+ vehicle routes into 7 driver clusters.
- Built ArcGIS API visualizations of route patterns and congestion hotspots to inform fleet planning decisions.
- Tags: Scikit-learn, K-Means, V2X, ArcGIS, Python.

# Consulting Projects (via SAAS Berkeley)

## Autodesk — Data Consultant (2024)
Analyzed internal datasets and built structured reporting pipelines for Autodesk. Delivered data-driven recommendations to support product and business decisions at scale.

## AstraZeneca — Data Consultant (2024)
Applied NLP and data classification techniques to a pharmaceutical industry challenge. Worked with clinical datasets to surface insights and deliver a structured client report.

## Mercari — Data Consultant (2023)
Analyzed marketplace data to uncover user behavior patterns and seller trends. Delivered structured insights and actionable recommendations to the client team.

# Personal Projects

## Data & ML
- V2X Telematics ML: K-Means clustering on 2,700+ vehicle routes to segment 7 driver profiles, with ArcGIS visualizations of route patterns and congestion from GPS/speed/trajectory features.
- Hybrid Work Analytics Pipeline: end-to-end pipeline combining office check-in, NYC taxi, and weather data using Redshift, dbt, Airflow, and Looker Studio dashboards.
- CNN Image Classifier + TensorBoard: fine-tuned a 5-layer, 200M-parameter CNN with 98% accuracy on 2,000+ images, visualized embeddings with PCA/t-SNE.
- Credit Risk GNN + KNN Model: Graph Neural Network for loan default probability using PyTorch and Scikit-Learn, with a KNN similarity graph from 1,000+ applicant entries.
- BigQuery NYC Taxi ETL: full ETL pipeline into BigQuery with dbt modeling and Looker Studio dashboards surfacing fare analytics across millions of records.
- E-commerce ML Dashboard: real-time analytics dashboard using Kafka streaming and React, with ML models for demand forecasting and anomaly detection.
- Fraudulent Job Posting Detector (SAAS Berkeley): ML study detecting fraudulent job postings using TF-IDF on the EMSCAD dataset, benchmarking NLP classification models.
- Speech Proficiency Evaluator: production speech evaluation model fine-tuned with Whisper and Wav2Vec 2.0, combining deep learning with phoneme-level linguistic features via Librosa/Epitran.

## AI / LLM
- AI Data Quality Monitor: LangChain agent on ECS/Fargate and Lambda that triages dbt/Airflow failures, gives AI root-cause insights, and automates Jira/Slack alerting in production.
- Claude SQL Docs System: Claude-powered documentation system generating structured descriptions for 1,600+ dbt models at Envoy, enabling BI migration to Omni Analytics.
- RAG Pipeline: retrieval-augmented generation system using LangChain, OpenAI embeddings, and Chroma vector storage for semantic search and Q&A over custom knowledge bases.
- Emotional AI Interview Platform: built in 24 hrs at a hackathon — React + TypeScript frontend with HumeAI APIs for emotional analysis, mock interview feedback via OpenAI API and WebSockets.
- Automated Slack Bot (EthiCAL Apparel): Slack bot automating org reminders, using Slack API, AWS Lambda, and BeautifulSoup to scrape tabling sign-ups.

## Cloud / Infra
- Azure Olympics ETL Pipeline: Azure Data Factory ingesting 200K+ Olympic records, Spark/PySpark on Databricks, Synapse Analytics, Tableau dashboards.
- Amazon Product Similarity Microservice: cloud-native microservice using FastAPI, Docker, Kubernetes; hybrid TF-IDF + PCA + FAISS pipeline on 30K+ products with Azure Blob Storage.
- MERN Product Listing App: full-stack MERN app with 1,000+ CRUD operations, Chakra UI on React, deployed on Render with 99.9% uptime.

## Coursework
- RookieDB (CS 186): fault-tolerant relational database in Java — B+ tree indices, join algorithms, cost-based query optimizer, concurrency control, ARIES crash recovery.
- Secure File Sharing System (CS 161): cryptographically secure file-sharing system in Go with AES-GCM/RSA end-to-end encryption and revocation.
- Gitlet (CS 61B): Java implementation of a Git-like version control system.
- BYOW (CS 61B): seed-based 2D dungeon world generator in Java with tile rendering and pathfinding.
- Pacman AI Agents (CS 188): search algorithms, adversarial agents, and reinforcement learning in the Berkeley Pacman framework.
- Scheme Interpreter (CS 61A): full Scheme interpreter in Python with tail-call optimization and macro expansion.
- RISC-V CPU in Logisim (CS 61C): 2-stage pipelined RISC-V CPU with ALU, register file, and hazard forwarding.
- Network Routing Protocols (CS 168): distance-vector and link-state routing protocols, simulated BGP-style path-vector routing.
- Spam Classification + EDA (Data 100): exploratory analysis and classifiers for email spam detection.
- Data Engineering Workflows (Data 101): relational schema design, SQL/CTEs, ETL workflows — coursework that directly informed his DE work at Envoy.

# Campus Involvement

## EthiCAL Apparel — President · Executive Advisor · 3+ yrs
Grew from Sales to Internal VP to President of Berkeley's sustainable fashion org. Led strategy, operations, web development, and financial reporting across multiple cycles. Now serves as Executive Advisor.

## SAAS Berkeley — Director · Consultant · Advisor · 3+ yrs
Ran Berkeley's Data Foundations program directing mentorship and education. Led consulting engagements with Autodesk, AstraZeneca, and Mercari. Published research in NLP and data classification. Now serves as org advisor.

## Cal Animage Alpha — Head of Planning (2022–2023)
Led campus-wide event planning, team coordination, and social media strategy. Built community programming and managed logistics for large club events.

## Data 8, UC Berkeley — Academic Intern · Peer Tutor (2023)
Supported Foundations of Data Science as an Academic Intern, providing hands-on tutoring to students entering the data science pipeline.

# Contact

Email: jinnlk@berkeley.edu
LinkedIn: linkedin.com/in/jinnlk
GitHub: github.com/jinnlk
Resume: downloadable from the Contact section of this site.
