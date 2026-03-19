30-Year Longitudinal Pseudohypoparathyroidism Treatment and Outcomes Dataset

This database contains 30 years of longitudinal clinical data from a single patient with pseudohypoparathyroidism, spanning ages 4.5 to 35.1 years from 1996 to 2026. The dataset comprises three interconnected tables: laboratory measurements (18 timepoints across calcium, parathyroid hormone, vitamin D, phosphorus, and magnesium), treatment protocols (8 distinct medication regimens documenting calcium, calcitriol, vitamin K2, and cofactor supplementation), and complications timeline (12 documented complications including neurological, musculoskeletal, cardiovascular, and metabolic sequelae). This represents the longest continuous follow-up of pseudohypoparathyroidism documented in published literature.

The dataset captures two distinct treatment eras: 25 years of inadequate treatment (400-600 mg daily calcium) resulting in chronic hypocalcemia and progressive complications, followed by patient-directed protocol optimization (3600 mg calcium plus novel vitamin K2 supplementation) achieving calcium normalization. Key features include documentation of initial misdiagnosis as hypoparathyroidism despite elevated PTH (1000 pg/mL), comprehensive complication tracking with severity scoring, and the first report of vitamin K2 use in pseudohypoparathyroidism management.

This resource enables rare disease natural history studies, treatment dose-response modeling, complication risk assessment, machine learning model calibration for calcium homeostasis, and investigation of vitamin K2 effects in preventing soft tissue calcification. All data are de-identified, provided in CSV format following tidy data principles, and accompanied by complete documentation including variable definitions, measurement methods, and quality control procedures.

Pseudohypoparathyroidism (PHP) is a rare inherited disorder affecting approximately 1 in 100,000 individuals, characterized by end-organ resistance to parathyroid hormone (PTH) resulting in hypocalcemia despite elevated PTH levels. Understanding PHP natural history, optimal treatment strategies, and long-term outcomes is challenging due to the condition's rarity and limited availability of longitudinal data. Most published PHP cohorts include fewer than 70 patients followed for under 5 years, with the largest mean follow-up duration reported as 3.2 years.

The scarcity of long-term data creates critical gaps in understanding PHP trajectory, treatment-response relationships, complication development patterns, and optimal management strategies. These knowledge gaps are particularly acute given the serious consequences of inadequate treatment, including brain calcifications, seizures, cardiac complications, and skeletal abnormalities. Additionally, no publicly available datasets document PHP management over multiple decades, limiting opportunities for computational research, predictive modeling, and treatment optimization.

This dataset addresses these limitations by providing 30 years of continuous longitudinal data from a single PHP patient, representing the longest documented PHP follow-up in published literature. The patient was initially misdiagnosed with hypoparathyroidism at age 4.5 despite presenting with markedly elevated PTH (1000 pg/mL, normal range 15-65 pg/mL), leading to 25 years of inadequate treatment before self-directed diagnostic correction at age 35. This unique trajectory provides valuable insights into both the consequences of diagnostic error and the potential for treatment optimization.

The dataset's primary motivation is to contribute rare disease data to the research community, enable development of predictive models for PHP management, and provide calibration data for machine learning approaches to rare diseases where patient numbers are insufficient for traditional data-driven methods. The inclusion of novel vitamin K2 supplementation data represents the first documentation of this intervention in PHP literature and may inform future clinical trials. By sharing this data openly, we aim to accelerate PHP research, improve patient outcomes, and demonstrate how individual patient data can contribute meaningfully to rare disease science.
Reuse Potential

This dataset enables multiple research applications:

1. Rare Disease Natural History:

    Longest PHP follow-up documented (30 years vs literature maximum 3.2 years mean)
    Demonstrates disease trajectory under inadequate vs adequate treatment
    Documents complication development patterns and timing
    Provides real-world evidence of diagnostic error consequences

2. Treatment Optimization:

    Quantitative dose-response relationships for calcium supplementation in PHP
    Evidence for aggressive calcium supplementation (3600 mg/day) safety and efficacy
    First documentation of vitamin K2 use in PHP (hypothesis-generating for RCTs)
    Cofactor supplementation effects (magnesium, zinc, vitamin D3)

3. Machine Learning and Computational Modeling:

    Calibration data for physics-informed models of calcium homeostasis
    Training/validation data for rare disease synthetic data generation algorithms
    Benchmark dataset for handling sparse, irregular time-series medical data
    Test case for machine learning with extremely limited sample sizes (n=1)

4. Complication Risk Assessment:

    Severity scoring enables quantitative analysis
    Temporal relationships between calcium levels and complication onset
    Documentation source variation (imaging vs clinical vs patient-reported) enables quality assessment

5. Quality of Life Research:

    Longitudinal patient perspective on chronic disease management
    Impact quantification (QoL 3/10 → 7/10 post-optimization)

Previous Use

This dataset has been used to:

    Develop PHPSynth, a physics-informed synthetic data generation framework for rare diseases (manuscript in preparation)
    Calibrate machine learning models achieving R²=0.74, MAE=0.20 mg/dL for calcium prediction
    Generate 259,218 synthetic PHP patient records for algorithm development

