# Student Experience and Market Insights Analysis Project

## Executive Summary
This project simulates an end-to-end student experience and market insights workflow for a vocational education provider.  
The dataset contains **1,000 synthetic student survey responses** across campuses, course areas, study modes, enrolment channels, satisfaction ratings, completion intention, barriers and at-risk indicators.

The aim is to identify the key drivers of student experience, highlight growth and retention opportunities, and translate survey data into clear recommendations for non-technical stakeholders.

## Business Problem
Vocational education providers need to understand student expectations, course experience, support needs and market behaviour in order to improve student outcomes and support strategic planning.

This project answers four business questions:

1. Which course areas and campuses show the strongest student experience?
2. Which student groups show higher at-risk indicators?
3. What are the main barriers affecting student satisfaction and completion intention?
4. Which enrolment channels and market segments should be prioritised for growth and retention?

## Dataset
The dataset was created as a portfolio-ready synthetic dataset inspired by common student satisfaction and student experience survey structures.

**Rows:** 1,000  
**Main fields:** Student ID, survey date, campus, course area, qualification level, study mode, student type, enrolment channel, satisfaction scores, NPS score, completion intention, at-risk flag, main barrier and recommendation category.

Reference dataset styles:
- Kaggle Student Satisfaction Survey: https://www.kaggle.com/datasets/prasad22/student-satisfaction-survey
- Kaggle Student Survey: https://www.kaggle.com/datasets/razibmustafiz/student-survey
- QILT Student Experience Survey overview: https://qilt.edu.au/surveys/student-experience-survey-%28ses%29

## Methodology
### 1. Data Collection Design
A survey-style dataset was structured to reflect the type of information an education provider may collect from students, including:
- teaching quality
- learning resources
- support services
- digital experience
- industry relevance
- assessment feedback
- overall satisfaction
- likelihood to recommend
- completion intention
- main barriers

### 2. Data Preparation
The data was cleaned and structured into analysis-ready fields:
- standardised categorical values
- created an at-risk student flag
- grouped satisfaction scores by course, campus and study mode
- prepared summary tables for dashboard reporting

### 3. Exploratory Analysis
The analysis focused on:
- overall satisfaction and NPS
- course area performance
- campus-level experience differences
- student barriers
- enrolment channel patterns
- at-risk student segments

### 4. Insight Development
The final step translated the findings into practical recommendations for strategy, student support and market planning.

## Key Metrics
| Metric | Result |
|---|---:|
| Total survey responses | 1,000 |
| Average overall satisfaction | 3.73 / 5 |
| Net Promoter Score | -2.7 |
| Likely to complete | 72.3% |
| At-risk students | 18.2% |


## Data Visualisations

The following visuals were created to make the analysis easier to understand for non-technical stakeholders and to support strategic discussion around student experience, retention risk and growth opportunities.

### KPI Summary
<img width="1584" height="753" alt="kpi_summary" src="https://github.com/user-attachments/assets/ed375761-5672-46dd-b90c-30c0f11440ef" />


### Course Satisfaction Performance
![Average Overall Satisfaction by Course Area](images/course_satisfaction.png)

### At-Risk Student Segments by Course Area
<img width="1571" height="937" alt="course_satisfaction" src="https://github.com/user-attachments/assets/7dc3042f-5f42-4c61-ad1b-a6c2cdfef47c" />


### Main Student Barriers
![Main Barriers Reported by Students](images/main_barriers.png)

### Campus Experience Comparison
![Campus Experience: Satisfaction and Completion Intention](images/campus_experience.png)

### Enrolment Channel Mix
![Survey Responses by Enrolment Channel](images/enrolment_channels.png)

### Experience Driver Correlation
![Correlation Between Experience Drivers](images/experience_driver_correlation.png)

## Key Findings
### 1. Strongest course experience
**Hospitality & Tourism** recorded the highest average satisfaction score at **3.97/5**.

**Recommendation:** Use this course area as a benchmark to identify strong teaching, support and industry engagement practices that can be shared across other course areas.

### 2. Highest at-risk course segment
**Creative Industries** had the highest at-risk rate at **21.2%**.

**Recommendation:** Review student feedback, workload expectations, support access and course delivery experience for this course area.

### 3. Main student barrier
The most common barrier was **Work commitments**, reported by **221 students**.

**Recommendation:** Create targeted student communication and support interventions around this barrier, especially for students balancing study with employment or long commute times.

### 4. Campus experience variation
**Docklands** had the highest average satisfaction score, while **Broadmeadows** had the lowest.

**Recommendation:** Compare campus support practices, digital learning consistency and student service processes to reduce experience variation.

### 5. Largest enrolment channel
**Website search** was the largest enrolment channel, with **271 students**.

**Recommendation:** Review channel quality, not only volume. Compare satisfaction and completion intention across channels to improve marketing targeting and student conversion quality.

## Skills Demonstrated
- Market insights analysis
- Student/customer experience analysis
- Survey data design
- Data cleaning and validation
- Excel dashboard reporting
- SQL querying and aggregation
- KPI reporting
- Trend and segment analysis
- Translating complex data into business recommendations
- Stakeholder-friendly insight communication

## Example SQL Analysis

```sql
-- Average satisfaction and at-risk rate by course area
SELECT
    Course_Area,
    COUNT(*) AS total_students,
    ROUND(AVG(Overall_Satisfaction_Score), 2) AS avg_satisfaction,
    ROUND(AVG(CASE WHEN At_Risk_Flag = 'Yes' THEN 1.0 ELSE 0 END) * 100, 1) AS at_risk_rate
FROM student_experience_survey
GROUP BY Course_Area
ORDER BY avg_satisfaction DESC;
```

```sql
-- Main barriers affecting student experience
SELECT
    Main_Barrier,
    COUNT(*) AS student_count,
    ROUND(AVG(Overall_Satisfaction_Score), 2) AS avg_satisfaction
FROM student_experience_survey
GROUP BY Main_Barrier
ORDER BY student_count DESC;
```

```sql
-- Enrolment channel performance
SELECT
    Enrolment_Channel,
    COUNT(*) AS total_students,
    ROUND(AVG(Overall_Satisfaction_Score), 2) AS avg_satisfaction,
    ROUND(AVG(CASE WHEN Completion_Intention = 'Likely' THEN 1.0 ELSE 0 END) * 100, 1) AS likely_complete_rate
FROM student_experience_survey
GROUP BY Enrolment_Channel
ORDER BY total_students DESC;
```

## Results and Business Recommendations
The analysis shows that student experience is influenced by course area, campus, study mode, support access, commute time and work commitments. The project recommends:

1. **Improve student support visibility**  
   Make support services easier to find and communicate them earlier in the student journey.

2. **Target at-risk course segments**  
   Prioritise course areas with higher at-risk rates for deeper qualitative feedback and action planning.

3. **Use high-performing course areas as benchmarks**  
   Identify what is working well in stronger course areas and transfer those practices across the institute.

4. **Optimise enrolment channels**  
   Compare not only enrolment volume, but also student satisfaction and completion intention by channel.

5. **Support flexible study options**  
   Students reporting work commitments and commute barriers may benefit from more flexible delivery and clearer timetable planning.

## Next Steps
- Build an interactive Power BI dashboard using the survey dataset.
- Add external market data such as labour market demand, population growth and course competitor analysis.
- Run correlation or regression analysis to identify stronger drivers of satisfaction and completion intention.
- Add a text analysis section using open feedback comments.
- Create stakeholder-ready presentation slides for strategy, education and student support teams.
