Part 1: SDG Selection and Problem Definition
SDG Selection: SDG 3: Good Health and Well-being.

Problem Definition: Low Child Vaccination Coverage in Turkana, Kenya. In Turkana, Kenya, many children are not receiving essential vaccinations, leaving them vulnerable to preventable diseases. Contributing factors include remote locations, limited access to healthcare services, insufficient vaccine supply, and a lack of awareness about the importance of childhood vaccinations. This project will use data to pinpoint areas within Turkana where child vaccination rates are particularly low and analyze the causes behind these trends. The goal is to help guide healthcare interventions and strategies to improve vaccination rates for children in this region.

Part 2: Database Design
1. ERD (Entity Relationship Diagram)
The following entities are relevant to the problem of low child vaccination coverage in Turkana:

Children: Represents individual children eligible for vaccination.

Attributes: ChildID, Name, DateOfBirth, Gender, RegionID
Vaccines: Contains information about the different types of vaccines.

Attributes: VaccineID, VaccineName, DiseasePrevented, DoseNumber
Health Centers: Represents health facilities where vaccinations are provided.

Attributes: HealthCenterID, Name, Location, RegionID
Vaccination Records: Tracks vaccinations administered to children.

Attributes: RecordID, ChildID, VaccineID, HealthCenterID, DateAdministered
Regions: Represents different regions in Turkana.

Attributes: RegionID, RegionName, Population
Healthcare Workers: Represents individuals who administer vaccines.

Attributes: WorkerID, Name, HealthCenterID, Specialization
The relationships between these entities:

A Child lives in one Region.
A Health Center serves a Region.
A Child receives multiple Vaccines.
A Health Center administers multiple Vaccination Records.
A Healthcare Worker works at a Health Center and administers vaccines to children.