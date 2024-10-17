# MIST 4610 Fall 2024 Project 1

## Group 2 Team Members
- Aryan Patel (insert @ to repo)
- Caleb Maine (insert @ to repo)
- Campbell Durbin (insert @ to repo)
- Chandler Boyd (insert @ to repo)
- Maddie Sells (insert @ to repo)

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
![image](https://github.com/user-attachments/assets/22c46b81-886d-4094-bd75-c20e81a664d0)

![image](https://github.com/user-attachments/assets/d935963b-f9b0-437a-9e44-9c7729cff202)

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


## Database Information
Database Name: ns_4610Fa24Group2
