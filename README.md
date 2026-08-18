<h1 align="center">End-to-End-Analysis-of-Nvidia-GPU-Market-Sales-Dynamics</h1>

<p>
An end-to-end data science project analyzing transaction dynamics across consumer gaming cards and enterprise AI accelerators. The pipeline covers robust data ingestion, automated cleaning, feature engineering, exploratory visual analysis, an XGBoost predictive revenue model, and structured dataset exports for Tableau dashboarding.
</p>

<h2>Business Problems</h2>
<p>
The hardware graphics and AI accelerator market faces structural volatility across supply chains, distribution channels, and regional customer segments. This project addresses three primary business questions:
</p>
<ul>
    <li><b>Supply Chain Premium Capture:</b> How severely do regional stock shortages inflate secondary market street prices over MSRP, and how can pricing strategies capture this lost margin?</li>
    <li><b>Channel & Segment Yield Analysis:</b> Which sales channels (System Integrators, Direct-to-Consumer, Retail) and customer segments (Hyperscale Datacenters vs. Gaming) yield the highest per-unit revenue realization?</li>
    <li><b>Predictive Revenue Modeling:</b> Can machine learning accurately predict order-level revenue based on product age, regional channel parameters, and pricing spread without relying on target-derived features?</li>
</ul>

<h2>Dataset Description</h2>
<p>
This project utilizes a synthetic dataset containing 7,000 fictional GPU transaction records designed for learning and visualization practice.
</p>
<p>
<i>Note: This dataset is fully fictional and created under the CC0 license. It does not represent real NVIDIA financial records or actual company sales figures. Real GPU model names (e.g., RTX 4090, RTX 5090, H100, H200, B200) and public MSRPs are used solely for realistic context.</i>
</p>

<table>
    <thead>
        <tr>
            <th>Field Name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>sale_id</code></td>
            <td>Integer</td>
            <td>Unique identifier for each transaction record.</td>
        </tr>
        <tr>
            <td><code>sale_date</code></td>
            <td>Datetime</td>
            <td>Timestamp indicating when the sale occurred.</td>
        </tr>
        <tr>
            <td><code>gpu_model</code></td>
            <td>String</td>
            <td>Specific GPU architecture (e.g., RTX 4090, H100, B200).</td>
        </tr>
        <tr>
            <td><code>gpu_family</code></td>
            <td>String</td>
            <td>Product categorizations: Consumer Gaming or Data Center AI.</td>
        </tr>
        <tr>
            <td><code>launch_year</code></td>
            <td>Integer</td>
            <td>Original release year of the GPU hardware.</td>
        </tr>
        <tr>
            <td><code>region</code></td>
            <td>String</td>
            <td>Geographic territory (e.g., North America, Asia-Pacific, Europe).</td>
        </tr>
        <tr>
            <td><code>sales_channel</code></td>
            <td>String</td>
            <td>Distribution route (Retail/Etail, System Integrator, Direct OEM).</td>
        </tr>
        <tr>
            <td><code>customer_segment</code></td>
            <td>String</td>
            <td>Target user vertical (Gaming, AI Research, Hyperscale Datacenter, etc.).</td>
        </tr>
        <tr>
            <td><code>units_sold</code></td>
            <td>Integer</td>
            <td>Quantity of units purchased in the order.</td>
        </tr>
        <tr>
            <td><code>msrp_usd</code></td>
            <td>Float</td>
            <td>Official manufacturer suggested retail price per unit.</td>
        </tr>
        <tr>
            <td><code>avg_street_price_usd</code></td>
            <td>Float</td>
            <td>Observed market transaction price per unit.</td>
        </tr>
        <tr>
            <td><code>price_premium_pct</code></td>
            <td>Float</td>
            <td>Percentage markup of street price relative to MSRP.</td>
        </tr>
        <tr>
            <td><code>stock_status</code></td>
            <td>String</td>
            <td>Inventory status at transaction time (In Stock, Low Stock, Out of Stock).</td>
        </tr>
        <tr>
            <td><code>customer_satisfaction_score</code></td>
            <td>Float</td>
            <td>Post-purchase rating score (1 to 5 scale).</td>
        </tr>
        <tr>
            <td><code>warranty_months</code></td>
            <td>Integer</td>
            <td>Duration of hardware warranty coverage.</td>
        </tr>
        <tr>
            <td><code>bundle_addon</code></td>
            <td>String</td>
            <td>Included software or hardware accessories.</td>
        </tr>
        <tr>
            <td><code>revenue_usd</code></td>
            <td>Float</td>
            <td>Total financial value realized from the transaction (Target variable).</td>
        </tr>
    </tbody>
</table>

<h2>Methodology</h2>
<ul>
    <li><b>Data Cleaning & Safeguards:</b> Standardized header strings, converted datatypes, imputed categorical missing values, and implemented multi-path ingestion routines to prevent directory runtime errors in Kaggle/Colab.</li>
    <li><b>Feature Engineering:</b> Calculated product age from launch metrics, extracted calendar quarters, derived unit price realizations, and constructed pricing spread indicators.</li>
    <li><b>Exploratory Visualizations:</b> Generated high-resolution dual-axis plots, regional bar charts, and correlation heatmaps to isolate unit price markups against stock availability.</li>
    <li><b>Machine Learning Pipeline:</b> Built a scikit-learn Pipeline with a <code>ColumnTransformer</code> (StandardScaler for numerical features, OneHotEncoder for categorical features) feeding an XGBoost Regressor to predict target revenue.</li>
    <li><b>BI Integration:</b> Formatted and exported a dedicated CSV structured for custom Tableau visualization (Dual-axis trends, Pareto analysis, and Scatter Matrices).</li>
</ul>

<h2>Results</h2>
<ul>
    <li><b>Model Accuracy:</b> The XGBoost Regressor achieved an <b>R² Score of 0.9981</b> with a Mean Absolute Error (MAE) of <b>$1,157.94</b> and a Root Mean Squared Error (RMSE) of <b>$3,909.13</b>.</li>
    <li><b>Inventory Shortage Dynamics:</b> Transactions marked as <b>"Sold Out"</b> suffered the highest scalping markups (median ~45%, peaking near 100% over MSRP), followed by <b>"Backordered"</b> items (~28% median). <b>"Low Stock"</b> items averaged between 10%–18%, while <b>"In Stock"</b> inventory remained stable near MSRP (~4%).</li>
    <li><b>Enterprise vs. Consumer Distribution:</b> <b>Data Center AI</b> cards generated <b>~59% (~$232M)</b> of total revenue volume across Hyperscale, AI Research, and Crypto segments, while <b>Consumer Gaming</b> cards generated <b>~$162M</b>, led by the core Gaming segment (~$130M).</li>
</ul>

<h2>Tech Stack</h2>
<p>
<b>Language:</b> Python<br>
<b>Data Manipulation:</b> Pandas, NumPy<br>
<b>Visualization:</b> Matplotlib, Seaborn<br>
<b>Machine Learning:</b> Scikit-Learn, XGBoost<br>
<b>Data Ingestion:</b> Kagglehub<br>
<b>Business Intelligence:</b> Tableau
</p>

<h2>Learning Experience</h2>
<p>
This project provided hands-on experience in building robust data ingestion wrappers that adapt seamlessly across local and cloud runtime environments. Key takeaways included strict prevention of target leakage during feature engineering and structuring modular Python scripts that bridge machine learning models with interactive BI dashboards.
</p>
