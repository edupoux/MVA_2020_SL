MVA - Algorithms for Speech and NLP TD 4
========================================

## Contact Information
For any question/request related to this course, please send an email to this address: mva.speech.language@gmail.com

## Assignment details
**The goal of this assignment is to develop a basic probabilistic parser for French based on the CYK algorithm and the
PCFG model.**

If you need more information about the CYK algorithm, read [the most
recent version of Jurafsky and Martin's chapter on Syntactic Parsing](https://web.stanford.edu/~jurafsky/slp3/12.pdf). If you need more information about PCFGs,
read [the most recent version of Jurafsky and Martin's chapter on Statistical Parsing](https://web.stanford.edu/~jurafsky/slp3/13.pdf).

Use the SEQUOIA treebank v6.0 (file in the GitHub, bracketed format):

- Split it into 3 parts (80% / 10% / 10%)
- Use the 80% for training (extract CFG rules + learn CFG rule probabilities)
- Use the first 10% for development purposes (whatever you want to use them for)
- Use the last 10% to evaluate your parser

IMPORTANT: I strongly advice you ignore the functional labels: whenever you find a hyphen in a non-terminal name, ignore
it and everything that follows.
For instance, let us consider the sentence:

        ( (SENT (PP-MOD (P En) (NP (NC 1996))) (PONCT ,) (NP-SUJ (DET la) (NC municipalité)) (VN (V étudie)) (NP-OBJ (DET la) (NC possibilité) (PP (P d') (NP (DET une) (NC construction) (AP (ADJ neuve))))) (PONCT .)))

I recommend you interpret it as:
		
        ( (SENT (PP (P En) (NP (NC 1996))) (PONCT ,) (NP (DET la) (NC municipalité)) (VN (V étudie)) (NP (DET la) (NC possibilité) (PP (P d') (NP (DET une) (NC construction) (AP (ADJ neuve))))) (PONCT .)))
Otherwise you might face sparsity issues.

You can use any other resource you want (e.g. lexicon for dealing with unknown words)

## Assignment deliverable
Your assignment will be sent in the form of a tgz archive that will contain:
1. a report (min 1 full page, max 2 full pages, font size 11pt, reasonable margins, PDF format, in English or French) **named MVA\_TP4\__LASTNAME_\__Firstname_\_report.pdf** containing 2 sections:
     - a first section describing how your parser works, how you built it, which additional resources you used (if any) and how,
     - a second section with a brief error analysis: what seems to work, what does not? Any idea why? What would you
       suggest to improve your parser?
2. a folder named `parser` containing your parser. This folder will contain (at least):
     - a shell script named `run_parser.sh` that reads tokenised text on the standard input (one sentence per line,
       exactly one whitespace between each word)
     - a `README` file describing other options or argument to `run_parser.sh` (or explicitly stating the absence thereof)

## Handing the assignment
Send your tgz archive to mva.speech.language@gmail.com before the next class on Monday, February 26th. You must follow the following naming conventions:
1. Start the title of your email with "TP4".
2. Name your tgz archive according to the following pattern: **MVA\_TP4\__LASTNAME_\__Firstname_.tgz**


