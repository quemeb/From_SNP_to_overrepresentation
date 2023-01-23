# SNP to rsID to Overrepresentation 

Workflow for mapping SNPs to rsID to performing overrepresentation analysis 

```mermaid
flowchart TD

A[SNP file] --> B[[R_Script]]
B --> |rsID list| C[(AnnoQ)]
Z[rsID list] --> C
C --> D{{Annovar}} & E{{SnpEff}} & F{{VEP}}
D & E & F ---> |gene IDs| G[[Python_script]] 
G --> |unique gene IDs| H[(Panther)]
H --> |Fisher's exact|I[Overpresentation]

click C "http://annoq.org/" _blank
click H "http://pantherdb.org/" _blank

```

The pipeline allows for the user to start from a list of SNPs (Version Seq37) or from a list of rsID. 

If you start from the list of SNPs, please refer to SNPs_Seq37_example.csv to see the input format that the R program accepts (this can be modified by the user). 
Next, you will receive a list of rsID from the R program. 

The rsID list will need to be run through [ANNOQ](annoq.org) to obtain the geneIDs for the SNPs. 

Using the Python script you will be able to obtain the unique list of gene IDs, which you will run through [Panther](pantherdb.org).

[Panther](pantherdb.org) will perform a Fisher's exact test to find any overrepresentation in your input list. 


