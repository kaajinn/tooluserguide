# User Guide

## Quick start
1. Ensure you have Java `8` or above installed in your Computer.
2. Copy the `.jar` file and input `.xlsx` file to a new folder. This will be the root folder.
3. Within the root folder, create another new folder (name it anything you like). This will be the output folder used to store the output JSON files.
4. Within the root folder, open a command terminal (Right-click > Open in Terminal) and enter `java -jar IDMInput <absolute path to .xlsx file> <absolute path to output folder>`.
    - For example, `java -jar IDMInput "C:\Users\User\Desktop\tool\data.xlsx" "C:\Users\User\Desktop\tool\output"`.
4. Within the output folder, a number of JSON files will be generated, depending on the number of inputs within the `.xlsx` file.

## Proper data formatting within the input `.xlsx` file
1. Firstly, input `.xlsx` file should have the following sheets.
<p align="center">
<img width="577" alt="image" src="https://github.com/user-attachments/assets/e22391db-89c6-464c-a978-ecf81294b986" />
</p>

2. In the **Resident** sheet, ensure that the following fields are present:
<p align="center">
<img width="786" alt="image" src="https://github.com/user-attachments/assets/4fbf5164-6182-4030-abc1-c3613e095cf1" />
<img width="609" alt="image" src="https://github.com/user-attachments/assets/24f5a39a-2b14-499f-932a-6afd41492696" />
</p>

  - Note that the <mark>yellow highlighted</mark> fields are **mandatory** to prevent any parsing error.
    - Non-mandatory fields which are not filled will be shown as an empty string or `null` in the JSON output.
  - **S.No** and **Scenario** are to be supplied in the following format:
      - Scenario should start with `TS`, followed by `XXX_DESCRIPTION`, where `XXX` is the scenario identification number and `DESCRIPTION` is the description of the scenario.
      - Example input:
  <p align="center">
  <img width="429" alt="image" src="https://github.com/user-attachments/assets/aa891ace-372c-4487-83ea-d3ff7de71f5a" />
  </p>
  
  - Total number of **enrolments**, **next year enrolments**, **health plans**, **care reports**, **screenings** and **vaccinations** represents the number of inputs you must provide within their respective sheets so that no parsing error occurs.
      - For example, TS_001 has 3 enrolments. Within the enrolments sheet, we must provide data required for 3 enrolments and not less, otherwise there will be a parsing error. The data required for each sheet will be specified further below.
      - Example input:
   <p align="center"> 
   <img width="613" alt="image" src="https://github.com/user-attachments/assets/1f8d8f75-724c-4e04-9881-b70816c1f231" />
   </p>
   
3. In the **Enrolments** sheet, ensure that the following fields are present:
<p align="center">
<img width="802" alt="image" src="https://github.com/user-attachments/assets/907f7b9c-61ee-498b-aad8-3922fd171722" />
</p>

- For each enrolment, we must specify the **enrolment ID**, **organization ID**, **enrolment start date**, and **enrolment end date**.
- Depending on the total number of enrolments specified in the **Resident** sheet, it is possible that we must include multiple sets of such data. To do so, we simply increase the iteration number within the name of each field.
    - For example:
<p align="center">
<img width="716" alt="image" src="https://github.com/user-attachments/assets/beaaa59b-f53a-45ec-8988-c12e4a2b9a48" />
</p>

4. The same applies to the **NextYearEnrolments** sheet, except fields start with an additional **"ny_"** prefix.
5. In the **HealthPlans** sheet, ensure that the following fields are present:
<p align="center">
<img width="843" alt="image" src="https://github.com/user-attachments/assets/5612f48a-2a59-4d30-a5e2-e98cd97898d0" />
</p>

- For each health plan, we must specify the **health plan ID**, **health plan organization ID**, **health plan start date**, and **health plan end date**.
- Depending on the total number of enrolments specified in the **Resident** sheet, it is possible that we must include multiple sets of such data. To do so, we simply increase the iteration number within the name of each field.
  - For example:
<p align="center">
<img width="821" alt="image" src="https://github.com/user-attachments/assets/0424f872-6935-467b-90ec-95d623d44dde" />
</p>

6. The **CareReport** sheets work differently. Depending on the total number of care reports specified in the **Resident sheet**, we create a separate care report sheet with an increasing iteration number.
<p align="center">
<img width="218" alt="image" src="https://github.com/user-attachments/assets/6e488096-7529-4711-9310-34e17f2e32c4" />
</p>

- Each care report contains some information about itself, and is further split into multiple sections.
- For **care report information** section, ensure that the following fields are present:
  <p align="center">
  <img width="770" alt="image" src="https://github.com/user-attachments/assets/9c667592-affe-416c-baa1-e0016d93b327" />
  </p>
  
  - We must specify the **care report ID**, **care report organization ID**, **care report year**, **care report submission date**.
