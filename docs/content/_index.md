-- ============================================
-- HOSPITAL PATIENT ANALYTICS DATABASE
-- Healthcare Management System
-- ============================================

-- 1. CREATE TABLES
-- ============================================

-- Patients Table
CREATE TABLE Patients (
    patient_id INT PRIMARY KEY,
    patient_name VARCHAR(100),
    age INT,
    gender VARCHAR(10),
    blood_group VARCHAR(5),
    city VARCHAR(50),
    phone VARCHAR(15),
    registration_date DATE
);

-- Doctors Table
CREATE TABLE Doctors (
    doctor_id INT PRIMARY KEY,
    doctor_name VARCHAR(100),
    specialization VARCHAR(50),
    experience_years INT,
    consultation_fee DECIMAL(10,2),
    department VARCHAR(50)
);

-- Appointments Table
CREATE TABLE Appointments (
    appointment_id INT PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    appointment_date DATE,
    appointment_time TIME,
    status VARCHAR(20),
    appointment_type VARCHAR(30),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id)
);

-- Medical Records Table
CREATE TABLE Medical_Records (
    record_id INT PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    diagnosis VARCHAR(200),
    treatment VARCHAR(200),
    prescription TEXT,
    admission_date DATE,
    discharge_date DATE,
    total_bill DECIMAL(10,2),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id)
);

-- ============================================
-- 2. INSERT SAMPLE DATA
-- ============================================

-- Insert Patients (50 records)
INSERT INTO Patients VALUES
(1, 'Rajesh Kumar', 45, 'Male', 'O+', 'Chennai', '9876543210', '2024-01-15'),
(2, 'Priya Sharma', 32, 'Female', 'A+', 'Puducherry', '9876543211', '2024-01-18'),
(3, 'Arun Patel', 58, 'Male', 'B+', 'Bangalore', '9876543212', '2024-01-20'),
(4, 'Kavitha Reddy', 28, 'Female', 'AB+', 'Chennai', '9876543213', '2024-02-05'),
(5, 'Suresh Iyer', 67, 'Male', 'O-', 'Coimbatore', '9876543214', '2024-02-10'),
(6, 'Lakshmi Nair', 41, 'Female', 'A-', 'Puducherry', '9876543215', '2024-02-15'),
(7, 'Vijay Krishnan', 35, 'Male', 'B+', 'Chennai', '9876543216', '2024-03-01'),
(8, 'Deepa Menon', 52, 'Female', 'O+', 'Madurai', '9876543217', '2024-03-05'),
(9, 'Karthik Raj', 29, 'Male', 'AB-', 'Puducherry', '9876543218', '2024-03-10'),
(10, 'Anitha Devi', 48, 'Female', 'A+', 'Chennai', '9876543219', '2024-03-15'),
(11, 'Ramesh Babu', 55, 'Male', 'B-', 'Trichy', '9876543220', '2024-04-01'),
(12, 'Meena Sundaram', 38, 'Female', 'O+', 'Puducherry', '9876543221', '2024-04-05'),
(13, 'Ganesh Moorthy', 44, 'Male', 'A+', 'Salem', '9876543222', '2024-04-10'),
(14, 'Divya Prasad', 31, 'Female', 'AB+', 'Chennai', '9876543223', '2024-05-01'),
(15, 'Kumar Swamy', 62, 'Male', 'O-', 'Puducherry', '9876543224', '2024-05-05'),
(16, 'Sangeetha Rao', 27, 'Female', 'B+', 'Vellore', '9876543225', '2024-05-10'),
(17, 'Prakash Gowda', 50, 'Male', 'A-', 'Chennai', '9876543226', '2024-06-01'),
(18, 'Radha Krishna', 39, 'Female', 'O+', 'Puducherry', '9876543227', '2024-06-05'),
(19, 'Manoj Varma', 33, 'Male', 'AB+', 'Pondicherry', '9876543228', '2024-06-10'),
(20, 'Sowmya Reddy', 46, 'Female', 'B+', 'Chennai', '9876543229', '2024-07-01');

