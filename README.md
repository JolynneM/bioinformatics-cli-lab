
# =========================
# 1. Install Miniconda
# =========================

# Download Miniconda installer (Linux version)
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# Run the installer
bash Miniconda3-latest-Linux-x86_64.sh


# =========================
# 2. Initialise Conda in the shell
# =========================

# Set up Conda so "conda activate" works in terminal
conda init

# Reload shell configuration so changes take effect immediately
source ~/.bashrc


# =========================
# 3. Configure Conda channels
# =========================

# Add main community channel (scientific computing packages)
conda config --add channels conda-forge

# Add bioinformatics-specific channel (FastQC, samtools, etc.)
conda config --add channels bioconda

# Ensure Conda prioritises channels strictly (prevents conflicts)
conda config --set channel_priority strict

# Remove default Anaconda channels (avoids license/TOS issues)
conda config --remove channels defaults


# =========================
# 4. Create and activate environment
# =========================

# Create a clean isolated environment for bioinformatics
conda create -n bioinfo python=3.10 -y

# Activate the environment (switch into it)
conda activate bioinfo


# =========================
# 5. Install FastQC tool
# =========================

# Install FastQC (quality control tool for sequencing data)
conda install fastqc -y


# =========================
# 6. Download example sequencing data (ENA/SRA)
# =========================

# Download paired-end FASTQ file (read 1)
wget ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR116/091/SRR11669591/SRR11669591_1.fastq.gz

# Download paired-end FASTQ file (read 2)
wget ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR116/091/SRR11669591/SRR11669591_2.fastq.gz