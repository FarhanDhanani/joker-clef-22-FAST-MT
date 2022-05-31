# [![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger) joker-clef-22-FAST-MT
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


**Evaluation**. Pilot Task 1 includes both classification and interpretation components. Classification performance will be evaluated with respect to accuracy, while interpretation performance will be evaluated semi-manually.

**Result submission**. Participants should put their run results into the folder Documents created for their user and submit them by email to contact@joker-project.com. The email subject has to be in the format [CLEF TASK 1] TEAM_ID.
