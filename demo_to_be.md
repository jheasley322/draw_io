:::mermaid
graph TB
  %% Unified Data Integration Layer
  subgraph A1["Data Ingestion & Integration (Qlik QDI + Talend)"]
    A2["Qlik Replicate (CDC)"] -->|Real-time data sync| A3["Snowflake"]
    A4["Talend (Data Quality)"] -->|Validation & Governance| A3
    A5["Kafka (Streaming)"] -->|Event Processing| A3
  end

  %% Centralized Cloud Storage & Processing
  subgraph B1["Unified Cloud Storage & Compute (Snowflake)"]
    B2["Raw Data Zone"] -->|Cleansing & Transformation| B3["Processed Data Zone"]
    B3 -->|Semantic Modeling| B4["Business Data Warehouse"]
    B4 -->|AI/ML Ready Data| B5["Predictive Analytics & AutoML"]
  end

  %% Analytics & Visualization
  subgraph C1["Qlik Sense (BI & AI Analytics)"]
    C2["Dashboards & Reports"]
    C3["Augmented Insights (AI)"]
    C4["Self-Service Data Exploration"]
    C5["Qlik AutoML"]
    
    B4 -->|BI & Visualization| C2
    B5 -->|AI-Driven Insights| C3
    B4 -->|Business User Access| C4
    B5 -->|Predictive Modeling| C5
  end

  %% Divisional Data Sources
  subgraph D1["Enterprise Data Sources"]
    direction TB
    D2["ERP (SAP, Oracle)"]
    D3["CRM (Salesforce, HubSpot)"]
    D4["HR & Payroll (Workday)"]
    D5["TMS & WMS (Pelican)"]
    D6["IoT & Telematics (Sensors)"]
    D7["Security Logs (Splunk, Elasticsearch)"]
    
    D2 -->|ETL via Qlik Replicate| A2
    D3 -->|ETL via Qlik Replicate| A2
    D4 -->|ETL via Talend| A4
    D5 -->|Streaming Data| A5
    D6 -->|IoT Real-Time Sync| A5
    D7 -->|Security Monitoring| A5
  end

  %% AI/ML Processing
  subgraph E1["AI & Predictive Analytics"]
    direction TB
    E2["Qlik AutoML (Business-Driven AI)"]
    E3["Snowflake ML (Advanced AI)"]
    E4["Anomaly Detection"]
    E5["Predictive Maintenance"]
    E6["Customer Churn Forecasting"]
    
    B5 -->|Data for AI| E2
    B5 -->|Data for AI| E3
    E2 -->|Insights to BI| C3
    E3 -->|AI-Driven Alerts| E4
    E3 -->|Predictive Maintenance| E5
    E3 -->|Churn Analysis| E6
  end

  %% Security & Governance
  subgraph F1["Security & Data Governance"]
    direction TB
    F2["Talend Data Catalog"]
    F3["Snowflake RBAC (Role-Based Access)"]
    F4["Data Masking & Compliance"]
    
    A3 -->|Metadata Management| F2
    B1 -->|Row-Level Access Control| F3
    B1 -->|Regulatory Compliance| F4
  end

  %% Connections Between Layers
  A3 -->|Stores & Processes| B1
  B1 -->|Feeds AI/ML & BI| C1
  B1 -->|Governance Layer| F1
  C1 -->|Business Decision Making| E1