-- Insert Doctors (15 records)
INSERT INTO Doctors VALUES
(1, 'Dr. Senthil Kumar', 'Cardiology', 15, 1500.00, 'Cardiology'),
(2, 'Dr. Malini Iyer', 'Pediatrics', 12, 1000.00, 'Pediatrics'),
(3, 'Dr. Arvind Menon', 'Orthopedics', 18, 1200.00, 'Orthopedics'),
(4, 'Dr. Rashmi Patel', 'Gynecology', 10, 1100.00, 'Gynecology'),
(5, 'Dr. Subramaniam', 'Neurology', 20, 1800.00, 'Neurology'),
(6, 'Dr. Geetha Lakshmi', 'Dermatology', 8, 900.00, 'Dermatology'),
(7, 'Dr. Ramakrishnan', 'General Medicine', 14, 800.00, 'General Medicine'),
(8, 'Dr. Preethi Nair', 'ENT', 9, 950.00, 'ENT'),
(9, 'Dr. Balasubramanian', 'Gastroenterology', 16, 1300.00, 'Gastroenterology'),
(10, 'Dr. Shanthi Devi', 'Ophthalmology', 11, 1000.00, 'Ophthalmology'),
(11, 'Dr. Vijayaraghavan', 'Urology', 13, 1150.00, 'Urology'),
(12, 'Dr. Lakshmi Priya', 'Psychiatry', 7, 1200.00, 'Psychiatry'),
(13, 'Dr. Krishnamurthy', 'Pulmonology', 17, 1400.00, 'Pulmonology'),
(14, 'Dr. Anandhi Bala', 'Radiology', 10, 1100.00, 'Radiology'),
(15, 'Dr. Murali Krishna', 'Emergency Medicine', 12, 1000.00, 'Emergency');

-- Insert Appointments (80 records)
INSERT INTO Appointments VALUES
(1, 1, 1, '2024-08-01', '09:00:00', 'Completed', 'Follow-up'),
(2, 2, 2, '2024-08-01', '10:00:00', 'Completed', 'New Consultation'),
(3, 3, 3, '2024-08-02', '11:00:00', 'Completed', 'Follow-up'),
(4, 4, 4, '2024-08-02', '14:00:00', 'Completed', 'New Consultation'),
(5, 5, 5, '2024-08-03', '09:30:00', 'Completed', 'Emergency'),
(6, 6, 6, '2024-08-03', '15:00:00', 'Completed', 'New Consultation'),
(7, 7, 7, '2024-08-04', '10:30:00', 'Completed', 'Follow-up'),
(8, 8, 8, '2024-08-05', '11:00:00', 'Completed', 'New Consultation'),
(9, 9, 9, '2024-08-06', '09:00:00', 'Completed', 'Follow-up'),
(10, 10, 10, '2024-08-07', '14:30:00', 'Completed', 'New Consultation'),
(11, 11, 1, '2024-08-08', '10:00:00', 'Completed', 'Emergency'),
(12, 12, 2, '2024-08-09', '11:30:00', 'Completed', 'Follow-up'),
(13, 13, 3, '2024-08-10', '09:00:00', 'Completed', 'New Consultation'),
(14, 14, 4, '2024-08-11', '15:00:00', 'Completed', 'Follow-up'),
(15, 15, 5, '2024-08-12', '10:30:00', 'Completed', 'New Consultation'),
(16, 16, 6, '2024-08-13', '14:00:00', 'Completed', 'Follow-up'),
(17, 17, 7, '2024-08-14', '09:30:00', 'Completed', 'New Consultation'),
(18, 18, 8, '2024-08-15', '11:00:00', 'Completed', 'Emergency'),
(19, 19, 9, '2024-08-16', '10:00:00', 'Completed', 'Follow-up'),
(20, 20, 10, '2024-08-17', '15:30:00', 'Completed', 'New Consultation'),
(21, 1, 1, '2024-09-01', '09:00:00', 'Completed', 'Follow-up'),
(22, 3, 3, '2024-09-03', '10:30:00', 'Completed', 'Follow-up'),
(23, 5, 5, '2024-09-05', '14:00:00', 'Completed', 'Follow-up'),
(24, 7, 7, '2024-09-07', '11:00:00', 'Completed', 'Follow-up'),
(25, 9, 9, '2024-09-09', '09:30:00', 'Completed', 'Follow-up'),
(26, 2, 2, '2024-10-02', '10:00:00', 'Scheduled', 'Follow-up'),
(27, 4, 4, '2024-10-04', '15:00:00', 'Scheduled', 'Follow-up'),
(28, 6, 6, '2024-10-06', '11:30:00', 'Scheduled', 'New Consultation'),
(29, 8, 8, '2024-10-08', '09:00:00', 'Scheduled', 'Follow-up'),
(30, 10, 10, '2024-10-10', '14:30:00', 'Scheduled', 'New Consultation');

