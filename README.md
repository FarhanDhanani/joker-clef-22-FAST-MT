# [![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger) **joker-clef-22-FAST-MT**
## FAST-MT team submission to [Joker CLEF 2022 workshop](https://www.joker-project.com/clef-2022/EN/project)

[![N|Solid](https://upload.wikimedia.org/wikipedia/en/e/e4/National_University_of_Computer_and_Emerging_Sciences_logo.png)](https://nodesource.com/products/nsolid)


The repository contains our submission to the three tasks provided by the [JOKER CLEF](https://www.joker-project.com/clef-2022/EN/project) workshop.

# **TASK 1: CLASSIFY AND EXPLAIN INSTANCES of WORDPLAY**

Train data format: List of classified wordplay instances in a JSON format or a CSV file (for manual runs) with the following fields:

    ID: a unique wordplay identifier
    
    WORDPLAY: wordplay text
    
    TARGET_WORD: word(s)
    
    DISAMBIGUATION: explanation of the wordplay
    
    HORIZONTAL/VERTICAL: co-presence of source and target of the wordplay. In horizontal wordplay, both the source and the target of the wordplay are given (ex. 1: “They’re called lessons because they lessen from day to day”); in vertical wordplay, source and target are collapsed in a single occurrence (ex. 2: “How do you make a cat drink? Easy: put it in a liquidizer”)
    
    MANIPULATION_TYPE: Identity (source and target are formally identical, as in ex. 2 above); Similarity (as in ex. 1 above: source and target are not perfectly identical, but the resemblance is obvious); Permutation (the textual material is given a new order, as in anagrams or spoonerism. Ex. 3: “Dormitory = dirty room”); Abbreviation (an ad-hoc category for textual material where the initials form another meaning, as in acrostics or “funny” acronyms. Ex. 4: “BRAINS: Biobehavioral Research Awards for Innovative New Scientists”)
    
    MANIPULATION_LEVEL: most wordplay involves some kind of phonological manipulation – that’s why Sound will be the default category. Examples 1 and 2 involve a clear sound similarity (ex. 1) or identity (ex. 2). Only if this category cannot be applied to the wordplay should you look for another level of manipulation. First consider whether the manipulation involves Writing (as in ex. 3 and 4). If neither Sound nor Writing are manipulated, specify the level of manipulation as Other. This level of manipulation may arise, for instance, in chiasmuses (ex. 5: “We shape our buildings, and afterwards our buildings shape us”).
    
    CULTURAL_REFERENCE: this is a binary (True/False) category. In order to understand some instances of wordplay, one has to be aware of some extra-linguistic factors
    
    CONVENTIONAL_FORM: this is a binary (True/False) category, e.g. Tom Swifty (wellerism), Monsieur et Madame… ont un fils
    
    OFFENSIVE (not evaluated category): some wordplay instances are marked as offensive.


Example:Train data format: 

    [{"ID":"noun_1063","WORDPLAY":"Elimentaler","TARGET_WORD":"Elimentaler","DISAMBIGUATION":"Emmental (cheese) + Eliminator","HORIZONTAL\/VERTICAL":"vertical","MANIPULATION_TYPE":"Similarity","MANIPULATION_LEVEL":"Sound","CULTURAL_REFERENCE":false,"CONVENTIONAL_FORM":false,"OFFENSIVE":null},{"ID":"pun_341","WORDPLAY":"Geologists can be sedimental about their work.","TARGET_WORD":"sedimental","DISAMBIGUATION":"sentimental\/sediment","HORIZONTAL\/VERTICAL":"vertical","MANIPULATION_TYPE":"Similarity","MANIPULATION_LEVEL":"Sound","CULTURAL_REFERENCE":false,"CONVENTIONAL_FORM":false,"OFFENSIVE":null}]

Test data input format: List of wordplay instances to classify in a JSON format or a CSV file (for manual runs) with the following fields:

    ID: a unique wordplay identifier
    WORDPLAY: wordplay text

Input example:

    [{"ID":"noun_1","WORDPLAY":"Ambipom"},{"ID":"het_1011","WORDPLAY":"These are my parents, said Einstein relatively"}]

Test data output format:

List of wordplay instances to be classified in a JSON format or a CSV file (for manual runs) with the following fields:

    RUN_ID: Run ID starting with team_id_ (as registered at the CLEF website)
    
    MANUAL: Whether the run is manual {0,1}
    
    ID: a unique wordplay identifier from the input file
    
    WORDPLAY: wordplay text
    
    TARGET_WORD: word(s)
    
    DISAMBIGUATION: explanation of the wordplay
    
    HORIZONTAL/VERTICAL: co-presence of source and target of the wordplay (horizontal/vertical)
    
    MANIPULATION_TYPE: Identity/Similarity/Permutation/Abbreviation
    
    MANIPULATION_LEVEL: Sound/Writing/Other.
    
    CULTURAL_REFERENCE: this is a binary (True/False) category. In order to understand some instances of wordplay, one has to be aware of some extra-linguistic factors
    
    CONVENTIONAL_FORM: this is a binary (True/False) category, e.g. Tom Swifty (wellerism), Monsieur et Madame… ont un fils
    
    OFFENSIVE (not evaluated category): some wordplay instances are marked as offensive.

Output example:

    [{"RUN_ID":"RT","MANUAL":1,"ID":"noun_1063","WORDPLAY":"Elimentaler","TARGET_WORD":"Elimentaler","DISAMBIGUATION":"Emmental (cheese) + Eliminator","HORIZONTAL\/VERTICAL":"vertical","MANIPULATION_TYPE":"Similarity","MANIPULATION_LEVEL":"Sound","CULTURAL_REFERENCE":false,"CONVENTIONAL_FORM":false,"OFFENSIVE":null},{"RUN_ID":"RT","MANUAL":1,"ID":"pun_341","WORDPLAY":"Geologists can be sedimental about their work.","TARGET_WORD":"sedimental","DISAMBIGUATION":"sentimental\/sediment","HORIZONTAL\/VERTICAL":"vertical","MANIPULATION_TYPE":"Similarity","MANIPULATION_LEVEL":"Sound","CULTURAL_REFERENCE":false,"CONVENTIONAL_FORM":false,"OFFENSIVE":null}]




# **TASK 2: TRANSLATE SINGLE WORDS (NOUNS) CONTAINING WORDPLAY.**

Train data format: List of translated wordplay instances in a JSON format or a CSV file (for manual runs) with the following fields:

    id: a unique wordplay identifier
    en: wordplay text in English (source)
    fr: wordplay text in French (target)

Example:

    [{"id":"noun_1","en":"Ambipom","fr":"Capidextre"}]

Test data input format: List of wordplay instances to translate in a JSON format or a CSV file (for manual runs) with the following fields:

    id: a unique wordplay identifier
    en: wordplay text in English (source)

Input example:

    [{"id":"noun_1185","en":"Fungun"}]

Test data output format:

List of wordplay instances to be translated in a JSON format or a CSV file (for manual runs) with the following fields:

    RUN_ID: Run ID starting with team_id_ (as registered at the CLEF website)
    MANUAL: Whether the run is manual {0,1}
    id: a unique wordplay identifier
    en: wordplay text in English (source)
    fr: wordplay text in French (target)

Output example:List of wordplay instances to be translated in a JSON format or a CSV file (for manual runs) with the following fields:

    [{"RUN_ID":"OFFICIAL","MANUAL":1,"id":"noun_1","en":"Ambipom","fr":"Capidextre"}]
    
    
# **TASK 3: TRANSLATE ENTIRE PHRASES CONTAINING WORDPLAY.**

Train data format: List of translated wordplay instances in a JSON format or a CSV file (for manual runs) with the following fields:

    id: a unique wordplay identifier
    en: wordplay text in English (source)
    fr: wordplay text in French (target)

Example:

    [{"id":"pun_724_1","en":"My name is Wade and I'm in swimming pool maintenance.","fr":" Je m\u2019appelle Jacques Ouzy, je m\u2019occupe de l\u2019entretien des piscines."}]

Test data input format: List of wordplay instances to translate in a JSON format or a CSV file (for manual runs) with the following fields:

    id: a unique wordplay identifier
    en: wordplay text in English (source)

Input example:

    [{"id":"het_713","en":"Ever since my mineral extraction facility was converted to parking, I've had a lot on my mine."}]


Test data output format:

List of wordplay instances to be translated in a JSON format or a CSV file (for manual runs) with the following fields:

    RUN_ID: Run ID starting with team_id_ (as registered at the CLEF website)
    MANUAL: Whether the run is manual {0,1}
    id: a unique wordplay identifier
    en: wordplay text in English (source)
    fr: wordplay text in French (target)

Output example:

    [{"RUN_ID":"JCM","MANUAL":1,"id":"pun_724_1","en":"My name is Wade and I'm in swimming pool maintenance.","fr":" Je m\u2019appelle Jacques Ouzy, je m\u2019occupe de l\u2019entretien des piscines."}]


## Just to preset a quick overview, we have utilized the following Transformer models to complete the three tasks provided in the JOKER CLEF workshop.

### TASK-1: SOLVE VIA COMBINATION OF TOKEN-CLASSIFICATION, TEXT CLASSIFICATION AND TEXT GENERATION
 1) [BERT-BASE](https://huggingface.co/bert-base-cased) for token classification and predicting the words forming the wordplay.
 2) [KEY-BERT](https://maartengr.github.io/KeyBERT/) for token classification and predicting the words forming the wordplay.
 3) Distil-BERT(https://huggingface.co/distilbert-base-uncased) for text classification and predicting categorical values mentioned in the task-1
 4) GPT-X for generating interpretation

### TASK-2: SOLVE BY MAPPING THE PROBLEM TO QUESTION ANSWERING DOMAIN
 1) [CamemBERT](https://huggingface.co/etalab-ia/camembert-base-squadFR-fquad-piaf) for extractive question answering to predict french translation of popular English nouns from movies.
 2) [DistilBERT](https://huggingface.co/distilbert-base-cased-distilled-squad) for extractive question answering to predict french translation of popular English nouns from movies.

### TASK-3 SOLVE VIA SEQUENCE TO SEQUENCE LEARNING APPROACHES
 1)  [HELSINKI-NLP/opus-mt-en-fr](https://huggingface.co/Helsinki-NLP/opus-mt-en-fr) for sequence to sequence translation of English text to French.
 2)  [GOOGLE T5 small](https://huggingface.co/t5-small/tree/main) for sequence to sequence translation of English text to French.
 3)  [GOOGLE T5 base](https://huggingface.co/t5-base) for sequence to sequence translation of English text to French4
 4)  [GOOGLE T5 large](https://huggingface.co/t5-large) for sequence to sequence translation of English text to French.
