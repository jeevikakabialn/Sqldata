use Augnet
select * from userss

---1.Adminlogin in college addmission----------------
create table AdminLogin
(
AdminId  int Primary key ,
Password varchar(40)
)
insert into AdminLogin values
(334750,'jeev@1234')
select* from AdminLogin
-----------------------------------------------------------------
drop table AdminLogin
------------------------------------------------------------------
-------------------------------------------------------------


--------------
--2.student registration table-------for student registratin login---
--------------------------------------------------------------------------YYYY-MM-DD
CREATE TABLE StudentRegistration (
   StudentID INT PRIMARY KEY IDENTITY(1,1),
   PassWord varchar(50),
   FirstName NVARCHAR(50),
   LastName NVARCHAR(50),
   DateOfBirth DATE,
   Gender NVARCHAR(10),
   Email NVARCHAR(100),
   PhoneNumber NVARCHAR(15),
   Address NVARCHAR(255),
   Nationality NVARCHAR(50),

  
)

insert into StudentRegistration values
('jeevi@123','jeevika','K','2000-12-27','Female','kjeevika85@gmail.com','9361937091','Redhills','Indian')
select *from StudentRegistration
drop table  StudentRegistration
 -------------------Admission Management----------------
 ----coursetable----

 CREATE TABLE Course (
    CourseId INT PRIMARY KEY IDENTITY(1,1),
    CourseName NVARCHAR(100) NOT NULL,
    Duration INT NOT NULL,          -- Duration in years
    IntakeCapacity INT NOT NULL     -- Maximum number of students allowed
)
-- Inserting values into the Course table
INSERT INTO Course VALUES

('Computer Science', 4, 60),    -- 4 years, 60 seats
('Electrical Engineering', 4, 50),    -- 4 years, 50 seats
('Mechanical Engineering', 4, 55),    -- 4 years, 55 seats
('Civil Engineering', 4, 45),    -- 4 years, 45 seats
('Information Technology', 4, 65),    -- 4 years, 65 seats
('Business Administration', 3, 70),    -- 3 years, 70 seats
('Biotechnology', 4, 40),    -- 4 years, 40 seats
('Physics', 3, 30),    -- 3 years, 30 seats
('Mathematics', 3, 35);    -- 3 years, 35 seats

select *from Course
-----------------fee-----------------
CREATE TABLE Fee (
    FeeId INT PRIMARY KEY IDENTITY(1,1),
    AmountPaid DECIMAL(10, 2) NOT NULL,
    PaymentDate DATE NOT NULL,
    CourseId INT NOT NULL,       -- Foreign key referencing Course table
    StudentID INT NOT NULL,      -- Foreign key referencing Student table
   
   
)
drop table Fee
-- Inserting values into the Fee table
INSERT INTO Fee VALUES

(1500.00, '2024-01-10', 1, 1),  -- Student 1 paying for Course 1 (Computer Science)
(2000.00, '2024-01-15', 2, 2),  -- Student 2 paying for Course 2 (Electrical Engineering)
(1800.00, '2024-02-01', 3, 3),  -- Student 3 paying for Course 3 (Mechanical Engineering)
(1700.00, '2024-02-10', 4, 1),  -- Student 1 paying for Course 4 (Civil Engineering)
(1600.00, '2024-03-05', 5, 2),  -- Student 2 paying for Course 5 (Information Technology)
(1300.00, '2024-03-20', 6, 4),  -- Student 4 paying for Course 6 (Business Administration)
(2200.00, '2024-04-01', 7, 3),  -- Student 3 paying for Course 7 (Biotechnology)
(1250.00, '2024-04-10', 8, 4);  -- Student 4 paying for Course 8 (Physics)

