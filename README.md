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
<img width="577" alt="image" src="https://github.com/user-attachments/assets/e22391db-89c6-464c-a978-ecf81294b986" />

2. In the **Resident** sheet, ensure that the following fields are present:
<img width="786" alt="image" src="https://github.com/user-attachments/assets/4fbf5164-6182-4030-abc1-c3613e095cf1" />
<img width="609" alt="image" src="https://github.com/user-attachments/assets/24f5a39a-2b14-499f-932a-6afd41492696" />

  - Note that the <mark>yellow highlighted</mark> fields are **mandatory** to prevent any parsing error.
    - Non-mandatory fields which are not filled will be shown as an empty string or `null` in the JSON output.
  - **S.No** and **Scenario** are to be supplied in the following format:
      - Scenario should start with `TS`, followed by `XXX_DESCRIPTION`, where `XXX` is the scenario identification number and `DESCRIPTION` is the description of the scenario.
      - Example input:
  <img width="429" alt="image" src="https://github.com/user-attachments/assets/aa891ace-372c-4487-83ea-d3ff7de71f5a" />

  - Total number of **enrolments**, **next year enrolments**, **health plans**, **care reports**, **screenings** and **vaccinations** represents the number of inputs you must provide within their respective sheets so that no parsing error occurs.
      - For example, TS_001 has 3 enrolments. Within the enrolments sheet, we must provide data required for 3 enrolments and not less, otherwise there will be a parsing error. The data required for each sheet will be specified further below.
      - Example input:
   <img width="613" alt="image" src="https://github.com/user-attachments/assets/1f8d8f75-724c-4e04-9881-b70816c1f231" />
   
3. In the **Enrolments** sheet, ensure that the following fields are present:
<img width="825" alt="image" src="https://github.com/user-attachments/assets/59cbf403-6200-411a-aaea-c177e44900fd" />

- For each enrolment, we must specify the **enrolment ID**, **organization ID**, **enrolment start date**, and **enrolment end date**.
- Depending on the total number of enrolments specified in the **Resident** sheet, it is possible that we must include multiple sets of such data. To do so, we simply increase the iteration number within the name of each field.
    - For example:
<img width="710" alt="image" src="https://github.com/user-attachments/assets/5342aeba-7a35-470e-9749-248551ed6fb4" />

4. The same applies to the **NextYearEnrolments** sheet.
5. In the **HealthPlans** sheet, ensure that the following fields are present:
<img width="770" alt="image" src="https://github.com/user-attachments/assets/297c2c47-09c3-4933-9a32-86fab8751b93" />

- For each health plan, we must specify the **health plan ID**, **health plan organization ID**, **health plan start date**, and **health plan end date**.
- Depending on the total number of enrolments specified in the **HealthPlans** sheet, it is possible that we must include multiple sets of such data. To do so, we simply increase the iteration number within the name of each field.
  - For example:
<img width="809" alt="image" src="https://github.com/user-attachments/assets/747304b0-8cab-4e3f-b6b1-7d2dae28c9aa" />

6. The **CareReport** sheets work differently. Depending on the total number of care reports specified in the **Resident sheet**, we create a separate care report sheet with an increasing iteration number.
<img width="218" alt="image" src="https://github.com/user-attachments/assets/6e488096-7529-4711-9310-34e17f2e32c4" />

- Each care report contains some information about itself, and is further split into multiple sections.
- For **care report information** section, ensure that the following fields are present:
  <img width="703" alt="image" src="https://github.com/user-attachments/assets/a19759b0-8206-4ff0-96cb-62efc18c2c6a" />
  - We must specify the **care report ID**, **care report organization ID**, **care report year**, **care report submission date**.
- For **patient level information** section, ensure that the following fields are present:
  <img width="528" alt="image" src="https://github.com/user-attachments/assets/2ccb01ef-f7b0-4669-a2aa-90f7591f109a" />
  - We must specify the **smoking status**, **has number sticks per day**, and **CDMP conditions**.
- For **BMI information** section, ensure that the following fields are present:
  <img width="571" alt="image" src="https://github.com/user-attachments/assets/37ce97bb-c153-4121-a28b-1c64c0275f8b" />
  - We must specify whether **height/weight/waist measurement was taken**, **weight feasibility**, and **weight-height taken date and time**.
- For **smoking** section, ensure that the following field is present:
  <img width="146" alt="image" src="https://github.com/user-attachments/assets/beaf7549-1768-4216-8535-bd2971c74aa2" />
  - We must specify the **smoking assessment date**.
- For **diagnosis** section, ensure that the following fields are present:
  <img width="190" alt="image" src="https://github.com/user-attachments/assets/69e64e63-37f5-4ddc-ae94-4100a11edc0d" />
  - We must specify the **diagnosis code** and **diagnosis year**.
- For **general** or **chronic consults** section, we first specify the number of chronic consults:
  <img width="128" alt="image" src="https://github.com/user-attachments/assets/31eb9693-7285-4728-a71f-7d8a9c0f10d1" />
  - Each set of chronic consult data contains the following fields:
    <img width="249" alt="image" src="https://github.com/user-attachments/assets/7fc7f929-e2a4-4938-b25f-198b8ed05750" />
      - We must specify the **chronic consult data**, **visit mode**, and **visit date**.
  - To specify the next set of chronic consult data, we simply increase the iteration number within the name of each field (for `cc` and not `cr`!).
    - For example:
      <img width="505" alt="image" src="https://github.com/user-attachments/assets/e1d5cb0f-5d34-4b38-8d5b-3a7e068ef4d3" />
- For **screening** section, we first specify the number of screenings:
  <img width="104" alt="image" src="https://github.com/user-attachments/assets/220c7cd3-cac0-4079-8bda-70e75538579d" />
  - Note if number of screenings = 0, then there is no need to fill in the following mandatory fields.
  - Each set of screening data contains the following fields:
    <img width="363" alt="image" src="https://github.com/user-attachments/assets/102aa55c-10c2-4f9e-8a41-968e65db73b2" />



   











  


   

   





