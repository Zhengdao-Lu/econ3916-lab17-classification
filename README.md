# econ3916-lab17-classification
## Classification: When 90% Accurate Is Worthless
# Objective
I wanted to see how changing the cutoff for predicting loan defaults affects which applicants the model flags and how much its mistakes cost.
# Methodology
- I used 6,000 simulated loan applications and compared a logistic regression model with a rule that approves everyone.
- I interpreted the model’s coefficients as changes in log-odds, converted them to odds ratios, and compared their effects at different starting probabilities.
- I compared precision and recall across six thresholds and wrote precision_recall_at() to calculate both at any cutoff.
- I used cross-validated predictions on the training set to choose the cutoff with the lowest expected cost, then evaluated it on the test set.
# Key Findings
The default rate was 9.6%. Approving everyone was 90.4% accurate. At the usual cutoff of 0.5, my model had the same accuracy and predicted zero defaults.

One additional prior default multiplied the estimated odds of default by 1.63. The change in default probability depended on the starting probability.

The cutoff I chose on the training set was 0.121, close to the closed-form cutoff of 0.118. On the test set, the cutoff of 0.121 cost $944 per applicant, compared with $1,147 at 0.5. At the closed-form cutoff, precision was 0.181 and recall was 0.477.
