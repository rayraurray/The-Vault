Divergence based domain adaptation works on the principle of minimizing some divergence based criterion between source and target distribution, hence leading to domain invariant-features.

Domain-invariant features refers to features that do not change significantly whether they are observed in the source domain or the target domain.

The goal is to learn such features that are effective and relevant for the task in both the training (source) and the application (target) environments.

By identifying and using domain-invariant features, a machine learning model can perform well on data from the target domain even though it was trained on data from the source domain.

---

Imagine you have a dataset of car images taken during the day and you want to classify car types in images taken at night. The lighting conditions are different, but the shape of the cars, their logos, and design features like grills and window shapes do not change between day and night.

When training a model for car classification, domain-invariant features could include Car Shape, Logos, Wheels, etc.

By focusing on these domain-invariant features, a classification model trained on daytime images can still recognize and classify cars in nighttime images effectively. The domain shift due to lighting
conditions is mitigated by the model's focus on features that are constant across both domains.

![[Divergence based Domain Adaptation.png]]