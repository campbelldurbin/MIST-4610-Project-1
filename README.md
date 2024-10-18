# MIST 4610 Fall 2024 Project 1

## Group 2 Team Members
- Aryan Patel [@AryanUGA](https://github.com/AryanUGA)
- Caleb Maine [@trynagetdone](https://github.com/trynagetdone)
- Campbell Durbin [@campbelldurbin](https://github.com/campbelldurbin)
- Chandler Boyd [@ChandlerBoyd7](https://github.com/ChandlerBoyd7)
- Maddie Sells [@mrs34516](https://github.com/mrs34516)

## Scenario Description
Our data model and database were created to represent and manage the operations of a small, affordable general care clinic staffed by board-certified nurses and doctors who diagnose and treat minor illnesses in convenient retail locations (e.g. Kroger). At the core of this model is the Appointment entity, which helps to ensure streamlined data management and operations as the key supporting entities – Nurse, Doctor, Patient, Room, Insurance, and Bill – are each related to the Appointment entity. In addition to serving patients through appointments, the clinic also fulfills prescriptions and stores medical records, test results, and emergency contacts.

## Data Model
![Revised Data Model Project 1](https://github.com/user-attachments/assets/e56c488c-3bcb-4cf8-bb9e-2432e46e1cce)

Our model features 11 entities: Appointment, Bill, Doctor, EmergencyContact, Insurance, MedicalRecord, Nurse, Patient, Prescription, Room, and TestResult. As mentioned, the Appointment entity serves as the backbone of our model. The Insurance, Doctor, Patient, Nurse, and Room entities each have a one-to-many non-identifying relationship with the Appointment entity. Thus, each of their primary keys appears as a foreign key within the Appointment entity. These are classified as one-to-many relationships because each instance of the Appointment entity is associated with a single instance of each supporting entity, while each supporting entity can be linked to multiple appointments. These are non-identifying relationships because each supporting entity can exist independently of the Appointment entity. The specific logic supporting these relationships is as follows:
- Each appointment is associated with only one patient, but a patient can have many appointments.
- Each appointment is assigned to only one doctor, but a doctor can be assigned to many appointments.
- Each appointment is assigned to only one nurse, but a nurse can be assigned to many appointments.
- Each appointment is assigned to only one room, but a room can be assigned to many appointments.
- Each appointment is associated with only one insurance policy, but an insurance policy can be associated with many appointments. 

Additionally, there is a one-to-many non-identifying recursive relationship within the Doctor entity, which results in the "supervisorId" foreign key. This relationship indicates that while a doctor has only one supervising doctor, one doctor can supervise many other doctors. Again, this relationship is non-identifying because each and any of the doctors can exist independently of one another. On the other hand, there is a one-to-one identifying relationship between Appointment and Bill as a bill only exists if there is an appointment, and an appointment generates only one bill. Appointment’s primary key therefore appears as a foreign key in Bill.

There are also one-to-many non-identifying relationships between Patient and EmergencyContact, Doctor and Prescription, MedicalRecord and Prescription, as well as MedicalRecord and TestResult. These relationships follow the same logic as the one-to-many non-identifying relationships discussed earlier:
- Each emergency contact is associated with only one patient, but a patient can have many emergency contacts. 
- Each prescription is written by only one doctor, but a doctor can write many prescriptions. 
- Each prescription is found in only one medical record, but a medical record can contain many prescriptions. 
- Each test result is found on only one medical record, but a medical record can contain many test results.

Again, the primary key of the entity representing the 'one' side in the one-to-many relationship appears as a foreign key in the entity representing the 'many' side, and these relationships are designated as non-identifying because each of the entities can exist independently of one another. 

The final relationship within the data model is a one-to-one identifying relationship between Patient and MedicalRecord. The logic supporting this relationship is as follows: a medical record only exists if there is a patient, and a patient only has one medical record. With that said, Patient’s primary key appears as a foreign key in the MedicalRecord entity.  


## Data Dictionary
![image](https://github.com/user-attachments/assets/bcde0ac3-0f09-4a81-8655-965eda364f79)

![image](https://github.com/user-attachments/assets/4db7f242-167d-4288-a1fe-b3885d1f879a)

![image](https://github.com/user-attachments/assets/1a346d4d-6f12-4324-83d6-8986533ffa7b)

![image](https://github.com/user-attachments/assets/127c54e2-ab80-4e61-85c7-55a7cc205ada)

![image](https://github.com/user-attachments/assets/b449fbef-b122-44b2-b1ae-e4d62b30ba42)

![image](https://github.com/user-attachments/assets/596a4b49-fca0-4462-a824-208887fc0f4c)

![image](https://github.com/user-attachments/assets/159d0998-6b96-4100-938f-f49a97a3390d)

![image](https://github.com/user-attachments/assets/5f355507-3b38-4b9e-aea4-f6ad3475bf3c)

![image](https://github.com/user-attachments/assets/5ca778fd-579c-4d69-9ef5-bf8a54b8c116)

![image](https://github.com/user-attachments/assets/8aeb8351-622a-42c5-8f9e-b048b43a8f53)

![image](https://github.com/user-attachments/assets/0e52eba9-b431-495d-a903-4250c7d1fc69)

## Ten Queries
1. Write a query to list the total amount owed by insurance companies representing patients who selected insurance as their payment method. Order the results from highest to lowest total amount due and include the count of patients associated with each total.
   
![Screenshot (289)](https://github.com/user-attachments/assets/48224c1b-81f2-4961-9390-d15dfd96ab81)
Justification: Query 1 identifies which insurance companies owe the clinic money and provides the total amount owed by each. This is useful from a managerial perspective because it allows the billing and related departments to accurately report financials, and by revealing the count of patients associated with the total amount due, managers are able to better understand the origins of the totals and can begin to take steps to collect what is owed to the clinic.

2. Write a query to list the first and last name of each doctor who has written more than one prescription, along with the medication name and count of how many times each doctor has prescribed that medication.

![Screenshot (290)](https://github.com/user-attachments/assets/6f4ead20-54be-4757-9b53-9aee21fe0c8d)
Justification: Query 2 is useful from a managerial standpoint because it assists managers in understanding prescribing trends, specifically which medications are prescribed most often and by which doctors. This information serves to support various functions including stock management, compliance, and performance analysis. 

3. Write a query to list the first name, last name, and salary of each nurse whose salary is greater than the minimum salary of doctors at the clinic.
   
![Screenshot (291)](https://github.com/user-attachments/assets/d125356a-a23f-4a2a-8da0-66adad6aa71c)
Justification: By identifying which nurses are paid more than the lowest paid doctor, Query 3 allows managers to engage in salary benchmarking, which is useful for identifying salary discrepencies and trends. By better understanding this information, managers can work to ensure fair and equal pay across their staff and are better informed when making budgeting and promotion decisions.

4. Write a query to list the names of doctors who have more years of experience than their supervisor. Also list the supervisor's name and the difference in their years of experience. 

![Screenshot (293)](https://github.com/user-attachments/assets/3859286d-4e3d-44cb-bd33-e95caa137e1b)
Justification: Query 4 reveals those doctors who have more years of experience than their supervisor as well as their difference in years of experience, which provides managers with relevant insight into the clinic's hierarchical structure and could support in the decision to possibly re-evaluate roles.

5. Write a query to list the patientId, firstName, lastName, status, and total amount due for those patients who owe more than $100 to the clinic. Order the results in descending order based on the total amount due.

![Screenshot (294)](https://github.com/user-attachments/assets/dd6ec149-2677-443e-8d5e-b822630702af)
Justification: Query 5 allows managers to identify those patients who owe over $100 to the clinic. By identifying these patients, managers can begin to look further into the patient's relevant records, including their appointments, prescriptions, insurance, and test results, and can access their contact information to notify them of their outstanding dues. Further, sorting the amounts owed from highest to lowest and indicating if the patients have at least partially paid their bill(s) allows the manager to strategize and priortize efforts on those patients who owe the most money to the clinic.

6. Write a query to list the names of the nurses who have appointments in the future, as well as the date and time of those appointments.

![Screenshot (295)](https://github.com/user-attachments/assets/f6f494d5-c959-41a5-8bb8-3f4de3eba94a)
Justification: Query 6 would be useful for the clinic manager when needing to assign nurses to new appoints as it allows the manager to see which nurses are unavailable and at what times, and at a higher level, which nurses have the fullest upcoming schedule. This query would also offer support in the clinic's general scheduling (doctors, testing, etc.).

7. Write a query to calculate and list the average bill amount for each doctor's appointments in order from highest to lowest.

![Screenshot (296)](https://github.com/user-attachments/assets/b1d1a4c0-13d1-4c7f-9da0-20ec6c7a863f)
Justification: By calculating the average bill amount by doctor, Query 7 allows managers to see which doctors drive the most "revenue" for the clinic. A higher average bill amount could also provide reason to explore a particular doctor's appointment and prescription history to ensure they are providing comprehensive care when diagnosing patients and prescribing particular medications. 

8. Write a query to list the doctorId, first name, and last name of doctors in the clinic who have not wrote any prescriptions.

![Screenshot (297)](https://github.com/user-attachments/assets/9681e204-1718-4787-b5f6-9c5e481d5fc9)
Justification: Query 8 provides significance as it reveals those doctors who have not issued any prescriptions. This is important because it can provide valuable information in assessing the roles, responsibilities, and contributions of each doctor, which can help to highlight any gaps in patient car.

9.  Write a query to list the patient name, phone number, email address, and medical history for those patients who tested positive for any illness and who have any indication of an allergy in their medical history.

![Screenshot (298)](https://github.com/user-attachments/assets/bd29137c-78cb-4967-a9b5-ba7fd8be28d2)
Justification: Query 9 is important from a managerial perspective primarily because it ensures patient safety. By retrieving the contact information for those patients who have tested positive for some illnesss, the clinic can notify these patients of the result so they can receive prompt medical attention. Further, by checking for any allergies, the clinic can be certain the patient is not prescribed any medication they are allergic to, ensuring the safety of the patient and reducing liability for the clinic and its doctors.

10. Write a query to list the patient’s first name, last name, and total number of appointments for those patient's who tested positive for any illness.
    
![Screenshot (302)](https://github.com/user-attachments/assets/b18bd268-4910-45b7-90e3-bebae68b6c33)
Justification: Query 10 offers managerial significance because it reveals those patient's who have tested positive for an illness and provides insight into actions the patient may or may not have taken after the test. The count of the patient's total number of appointments in this context reveals to the clinic if a patient may have needed a follow up appointment to receive greater care after their diagnosis. 

![Screenshot (301)](https://github.com/user-attachments/assets/6241c5d7-2f11-4186-be14-a2080a4bb6c8)

## Database Information
Database Name: ns_4610Fa24Group2
