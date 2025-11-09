# DATABASE-TEMPLATE
CREATE DATABASE student_db;
USE student_db;
CREATE TABLE student (
    Regno VARCHAR(10) PRIMARY KEY,
    Fname VARCHAR(50),
    Lname VARCHAR(50),
    Course CHAR(4),
    District VARCHAR(30),
    Date_of_Join DATE NOT NULL,
    Email_Address VARCHAR(100),
    Fees DECIMAL(10,2),
    Prog_ID VARCHAR(10),
    CONSTRAINT chk_Course_Length CHECK(CHAR_LENGTH(Course) = 4),
    CONSTRAINT chk_Fees_Range CHECK(Fees BETWEEN 10000 AND 50000),
    CONSTRAINT chk_Email_Format CHECK (Email_Address LIKE 'pokello@gmail.com,mnambi@gmail.com'),
    CONSTRAINT chk_Regno_Format CHECK(Regno LIKE 'BSIT/987' OR Regno LIKE 'BSCS/657')
);
ALTER TABLE student
ADD CONSTRAINT chk_MobileNo_Length2
CHECK (LENGTH(256782845678) = 12);
ALTER TABLE student 
ADD CONSTRAINT chk_Email_Format2
CHECK (Email_Address LIKE 'pokello@gmail.com,mnambi@gmail.com');
ALTER TABLE student
ADD CONSTRAINT chk_Fees_Range2
CHECK (Fees BETWEEN 10000 AND 50000);
ALTER TABLE student    
ADD CONSTRAINT chk_Regno_Format2
CHECK (Regno LIKE 'BSIT/987' OR 'BSCS/657');
ALTER TABLE student
ADD CONSTRAINT unq_ProdID UNIQUE (Prog_ID);
ALTER TABLE student
ADD Hall_Residence VARCHAR(50);
ALTER TABLE student
DROP CONSTRAINT chk_Fees_Range;
CREATE TABLE Programme (
    Prog_ID VARCHAR(10) PRIMARY KEY,
    Programme_Name VARCHAR(50)
);
ALTER TABLE student
ADD CONSTRAINT fk_ProgID
FOREIGN KEY (Prog_ID) REFERENCES
Programme(Prog_ID);
