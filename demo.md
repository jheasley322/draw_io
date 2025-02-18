:::mermaid
graph TB
    %% Consulting Division (Swimlane)
    subgraph A1["Consulting Division"]
      direction TB
      A2["Mammoth Sourcing"]
      A3["Owl Strategy"]
      A4["HubSpot CRM"]
      A5["SharePoint (Financials)"]
      A6["Power BI (Manual)"]
      A7["Salesforce CRM"]
      A8["SQL Server (Operations)"]
      A9["Tableau (Strategy)"]

      A2 -->|Uses| A4
      A2 -->|Stores| A5
      A2 -->|Reports| A6
      A3 -->|Uses| A7
      A3 -->|Stores| A8
      A3 -->|Reports| A9
    end

    %% Hardware Division (Swimlane)
    subgraph B1["Hardware Division"]
      direction TB
      B2["Hawk Mobility"]
      B3["Panther Robotics"]
      B4["Shark Networking"]
      B5["SAP ECC"]
      B6["On-Prem SQL Server"]
      B7["QlikView (Outdated)"]
      B8["Oracle Cloud"]
      B9["Tableau (Factory Ops)"]
      B10["Google BigQuery (No Integration)"]
      B11["Python (Limited Access)"]

      B2 -->|ERP| B5
      B2 -->|Stores| B6
      B2 -->|Reports| B7
      B3 -->|ERP| B8
      B3 -->|Reports| B9
      B4 -->|Stores| B10
      B4 -->|Analysis| B11
    end

    %% Managed Services (Swimlane)
    subgraph C1["Managed Services"]
      direction TB
      C2["Badger Back Office"]
      C3["Bear Data"]
      C4["Fox Accounting"]
      C5["ServiceNow (ITSM)"]
      C6["PostgreSQL (AWS RDS)"]
      C7["Workday (HR System)"]
      C8["Azure Blob Storage"]
      C9["Zendesk (Separate Instance)"]
      C10["Excel (Manual HR Analytics)"]
      C11["Oracle (Finance)"]
      C12["Tableau (Financial Reports)"]

      C2 -->|Uses| C5
      C2 -->|Stores| C6
      C2 -->|HR Data| C7
      C2 -->|Stores| C8
      C3 -->|Uses| C9
      C3 -->|Reports| C10
      C4 -->|Uses| C11
      C4 -->|Reports| C12
    end

    %% Software Division (Pelican + Other Companies)
    subgraph D1["Software Division"]
      direction TB
      D2["Pelican TMS"]
      D3["Pelican WMS"]
      D4["Firestorm AI"]
      D5["StormShield Cyber"]
      D6["AWS Redshift (TMS)"]
      D7["Looker (Dashboards)"]
      D8["Kafka (Streaming)"]
      D9["Azure SQL (Warehouse)"]
      D10["Power BI (WMS)"]
      D11["Snowflake (Archives)"]
      D12["Google BigQuery (ML)"]
      D13["Looker (AI Insights)"]
      D14["Splunk (Security Logs)"]
      D15["Elasticsearch (Security Events)"]

      D2 -->|Storage| D6
      D2 -->|Dashboards| D7
      D2 -->|Streaming| D8
      D3 -->|Storage| D9
      D3 -->|Dashboards| D10
      D3 -->|Archiving| D11
      D4 -->|Storage| D12
      D4 -->|Dashboards| D13
      D5 -->|Logs| D14
      D5 -->|Events| D15
    end

    %% Logistics & Operations (Swimlane)
    subgraph E1["Logistics & Operations"]
      direction TB
      E2["TMS"]
      E3["WMS"]
      E4["Azure Data Lake (Shipments)"]
      E5["MySQL (On-Prem)"]
      E6["Snowflake (Inventory)"]
      E7["IoT Fleet Data (No Integration)"]

      E2 -->|Stores| E4
      E2 -->|Uses| E5
      E3 -->|Stores| E6
      E3 -->|Tracking| E7
    end

    %% Finance & HR (Swimlane)
    subgraph F1["Finance & HR"]
      direction TB
      F2["Corporate Finance"]
      F3["Budgeting & Forecasting"]
      F4["SAP S/4HANA"]
      F5["Workday (Payroll)"]
      F6["Hyperion (Budgeting)"]
      F7["Excel (Manual Forecasting)"]

      F2 -->|ERP| F4
      F2 -->|Payroll| F5
      F3 -->|Budgeting| F6
      F3 -->|Exports| F7
    end

    %% Disconnections & Silos (Dotted Lines for Gaps)
    subgraph "Data Silos & Integration Issues"
      A1 -.->|No Data Sharing| B1
      B1 -.->|Inventory Not Linked| F2
      C1 -.->|HR Data Not Integrated| F1
      D1 -.->|No Financial Integration| F3
      E1 -.->|Logistics & Finance Disconnected| F2
    end