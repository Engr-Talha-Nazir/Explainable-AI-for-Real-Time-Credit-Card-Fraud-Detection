<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Explainable AI for Real-Time Credit-Card Fraud Detection</title>
</head>
<body style="font-family: Arial, sans-serif; line-height: 1.6;">
    <header>
        <h1 style="color: #2C3E50; text-align: center;">Explainable AI for Real-Time Credit-Card Fraud Detection: Enhancing Accuracy, Transparency, and Trust in Financial Systems</h1>
        <p style="text-align: center;"><strong>Author:</strong> Talha Nazir</p>
        <p style="text-align: center;"><strong>Institution:</strong> The National Research University Higher School of Economics</p>
        <p style="text-align: center;"><strong>Thesis:</strong> Master's Research Thesis</p>
        <hr>
    </header>
    <section>
        <h2>Overview</h2>
        <p>
            This repository contains the implementation of a real-time credit card fraud detection system using machine learning (ML) and explainable AI (XAI) techniques. The primary model used is <strong>XGBoost</strong>, selected for its superior performance in handling imbalanced datasets. The project also integrates a <strong>multi-agent system</strong> for decision-making, reporting, and fraud analysis. The system leverages <strong>SHAP</strong>, <strong>LIME</strong>, and <strong>permutation importance</strong> methods to provide transparency and explainability in the predictions, improving trust in the model's decisions.
        </p>
    </section>
    <section>
        <h2>Key Features</h2>
        <ul>
            <li>Comparative evaluation of multiple machine learning models (Logistic Regression, Random Forest, Extra Trees, Isolation Forest, XGBoost, LightGBM).</li>
            <li>Integration of explainable AI techniques, including <strong>SHAP</strong>, <strong>LIME</strong>, and <strong>permutation importance</strong> for global and local model explanations.</li>
            <li>A <strong>multi-agent framework</strong> that separates prediction, triage, explainability, reporting, and analyst explanation generation for greater modularity and operational utility.</li>
            <li>Real-time fraud detection capability with fraud predictions, risk categories, recommended actions, and human-readable explanations.</li>
        </ul>
    </section>
    <section>
        <h2>Installation</h2>
        <h3>1. Clone the Repository</h3>
        <pre><code>git clone https://github.com/your-username/FraudDetectionProject.git</code></pre>
        <h3>2. Install Required Dependencies</h3>
        <p>Install the required Python libraries:</p>
        <pre><code>pip install -r requirements.txt</code></pre>
        <h3>3. Install Required Libraries</h3>
        <ul>
            <li>Ensure <strong>XGBoost</strong>, <strong>LightGBM</strong>, and <strong>SHAP</strong> are installed:</li>
            <pre><code>pip install xgboost lightgbm shap</code></pre>
        </ul>
    </section>
    <section>
        <h2>Dataset</h2>
        <p>
            The dataset used in this research is from European credit card transactions from 2013. It contains both legitimate and fraudulent transactions. The dataset consists of 284,807 transactions, of which 492 are fraudulent, making up <strong>0.1727%</strong> of the total data. The dataset features 31 variables, including anonymized PCA-transformed variables (<strong>V1</strong> to <strong>V28</strong>), <strong>Time</strong>, <strong>Amount</strong>, and the target variable (<strong>Class</strong>).
        </p>
    </section>
    <section>
        <h2>Model Performance</h2>
        <h3>Best Experimental Model</h3>
        <p><strong>Best model based on validation PR-AUC:</strong> XGBoost</p>
        <h3>Test Performance of Operational Model</h3>
        <table border="1" cellpadding="10" cellspacing="0" style="border-collapse: collapse; width: 100%; margin-bottom: 20px;">
            <thead>
                <tr>
                    <th>Metric</th>
                    <th>Value</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>ROC-AUC</td>
                    <td>0.9872</td>
                </tr>
                <tr>
                    <td>PR-AUC</td>
                    <td>0.7942</td>
                </tr>
                <tr>
                    <td>Precision</td>
                    <td>0.8615</td>
                </tr>
                <tr>
                    <td>Recall</td>
                    <td>0.7467</td>
                </tr>
                <tr>
                    <td>F1-score</td>
                    <td>0.8000</td>
                </tr>
            </tbody>
        </table>
        <h3>Novel Contribution</h3>
        <p>This work introduces a novel framework combining:</p>
        <ul>
            <li>Comparative evaluation of several fraud detection algorithms.</li>
            <li>Threshold optimization under severe class imbalance.</li>
            <li><strong>SHAP</strong>-based global and local explainability.</li>
            <li><strong>LIME</strong> and permutation importance as additional model-agnostic XAI methods.</li>
            <li>A <strong>multi-agent fraud decision architecture</strong>.</li>
            <li>Optional <strong>Gemini-based analyst explanation generation</strong>.</li>
        </ul>
        <p>The framework is designed to provide not only predictions but also risk categories, recommended actions, and human-readable explanations, making it highly suitable for real-time fraud operations.</p>
    </section>
    <section>
        <h2>Framework and Components</h2>
        <p>The fraud detection system is implemented as a <strong>multi-agent architecture</strong> consisting of the following components:</p>
        <ul>
            <li><strong>Prediction Agent:</strong> Uses the XGBoost model to estimate fraud probability.</li>
            <li><strong>Triage Agent:</strong> Converts the fraud score into risk levels and makes operational decisions (e.g., block, review).</li>
            <li><strong>XAI Explanation Agent:</strong> Provides human-readable explanations of the model's decision using SHAP.</li>
            <li><strong>Report Agent:</strong> Combines prediction, triage, and explanation results into a fraud detection report.</li>
            <li><strong>Gemini Analyst Agent:</strong> Translates technical fraud reports into understandable explanations for fraud analysts.</li>
        </ul>
    </section>
    <section>
        <h2>Usage</h2>
        <h3>Run the Fraud Scoring Tool</h3>
        <p>Use the <strong>fraud_scoring_tool()</strong> function to score new transactions and get fraud predictions along with recommendations:</p>
        <pre><code>result = fraud_scoring_tool(Time=146022, V1=-1.3598, V2=-0.0728, ..., Amount=1.18)</code></pre>
        <p>Example Output:</p>
        <pre><code>print(result)</code></pre>
        <h3>Generate Fraud Reports</h3>
        <p>Once the model makes a prediction, the report is automatically generated with explanations based on SHAP, LIME, and other XAI methods.</p>
        <h3>Real-Time Integration</h3>
        <p>Integrate the <strong>Gemini Analyst Agent</strong> to generate human-readable reports for fraud analysts.</p>
    </section>
    <section>
        <h2>Results & Performance</h2>
        <p><strong>XGBoost</strong> was selected as the operational model for real-time fraud detection due to its high <strong>ROC-AUC</strong> (0.9872), <strong>PR-AUC</strong> (0.7942), and ability to handle severe class imbalance. The system is designed to give actionable decisions, with the risk level and recommended actions. <strong>Explainability</strong> is integrated using <strong>SHAP</strong> and <strong>LIME</strong> to ensure transparency in decision-making.</p>
    </section>
    <section>
        <h2>Future Work</h2>
        <ul>
            <li><strong>Model Improvement:</strong> Incorporate additional models and fine-tune the existing ones for better performance.</li>
            <li><strong>Real-Time Data Integration:</strong> Implement live transaction streams to further test and validate the model’s performance.</li>
            <li><strong>Improved Explainability:</strong> Explore additional XAI methods and model refinement for better interpretability.</li>
        </ul>
    </section>
    <section>
        <h2>License</h2>
        <p>This project is licensed under the MIT License - see the <a href="LICENSE">LICENSE</a> file for details.</p>
    </section>
    <footer>
        <p>Repository: <a href="https://github.com/Engr-Talha-Nazir/Explainable-AI-for-Real-Time-Credit-Card-Fraud-Detection">https://github.com/your-username/FraudDetectionProject</a></p>
    </footer>
</body>
</html>
