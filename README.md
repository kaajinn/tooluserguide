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
  - **S.No** and **Scenario** are to be supplied in the following format:
      - Scenario should start with `TS`, followed by `XXX_DESCRIPTION`, where `XXX` is the scenario identification number and `DESCRIPTION` is the description of the scenario.
      - Example input:
  <img width="429" alt="image" src="https://github.com/user-attachments/assets/aa891ace-372c-4487-83ea-d3ff7de71f5a" />

  - Total number of **enrolments**, **next year enrolments**, **health plans**, **care reports**, **screenings** and **vaccinations** represents the number of inputs you must provide within their respective sheets so that no parsing error occurs.
      - For example, TS_001 has 3 enrolments. Within the enrolments sheet, we must provide data required for 3 enrolments and not less, otherwise there will be a parsing error. The data required for each sheet will be specified further below.
      - Example input:
   <img width="613" alt="image" src="https://github.com/user-attachments/assets/1f8d8f75-724c-4e04-9881-b70816c1f231" />

