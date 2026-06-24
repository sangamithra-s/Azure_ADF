# ☁️ Azure Data Factory — ADF Pipelines

This repository contains the **Azure Data Factory (ADF)** pipeline definitions, datasets, linked services, data flows, and triggers, version-controlled via ADF's native **Git integration**. It serves as the source of truth for all data pipeline configurations in this Azure data engineering project.

---

## 📌 Overview

Azure Data Factory is a cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating and automating data movement and transformation. This repo stores all ADF artifacts as JSON files, enabling version control, collaboration, and CI/CD for data pipelines.

---

## 📁 Repository Structure

```
Azure_ADF/
├── dataflow/            # Mapping Data Flows for complex data transformations
├── dataset/             # Dataset definitions (source and sink)
├── factory/             # Factory-level global settings and configurations
├── linkedService/       # Linked service connections (Azure Storage, SQL, ADLS, etc.)
├── pipeline/            # Pipeline definitions (ETL orchestration logic)
├── trigger/             # Trigger definitions (schedule / event / tumbling window)
├── publish_config.json  # ADF Git publish configuration
└── README.md
```

### Folder Breakdown

| Folder | Description |
|---|---|
| `pipeline/` | Defines the orchestration logic — activities like Copy, Data Flow, Stored Procedure, etc. |
| `dataset/` | Defines the schema and location of source and destination data |
| `linkedService/` | Stores connection configurations to Azure services and external systems |
| `dataflow/` | Visual ETL transformations built using Mapping Data Flows |
| `trigger/` | Defines when pipelines run — scheduled, event-based, or tumbling window |
| `factory/` | Factory-level settings like global parameters and integration runtimes |

---

## 🛠️ Tech Stack & Azure Services

| Service | Purpose |
|---|---|
| **Azure Data Factory** | Core ETL / orchestration engine |
| **Azure Blob Storage** | Source / sink for raw and processed data |
| **Azure Data Lake Storage Gen2** | Scalable data lake storage |
| **Azure SQL Database** | Relational data source or destination |
| **Azure Key Vault** | Secure storage of credentials and secrets |
| **Mapping Data Flows** | Code-free data transformation at scale |
| **Integration Runtime** | Compute used to run pipeline activities |

---

## ⚙️ How ADF Git Integration Works

When ADF is connected to a Git repository:

1. All pipeline, dataset, linked service, data flow, and trigger definitions are saved as **JSON files**
2. Changes made in ADF Studio are **committed directly to this repo**
3. The `main` branch acts as the **collaboration branch**
4. Publishing from ADF Studio deploys changes to the **ADF live mode**

```
ADF Studio → Edit → Commit to Git (main branch) → Publish → Live ADF
```

---

## 🚀 Getting Started

### Prerequisites

- An active **Microsoft Azure** subscription
- An **Azure Data Factory** instance
- Access to this GitHub repository

### Connect ADF to This Repository

1. Open your **Azure Data Factory Studio**
2. Go to **Manage** → **Git configuration**
3. Select **GitHub** as the repository type
4. Enter the following details:
   - **Repository owner**: `sangamithra-s`
   - **Repository name**: `Azure_ADF`
   - **Collaboration branch**: `main`
   - **Publish branch**: `adf_publish`
   - **Root folder**: `/`
5. Click **Apply** — ADF will load all pipelines and resources from this repo

---

## 🔄 CI/CD Pipeline (Recommended Setup)

For automated deployments across environments (Dev → UAT → Prod):

1. Use the `adf_publish` branch — ADF auto-generates ARM templates here when you publish
2. Use **Azure DevOps Pipelines** or **GitHub Actions** to deploy ARM templates to other environments
3. Store environment-specific parameters in a `parameters.json` file per environment

```
Dev (Git-connected ADF)
    ↓ Publish
adf_publish branch (ARM Templates)
    ↓ CI/CD Pipeline
UAT ADF → Prod ADF
```

---

## 🔐 Security Best Practices

- Store all credentials and connection strings in **Azure Key Vault**
- Reference secrets in Linked Services using **Key Vault references** — never hardcode secrets
- Use **Managed Identity** for authentication between Azure services wherever possible
- Ensure sensitive parameters are marked as **secure strings** in global parameters

---

## 🧠 What I Learned

- Designing and building ETL pipelines using Azure Data Factory
- Configuring Linked Services for various Azure data sources
- Using Mapping Data Flows for complex transformations without code
- Version-controlling ADF artifacts using Git integration
- Setting up pipeline triggers (schedule-based and event-based)
- Best practices for ADF CI/CD deployment across environments

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👩‍💻 Author

**Sangamithra S**
[GitHub](https://github.com/sangamithra-s)
