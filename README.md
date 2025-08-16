# Project Title
Automated Yearly Report Generation using Robotic Enterprise Framework (REFramework)

## Project Description
This RPA workflow automates the end-to-end process of generating and uploading yearly reports for vendors in the ACME System 1 Web Application. The robot will log in, access a list of tasks, and for each WI4 type activity, it will extract the Vendor Tax ID. The bot will then navigate to the reports section, download all corresponding monthly reports for 2024, consolidate them into a single yearly Excel file, and upload the consolidated report. Finally, it will update the original work item with the unique upload ID.

## Project Objective
The primary objective is to eliminate the manual, time-consuming, and repetitive tasks of downloading, compiling, and uploading monthly vendor reports, thereby increasing operational efficiency and ensuring accurate reporting.

This project aims to:

- Improve Efficiency: Significantly reduce the time and effort required to process each vendor report.

- Enhance Data Integrity: Ensure correct data consolidation and accurate reporting, minimizing human error.

- Streamline Operations: Automate a critical business process, allowing staff to focus on more strategic and complex tasks.

## Process Map
<img width="1260" height="235" alt="image" src="https://github.com/user-attachments/assets/e25a31c3-77ce-49a6-9935-23404ec09d43" />

## Process Workflow
<img width="1086" height="734" alt="image" src="https://github.com/user-attachments/assets/67ddb453-0111-4475-9be0-2e5aadc93239" />


### Documentation is included in the Documentation folder ###


### REFrameWork Template ###
**Robotic Enterprise Framework**

* Built on top of *Transactional Business Process* template
* Uses *State Machine* layout for the phases of automation project
* Offers high level logging, exception handling and recovery
* Keeps external settings in *Config.xlsx* file and Orchestrator assets
* Pulls credentials from Orchestrator assets and *Windows Credential Manager*
* Gets transaction data from Orchestrator queue and updates back status
* Takes screenshots in case of system exceptions


### How It Works ###

1. **INITIALIZE PROCESS**
 + ./Framework/*InitiAllSettings* - Load configuration data from Config.xlsx file and from assets
 + ./Framework/*GetAppCredential* - Retrieve credentials from Orchestrator assets or local Windows Credential Manager
 + ./Framework/*InitiAllApplications* - Open and login to applications used throughout the process

2. **GET TRANSACTION DATA**
 + ./Framework/*GetTransactionData* - Fetches transactions from an Orchestrator queue defined by Config("OrchestratorQueueName") or any other configured data source

3. **PROCESS TRANSACTION**
 + *Process* - Process trasaction and invoke other workflows related to the process being automated 
 + ./Framework/*SetTransactionStatus* - Updates the status of the processed transaction (Orchestrator transactions by default): Success, Business Rule Exception or System Exception

4. **END PROCESS**
 + ./Framework/*CloseAllApplications* - Logs out and closes applications used throughout the process