- For **patient level information** section, ensure that the following fields are present:<br>
  <p align="center">
  <img width="397" alt="image" src="https://github.com/user-attachments/assets/8c0a41f8-58c2-4bd5-8311-a0d439e72ca5" />
  </p>
  
  - We must specify the **smoking status**, **has number sticks per day**, and **CDMP conditions**.
- For **BMI information** section, ensure that the following fields are present:
  <p align="center">
  <img width="590" alt="image" src="https://github.com/user-attachments/assets/4c11ef88-dc24-4b19-ae42-72c67c3cbbbd" />
  </p>
  
  - We must specify whether **height/weight/waist measurement was taken**, **weight feasibility**, and **weight-height taken date and time**.
- For **smoking** section, ensure that the following field is present:<br>
  <p align="center">
  <img width="160" alt="image" src="https://github.com/user-attachments/assets/4632f633-f1cb-4caf-95fd-d26035bc66a7" />
  </p>
  
  - We must specify the **smoking assessment date**.
- For **diagnosis** section, ensure that the following fields are present:<br>
  <p align="center">
  <img width="201" alt="image" src="https://github.com/user-attachments/assets/efcd29e2-a397-4e52-aa5d-84cee66cda9c" />
  </p>
  
  - We must specify the **diagnosis code** and **diagnosis year**.
- For **general** or **chronic consults** section, we first specify the number of chronic consults:
  <p align="center">
  <img width="128" alt="image" src="https://github.com/user-attachments/assets/31eb9693-7285-4728-a71f-7d8a9c0f10d1" />
  </p>
  
  - Each set of chronic consult data contains the following fields:<br>
    <p align="center">
    <img width="256" alt="image" src="https://github.com/user-attachments/assets/fc701e00-1003-429f-be27-a140b5c33631" />
    </p>
    
      - We must specify the **chronic consult data**, **visit mode**, and **visit date**.
  - To specify the next set of chronic consult data, we simply increase the iteration number within the name of each field (for `cc` and not `cr`!):
    <p align="center">
    <img width="505" alt="image" src="https://github.com/user-attachments/assets/e1d5cb0f-5d34-4b38-8d5b-3a7e068ef4d3" />
    </p>
    
- For **screening** section, we first specify the number of screenings:<br>
  <p align="center">
  <img width="104" alt="image" src="https://github.com/user-attachments/assets/220c7cd3-cac0-4079-8bda-70e75538579d" />
  </p>
  
  - Each set of screening data contains the following fields:<br>
    <p align="center">
    <img width="364" alt="image" src="https://github.com/user-attachments/assets/2f56d528-fb3d-4ced-92ec-400bdde4ef22" />
    </p>
    
    - We must specify the **screening date**, **screening type**, **whether there is screening value**, and **clinical indication**.
  - To specify the next set of screening data, we simply increase the iteration number within the name of each field (for `s` and not `cr`!):
    <p align="center">
    <img width="734" alt="image" src="https://github.com/user-attachments/assets/d51348bd-4995-455c-a384-bad62ef9bd70" />
    </p>
    
- For **vaccination** section, we first specify the number of screenings:
  <p align="center">
  <img width="122" alt="image" src="https://github.com/user-attachments/assets/1c493d2b-a3c6-4e6b-9f71-dc1a3412ae2e" />
  </p>
  
  - Each set of vaccination data contains the following fields:<br>
    <p align="center">
    <img width="247" alt="image" src="https://github.com/user-attachments/assets/bb1d7b6f-0403-487f-8b16-d0435d530771" />
    </p>
    
    - We must specify the **vaccination date**, and **vaccination type**.
  - To specify the next set of vaccination data, we simply increase the iteration number within the name of each field (for `v` and not `cr`!):
    <p align="center">
    <img width="497" alt="image" src="https://github.com/user-attachments/assets/f846bfb3-b535-49d7-9b55-e1b595b8c056" />
    </p>
    
- For **measurement** section, we first specify the number of measurements:<br>
  <p align="center">
  <img width="122" alt="image" src="https://github.com/user-attachments/assets/4503287f-0806-4520-b4ba-ce922d94f1d9" />
  </p>
  
  - Each set of measurement data contains the following fields:<br>
    <p align="center">
    <img width="394" alt="image" src="https://github.com/user-attachments/assets/e8e7a73c-0dbf-466f-8169-971bc9e408bc" />
    </p>
    
    - We must specify the **measurement code**, **measurement date**, and **whether there is measurement value**.
  - To specify the next set of measurement data, we simply increase the iteration number within the name of each field (for `measurement` and not `cr`!):
    <p align="center">
    <img width="789" alt="image" src="https://github.com/user-attachments/assets/4dec3b9f-c2e0-42e7-b50a-ba7ba124159f" />
    </p>
    
