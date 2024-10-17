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

On the other hand, there is a one-to-one identifying relationship between Appointment and Bill as a bill only exists if there is an appointment, and an appointment generates only one bill. Appointment’s primary key therefore appears as a foreign key in Bill.

There are also one-to-many non-identifying relationships between Patient and EmergencyContact, Doctor and Prescription, MedicalRecord and Prescription, as well as MedicalRecord and TestResult. These relationships follow the same logic as the one-to-many non-identifying relationships discussed earlier:
- Each emergency contact is associated with only one patient, but a patient can have many emergency contacts. 
- Each prescription is written by only one doctor, but a doctor can write many prescriptions. 
- Each prescription is found in only one medical record, but a medical record can contain many prescriptions. 
- Each test result is found on only one medical record, but a medical record can contain many test results.
Again, the primary key of the applicable entity appears as a foreign key in the related entity and these relationships are designated as non-identifying because each of the entities can exist independently. 

The final relationship within the data model is a one-to-one identifying relationship between Patient and Medical Record. The logic supporting this relationship is as follows: a medical record only exists if there is a patient, and a patient only has one medical record. With that said, Patient’s primary key appears as a foreign key in the MedicalRecord entity.  


## Data Dictionary
![image](https://github.com/user-attachments/assets/d0183794-0fce-4a42-839b-1e7a6fb79622)

![image](https://github.com/user-attachments/assets/c39b7141-39cc-413d-b815-543992017666)

![image](https://github.com/user-attachments/assets/4ae72d4c-6660-4486-9540-50e9776efff8)

![image](https://github.com/user-attachments/assets/0b03bb69-d5f8-48d3-b387-23bc1ac8664a)

![image](https://github.com/user-attachments/assets/dc061b11-6490-4bb0-afef-13de9c0c5117)

![image](https://github.com/user-attachments/assets/fdf47aaa-47b8-457c-966b-bd3f0f62a316)

![image](https://github.com/user-attachments/assets/f2e2cb99-412a-43d6-8a30-c71e0523c79f)

![image](https://github.com/user-attachments/assets/fd05bb0a-bde9-4416-a1fc-10b40110ffbb)

![image](https://github.com/user-attachments/assets/1feece2f-ac24-441c-a294-46cc026687b7)

![image](https://github.com/user-attachments/assets/80c1d2bb-e959-4dd0-af98-c969cb7866a3)

![image](https://github.com/user-attachments/assets/2d23dbf3-e77b-492a-99b2-ca080520efba)

## Ten Queries

## Database Information
Database Name: ns_4610Fa24Group2
