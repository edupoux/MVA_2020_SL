MVA - Algorithms for Speech and NLP TD 3
========================================

## Contact Information
For any question/request related to this course, please send an email to this address: mva.speech.language@gmail.com

## Assignment details
**The goal of this assignment is to develop a normalisation system that can change raw English tweets into (partially) normalised tweets, suitable for further NLP processing.**

Your system will have to use two types of information for performing this normalisation task:
- contextual information (the context surrounding a given position helps guessing which correct word are possible in this position)
- formal similarity iformation (a misspelled/non-standard word is usually similar to its correct counterpart)

You are advised to program your system in Python, but this is not mandatory (although using context2vec makes Python a reasonable choice)

For dealing with contextual information, you will use the [*context2vec* program](https://github.com/orenmel/context2vec).

For dealing with formal similarity, you will use the notion of edit distance as computed by the Levenshtein algortithm (or any improvement thereof that you would prefer). You are requested to code yourself the algorithm using dynamic programming (i.e. you are not allowed to use an existing package for computing edit distance).

Beyond these constraints, you are free to do whatever you feel useful:
- You can train context2vec models or use existing ones (if you want to re-train context2vec, you will need a training corpus, which you can create by using tweet corpus creation tools; alternatively, you can play with the corpus provided in this folder).
- You can develop a training corpus and learn whatever you want on this corpus (e.g. the way to combine contextual and formal similarity information), or you can use a fully unsupervised approach.
- You can also develop complementary resources: normalisation lexicon, word embeddings such as those provided by GloVe (tweet-based embeddings available, see [here](https://nlp.stanford.edu/projects/glove/)), etc.
- You can design ways to deal with one-to-many (e.g. _ttyl_ -> _talk to you later_)  and even many-to-many mappings, or chose to only deal with one-to-one mappings.


## Assignment deliverable
Your assignment will be sent in the form of a tgz archive that will contain:
1. a report (min 1 full page, max 2 full pages, font size 11pt, reasonable margins, PDF format, in English or French) **named MVA\_TP3\__LASTNAME_\__Firstname_\_report.pdf** containing 2 sections:
     - a first section describing how your system works, why you decided to design it the way you did, how you built it, which existing software and resources you used, and which software and resources you developed yourself, why, and how,
     - a second section describing which cases are correctly handled by your system, which cases are not handled or not properly handled (overnormalisations and missed normalisations), a brief discussion about the causes of these errors and a few thoughts about how your system could be improved
2. a folder named *system* containing your system. This folder will contain (at least):
     - a shell script named run_system.sh that takes as a first argument the path to a raw corpus to be normalised; this script will assume that the context2vec directory is stored in the variable $CONTEXT2VECDIR
     - a README file describing other options or argument to run_system.sh (or explicitely stating the absence thereof)

## Handing the assignment
Send your tgz archive to mva.speech.language@gmail.com before the next class on Monday, February 19th. You must follow the following naming conventions:
1. Start the title of your email with "TP3".
2. Name your tgz archive according to the following pattern: **MVA\_TP3\__LASTNAME_\__Firstname_.tgz**