- For **diabetes** section, we further split into 2 subsections, <ins>DRP</ins> and <ins>DFS</ins>. Firstly, we specify the number of DRP sections: <br>
<p align="center">
<img width="122" alt="image" src="https://github.com/user-attachments/assets/972596fd-b930-4c16-ad81-e630927cd88c" />
</p>
 
  - Each set of DRP data contains the following fields:<br>
    <p align="center">
    <img width="487" alt="image" src="https://github.com/user-attachments/assets/d35b14e6-e357-46ed-8095-2ab98a7f8f3b" />
    </p>
    
    - We must specify **whether DRP is conducted** (Yes/No), **DRP date**, **DRP type**, and **DRP result**.
  - To specify the next set of DRP data, we simply increase the iteration number within the name of each field (for `drp` and not `cr`!):
    <p align="center">
    <img width="946" alt="image" src="https://github.com/user-attachments/assets/4ae370af-2ec1-426e-b423-257009260f21" />
    </p>
    
  - Next, we specify the number of DFS sections: <br>
<p align="center">
<img width="127" alt="image" src="https://github.com/user-attachments/assets/0e39b809-0c27-4568-8994-64600185444c" />
</p>

  - Each set of DFS data contains the following fields:<br>
    <p align="center">
    <img width="451" alt="image" src="https://github.com/user-attachments/assets/daa0e5ab-3775-4e56-9482-b0f3d7ad1b0f" />
    </p>
    
    - We must specify **whether DFS is conducted** (Yes/No), **DFS date**, **DRP type**, and **DFS outcome**.
  - To specify the next set of DFS data, we simply increase the iteration number within the name of each field (for `dfs` and not `cr`!):
    <p align="center">
    <img width="908" alt="image" src="https://github.com/user-attachments/assets/942ca116-e53a-429d-9c15-39b0c71a08db" />
    </p>
    
7. In the **Screenings** sheet, ensure that the following fields are present: <br>
<p align="center">
<img width="628" alt="image" src="https://github.com/user-attachments/assets/e85ee3c9-7148-4ff3-91dc-78bc1afe9024" />
</p>

- For each screening, we must specify the **screening date**, **screening type**, **EISS result**.
- Depending on the total number of screenings specified in the **Resident** sheet, it is possible that we must include multiple sets of such data. To do so, we simply increase the iteration number within the name of each field.
    - For example:
<p align="center">
<img width="597" alt="image" src="https://github.com/user-attachments/assets/bf41d7d0-3604-4b90-8afe-66d121d8a603" />
</p>

8. In the **Vaccinations** sheet, ensure that the following fields are present:
<p align="center">
<img width="1001" alt="image" src="https://github.com/user-attachments/assets/74e2b8fc-aec3-492b-bd8f-0f3ce648cc38" />
</p>

- For each vaccination, we must specify the **vaccination type**, **claim status**, **validation result**, **max claim reached step**, **dose step**, **dose count for course completion**, **date of given vaccination**, **exceptional conditions**.
- Depending on the total number of vaccinations specified in the **Resident** sheet, it is possible that we must include multiple sets of such data. To do so, we simply increase the iteration number within the name of each field.
    - For example:
<p align="center">
<img width="977" alt="image" src="https://github.com/user-attachments/assets/31afef4a-973c-47a9-a95d-6a3b8e8d22d8" />
</p>

## Example output JSON files
- A single output JSON file is generated for each scenario, containing only that scenario's data. These files will be named `TSXXX` where `XXX` refers to the scenario identifcation number.
- An additional JSON file `AllTestData.` containing the data of all scenarios is also generated.
- Example of a single output JSON file:
<p align="center">
<img width="475" alt="image" src="https://github.com/user-attachments/assets/a92dd407-769c-46bc-b6ee-c10dd4e7fee8" />
</p>
<p align="center">
<img width="418" alt="image" src="https://github.com/user-attachments/assets/9977bbb0-ef2c-4497-9a0f-dfa5c09bf046" />
</p>
<p align="center">
<img width="349" alt="image" src="https://github.com/user-attachments/assets/cc996a3f-9c9c-496d-8209-e66237836c6b" />
</p>
<p align="center">
<img width="334" alt="image" src="https://github.com/user-attachments/assets/19f26350-7ad4-4dca-96d6-ae8c6c3b114e" />
</p>
<p align="center">
<img width="344" alt="image" src="https://github.com/user-attachments/assets/59e32c45-9d0e-4422-a90f-5542f36be397" />
</p>
<p align="center">
<img width="313" alt="image" src="https://github.com/user-attachments/assets/07aaddf8-737e-4fc9-84fa-80085b80ed73" />
</p>
