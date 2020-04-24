# UMLS Knowledge Sources Tutorial
This is instruction on how to make use of UMLS to generate the knowledge graph dataset. 


The Three UMLS Knowledge Sources
* [Metathesaurus](https://www.nlm.nih.gov/research/umls/knowledge_sources/metathesaurus/index.html): Terms and codes from many vocabularies, including CPT, ICD-10-CM, LOINC, MeSH, RxNorm, and SNOMED CT. Hierarchies, definitions, and other relationships and attributes.
* [Semantic Network](https://semanticnetwork.nlm.nih.gov/): Broad categories (semantic types) and their relationships (semantic relations).
* [SPECIALIST Lexicon and Lexical Tools](https://lexsrv3.nlm.nih.gov/Specialist/Home/index.html): A large syntactic lexicon of biomedical and general English and tools for normalizing strings, generating lexical variants, and creating indexes.


## Install:

[Install software guide](https://www.nlm.nih.gov/research/umls/implementation_resources/metamorphosys/help.html)

## Dataset:

[Data set description](https://www.ncbi.nlm.nih.gov/books/NBK9685/)
RRF file can be read by line and set sep='|'. 


### 1. [Concepts Names and Sources](https://www.ncbi.nlm.nih.gov/books/NBK9685/#ch03.sec3.3.4)  File = MRCONSO.RRF
       
### 2. [Related Concepts](https://www.ncbi.nlm.nih.gov/books/NBK9685/#ch03.sec3.3.9)  File = MRREL.RRF

  [the abbrevation list](https://www.nlm.nih.gov/research/umls/knowledge_sources/metathesaurus/release/abbreviations.html) 
  concludes all **CONCEPTS Relation** in two tables: 
   * REL: 10 types
   * RELA: 577 types
   * CUI Concepts: 3,338,414
            
            some main cols.
            CUI1	Unique identifier of first concept        **3,338,414**
            AUI1	Unique identifier of first atom
            STYPE1	The name of the column in MRCONSO.RRF that contains the identifier used for the first element in the relationship, i.e. AUI, CODE, CUI, SCUI, SDUI.
            REL	Relationship of second concept or atom to first concept or atom  
            10 types, find REL list in abbreviations table link before** 
            CUI2	Unique identifier of second concept
            AUI2	Unique identifier of second atom
            STYPE2	The name of the column in MRCONSO.RRF that contains the identifier used for the second element in the relationship, i.e. AUI, CODE, CUI, SCUI, SDUI.
            RELA Additional (more specific) relationship label (optional)         
                  577 types, find RELA in abbreviations table link before
            
            some examples
                  REL: 
                        AQ	Allowed qualifier
                        CHD	has child relationship in a Metathesaurus source vocabulary
                        DEL	Deleted concept
                        PAR	has parent relationship in a Metathesaurus source vocabulary
                  RELA: (the paper manually select one list of rela from 577)
                        isa	                                   Is a
                        is_normal_cell_origin_of_disease	is normal cell origin of disease
                     
### 3. [Semantic Types](https://www.ncbi.nlm.nih.gov/books/NBK9685/#ch03.sec3.3.7) （File = MRSTY.RRF）  
   STY: total **127 Semantic Types**
            
### 4. [Semantic Network](https://www.ncbi.nlm.nih.gov/books/NBK9679/) （File = SRDEF.RRF or SRSTR.RRF）
       
   * In SRSTR.RRF: there are **49 types of sematics RL**  and **182 semantic Typs**
   
        SRDEF.RRF: Basic information about the Semantic Types and Relations.
        
              Field	Description
              RT:	Record Type (STY = Semantic Type or RL = Relation). 
              UI:	Unique Identifier of the Semantic Type or Relation.
              STY/RL:	Name of the Semantic Type or Relation.
              STN/RTN:	Tree Number of the Semantic Type or Relation.
              DEF:	Definition of the Semantic Type or Relation.
              EX:	Examples of Metathesaurus concepts with this Semantic Type (STY records only).
              UN:	Usage note for Semantic Type assignment (STY records only).
              NH:	The Semantic Type and its descendants allow the non-human flag (STY records only).
              ABR:	Abbreviation of the Relation Name or Semantic Type.
              RIN:	Inverse of the Relation (RL records only).
 
       SRSTR.RRF: Structure of the Network. 
       
            Field	Description
            STY/RL:	Argument 1 (Name of a Semantic Type or Relation).      
            RL:	Relation ("isa" or the name of a non-hierarchical Relation). 
            STY/RL:	Argument 2 (Name of a Semantic Type or Relation); if this field is blank this means that the Semantic     Type or Relation is one of the top nodes of the Network.
            LS:	Link Status (D = Defined for the Arguments and its children; B = Blocked; DNI = Defined but Not Inherited by the children of the Arguments).
            N.B.: The relations expressed in this table are binary relations and the arguments are ordered pairs. The relations are stated only for the top-most node of the "isa" hierarchy of the Semantic Types to which they may apply.
            
            

  