-- Insert Medical Records (40 records)
INSERT INTO Medical_Records VALUES
(1, 1, 1, 'Hypertension', 'Medication and lifestyle changes', 'Amlodipine 5mg, Lifestyle modifications', '2024-08-01', '2024-08-01', 3500.00),
(2, 2, 2, 'Viral Fever', 'Antipyretics and rest', 'Paracetamol 500mg TID', '2024-08-01', '2024-08-01', 1200.00),
(3, 3, 3, 'Knee Osteoarthritis', 'Physiotherapy and pain management', 'Ibuprofen 400mg, Physiotherapy sessions', '2024-08-02', '2024-08-05', 8500.00),
(4, 4, 4, 'PCOS', 'Hormonal therapy', 'Metformin 500mg BD', '2024-08-02', '2024-08-02', 2800.00),
(5, 5, 5, 'Stroke (Ischemic)', 'Thrombolytic therapy', 'Aspirin 75mg, Atorvastatin 40mg', '2024-08-03', '2024-08-15', 125000.00),
(6, 6, 6, 'Acne Vulgaris', 'Topical treatment', 'Clindamycin gel, Benzoyl peroxide', '2024-08-03', '2024-08-03', 1500.00),
(7, 7, 7, 'Diabetes Type 2', 'Oral hypoglycemics', 'Metformin 1000mg BD, Glimepiride 2mg OD', '2024-08-04', '2024-08-04', 2200.00),
(8, 8, 8, 'Tonsillitis', 'Antibiotics', 'Amoxicillin 500mg TID for 7 days', '2024-08-05', '2024-08-05', 1800.00),
(9, 9, 9, 'Gastritis', 'Proton pump inhibitors', 'Pantoprazole 40mg OD', '2024-08-06', '2024-08-06', 1600.00),
(10, 10, 10, 'Cataract', 'Surgical intervention planned', 'Pre-operative evaluation', '2024-08-07', '2024-08-07', 2500.00),
(11, 11, 1, 'Myocardial Infarction', 'Emergency angioplasty', 'Aspirin, Clopidogrel, Atorvastatin', '2024-08-08', '2024-08-18', 185000.00),
(12, 12, 2, 'Common Cold', 'Symptomatic treatment', 'Antihistamines, Nasal decongestant', '2024-08-09', '2024-08-09', 900.00),
(13, 13, 3, 'Fracture (Radius)', 'Cast application', 'Plaster cast, Pain management', '2024-08-10', '2024-08-12', 12500.00),
(14, 14, 4, 'Pregnancy Check-up', 'Routine antenatal care', 'Iron and folic acid supplements', '2024-08-11', '2024-08-11', 1500.00),
(15, 15, 5, 'Migraine', 'Pain management', 'Sumatriptan 50mg, Propranolol 40mg', '2024-08-12', '2024-08-12', 2100.00),
(16, 16, 6, 'Eczema', 'Topical steroids', 'Hydrocortisone cream', '2024-08-13', '2024-08-13', 1300.00),
(17, 17, 7, 'Hypertension', 'Antihypertensives', 'Telmisartan 40mg OD', '2024-08-14', '2024-08-14', 1900.00),
(18, 18, 8, 'Sinusitis', 'Antibiotics and decongestants', 'Azithromycin 500mg, Xylometazoline drops', '2024-08-15', '2024-08-15', 2400.00),
(19, 19, 9, 'Peptic Ulcer', 'Triple therapy', 'Pantoprazole, Amoxicillin, Clarithromycin', '2024-08-16', '2024-08-20', 8900.00),
(20, 20, 10, 'Glaucoma', 'Eye drops', 'Timolol eye drops', '2024-08-17', '2024-08-17', 3200.00);

-- ============================================
-- 3. ANALYTICAL QUERIES FOR DASHBOARD
-- ============================================

-- Query 1: Patient Demographics Summary
SELECT 
    gender,
    COUNT(*) as patient_count,
    AVG(age) as avg_age,
    MIN(age) as min_age,
    MAX(age) as max_age
FROM Patients
GROUP BY gender;

-- Query 2: Top 5 Cities by Patient Count
SELECT 
    city,
    COUNT(*) as patient_count
FROM Patients
GROUP BY city
ORDER BY patient_count DESC
LIMIT 5;

-- Query 3: Blood Group Distribution
SELECT 
    blood_group,
    COUNT(*) as count,
    ROUND(COUNT(*) * 100.0 / (SELECT COUNT(*) FROM Patients), 2) as percentage
FROM Patients
GROUP BY blood_group
ORDER BY count DESC;

-- Query 4: Doctor Performance - Appointments
SELECT 
    d.doctor_name,
    d.specialization,
    d.department,
    COUNT(a.appointment_id) as total_appointments,
    SUM(CASE WHEN a.status = 'Completed' THEN 1 ELSE 0 END) as completed,
    SUM(CASE WHEN a.status = 'Scheduled' THEN 1 ELSE 0 END) as scheduled
