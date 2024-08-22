# Checklist

Ensure we don't get sued!

These standards must be hidden:

- SOC-2
- ISO 27002
- ISO 27017
- ISO 27018
- ISO 27701
- CCM
- EU CoC

These standards are approved to show:
- FedRAMP
- C5


Explain this limitation in the README.md, e.g., we can't provide all data used, and we can't provide the model that we finetuned. 
Explain too that anyone else can do this same thing, but they'd need to be buy the documents themselves and be aware that there could be legal risk.

Ensure things actually run for each IPYNB
- Gentlemen's agreement that we always update PIP first
- ensure the requirements file will run code without error
- TODO: ask Prith if I need a requirements.txt for all notebooks, since they have very different and big requirements, or just one for everything

Note: What all IPYNBs are needed? First priority is doing what the paper said.
Note: Don't need the data cleaning stuff or many visuals. 
Note: Potentially have one IPYNB that's a data exploration and visualization one
Note: Re data, provide what data as we can, used in the finetuning process (CSV for the final labeled data, CSV/xlsx for the control texts - the ones we can't include)
Note: Any others would come after the topic modeling one, probably not be that important.

# "1-OCR.ipynb" - IPYNB for passing the dirty control texts to be fixed by OpenAI
- Note: explain in the notebook that a lot of the cleaning had to be done manually, and it was mostly for the standards I had to redact
## Req: 
- "data.csv" - XLSX/CSV file with the control texts and metadata, plus ONLY the necessary other columns containing the embedding;
## Outputs:
- "data-clean.csv" - XLSX/CSV file with the control texts and metadata, plus ONLY the necessary other columns - no embeddings
## Status:
- DONE - nobody will be running the code anyways!

# "2-intercoder-reliability.ipynb" - IPYNB for passing the dirty control texts to be fixed by OpenAI
- Note: explain in the notebook that a lot of the cleaning had to be done manually
## Req: 
## Outputs:
- "train-data.csv" - XLSX/CSV file with the human-made training data, but only the agreed upon ones
## Status:
- DONE - just need the requirements file

# "3-finetune.ipynb" - IPYNB for LLM finetuning process
## Req:
- "data-clean.csv" - XLSX/CSV file with the control texts only ()
- "train-data-redacted.xlsx" - XLSX/CSV file with the human-made training data
## Outputs:
- "custom-model.__" # we don't include this though - TBC the extension for a finetuned model
## Status:
- DONE - just need the requirements file

# "4-embeddings.ipynb" - IPYNB for creating embeddings
## Req:
- "data-clean.csv" - XLSX/CSV file with the control texts and metadata, plus ONLY the necessary other columns - no embeddings
## Outputs:
- "data-clean-embeddings.csv" - same as data clean only with calculated embeddings
## Status:
- Prith said the requirements are done - TBC


# "5-topic-modeling.ipynb" - IPYNB for creating hierarchical topics
## Req:
"data-clean-embeddings.csv"

Note: must show what paper describes:
    - HDBScan clustering (min_cluster_size==5)
    - KeyBERTInspired, OpenAI topic representation
    - merge topics and recalculate centroid
    - KeyBERTInspired, OpenAI topic representation
    - Observing final names of the topics
    - Showing how many controls from each document winds up in the topic (Pivot Table)

## Outputs:
- Just stuff in the ipynb