select * from Fee
------------Admission table-------------
CREATE TABLE Admission (
    AdmissionId INT PRIMARY KEY IDENTITY(1,1),  -- Unique identifier for each admission record
    StudentId INT NOT NULL,                     -- ID of the student applying for admission
    CourseId INT NOT NULL,                      -- ID of the course the student is applying for
    AdmissionDate DATE NOT NULL,                -- Date of admission application
    Status NVARCHAR(20),                        -- Status of the admission (e.g., "Pending", "Accepted", "Rejected")
    FeesPaid DECIMAL(18, 2) DEFAULT 0.00       -- Fees paid by the student (default is 0)
)
INSERT INTO Admission VALUES

    (5, 1, '2024-10-01', 'Pending', 0.00),
    (6, 2, '2024-10-02', 'Accepted', 1500.00),
    (7, 3, '2024-10-03', 'Pending', 0.00)

select * from  Admission

CREATE TABLE Admission (
    AdmissionId INT PRIMARY KEY IDENTITY(1,1),  -- Unique identifier for each admission record
    StudentId INT NOT NULL,                     -- ID of the student applying for admission
    CourseId INT NOT NULL,                      -- ID of the course the student is applying for
    AdmissionDate DATE NOT NULL,                -- Date of admission application
    Status NVARCHAR(20),                        -- Status of the admission (e.g., "Pending", "Accepted", "Rejected")
    FeesPaid DECIMAL(18, 2) DEFAULT 0.00       -- Fees paid by the student (default is 0)
)
INSERT INTO Admission VALUES

    (5, 1, '2024-10-01', 'Pending', 0.00),
    (6, 2, '2024-10-02', 'Accepted', 1500.00),
    (7, 3, '2024-10-03', 'Pending', 0.00)

select * from  Admission
--------------

CREATE TABLE StudentAdmission (
    AdmissionId INT PRIMARY KEY IDENTITY(1,1),  -- Unique identifier for each admission record
    StudentId INT NOT NULL,                     -- ID of the student applying for admission
    CourseId INT NOT NULL,                      -- ID of the course the student is applying for
    AdmissionDate DATE NOT NULL,                -- Date of admission application
    Status NVARCHAR(20),                        -- Status of the admission (e.g., "Pending", "Accepted", "Rejected")
    FeesPaid DECIMAL(18, 2) DEFAULT 0.00       -- Fees paid by the student (default is 0)
)
INSERT INTO StudentAdmission VALUES

    (5, 1, '2024-10-01', 'Pending', 0.00),
    (6, 2, '2024-10-02', 'Accepted', 1500.00),
    (7, 3, '2024-10-03', 'Pending', 0.00)

select * from  StudentAdmission
------------ManageFeee------------------------
CREATE TABLE AdminCourses (
    CourseId INT PRIMARY KEY IDENTITY(1,1),
    CourseCode NVARCHAR(50) NOT NULL,
    CourseName NVARCHAR(100) NOT NULL,
    CourseDescription NVARCHAR(MAX),
    EligibilityCriteria NVARCHAR(255),
    Fees DECIMAL(10, 2) NOT NULL,
    IntakeCapacity INT NOT NULL,
    SeatsAvailable INT NOT NULL,
    AdmissionStartDate DATE NOT NULL,
    AdmissionEndDate DATE NOT NULL
)
drop table AdminCourses

INSERT INTO AdminCourses VALUES 
('CS101', 'Computer Science Basics',
        'An introduction to the fundamentals of computer science, including algorithms, data structures, and programming.',
        'Must have passed 12th grade with 60% marks in Science stream.',
        55000, 60, 60, '2024-09-15', '2024-12-01');
 
-- Insert course 2
INSERT INTO AdminCourses 
VALUES ('ENG202', 'Advanced English Literature',
        'A detailed study of English literature from the 19th and 20th centuries, including novels, poetry, and plays.',
        'Must have passed 12th grade with 50% marks in any stream.',
        35000, 40, 40, '2024-09-10', '2024-11-30');
 
-- Insert course 3
INSERT INTO AdminCourses
VALUES ('BIO301', 'Biotechnology',
        'An in-depth course focusing on genetic engineering, microbiology, and the principles of biotechnology.',
        'Must have passed 12th grade with 65% marks in Biology and Chemistry.',
        60000, 50, 50, '2024-09-20', '2024-12-15');
 
