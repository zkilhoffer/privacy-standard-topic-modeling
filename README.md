# Privacy Standard Topic Modeling

This repo demonstrates the topic modeling pipeline described in *[Kilhoffer and Bashir (2024). Cloud Privacy Beyond Legal Compliance: An NLP analysis of certifiable privacy and security standards](https://ieeexplore.ieee.org/abstract/document/10631062)*.

***TLDR***: The main question we're trying to understand via topic modeling is: *across privacy standards, how do controls accomplish privacy?* 

These terms mean:

- **Standards**: formal documents that give guidance to achieve something, like good cybersecurity protections, interoperability, or in our case, good privacy practices. Privacy standards include FedRAMP, the ISO 27000 series, etc.
- **Controls**: the observable, specific behaviors or actions listed in standards. To become certified with a given standard, a third party must audit an organization to confirm that it has fulfilled its obligations, which is basically doing what the controls say. For example, controls from a privacy standard might require that the organization: (1) thoroughly vets third party data services; (2) minimizes the amount of personally identifiable data it collects; and (3) define data retention and deletion policies.

> ***Note***: Due to concerns over intellectual property and copyright, I cannot provide the whole dataset we collected containing the controls of 9 privacy standards, or the model we finetuned. The model we finetuned could probably be used to view copyrighted content -- for example, by saying in an interactive chat: `Give me the text of this control: ISO 27002 Section 5 Organizational Controls Subsection 5.11 Return of Assets.` Instead, we provide a dataset with all controls of the two freely available standards (FedRAMP and C5) and illustrate the paper's process with that.

# File Overview

Notebooks 1 and 2 are there to demonstrate what we described in [the paper](https://ieeexplore.ieee.org/abstract/document/10631062), while notebooks 3, 4, and 5 walk you through the necessary steps to finetune an LLM and do topic modeling as we did. 

- ***1-OCR.ipynb***: Illustrates the optical character recognition (OCR) we performed to extract controls from the uncooperative PDFs.
- ***2-intercoder_reliability.ipynb***: Shows how we calculated intercoder reliability for our human-labeled data, which was used in the model finetuning.
- ***3-finetune.ipynb***: Performs the actual finetuning in two steps - using a specialized corpus of text, and using human-labeled data. The human-labeled data is a random selection of controls which three researchers labeled using a privacy / cybersecurity framework.
- ***4-embeddings.ipynb***: Creates embeddings using the finetuned model.
- ***5-topic-modeling.ipynb***: Performs the topic modeling, which essentially takes all the controls (which are texts from standards), places them into similar groups, and gives us suggestions for what those groups can be called.
