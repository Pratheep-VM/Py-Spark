# PySpark Setup Notes

 Here are the steps I used to get everything running on Windows 11.

## 1. Downloads
These are the versions I used (Spark 4.0.1 requires Hadoop 3.4.0):

*   **Anaconda:** [Download](https://www.anaconda.com/download)
*   **Java JDK:** JDK 17 or 21 [Oracle](https://www.oracle.com/in/java/technologies/downloads/)
*   **Apache Spark:** 4.0.1 [Spark Site](https://spark.apache.org/downloads.html)
*   **Winutils:** Hadoop 3.4.0 [GitHub Repo](https://github.com/kontext-tech/winutils)

## 2. Windows Environment Variables
After downloading, I extracted the files and set up the system variables so Windows can find Spark and Hadoop.

**Folder Structure:**
*   Spark: `C:\Spark\spark-4.0.1-bin-hadoop3`
*   Hadoop: `C:\hadoop\bin` (Put `winutils.exe` here)

**System Variables:**
1.  **SPARK_HOME** -> `C:\Spark\spark-4.0.1-bin-hadoop3`
2.  **HADOOP_HOME** -> `C:\hadoop`
3.  **JAVA_HOME** -> `C:\Program Files\Java\jdk-21` 

**Path Variable:**
*   Added `%SPARK_HOME%\bin`
*   Added `%HADOOP_HOME%\bin`
*   Added `%JAVA_HOME%\bin`

## 3. Conda Setup Commands
Run these in the Anaconda Prompt to set up the Python environment:

```bash
# Create and activate environment
conda create new --name pyspark 
conda activate pyspark

# Install dependencies
conda install -c conda-forge findspark 
conda install jupyter
# or use: pip install notebook

# Start
jupyter notebook