-- Insert course 4
INSERT INTO AdminCourses
VALUES ('MATH401', 'Advanced Calculus',
        'A comprehensive course covering integral and differential calculus, multivariable calculus, and real analysis.',
        'Must have passed 12th grade with 70% marks in Mathematics.',
        45000, 30, 30, '2024-10-01', '2024-12-25');
 
-- Insert course 5
INSERT INTO AdminCourses 
VALUES ('PHY501', 'Quantum Physics',
        'This course explores the fundamental principles of quantum mechanics, wave-particle duality, and quantum theory.',
        'Must have passed 12th grade with 70% marks in Physics and Mathematics.',
        50000, 35, 35, '2024-10-05', '2024-12-20');

		-- Insert course 6
INSERT INTO AdminCourses 
VALUES ('ECON101', 'Introduction to Economics',
        'An overview of microeconomic and macroeconomic principles, including supply and demand, markets, and fiscal policy.',
        'Must have passed 12th grade with 55% marks in any stream.',
        30000, 50, 50, '2024-09-12', '2024-12-02');
 
-- Insert course 7
INSERT INTO AdminCourses 
VALUES ('HIST201', 'World History',
        'A study of significant global historical events from ancient civilizations to the modern era.',
        'Must have passed 12th grade with 50% marks in any stream.',
        25000, 40, 40, '2024-09-18', '2024-11-25');
 
-- Insert course 8
INSERT INTO AdminCourses 
VALUES ('CHEM301', 'Organic Chemistry',
        'This course covers organic compounds, reactions, and mechanisms in chemistry.',
        'Must have passed 12th grade with 60% marks in Chemistry and Biology.',
        50000, 45, 45, '2024-09-20', '2024-12-05');
 
-- Insert course 9
INSERT INTO AdminCourses 
VALUES ('PSY101', 'Introduction to Psychology',
        'An introduction to the study of human behavior, cognitive processes, and mental health.',
        'Must have passed 12th grade with 50% marks in any stream.',
        35000, 60, 60, '2024-09-25', '2024-12-10');
 
-- Insert course 10
INSERT INTO AdminCourses 
VALUES ('MGMT401', 'Business Management',
        'A detailed study of organizational management, leadership, and strategic planning.',
        'Must have passed 12th grade with 60% marks in any stream.',
        60000, 35, 35, '2024-09-30', '2024-12-20');
 
-- Insert course 11
INSERT INTO AdminCourses 
VALUES ('CIV101', 'Introduction to Civil Engineering',
        'An introduction to the principles of civil engineering, including construction and environmental engineering.',
        'Must have passed 12th grade with 65% marks in Science stream.',
        55000, 50, 50, '2024-10-01', '2024-12-15');
 
-- Insert course 12
INSERT INTO AdminCourses 
VALUES ('LAW301', 'Constitutional Law',
        'An in-depth study of constitutional principles, government structures, and legal rights.',
        'Must have passed 12th grade with 55% marks in any stream.',
        45000, 30, 30, '2024-10-05', '2024-12-22');
 
-- Insert course 13
INSERT INTO AdminCourses 
VALUES ('ART101', 'Art History',
        'A survey of major art movements and styles from the Renaissance to contemporary art.',
        'Must have passed 12th grade with 50% marks in any stream.',
        32000, 40, 40, '2024-10-10', '2024-12-30');
 
-- Insert course 14
INSERT INTO AdminCourses 
VALUES ('IT501', 'Data Science',
        'A comprehensive course on data analysis, machine learning, and big data technologies.',
        'Must have passed 12th grade with 70% marks in Mathematics or Computer Science.',
        70000, 40, 40, '2024-10-15', '2024-12-25');
 
-- Insert course 15
INSERT INTO AdminCourses 
VALUES ('MED601', 'Medical Science',
        'An advanced course on human anatomy, physiology, and medical practices.',
        'Must have passed 12th grade with 80% marks in Biology and Chemistry.',
        80000, 30, 30, '2024-10-20', '2024-12-28');

		select * from AdminCourses
		--------------------student appliction subbmission-----------
