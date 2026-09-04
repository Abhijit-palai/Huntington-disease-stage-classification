# Huntington-disease-stage-classification
It is a Multiclass Classification Problem where we have to predict the disease stage of the patient.

---

Huntington's disease is a fatal, inherited neurodegenerative disorder that causes the progressive breakdown of nerve cells in the brain

**Huntington's disease (HD)** is a genetic, progressive disorder that gradually affects the brain. It can cause problems with movement, thinking, and behavior/emotions.

What **causes** Huntington's disease?

HD is caused by a mutation in the HTT gene. The mutation is an expansion of a repeated DNA sequence called a CAG repeat.

Normally, the gene has a limited number of CAG repeats. In Huntington's disease, there are too many.

This causes production of an abnormal huntingtin protein, which eventually damages and kills neurons, particularly in certain areas of the brain.

**Why** does someone get it?

The important point is that HD is inherited.

If one parent has the disease-causing HTT mutation, each child has approximately a 50% chance of inheriting it.

It is autosomal dominant, meaning one altered copy of the gene is sufficient to cause the disease.

Main **symptoms**

HD generally affects three major areas:

1. Movement

Involuntary jerking/twisting movements (chorea)
Problems with coordination and balance
Difficulty walking
Slower or rigid movements in later stages
Difficulty speaking or swallowing

2. Cognitive function

Slower thinking
Difficulty concentrating
Problems with planning and organization
Difficulty making decisions
Memory problems
Progressive cognitive decline

3. Behavioral/psychiatric

Depression
Irritability
Anxiety
Changes in personality
Impulsivity
In some people, hallucinations or other psychiatric symptoms
Simple way to remember it

Think of Huntington's disease as affecting:

🧠 Thinking + 🚶 Movement +  Behavior

And because it is progressive, symptoms generally become more significant over time.

If you're studying a Huntington's disease dataset for ML, variables such as age, motor symptoms, cognitive decline, psychiatric symptoms, family history, etc. may be used as features to predict a diagnosis or disease severity.

---

**Observations Till EDA**

* The dataset contains 48,536 records.
* The target variable is `Disease_Stage`, which is a multiclass categorical variable.
* The dataset contains both numerical and categorical features.
* Missing values were checked across the dataset using null counts and percentages.
* There have a column named as `Cognitive_decline` which have null values of approximately **25%** of the total columns data. It is a categorical data and it is important for prediction.

* Since the column has meaningful ordinal categories such as Mild, Moderate, and Severe, it is not a good idea to drop it. Missing-value handling should be evaluated carefully and also didn't fill by mode. i am normally fill it by 'Unknown'.
* Duplicate records were checked.
* No duplicate values in the dataset .
* Outliers or wrong values were checked.
* No outliers in the numerical col and no wrong values in the categorical col.
* Data are Normally distributed.

* There have value merged columns like `Chromosome_Location` . i was normally split into Chromosome , Chromosome_Arm , Chromosome_Region.

* These should generally be treated as categorical features, rather than treating 16.3 or 14.1 as ordinary continuous numbers.

* Using alpha = 0.05
`Protein_Aggregation_Level` and `HTT_CAG_Repeat_Length` showed statistically significant association with the target.
The remaining numerical features did not show statistically significant association based on this test.


* Therefore, at the 5% significance level, these features did not show statistically significant association with Disease_Stage according to the Chi-square test.

* I found Patient_ID , Random_Gene_Sequence , Random_Protein_Sequence
with extremely high Chi-square scores.
These should not automatically be selected because of their high Chi-square scores.

* Patient_ID is an identifier and should be removed.
* Random_Gene_Sequence and Random_Protein_Sequence appear to be random/high-cardinality sequence features.

* Then go for categorical data encoding , for diff categorical data using diff encoding methods , for target col use `LabelEncoder()`.
* After it Performing Splitting by `train_test_split`.