The Children's Book Test (CBT)
===============================

Copyright (c) 2015 Facebook. Permission is granted to copy, distribute and/or modify this document under the terms of the GNU Free Documentation License, Version 1.2 or any later version published by the Free Software Foundation; with no Invariant Sections, no Front-Cover Texts, and no Back-Cover
Texts. A copy of the license is included in the folder.


Paper
-------------------------
This README file accompanies the dataset introduced in the paper: 

The Goldilocks Principle: Reading Children's Books with Explicit Memory Representations
Hill, F. Bordes, A. Chopra, S & Weston, J. 2015 . http://arxiv.org/abs/1511.02301 .



Train / Valid / Test sets
-------------------------

All sets are created from Children's Books freely available via Project Gutenberg. Note that, since texts are freely available on the web, a solution that scans the web with no control over its access to content can probably find the test questions (and is therefore cheating). 

The train/valid/dev split is based on (98/5/5) entire books, so no book contains text in more than one of these sets. The valid and test sets contain 8k and 10k questions respectively subsampled from (larger) sets made of all possible questions from the valid or test books, 2k/2.5/ for each of the 4 word types (see below). 
For the titles of the books used to create each set, see BOOK_SPLIT.txt


Word types NE / CN / V / P
--------------------------

Data is in the included "data" folder. Questions are separated according to whether the missing word is a named entity (NE), common noun (CN), verb (V) or preposition (P). The POS/NER was done by Stanford CoreNLP and nothing else. Thus the dataset consists of the following files:


cbtest_NE_train.txt : 67128 questions
cbtest_NE_valid_2000ex.txt : 2000
cbtest_NE_test_2500ex.txt : 2500

cbtest_CN_train.txt : 121176 questions
cbtest_CN_valid_2000ex.txt : 2000
cbtest_CN_test_2500ex.txt : 2500

cbtest_V_train.txt : 109111 questions
cbtest_V_valid_2000ex.txt : 2000
cbtest_V_test_2500ex.txt : 2500

cbtest_P_train.txt : 67128 questions
cbtest_P_valid_2000ex.txt : 2000
cbtest_P_test_2500ex.txt : 2500

These files, the text is in the format of CBT questions (see below). We also release the raw text from test / valid / train sets, again tokenised by Stanford Core NLP. These files have the form cbt_{train, valid, test}.txt

Detailed stats of all question types are given in the "stats" folder.


CBT questions
--------------

Questions are built from sets of 21 consecutive sentences from the books. A sentence is defined by the Stanford Core NLP sentence splitter. 

A Named Entity (NE) is any entity identified by the Stanford Core NLP NER system. A Common Noun (CN) is any word tagged as a noun by the Stanford Core NLP POS tagger that is not already a NE. Verbs and Prepositions are identified similarly. 

An attempt is made to build a question out of every set of 21 consecutive sentences in each book. More than one question can be built from any set of 21 consecutive sentences. To build a question there must be an instance of one of the four word types in the 21st sentence (which becomes the 'missing word'). There must also be suitable candidates in sentences 1-20. This is the case if there are at least 9 candidates of the same word type as the missing word. If this condition is not met, a question can still be built if there are sufficient instances of another word type in sentences 1-20. For NE questions, we preferably sample complementary candidates from CN. For all other cases, we use any type of candidate available.


Questions about the dataset
---------------------------

If your questions are not answered by reading the paper about the dataset, email Felix Hill, felix.hill@cl.cam.ac.uk or Antoine Bordes, abordes@fb.com .





