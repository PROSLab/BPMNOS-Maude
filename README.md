# BPMNOS-Maude
BPMN Operational Semantics implemented in Maude

THE PROJECT IS STILL A WORK IN PROGRESS.

UP TO NOW, THE MAUDE IMPLEMENTATION OF THE BPMN OPERATIONAL SEMANTICS IS AVAILABLE.

REQUIREMENTS:
- RUNNING CONFIGURATION OF MAUDE (you can get Maude from http://maude.cs.uiuc.edu/download/)
- KNOWLEDGE ABOUT LINEAR TEMPORAL LOGIC (you can have an overview of LTL from https://en.wikipedia.org/wiki/Linear_temporal_logic)

WE PROVIDE TWO DIFFERENT VERSION OF THE IMPLEMENTATION:

- V1 IS THE DIRECT IMPLEMENTATION OF THE SEMANTICS WE DEFINED.
- V2 IS AN IMPROVED VERSION THAT MAKES USE OF PARTICULAR MAUDE OPTIMIZATION TECHNIQUES.

We also provide an additional optimization of V2.

AFTER DOWNLOADING THE BPMN OPERATIONAL SEMANTICS IMPLEMENTATION, YOU CAN EXTRACT
THE FILES AND INSPECT THEM WITH A SIMPLE TEXT EDITOR.

IF YOU WANT TO RUN SOME TEST, THE PROCEDURE IS REPORTED IN THE FOLLOWING.

ONCE EXTRACTED, YOU HAVE THE FOLLOWING FILES .MAUDE
- BPMNOS_SYNTAX CONTAINS THE SYNTAX WE NEED TO IMPLEMENT OUR SEMANTICS [it is equal for all the version]
- THE FILES NAMED BPMNOS_RULES CONTAIN ALL THE REWRITING RULES THAT COMPOSE OUR SEMANTICS
  Most Optimized Version:
  - BPMNOS_RULES_AS_EQUATIONS_COLLABORATION_LEVEL contains the implementation of the rules at Collaboration Level
  - BPMNOS_RULES_AS_EQUATIONS_POOL_LEVEL contains the implementation of the rules at Pool Level
  - BPMNOS_RULES_AS_EQUATIONS_PROCESS_LEVEL contains the implementation of the rules at Process Level
  First Major Optimized Version:
  - BPMNOS_RULES_AS_EQUATIONS_COLLABORATION_LEVEL_2 contains the implementation of the rules at Collaboration Level
  - BPMNOS_RULES_AS_EQUATIONS_POOL_LEVEL_2 contains the implementation of the rules at Pool Level
  - BPMNOS_RULES_AS_EQUATIONS_PROCESS_LEVEL_2 contains the implementation of the rules at Process Level
  First Version:
  - BPMNOS_RULES_3 is the first implementation we have done and is considered V1 of the semantics implementation;
    It contains all the rules for all the BPMN elements.
- BPMNOS_MODEL_CHECKER CONTAINS THE DEFINITION OF THE PROPERTIES TO VERIFY
  We can consider this file like the "main" file we need to load. It will in fact take care of loading the other files into maude.
  It is the only file we need to modify in such a way to pass from a version of the BPMNOS to another.
- BPMNOS_STARTER is a module that presents the rules from BPMNOS_MODEL_CHECKER redefined for being used with MultiVeStA
- BPMNOS_TEST CONTAINS TEST CASES THAT YOU CAN RUN

HOW TO MAKE IT WORK?

1) LAUNCH AN INSTANCE OF MAUDE
2) LOAD THE FILE BPMNOS_STARTER INTO MAUDE USING THE LOAD COMMAND OR OPEN THE FILE AND
COPY THE CONTENT OF THE FILE AND PASTE IT INTO MAUDE;
3) BPMNOS_TEST CONTAINS TESTS ON OUR CASE SCENARIO; YOU CAN SIMULATE AN EXECUTION
OF THE PROCESS OR TEST THE VERIFICATION OF PROPERTIES.
4) To switch between BPMNOS version, you need to modify the BPMNOS_MODEL_CHECKER.
   Open the file and change the lines reported below:

    load BPMNOS_RULES_AS_EQUATIONS_COLLABORATION_LEVEL
    ---load BPMNOS_RULES_AS_EQUATIONS_COLLABORATION_LEVEL_2
    ---load BPMNOS_RULES_3

    protecting BPMNOS-SEMANTICS . ---the most recent version
    ---protecting BPMNOS-SEMANTICS2 .
    ---protecting BPMNOS-SEMANTICS3 .

    the --- symbols are used to comment a codeline; use them to comment the actual used version
    and uncomment the version you want to use. If you want to use V1 (the oldest one) you need
    to comment/uncomment like in the following:

    ---load BPMNOS_RULES_AS_EQUATIONS_COLLABORATION_LEVEL
    ---load BPMNOS_RULES_AS_EQUATIONS_COLLABORATION_LEVEL_2
    load BPMNOS_RULES_3

    ---protecting BPMNOS-SEMANTICS . ---the most recent version
    ---protecting BPMNOS-SEMANTICS2 .
    protecting BPMNOS-SEMANTICS3 .

    If you want to use V2 but not the latest optimization you need to comment like:

    ---load BPMNOS_RULES_AS_EQUATIONS_COLLABORATION_LEVEL
    load BPMNOS_RULES_AS_EQUATIONS_COLLABORATION_LEVEL_2
    ---load BPMNOS_RULES_3

    ---protecting BPMNOS-SEMANTICS . ---the most recent version
    protecting BPMNOS-SEMANTICS2 .
    ---protecting BPMNOS-SEMANTICS3 .



