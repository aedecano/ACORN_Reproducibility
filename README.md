# Tutorial: Data Publication and Promoting Reproducibility in Bioinformatics Research

## Introduction

Bioinformatics is a field that heavily relies on the availability of data and computational methods. Reproducibility ensures that research findings can be consistently replicated by others using the same data and methods. This tutorial will guide you through the process of data publication and promote reproducibility in bioinformatics research.

## Step 1: Preparing Your Data for Publication

### 1.1 Data Organization

- **Raw Data:** Store raw sequencing data in standard formats like FASTQ, BAM, or VCF.
- **Processed Data:** Include files like alignment results, annotated sequences, or expression matrices.
- **Metadata:** Provide detailed metadata including sample information, experimental conditions, and data processing steps.

**Example Directory Structure:**
```
/project-directory

/raw-data

sample1.fastq
sample2.fastq

/processed-data

sample1_aligned.bam
sample2_aligned.bam

/metadata

samples_metadata.csv
processing_protocol.md
```

### 1.2 Data Documentation

- **Readme File:** Create a README.md file to explain the project, data structure, and how to use the data.
- **Protocol Documentation:** Include detailed protocols for data generation and processing in a markdown file or PDF.

**Example Readme File:**
```
Project Title
Description
Brief description of the project.

Data Structure
Explanation of the directory structure and files.

Usage
Instructions on how to access and use the data.

Contact
Contact information for further inquiries.
```

## Step 2: Choosing a Data Repository

Select a repository that suits your data type and ensures long-term accessibility. Consider repositories like:

- **NCBI Sequence Read Archive (SRA):** For raw sequence data.
  https://www.ncbi.nlm.nih.gov/sra
- **Gene Expression Omnibus (GEO):** For gene expression data.
  https://www.ncbi.nlm.nih.gov/gds
- **Figshare:** For a wide variety of data types.
  https://figshare.com/
- **Zenodo:** For datasets with a DOI for citation.
  https://zenodo.org/

## Step 3: Uploading and Publishing Data

### 3.1 Preparing Files for Upload

Compress large files to reduce upload time and storage space. Use standard compression formats like `.gz` or `.zip`.

**Example Compression Command:**
```
gzip sample1.fastq
```

### 3.2 Submitting Data to a Repository
Follow the submission guidelines of your chosen repository. Generally, you will need to:

Create an account.
Prepare a data submission form with metadata and project description.
Upload your files.

### 3.3 Obtaining a DOI
Ensure that your dataset receives a Digital Object Identifier (DOI) for easy citation.
Register through https://www.doi.org/

Example Data Citation:
```
Author(s). (Year). Title of dataset (Version) [Data set]. Repository Name. DOI
```
## Step 4: Making Your Research Reproducible

### 4.1 Sharing Analysis Scripts
Provide all scripts and tools used for data analysis. Use version control systems like Git to track changes.

GitHub: Host code repositories with version control.
Bitbucket: Another platform for version control and collaboration.
Example GitHub Repository Structure:
```
/project-directory

    /data

    /scripts

        analysis_script.R

        plotting_script.py

    /results

    README.md
```

Github tutorial: https://srse-git-github-zero2hero.netlify.app/00-intro-to-version-control/04a-anatomy-repo/

### 4.2 Setting Up a Conda Environment
Using a Conda environment ensures that all dependencies and software versions are consistent across different systems.

Step-by-Step Guide to Creating a Conda Environment:

1. Install Miniconda or Anaconda:
Follow the installation instructions from the official Conda documentation: https://docs.conda.io/en/latest/

2. Create a New Environment:
```
conda create --name myenv python=3.8
```
3. Activate the Environment:
```
conda activate myenv
```
4. Install Required Packages:
```
conda install numpy pandas scipy
conda install -c bioconda biopython
```
5. Export Environment for Reproducibility:
```   
conda env export > environment.yml
```
Example environment.yml File:
```
name: myenv
channels:
  - bioconda
  - defaults
dependencies:
  - python=3.8
  - numpy=1.19.2
  - pandas=1.1.3
  - scipy=1.5.2
  - biopython=1.78
```
Others can recreate this environment using:
```
conda env create -f environment.yml
```
### 4.3 Containerization
Use containerization tools like Docker to ensure that your computational environment can be reproduced.

Example Dockerfile:
```
FROM ubuntu:20.04

# Install necessary packages
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    r-base

# Copy scripts into the container
COPY ./scripts /scripts

# Set the working directory
WORKDIR /scripts

# Run the analysis script
CMD ["python3", "analysis_script.py"]
```

## Step 5: Providing Detailed Methods and Protocols
Ensure that your publication includes a detailed methods section describing:

Data collection.

Data processing.

Statistical analysis.

Software and tools used, with version numbers.

# References
Wilkinson, M. D., Dumontier, M., Aalbersberg, I. J., et al. (2016). The FAIR Guiding Principles for scientific data management and stewardship. Scientific Data, 3, 160018. doi:10.1038/sdata.2016.18

Eric W Sayers, Evan E Bolton, J Rodney Brister, Kathi Canese, Jessica Chan, Donald C Comeau, Catherine M Farrell, Michael Feldgarden, Anna M Fine, Kathryn Funk, Eneida Hatcher, Sivakumar Kannan, Christopher Kelly, Sunghwan Kim, William Klimke, Melissa J Landrum, Stacy Lathrop, Zhiyong Lu, Thomas L Madden, Adriana Malheiro, Aron Marchler-Bauer, Terence D Murphy, Lon Phan, Shashikant Pujar, Sanjida H Rangwala, Valerie A Schneider, Tony Tse, Jiyao Wang, Jian Ye, Barton W Trawick, Kim D Pruitt, Stephen T Sherry, Database resources of the National Center for Biotechnology Information in 2023, Nucleic Acids Research, Volume 51, Issue D1, 6 January 2023, Pages D29–D38, https://doi.org/10.1093/nar/gkac1032

Anaconda, Inc. (2021). Conda Documentation. Retrieved from https://docs.conda.io/projects/conda/en/latest/index.html

Docker, Inc. (2021). Docker Documentation. Retrieved from https://docs.docker.com/get-started/



