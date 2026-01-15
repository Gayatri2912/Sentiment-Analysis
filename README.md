### Sentiment Analysis
1. ⚙️ Modular Pipeline Architecture (DVC)
You transitioned from individual notebooks to a structured DVC (Data Version Control) pipeline. Each step of your project is now a "stage" defined in a dvc.yaml file.

📥 Data Ingestion: Automatically handles the collection of raw YouTube comment data.

🧹 Preprocessing: Standardizes text cleaning and converts comments into mathematical features using TF-IDF.

🧠 Model Building: Trains a LightGBM classifier specifically tuned for sentiment detection.

📊 Model Evaluation: Calculates accuracy and generates confusion matrices to visualize errors.

2. 🧪 Experiment Tracking & Registry (MLflow)
You integrated MLflow to move beyond local logging and manage the model lifecycle.

🌐 Remote Tracking: You deployed an MLflow server on an AWS EC2 instance, allowing you to log every run to a central dashboard.

📈 Metric Logging: The system captures training parameters and performance metrics for every single run.

🗃️ Model Registry: You implemented a system to "Register" successful models, versioning them (e.g., Version 1, Version 2) to track the best-performing weights.

3. ☁️ Cloud Artifact Management (AWS S3)
Because ML models are too large for GitHub, you implemented a scalable cloud storage solution.

🪣 AWS S3 Integration: You configured a bucket (bucket-mlflow-92) to act as your "Remote Storage".

🔗 Artifact Decoupling: Large .pkl files are pushed to S3, while only small metadata "pointers" stay in Git, keeping your repo light.

🔐 IAM Security: You managed AWS IAM policies to ensure secure, authorized access to your cloud data.

4. 🐳 Containerization & CI/CD
To ensure your project works on any machine, you adopted modern deployment standards.

📦 Dockerization: You created a Dockerfile that packages your code and dependencies into a single container, eliminating environment errors.

🤖 GitHub Actions: You set up CI/CD to automatically verify your code and run the pipeline every time you commit new work.