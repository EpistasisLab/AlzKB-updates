Although resources from Hetionet have newer versions, Hetionet itself does not have an up-to-date plan for updates. To ensure AlzKB has current data, we have replicated them using the [rephetio paper](https://git.dhimmel.com/rephetio-manuscript/) and [source code](https://github.com/dhimmel/integrate/blob/master/integrate.ipynb). The following is a detailed guide for regularly replicating this process.

## Gene Ontology
Download 
- gene2go.gz from ftp://ftp.ncbi.nih.gov/gene/DATA/gene2go.gz  (update daily, we downloaded on May 13, 2024)
- Entrez Gene info from ftp://ftp.ncbi.nih.gov/gene/DATA/gene_info.gz (update daily, we downloaded on May 13, 2024)
- go from https://purl.obolibrary.org/obo/go/go-basic.obo (V 2024-04-24)

Get GO_annotations-9606-inferred-allev.tsv from https://github.com/dhimmel/gene-ontology/blob/d57fd938f90c79152449f5cd23d3c438a19ac2f5/code/process.ipynb#L492 

Extract data with code from Anatomy Gene Ontology Domains https://github.com/dhimmel/integrate/blob/master/integrate.ipynb 


## MeSH 
Download https://nlmpubs.nlm.nih.gov/projects/mesh/MESH_FILES/xmlmesh/desc2024.xml

Get symptoms.tsv from https://github.com/dhimmel/mesh/blob/gh-pages/descriptors.ipynb 

Extract data with code from Symptom Nodes https://github.com/dhimmel/integrate/blob/master/integrate.ipynb 


## Uberon (requires MeSH)
[Download](http://obophenotype.github.io/uberon/current_release)
- http://purl.obolibrary.org/obo/uberon/uberon-basic.obo (V2024-03-22)
- http://purl.obolibrary.org/obo/uberon/uberon-ext.obo (V2024-03-22)
- negative evidence df https://github.com/obophenotype/uberon/issues/703#issuecomment-113131156

Get human-constraint.tsv from https://github.com/dhimmel/uberon/blob/gh-pages/human-constraint.ipynb

Get hetio-slim.tsv from https://github.com/dhimmel/uberon/blob/gh-pages/process.ipynb 

Extract data with code from Anotomy Nodes https://github.com/dhimmel/integrate/blob/master/integrate.ipynb 


## DrugCentral (requires Disease Ontology)
DrugBank
- Download drugbank.xml.gz from https://go.drugbank.com/releases/latest (V5.1.12 2024-03-14)
- Get drugbank-slim.tsv from https://github.com/dhimmel/drugbank/blob/gh-pages/parse.ipynb 


DrugCentral
- Download DrugCentral  database dump file from https://drugcentral.org/download (V 2023-11-01)
- Install PostgreSQL from https://www.enterprisedb.com/downloads/postgres-postgresql-downloads based on https://www.postgresql.org/download/macosx/ 
- Import table dump (.SQL) using pgAdmin based on  https://stackoverflow.com/questions/18736345/export-and-import-table-dump-sql-using-pgadmin 
- Get pharm_class.tsv & identifiers.tsv from the database above by running the following query and save as tsv
  - SELECT * FROM public.pharma_class 
  - SELECT * FROM public.identifier
  (previously: https://github.com/olegursu/drugtarget/tree/9a6d84bed8650c6c507a2d3d786814c774568610)

Get classes.tsv & drug-to-class.tsv from
https://github.com/dhimmel/drugcentral/blob/master/drugcentral-to-rephetio.ipynb 

Extract data with code from Pharmacologic Classes (Add 'Chemical Structure' to class_types)
https://github.com/dhimmel/integrate/blob/master/integrate.ipynb


## MEDLINE (requires MeSH & DiseaseOntology)
Download a slim DO https://think-lab.github.io/d/44/#144 

Download HumanDO.obo https://github.com/DiseaseOntology/HumanDiseaseOntology/blob/main/src/ontology/HumanDO.obo (V 2024-03-28)

Reads DO Slim terms and generates slim-specific datasets https://github.com/dhimmel/disease-ontology/blob/gh-pages/slim.ipynb 

Get disease-disease-cooccurrence.tsv from https://github.com/hetio/medline/blob/main/diseases.ipynb 

Get disease-symptom-cooccurrence.tsv from https://github.com/hetio/medline/blob/main/symptoms.ipynb 

Get disease-uberon-cooccurrence.tsv from https://github.com/hetio/medline/blob/main/tissues.ipynb 

Extract data with code from Symptom edges https://github.com/dhimmel/integrate/blob/master/integrate.ipynb 


## BindingDB
UniProt
- Download idmapping.dat.gz from https://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/idmapping/idmapping.dat.gz   (readme: https://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/idmapping/README ) (V 2024-05-13)
- Get GeneID.tsv.gz from https://github.com/dhimmel/uniprot/blob/gh-pages/mappings.ipynb

Entrez-Gene
- Use Homo_sapiens.gene_info.gz as same as NCBI data resource ([The data](https://ftp.ncbi.nih.gov/gene/DATA/GENE_INFO/Mammalia/Homo_sapiens.gene_info.gz) update daily, we downloaded on May 13, 2024)
- Get genes-human.tsv from https://github.com/dhimmel/entrez-gene/blob/gh-pages/process.ipynb
  
Drugbank
- Get drugbank.tsv, drugbank-slim.tsv, and proteins.tsv from https://github.com/dhimmel/drugbank/blob/gh-pages/parse.ipynb
  
Drugcentral
- Download Drug-target interaction data from https://drugcentral.org/download (previously: https://github.com/olegursu/drugtarget/blob/9a6d84bed8650c6c507a2d3d786814c774568610/drug_target.tsv  )
- Get targets.tsv from https://github.com/dhimmel/drugcentral/blob/master/drugcentral-to-rephetio.ipynb
  
BindingDB
- Get bindingdb.tsv  from https://github.com/dhimmel/drugbank/blob/6b9ae386d6ba4a0eca2d66d4b0337a6e90fe81f4/unichem-map.ipynb 
- Download BindingDB_All_202405_tsv.zip from https://www.bindingdb.org/rwd/bind/chemsearch/marvin/Download.jsp 
- Get binding.tsv.gz from https://github.com/dhimmel/bindingdb/blob/gh-pages/process.ipynb 
- Get bindings-drugbank-gene.tsv from https://github.com/dhimmel/bindingdb/blob/gh-pages/collapse.Rmd
  
Compile
- Get CbG-binding.tsv from https://github.com/dhimmel/integrate/blob/master/compile/CbG-binding.ipynb
  
Extract data with code from Compound bindings https://github.com/dhimmel/integrate/blob/master/integrate.ipynb 

