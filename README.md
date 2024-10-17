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
![image](https://github.com/user-attachments/assets/335e26be-880b-4133-93b7-2bf3746d7b24)

![image](https://github.com/user-attachments/assets/40f18852-0b7f-4a1d-80a7-a8dbb3d6410c)

![image](https://github.com/user-attachments/assets/6ee64b9a-da00-43d9-89cb-770e12c8cdd3)

![image](https://github.com/user-attachments/assets/1bb3cc1c-c4c7-47a4-a0fe-d48fda7050b0)

![image](https://github.com/user-attachments/assets/a658b321-3085-49a3-9821-c2ba45969714)

![image](https://github.com/user-attachments/assets/96156517-3e90-4327-ad98-e231bc354232)

![image](https://github.com/user-attachments/assets/1a8b7598-1e3e-4c11-8402-65955ad98a46)

![image](https://github.com/user-attachments/assets/5446945e-90f0-4ef7-b9eb-b348542afa8f)

![image](https://github.com/user-attachments/assets/7ac8e17d-c416-4bd8-84a5-f3bb3c7ea0a1)

![image](https://github.com/user-attachments/assets/ea8a8939-c76e-40e2-9c6b-2b3900834858)

![image](https://github.com/user-attachments/assets/dfd4a9a5-3b41-4630-ba2d-f1ef91323349)

## Ten Queries

## Database Information
Database Name: ns_4610Fa24Group2