CREATE TABLE StudentsApplication (
   StudentID INT PRIMARY KEY,
   FirstName NVARCHAR(50),
   LastName NVARCHAR(50),
   FatherName NVARCHAR(50),
   DateOfBirth DATE,
   Gender NVARCHAR(10),
   Email NVARCHAR(100),
   PhoneNumber NVARCHAR(15),
   Address NVARCHAR(255),
   Nationality NVARCHAR(50),
   HighSchoolMarks DECIMAL(5, 2),
   PreviousQualification NVARCHAR(100),
   YearOfPassing INT,
   AdmissionID INT,
   CourseID INT,
   ApplicationDate DATE,
   --AdmissionStatus NVARCHAR(20),
   Password NVARCHAR(255),
   ConfirmPassword NVARCHAR(100),
   GuardianPhoneNumber NVARCHAR(15),
   AnyDisability NVARCHAR(100),
   HostelRequired NVARCHAR(10)
)
-- Sample Insertion for a student applying for a course
 
INSERT INTO StudentsApplication VALUES

(1,'John', 'Doe', 'Michael Doe', '2002-05-14', 'Male', 'john.doe@example.com', '1234567890', '123 Main Street, City', 'American', 85.50, 'High School Diploma', 2020, 1, 101,'2022-05-06', 'hashedpassword123', 'hashedpassword123', '0987654321', 'None', 'Yes'),
 
(2,'Jane', 'Smith', 'Robert Smith', '2001-09-22', 'Female', 'jane.smith@example.com', '2345678901', '456 Elm Street, Town', 'Canadian', 92.75, 'High School Diploma', 2019, 2, 102,'2022-05-06', 'hashedpassword456', 'hashedpassword456', '1234567890', 'None', 'No'),
 
(3,'Adam', 'Johnson', 'Peter Johnson', '2003-03-30', 'Male', 'adam.johnson@example.com', '3456789012', '789 Oak Avenue, Suburb', 'British', 88.40, 'High School Diploma', 2021, 3, 103, '2022-05-06','hashedpassword789', 'hashedpassword789', '9876543210', 'Vision Impairment', 'Yes'),
 
(4,'Emily', 'Brown', 'Richard Brown', '2002-12-10', 'Female', 'emily.brown@example.com', '4567890123', '101 Pine Road, Village', 'Indian', 90.30, 'High School Diploma', 2020, 4, 104, '2022-05-06','hashedpassword321', 'hashedpassword321', '8765432109', 'None', 'No')
select * from StudentsApplication
-------------
-- Create BillingAddress Table
CREATE TABLE PayMent (
    BillingID INT PRIMARY KEY ,
    FullName VARCHAR(255) NOT NULL,
    Email VARCHAR(255) NOT NULL,
    Address VARCHAR(255) NOT NULL,
    City VARCHAR(100) NOT NULL,
    State VARCHAR(100) NOT NULL,
    ZipCode VARCHAR(20) NOT NULL,
	Cardaccepted varchar(100) Not Null,
	Nameoncard varchar(100) Not Null,
	CreditCardNumber varchar(100) not null,
	ExpMonth varchar(50),
	ExpYear int ,
	CVV Varchar(100),
)
drop table  PayMent
 INSERT INTO Payment (BillingID, FullName, Email, Address, City, State, ZipCode, CardAccepted, NameOnCard, CreditCardNumber, ExpMonth, ExpYear, CVV)
VALUES
(1, 'John Doe', 'john.doe@example.com', '123 Main St', 'New York', 'NY', '10001', 'Visa', 'John Doe', '4111111111111111', 12, 2025, '123'),
(2, 'Jane Smith', 'jane.smith@example.com', '456 Oak St', 'Los Angeles', 'CA', '90001', 'MasterCard', 'Jane Smith', '5555555555554444', 11, 2024, '456'),
(3, 'Alice Johnson', 'alice.j@example.com', '789 Pine St', 'Chicago', 'IL', '60601', 'American Express', 'Alice Johnson', '378282246310005', 10, 2026, '789');
select * from   PayMent
