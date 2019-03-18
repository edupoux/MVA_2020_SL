MVA - Algorithms for Speech and NLP TD 2 (NLP)
========================================

## Contact Information
For any question/request related to this course, please send an email to this address: mva.speech.language@gmail.com

## Assignment details
**The goal of this assignment is to develop a basic probabilistic
parser for French that is based on the CYK algorithm and the
PCFG model and that is robust to unknown words.**

The goal of this assignment is not to produce high-accuracy
parsers. Its goal is rather for you to build a working statistical constituency parsing
architecture based on the CYK algorithm, with a module for handling
out-of-vocabulary words (OOVs) based on edit distance and word
embedding similarity.

More precisely, what you have to develop is:

- a module to extract a PCFG from the training corpus provided (see
below), made of:
	- a probabilistic context-free grammar whose terminals are part-of-speech tags
    - a probabilistic lexicon, i.e. triples of the form (token,
      part-of-speech tag, probability) such that the sum of the
      probabilities for all triples for a given token sums to 1.
- an OOV module that assigns a (unique) part-of-speech to any token
  not included in the lexicon extracted from the training corpus. The
  underlying idea is to assign to an OOV the part-of-speech of a
  "similar" word. This similarity will be computed as a combination of
  formal similarity (to handle spelling errors) and embedding similarity (as
  measured by cosine similarity, i.e. scalar product between
  normalised vectors), to handle both spelling errors and genuine
  unknown words; you must design a reasonable way to combine these two
  similarities. For embedding similarity, you will use
  [the Polyglot embedding lexicon for French](https://sites.google.com/site/rmyeid/projects/polyglot)
  (see the
  [tutorial on Polyglot embeddings](https://nbviewer.jupyter.org/gist/aboSamoor/6046170);
  you can re-use this code)
- a probabilistic implementation of the CYK algorithm that takes tokenised sentences as
      an input. In other words, the input of the parser are files with
      one sentence per line, and each sentence is formed of tokens
      separated from one another by whitespace characters. The output
      should be in the same bracketed format as the training
      data. Regarding the probabilistic part, you will adapt the CYK
      algorithm so that only the best (i.e. most probable) way to
      rewrite an instanciated non-terminal symbol is retained. This
      will give you a recursive, straigtforward way to then retrieve
      the best (i.e. most probable) parse tree for the whole sentence.

You must reimplement yourself the CYK algorithm and the Levenshtein
distance computation.

Use the SEQUOIA treebank v6.0 (file in the GitHub, bracketed format):

- Split it into 3 parts (80% / 10% / 10%)
- Use the 80% for training (extract CFG rules + learn CFG rule probabilities)
- Use the first 10% for development purposes (whatever you want to use it)
- Use the last 10% to evaluate your parser. To keep it simple,
  you can evaluate your part-of-speech accuracy only, i.e. via the
  percentage of tokens for which your parser choses the correct
  part-of-speech. For your information, a standard
  tool for constituency parse evaluation is [`evalb`](https://nlp.cs.nyu.edu/evalb/)

IMPORTANT: You must ignore functional labels: whenever you find a hyphen in a non-terminal name, ignore
it and everything that follows.
For instance, let us consider the sentence:

        ( (SENT (PP-MOD (P En) (NP (NC 1996))) (PONCT ,) (NP-SUJ (DET la) (NC municipalité)) (VN (V étudie)) (NP-OBJ (DET la) (NC possibilité) (PP (P d') (NP (DET une) (NC construction) (AP (ADJ neuve))))) (PONCT .)))

You must interpret it as:
		
        ( (SENT (PP (P En) (NP (NC 1996))) (PONCT ,) (NP (DET la) (NC municipalité)) (VN (V étudie)) (NP (DET la) (NC possibilité) (PP (P d') (NP (DET une) (NC construction) (AP (ADJ neuve))))) (PONCT .)))
Otherwise you might face sparsity issues.


If you need more information about PCFGs and/or CYK algorithm, read [the most
recent version of Jurafsky and Martin's chapter on Syntactic Parsing](https://web.stanford.edu/~jurafsky/slp3/12.pdf).


## Assignment deliverable
Your assignment will be sent in the form of a folder **named according to the  pattern `MVA_TD2_LASTNAME_Firstname`** that
contains two elements:
1. a report (**at least 1 full page, at most 2 full pages, font size 11pt**, reasonable margins, PDF format, in English or French) **named `MVA_TD2_LASTNAME_Firstname_report.pdf`** containing 2 sections:
     - a first section describing your work, how things work, and the
       rationale behind the choices you made,
     - a second section with a brief error analysis: what seems to work, what does not? Any idea why? What would you
       suggest to improve your system?
2. a folder named `system` containing your system. This folder will
   contain three files:
     - a shell script named `run.sh` that reads tokenised text on the standard input (one sentence per line,
       exactly one whitespace between each token, as explained above)
     - a `README` file describing other options or argument to
     `run.sh` (or explicitly stating the absence thereof)
	 - the output of your parser on the evaluation dataset (the last
       10% of the provided treebank). Of course, the input to your
       parser will be the evaluation dataset from which you will have
       first removed all annotations, only retaining the raw
       tokens. This file will be named `evaluation_data.parser_output`

## Handing the assignment
Send your tgz archive to mva.speech.language@gmail.com before the  class on Monday, March 18th. You must follow the following naming conventions:
1. Start the title of your email with "TD2".
2. A tgz compressed version of your `MVA_TD2_LASTNAME_Firstname`
   folder. The tgz archive must be named according to the following
   pattern: **`MVA_TD2_LASTNAME_Firstname.tgz`**


