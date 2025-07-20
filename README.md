Overview
========

Welcome to Astronomer! This project was generated after you ran 'astro dev init' using the Astronomer CLI. This readme describes the contents of the project, as well as how to run Apache Airflow on your local machine.

Project Contents
================

Your Astro project contains the following files and folders:

- dags: This folder contains the Python files for your Airflow DAGs. By default, this directory includes one example DAG:
    - `example_astronauts`: This DAG shows a simple ETL pipeline example that queries the list of astronauts currently in space from the Open Notify API and prints a statement for each astronaut. The DAG uses the TaskFlow API to define tasks in Python, and dynamic task mapping to dynamically print a statement for each astronaut. For more on how this DAG works, see our [Getting started tutorial](https://www.astronomer.io/docs/learn/get-started-with-airflow).
- Dockerfile: This file contains a versioned Astro Runtime Docker image that provides a differentiated Airflow experience. If you want to execute other commands or overrides at runtime, specify them here.
- include: This folder contains any additional files that you want to include as part of your project. It is empty by default.
- packages.txt: Install OS-level packages needed for your project by adding them to this file. It is empty by default.
- requirements.txt: Install Python packages needed for your project by adding them to this file. It is empty by default.
- plugins: Add custom or community plugins for your project to this file. It is empty by default.
- airflow_settings.yaml: Use this local-only file to specify Airflow Connections, Variables, and Pools instead of entering them in the Airflow UI as you develop DAGs in this project.

Deploy Your Project Locally
===========================

Start Airflow on your local machine by running 'astro dev start'.

This command will spin up five Docker containers on your machine, each for a different Airflow component:

- Postgres: Airflow's Metadata Database
- Scheduler: The Airflow component responsible for monitoring and triggering tasks
- DAG Processor: The Airflow component responsible for parsing DAGs
- API Server: The Airflow component responsible for serving the Airflow UI and API
- Triggerer: The Airflow component responsible for triggering deferred tasks

When all five containers are ready the command will open the browser to the Airflow UI at http://localhost:8080/. You should also be able to access your Postgres Database at 'localhost:5432/postgres' with username 'postgres' and password 'postgres'.

Note: If you already have either of the above ports allocated, you can either [stop your existing Docker containers or change the port](https://www.astronomer.io/docs/astro/cli/troubleshoot-locally#ports-are-not-available-for-my-local-airflow-webserver).

Deploy Your Project to Astronomer
=================================

If you have an Astronomer account, pushing code to a Deployment on Astronomer is simple. For deploying instructions, refer to Astronomer documentation: https://www.astronomer.io/docs/astro/deploy-code/

Contact
=======

The Astronomer CLI is maintained with love by the Astronomer team. To report a bug or suggest a change, reach out to our support.


## Difference Between maths_operation.py and taskflowapi.py
In **maths_operation.py**, tasks are defined using traditional PythonOperator, requiring manual setup of task IDs, XComs for data passing, and explicit dependency chaining using >>. In contrast, **taskflowapi.py** leverages Apache Airflow's modern TaskFlow API with the @task decorator, enabling cleaner syntax and automatic XCom handling. This simplifies task creation, data flow, and improves readability without the boilerplate of PythonOperator.

Here’s a professionally written version of your execution steps section for documentation (like a `README.md`):

---

##  Steps to Execute the Files

1. **Ensure Python Version Compatibility**
   Use Python version **3.10 to 3.12** for optimal compatibility with Apache Airflow and Astro.

2. **Install Astro CLI (Astronomer CLI)**
   Open your terminal or PowerShell and run the following command to install the Astro CLI:

   ```powershell
   Invoke-WebRequest -UseBasicParsing https://install.astronomer.io | Invoke-Expression
   ```

3. **Install Apache Airflow (v2.9.0)**
   Install Airflow using the appropriate constraints for Python 3.10:

   ```bash
   pip install apache-airflow==2.9.0 --constraint "https://raw.githubusercontent.com/apache/airflow/constraints-2.9.0/constraints-3.10.txt"
   ```

4. **Start Your Airflow Project (with Astro CLI)**
   Launch the Airflow environment:

   ```bash
   astro dev start
   ```

5. **Stop the Airflow Project**
   To shut down the development environment:

   ```bash
   astro dev stop
   ```

6. **Restart the Airflow Project (after changes)**
   Use this command to restart the environment after modifying DAG files:

   ```bash
   astro dev restart
   ```
