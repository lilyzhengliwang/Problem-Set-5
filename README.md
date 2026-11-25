# Problem-Set-5

### Recommendation to Head of Risk

Sign the penalised logistic model, but not on the vendor's 93% accuracy. That is what approving every applicant scores (93.2% on our test set), so it proves nothing.

**What it is worth** 

On 3,000 simulated test applications (206 defaults), the model ranks risk well: ROC AUC 0.82, and precision-recall AUC 0.28 against 0.07 for a no-skill model. At the right threshold it cuts expected loss by 32% versus approving everyone: 2.8 cents lost per $1 lent, against 4.1 cents. A random forest was no better (McNemar p = 0.38), so we use the simpler, easier-to-explain model. Its probabilities passed a calibration check.

**Threshold**

decline above about 14%, not 0.5. At 0.5 the model declines only 17 applicants and catches 4% of defaults. At 0.13 to 0.14 it declines about 15% of applicants, catches about 59% of defaults, and wrongly declines about 330 good borrowers. Accuracy falls to 86%, which is the price of catching defaults.

**Cost assumptions**

A missed default loses 60% of principal. A wrongly declined good applicant costs 10%: 8% lost interest margin plus 2% reputational cost (my estimate of lost future business). The rule is to decline when default probability exceeds 1/(1+R), where R = 6 is the ratio of the two costs.

**What would change my answer**

The cost ratio. The 2% reputational figure is an assumption, and if real costs put R far from 6, the threshold moves with it. Measure it before go-live.
