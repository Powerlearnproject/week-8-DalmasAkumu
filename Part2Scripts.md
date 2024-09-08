-- Create the database
CREATE DATABASE VaccinationCoverage;

-- Use the newly created database
USE VaccinationCoverage;

-- Create Regions table
CREATE TABLE Regions (
    RegionID INT PRIMARY KEY AUTO_INCREMENT,
    RegionName VARCHAR(100),
    Population INT
);

-- Create Health Centers table
CREATE TABLE HealthCenters (
    HealthCenterID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100),
    Location VARCHAR(100),
    RegionID INT,
    FOREIGN KEY (RegionID) REFERENCES Regions(RegionID)
);

-- Create Children table
CREATE TABLE Children (
    ChildID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100),
    DateOfBirth DATE,
    Gender VARCHAR(10),
    RegionID INT,
    FOREIGN KEY (RegionID) REFERENCES Regions(RegionID)
);

-- Create Vaccines table
CREATE TABLE Vaccines (
    VaccineID INT PRIMARY KEY AUTO_INCREMENT,
    VaccineName VARCHAR(100),
    DiseasePrevented VARCHAR(100),
    DoseNumber INT
);

-- Create Vaccination Records table
CREATE TABLE VaccinationRecords (
    RecordID INT PRIMARY KEY AUTO_INCREMENT,
    ChildID INT,
    VaccineID INT,
    HealthCenterID INT,
    DateAdministered DATE,
    FOREIGN KEY (ChildID) REFERENCES Children(ChildID),
    FOREIGN KEY (VaccineID) REFERENCES Vaccines(VaccineID),
    FOREIGN KEY (HealthCenterID) REFERENCES HealthCenters(HealthCenterID)
);

-- Create Healthcare Workers table
CREATE TABLE HealthcareWorkers (
    WorkerID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100),
    HealthCenterID INT,
    Specialization VARCHAR(100),
    FOREIGN KEY (HealthCenterID) REFERENCES HealthCenters(HealthCenterID)
);

-- Insert sample data into Regions
INSERT INTO Regions (RegionName, Population) VALUES
('Lodwar', 60000),
('Kakuma', 30000),
('Lokichar', 20000);

-- Insert sample data into HealthCenters
INSERT INTO HealthCenters (Name, Location, RegionID) VALUES
('Lodwar General Hospital', 'Lodwar Town', 1),
('Kakuma Health Clinic', 'Kakuma Town', 2),
('Lokichar Community Health Center', 'Lokichar Town', 3);

-- Insert sample data into Children
INSERT INTO Children (Name, DateOfBirth, Gender, RegionID) VALUES
('John Doe', '2020-05-12', 'Male', 1),
('Jane Doe', '2019-11-25', 'Female', 2),
('Mark Smith', '2021-01-10', 'Male', 3),
('Anne Kip', '2018-03-05', 'Female', 1),
('David Okoth', '2020-07-22', 'Male', 2),
('Grace Wanjiku', '2020-09-15', 'Female', 3),
('Michael Otieno', '2021-01-18', 'Male', 1),
('Sarah Kiptoo', '2019-04-12', 'Female', 1),
('Peter Achieng', '2019-11-10', 'Male', 3),
('Linda Amolo', '2020-06-07', 'Female', 1),
('Kevin Obuya', '2021-02-11', 'Male', 2),
('Brian Kip', '2019-09-17', 'Male', 1),
('Martha Juma', '2020-12-19', 'Female', 2),
('Faith Lokomo', '2021-03-21', 'Female', 3),
('Edward Kariuki', '2021-02-05', 'Male', 1),
('Catherine Mueni', '2020-10-30', 'Female', 3),
('Paul Lokichar', '2020-08-25', 'Male', 2),
('Susan Ngala', '2019-07-22', 'Female', 3),
('Frank Nyang', '2020-11-14', 'Male', 1),
('Lucy Wafula', '2021-01-25', 'Female', 2);

-- Insert sample data into Vaccines
INSERT INTO Vaccines (VaccineName, DiseasePrevented, DoseNumber) VALUES
('BCG', 'Tuberculosis', 1),
('Measles Vaccine', 'Measles', 2),
('Polio Vaccine', 'Polio', 3),
('Hepatitis B', 'Hepatitis B', 2),
('DTP', 'Diphtheria, Tetanus, Pertussis', 3);

-- Insert sample data into VaccinationRecords
INSERT INTO VaccinationRecords (ChildID, VaccineID, HealthCenterID, DateAdministered) VALUES
(1, 1, 1, '2020-06-15'),
(2, 2, 2, '2020-12-01'),
(3, 3, 3, '2021-02-15'),
(4, 1, 1, '2018-03-10'),
(5, 4, 2, '2020-07-30'),
(6, 5, 3, '2020-09-20'),
(7, 3, 1, '2021-01-25'),
(8, 2, 1, '2019-05-01'),
(9, 5, 3, '2020-01-15'),
(10, 1, 1, '2020-06-15'),
(11, 4, 2, '2021-03-01'),
(12, 3, 1, '2019-09-20'),
(13, 2, 2, '2021-01-10'),
(14, 1, 3, '2021-03-25'),
(15, 4, 1, '2021-02-15'),
(16, 5, 3, '2021-03-10'),
(17, 3, 2, '2020-09-01'),
(18, 2, 3, '2020-11-10'),
(19, 5, 1, '2021-01-10'),
(20, 1, 2, '2021-02-15');

-- Insert sample data into HealthcareWorkers
INSERT INTO HealthcareWorkers (Name, HealthCenterID, Specialization) VALUES
('Dr. James', 1, 'Pediatrics'),
('Nurse Mary', 2, 'General'),
('Dr. Ahmed', 3, 'Community Health');