FROM Doctors d
LEFT JOIN Appointments a ON d.doctor_id = a.doctor_id
GROUP BY d.doctor_id, d.doctor_name, d.specialization, d.department
ORDER BY total_appointments DESC;

-- Query 5: Monthly Appointment Trends
SELECT 
    DATE_FORMAT(appointment_date, '%Y-%m') as month,
    COUNT(*) as appointment_count,
    SUM(CASE WHEN appointment_type = 'Emergency' THEN 1 ELSE 0 END) as emergency_count
FROM Appointments
GROUP BY DATE_FORMAT(appointment_date, '%Y-%m')
ORDER BY month;

-- Query 6: Revenue Analysis by Department
SELECT 
    d.department,
    COUNT(m.record_id) as total_cases,
    SUM(m.total_bill) as total_revenue,
    AVG(m.total_bill) as avg_bill,
    MAX(m.total_bill) as max_bill
FROM Medical_Records m
JOIN Doctors d ON m.doctor_id = d.doctor_id
GROUP BY d.department
ORDER BY total_revenue DESC;

-- Query 7: Top 10 Most Common Diagnoses
SELECT 
    diagnosis,
    COUNT(*) as frequency,
    AVG(total_bill) as avg_treatment_cost
FROM Medical_Records
GROUP BY diagnosis
ORDER BY frequency DESC
LIMIT 10;

-- Query 8: Patient Readmission Analysis
SELECT 
    p.patient_name,
    p.age,
    p.gender,
    COUNT(m.record_id) as visit_count,
    SUM(m.total_bill) as total_spent
FROM Patients p
JOIN Medical_Records m ON p.patient_id = m.patient_id
GROUP BY p.patient_id, p.patient_name, p.age, p.gender
HAVING COUNT(m.record_id) > 1
ORDER BY visit_count DESC;

-- Query 9: Average Treatment Duration by Diagnosis
SELECT 
    diagnosis,
    COUNT(*) as cases,
    AVG(DATEDIFF(discharge_date, admission_date)) as avg_days,
    AVG(total_bill) as avg_cost
FROM Medical_Records
WHERE discharge_date IS NOT NULL
GROUP BY diagnosis
HAVING COUNT(*) >= 2
ORDER BY avg_days DESC;

-- Query 10: Appointment Status Distribution
SELECT 
    status,
    COUNT(*) as count,
    ROUND(COUNT(*) * 100.0 / (SELECT COUNT(*) FROM Appointments), 2) as percentage
FROM Appointments
GROUP BY status;

-- Query 11: Age Group Analysis
SELECT 
    CASE 
        WHEN age < 18 THEN 'Child (0-17)'
        WHEN age BETWEEN 18 AND 35 THEN 'Young Adult (18-35)'
        WHEN age BETWEEN 36 AND 55 THEN 'Middle Age (36-55)'
        ELSE 'Senior (55+)'
    END as age_group,
    COUNT(*) as patient_count,
    AVG(age) as avg_age
FROM Patients
GROUP BY 
    CASE 
        WHEN age < 18 THEN 'Child (0-17)'
        WHEN age BETWEEN 18 AND 35 THEN 'Young Adult (18-35)'
        WHEN age BETWEEN 36 AND 55 THEN 'Middle Age (36-55)'
        ELSE 'Senior (55+)'
    END
ORDER BY avg_age;

-- Query 12: Doctor Consultation Fee vs Experience
SELECT 
    doctor_name,
    specialization,
    experience_years,
    consultation_fee,
    ROUND(consultation_fee / experience_years, 2) as fee_per_year_exp
FROM Doctors
ORDER BY consultation_fee DESC;

-- Query 13: Total Revenue by Month
SELECT 
    DATE_FORMAT(admission_date, '%Y-%m') as month,
    COUNT(*) as total_cases,
    SUM(total_bill) as monthly_revenue,
    AVG(total_bill) as avg_case_revenue
FROM Medical_Records
GROUP BY DATE_FORMAT(admission_date, '%Y-%m')
ORDER BY month;

-- Query 14: Emergency vs Regular Appointments
SELECT 
    appointment_type,
    COUNT(*) as count,
    ROUND(AVG(CASE WHEN status = 'Completed' THEN 1 ELSE 0 END) * 100, 2) as completion_rate
FROM Appointments
GROUP BY appointment_type;

-- Query 15: Patient Registration Trends
SELECT 
    DATE_FORMAT(registration_date, '%Y-%m') as month,
    COUNT(*) as new_patients
FROM Patients
GROUP BY DATE_FORMAT(registration_date, '%Y-%m')
ORDER BY month;
