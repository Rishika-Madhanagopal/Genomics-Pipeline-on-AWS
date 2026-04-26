# 🧬 Genomics Pipeline on AWS
### *End-to-end NGS workflow for scalable variant discovery and cloud-native analysis.*

<div align="center">
  <img src="docs/AWS_Architecture_Diagram.png" width="100%" style="border-radius: 10px;" />
</div>

## 🛰️ OVERVIEW
This repository implements a production-ready **Bioinformatics Pipeline** designed for the AWS ecosystem. It automates the transition from raw sequencing data (FASTQ) to validated variant calls (VCF), leveraging cloud elasticity for high-throughput genomic analysis.

> **Key Objective:** To demonstrate a scalable, cloud-native approach to NGS data processing using industry-standard tools (GATK, BWA, FastQC) integrated with AWS core services.


## 🏗️ ARCHITECTURE & WORKFLOW
The pipeline follows a modular design pattern to ensure scalability and cost-optimization:

* **Compute:** Elastic execution on **Amazon EC2** (t3.medium+) with automation potential via **AWS Batch**.
* **Storage:** Decoupled data architecture using **Amazon S3** for raw data lakes and result persistence.
* **Orchestration:** Event-driven triggers using **AWS Lambda** for automated metadata extraction and process initiation.
* **Analysis:** Interactive visualization and downstream statistics via **Jupyter Notebooks**.


## 🚀 FEATURES
- ✅ **Quality Control:** Comprehensive read assessment using **FastQC**.
- ✅ **Alignment:** High-sensitivity mapping via **Bowtie2** or **BWA**.
- ✅ **Processing:** Efficient SAM/BAM manipulation with **Samtools**.
- ✅ **Variant Discovery:** Gold-standard variant calling using **GATK**.
- ✅ **Cloud Sync:** Automated results synchronization with **Amazon S3**.
- ✅ **Insights:** Integrated Python-based analysis for VCF interpretation.


## 📁 PROJECT STRUCTURE
```bash
bioinformatics-pipeline-aws/
├── data/                   # Sample genomic datasets (FASTQ/Reference)
├── pipeline/
│   ├── install_tools.sh    # Infrastructure setup & tool dependency management
│   ├── run_pipeline.sh     # Main orchestration engine
│   └── analysis/           # Intermediate processing (BAM/SAM/QC)
├── scripts/
│   ├── s3_upload.sh        # S3 Lifecycle & Data Transfer scripts
│   └── jupyter_analysis.py # Downstream VCF parsing & visualization
└── docs/                   # Architecture diagrams & Technical documentation
```
## ⚙️ DEPLOYMENT GUIDE

### 1️⃣ Environment Initialization
```bash
git clone https://github.com/Rishika-Madhanagopal/Genomics-Pipeline-on-AWS.git
cd Genomics-Pipeline-on-AWS
```
### 2️⃣ Cloud Infrastructure Setup
Launch an Ubuntu-based EC2 instance and provision the environment:
```bash
cd pipeline
bash install_tools.sh
```
### 3️⃣ Execution & Data Lifecycle
Execute the core pipeline. The script automates QC, Alignment, and Variant Calling:
```bash
bash run_pipeline.sh
```
Sync validated results to your Amazon S3 Bucket:
```bash
bash ../scripts/s3_upload.sh
```

## 📊 DATA ANALYSIS
Post-pipeline analysis is handled via Jupyter, allowing for interactive exploration of variant distributions:
```bash
pip3 install jupyter pandas matplotlib
jupyter notebook scripts/jupyter_analysis.py
```

## 🛠️ PREREQUISITES

- **AWS Account:** Active access to EC2, S3, Lambda, and Batch.  
- **CLI:** AWS CLI configured with appropriate IAM permissions.  
- **Compute:** Minimum t2.medium instance (t3.large recommended for BWA alignment).

## 🙌 ACKNOWLEDGEMENTS
- **Data Sources:** NCBI SRA & 1000 Genomes Project.
- **Toolkits:** Broad Institute GATK & Wellcome Trust Sanger Institute.
- **Infrastructure:** Amazon Web Services (AWS) Cloud Credits.

### 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
