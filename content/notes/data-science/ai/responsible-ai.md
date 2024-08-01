---
title: responsible ai
date: 2023-12-05T00:00:00-06:00
draft: false
weight: 1
---

# Abstract [[Documentation](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE5cmFl)]
Microsoft's Responsible AI standard defines a responsible AI system as ethical (inclusive and accountable) and explainable (fair, transparent, reliable, safe, private and secure).

The Six Responsible AI Principles:

## Fairness
> How might an AI system allocate opportunities, resources, or information in ways that are fair to the humans who use it?

An AI system's decisions must not discriminate against, or express a bias toward, a group or individual based on gender, race, sexual orientation, or religion.

## Inclusiveness
> How might the system be designed to be inclusive of people of all abilities?

An AI system must be fair and inclusive in its assertions. It must not discriminate or hinder different races, disabilities, or backgrounds.

AI must consider all human races and experiences. Inclusive design practices can help developers understand and address potential barriers that could unintentionally exclude people.

## Reliability & Safety
> How might the system function well for people across different use conditions and contexts, including ones it was not originally intended for?

An AI system should perform as it was originally designed and to respond safely to new situations. Its inherent resilience should resist intended or unintended manipulation.
- Reliability and safety can be achieved through:
  - Rigorous testing and validation for operating conditions to ensure that the system responds safely to edge cases.
  - Integrating  A/B testing and champion/challenger methods into the evaluation process.
  - Robust monitoring and model-tracking process to reactively and proactively measure the model's performance (and retrain it for modernization, as necessary).

## Security & Privacy
> How might the system be designed to support privacy and security?

- AI systems must secure sensitive data.
- AI systems must not compromise and individual's privacy.
- AI developers may consider differential privacy as one approach toward security and privacy.  This approach randomizes data and adds noise to conceal personal information.

## Transparency
> What data and algorithms were used to train the model?  
> What transformation logic was applied to the data?  
> What is the final model that was generated?  
> What assets are associated with the model?

AI systems must justify their decisions and how they reach their conclusions.

## Accountability
>How might people misunderstand, misuse, or incorrectly estimate the capabilities of the system?  
>How can we create oversight so that humans can be accountable and in control?

- The people who design and deploy an AI system need to be accountable for its actions and decisions, especially as we progress toward more autonomous systems.
- Organizations should consider establishing an internal review body that provides oversight, insights, and guidance about developing and deploying AI systems.

# Other Resources
- [Responsible AI Tools & Practices](https://www.microsoft.com/en-us/ai/tools-practices)
- [Responsible AI Toolbox](https://responsibleaitoolbox.ai/)
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
- [Blueprint for an AI Bill of Rights](https://www.whitehouse.gov/ostp/ai-bill-of-rights/)