Known Limitations

Sample Size:

    Single patient (n=1) limits generalizability
    Results represent individual response, not population average
    Use for hypothesis generation or model calibration, not definitive conclusions

Measurement Sparsity:

    Variable intervals (0.75-96 months) limit continuous trajectory modeling
    PTH particularly sparse (4 measurements over 30 years)
    Missing data are not missing-at-random (reflects clinical decision-making)

Confounding:

    Multiple interventions changed simultaneously in optimized era
    Cannot isolate individual effects of calcium, K2, magnesium, zinc
    Patient's biomedical engineering background enabled educated self-optimization (not representative)

Geographic Variation:

    Data collected across three countries with different healthcare systems
    Laboratory assay changes over 30 years
    Cross-laboratory comparability assessed but not perfect

Bias:

    Self-reported adherence and symptoms
    Patient-directed optimization introduces selection bias
    Retrospective data collection



The dataset comprises three CSV files totaling approximately 15 KB:
File 1: php_laboratory_measurements_30y.csv

Structure: 18 rows × 15 columns

Columns:

    measurement_id: Unique identifier (YYYY-MM format)
    years_since_diagnosis: Time from diagnosis (decimal years, range 0.0-30.1)
    age_years: Patient age (decimal years, range 4.5-35.1)
    date_category: Temporal grouping (year_1-5, year_6-10, etc.)
    serum_calcium_mgdL: Total serum calcium (mg/dL)
    ionized_calcium_mmolL: Ionized calcium (mmol/L)
    pth_intact_pgmL: Intact PTH 1-84 (pg/mL)
    vitamin_d_25oh_ngmL: 25-hydroxyvitamin D (ng/mL)
    phosphorus_mmolL: Serum phosphorus (mmol/L)
    magnesium_mmolL: Serum magnesium (mmol/L)
    treatment_era: Categorical (inadequate / optimized)
    country: Geographic location (Egypt / China / Current)
    data_quality_flag: Binary (0=normal, 1=flagged)
    reference_range_calcium: Lab reference range (text)
    notes: Free text annotations

Summary Statistics:

    Total measurements: 18 over 30 years
    Mean measurement interval: 20 months (range: 0.75-96 months)
    Calcium range: 4.50-8.28 mg/dL (inadequate era mean: 6.3±0.9; optimized era mean: 7.7±0.6)
    PTH measurements: 4 total (1000, 269.5, 247.0, 214.3, 206.1 pg/mL)
    Missing data: Varies by variable (PTH 78% missing, vitamin D 78% missing, phosphorus/magnesium 89% missing)

File 2: php_treatment_protocols_30y.csv

Structure: 8 rows × 13 columns

Columns:

    protocol_id: Sequential identifier (P1, P2, etc.)
    start_date: Protocol initiation (YYYY-MM)
    end_date: Protocol termination (YYYY-MM)
    duration_years: Protocol duration (decimal years)
    calcium_dose_mg: Daily elemental calcium (mg)
    calcitriol_dose_mcg: Daily calcitriol (mcg)
    vitamin_d3_dose_IU: Daily vitamin D3 (IU)
    vitamin_k2_mk7_dose_mcg: Daily vitamin K2 as MK-7 (mcg)
    magnesium_dose_mg: Daily elemental magnesium (mg)
    zinc_dose_mg: Daily zinc (mg)
    adherence_estimated: Medication adherence (percentage)
    treatment_era: Categorical (inadequate / optimized)
    protocol_rationale: Brief description (text)

Summary Statistics:

    Total protocols: 8 over 30 years
    Protocol durations: 0.13-6.9 years
    Calcium dose range: 400-3600 mg/day
    Calcitriol dose range: 0.5-2.0 mcg/day
    Vitamin K2 used only in optimized era: 200 mcg/day
    Adherence range: 65-98%

File 3: php_complications_30y.csv

Structure: 12 rows × 10 columns

Columns:

    complication_id: Unique identifier (C01, C02, etc.)
    complication_name: Standardized description
    complication_category: Broad category (neurological / musculoskeletal / cardiovascular / metabolic / other)
    onset_age_years: Age at onset (decimal years)
    onset_year_relative: Years since diagnosis at onset
    severity_score: 1-10 scale (1-3 mild, 4-6 moderate, 7-9 severe, 10 life-threatening)
    documentation_source: Evidence type (imaging / clinical / patient-reported)
    treatment_era_at_onset: Era when first appeared (inadequate / optimized)
    resolution_status: Current status (ongoing / resolved / stabilized / improving)
    clinical_impact_description: Functional impact (text)

Summary Statistics:

    Total complications: 12
    Category distribution: neurological (2), musculoskeletal (3), cardiovascular (1), metabolic (5), other (1)
    Onset ages: 4.5-29.0 years
    Severity distribution: mild (1), moderate (5), severe (4), life-threatening (2)
    All complications onset during inadequate treatment era
    Resolution: 3 resolved, 4 stabilized, 4 improving, 1 ongoing
