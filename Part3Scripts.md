
                                                                      Part 3: SQL Programming
                            1. Data Retrieval Queries

--  Retrieve all children who have been vaccinated
SELECT c.ChildID, c.Name, c.DateOfBirth, c.Gender, r.RegionName
FROM Children c
JOIN Regions r ON c.RegionID = r.RegionID
JOIN VaccinationRecords vr ON c.ChildID = vr.ChildID;

-- Retrieve children who have not received any vaccinations
SELECT c.ChildID, c.Name, c.DateOfBirth, c.Gender, r.RegionName
FROM Children c
JOIN Regions r ON c.RegionID = r.RegionID
LEFT JOIN VaccinationRecords vr ON c.ChildID = vr.ChildID
WHERE vr.RecordID IS NULL;

-- List all vaccines given to children in a specific region (e.g., Lodwar)
SELECT c.Name AS ChildName, v.VaccineName, vr.DateAdministered
FROM VaccinationRecords vr
JOIN Children c ON vr.ChildID = c.ChildID
JOIN Vaccines v ON vr.VaccineID = v.VaccineID
JOIN Regions r ON c.RegionID = r.RegionID
WHERE r.RegionName = 'Lodwar';

-- Retrieve the total number of children vaccinated per health center
SELECT hc.Name AS HealthCenterName, COUNT(vr.RecordID) AS TotalVaccinated
FROM HealthCenters hc
JOIN VaccinationRecords vr ON hc.HealthCenterID = vr.HealthCenterID
GROUP BY hc.HealthCenterID;

                          2. Data Analysis Queries
-- Count the total number of children vaccinated in each region
SELECT r.RegionName, COUNT(vr.RecordID) AS TotalVaccinated
FROM VaccinationRecords vr
JOIN Children c ON vr.ChildID = c.ChildID
JOIN Regions r ON c.RegionID = r.RegionID
GROUP BY r.RegionID;

-- Find the percentage of children vaccinated in each region
SELECT r.RegionName, 
       COUNT(vr.RecordID) AS VaccinatedCount, 
       (COUNT(vr.RecordID) / (SELECT COUNT(*) FROM Children c WHERE c.RegionID = r.RegionID) * 100) AS VaccinationPercentage
FROM VaccinationRecords vr
JOIN Children c ON vr.ChildID = c.ChildID
JOIN Regions r ON c.RegionID = r.RegionID
GROUP BY r.RegionID;

-- Identify regions with the lowest child vaccination rates
SELECT r.RegionName, 
       (COUNT(vr.RecordID) / (SELECT COUNT(*) FROM Children c WHERE c.RegionID = r.RegionID) * 100) AS VaccinationRate
FROM VaccinationRecords vr
JOIN Children c ON vr.ChildID = c.ChildID
JOIN Regions r ON c.RegionID = r.RegionID
GROUP BY r.RegionID
ORDER BY VaccinationRate ASC
LIMIT 5;  
-- Determine the most frequently administered vaccines
SELECT v.VaccineName, COUNT(vr.RecordID) AS TotalAdministered
FROM VaccinationRecords vr
JOIN Vaccines v ON vr.VaccineID = v.VaccineID
GROUP BY v.VaccineID
ORDER BY TotalAdministered DESC;

-- Identify children who are missing specific vaccines (e.g., Polio)
SELECT c.ChildID, c.Name, r.RegionName
FROM Children c
JOIN Regions r ON c.RegionID = r.RegionID
LEFT JOIN VaccinationRecords vr ON c.ChildID = vr.ChildID AND vr.VaccineID = (SELECT VaccineID FROM Vaccines WHERE VaccineName = 'Polio Vaccine')
WHERE vr.RecordID IS NULL;














