# USA QA and Testing Jobs Research

## Overview

This research project analyzes the software testing and quality assurance job market in the United States. The study focuses on understanding job requirements, technologies in demand, salary ranges, and employment trends in the QA/testing field through systematic data collection and analysis from LinkedIn job postings.

## Research Timeline

- **Data Extraction**: September 7-8 (2025)
- **Data Evaluation Script Development**: September 8 - October 1st (2025)

## Methodology

### Phase 1: Exploratory Observation
Initial observation of job positions to understand the landscape of software testing roles available in the market.

### Phase 2: Definition of Research Scope
Defined specific software testing titles that would be included in the research to ensure comprehensive coverage of the QA/testing domain.

### Phase 3: Data Scraping
- **Source**: LinkedIn.com job postings
- **Method**: Manual data extraction using JavaScript in browser console
- **Batch Size**: 25 records per extraction cycle
- **Initial Dataset**: 3,751 job postings
- **Data Points Collected**: 
  - Job title
  - Company name
  - Location
  - Payment frequency (paymentPer)
  - Minimum salary (minSalary)
  - Maximum salary (maxSalary)
  - Average salary (avgSalary)
  - Job posting URL

### Phase 4: Data Cleaning and Deduplication
- **Deduplication Method**: URL comparison to remove duplicate postings
- **Post-deduplication Dataset**: 3,726 unique job postings

### Phase 5: Data Enrichment
- **Tool**: JavaScript with WebDriver automation
- **Purpose**: Extract detailed job descriptions for analysis
- **Final Enriched Dataset**: 3,714 job postings (removed positions that couldn't be enriched automatically since they were no public), also, applying a second filter to identify posting that mention test automation as an expression instead of a tool name.

### Phase 6: Description Analysis
- **Method**: JavaScript-based keyword analysis
- **Purpose**: Analyze job descriptions to populate additional analytical columns
- **Approach**: Pattern matching against predefined testing-related keywords and technologies

## Data Structure

Each job record contains the following fields:

### Basic Information
- `title`: Job position title
- `company`: Hiring company name
- `location`: Job location
- `url`: LinkedIn job posting URL
- `id`: Unique job identifier extracted from URL

### Compensation
- `paymentPer`: Payment frequency ("year", "month", "hour", "n/a")
- `minSalary`: Minimum salary offered
- `maxSalary`: Maximum salary offered
- `avgSalary`: Calculated average salary

### Job Content
- `description`: Complete job description text

### Work Characteristics
- `type`: Work arrangement ("on-site", "remote", "hybrid")
- `agile*`: Boolean indicating if Agile methodology is mentioned
- `programming*`: Boolean indicating if programming skills are required
- `automation*`: Boolean indicating if test automation is involved
- `yearsOfExperience`: Years of experience required (when specified)

### Testing Types
- `webTesting*`: Web application testing
- `apiTesting*`: API testing capabilities
- `mobileTesting*`: Mobile application testing
- `desktopTesting*`: Desktop application testing

### Requirements
- `higherEducationDegree*`: Boolean indicating if degree is required
- `spanish*`: Boolean indicating if Spanish language skills are required
- `continuousIntegration*`: Boolean indicating CI/CD involvement
- `certification*`: Boolean indicating if certifications are required

### Technologies and Tools
- `testAutomationTecnologies*`: Array of test automation tools mentioned
- `tecnologies*`: Array of test management tecnologies
- `programmingLanguages*`: Array of programming languages required

### Analysis Metrics
- `skillsRequiredCounter`: Total count of technical skills required
- `testingRelatedKeywords*`: Array of testing-specific terms found
- `amountOfTestingRelatedKeywords`: Count of testing keywords

### Classification
- `level`: Seniority level ("Junior", "Mid-level", "Senior", "Principal", "Lead", etc.)
- `classification`: Job category ("Quality", "Testing", "Software Developer Engineering in Test", etc.)
- `role`: Role type ("Engineer", "Analyst", "Manager", etc.)
- `especialization`: Specialization area ("Automation", "Performance", etc.)

(*) Properties classified based on the files in the terms folder.

## Data Files Structure

The `2025-09/` folder contains the complete dataset evolution through the research process:

### File Descriptions

1. **`raw-dataset.json`** (3,751 records)
   - Initial scraped data from LinkedIn
   - Contains basic job information without descriptions
   - Includes all originally collected postings before any filtering

2. **`raw-dataset-deduped.json`** (3,726 records)
   - Deduplicated version of the raw dataset
   - Removed duplicate postings based on URL comparison
   - Clean dataset ready for enrichment

3. **`enriched-dataset.json`** (3,714 records)
   - Filtered version containing only confirmed testing-related positions

4. **`enriched-dataset-final.json`** (3,714 records)
   - After enriched-dataset.json is created, a new filter for the terms "test automation”, "automate test”, and "automated test” were applied. Is is done after because there are job positions that are not testing-related which mentions in some manner these expressions.
   - Quality-assured dataset for focused testing job market analysis

5. **`enriched-dataset-with-non-testing-related.json`**
   - Non-testing related job positions

## Technical Implementation

### Data Scraping Tools
- **JavaScript**: Browser console scripting for LinkedIn data extraction
- **WebDriver**: Automated browser control for description enrichment
- **Manual Process**: 25-record batches to respect LinkedIn's architectural limitations

### Analysis Engine
- **Keyword Matching**: Pattern-based analysis for technology identification
- **Boolean Logic**: Multi-criteria evaluation for job characteristics
- **Classification Algorithm**: Rule-based categorization of roles and specializations

## Research Applications

This dataset enables analysis of:
- Technology adoption trends in QA/testing roles
- Salary ranges across different testing specializations
- Geographic distribution of testing opportunities
- Skills demand patterns in the testing industry
- Evolution of testing role requirements
- Remote work availability in QA positions

## Data Quality Notes

- LinkedIn's web architecture limited scraping to 25-record batches
- Some job postings could not be enriched with descriptions automatically (12 records)
- Salary data availability varies by posting (many marked as "n/a")
- Classification accuracy depends on keyword presence in job descriptions
- All data reflects the specific time window of September 7-8, 2025

## Usage

The datasets can be used for:
- Market research and trend analysis
- Salary benchmarking for QA positions
- Technology stack planning for testing teams
- Career development guidance for testing professionals
- Academic research on software testing industry trends
