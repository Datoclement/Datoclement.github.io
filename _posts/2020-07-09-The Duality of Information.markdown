---
layout: post
title:  "Duality of Information"
date:   2020-07-09
categories: jekyll update
---
We discussed the copycat problem last time, where we ask subjects to detect transformation rules from a given example. One typical example of such questions is as follows:



If `abc` is transformed into `abd`, what will `ijk` be transformed into?



As is discussed, this is an, say, intrinsically ambiguous question. There are many possible answers. One obvious answer is `ijl` using the most intuitive analogy. However, the rule may as well be *transform the last letter to `d`*, which would yield a different answer `ijd`. There are actually infinite possibilities in this ambiguous question, as the test sample `ijk` is never provided in the *training* set of the problem. The extrapolation can be done with whatever type of priors you give.

However, most human would answer `ijl`. In fact, while in our previous thought, every prior is almost *equally* good, this isn't really the case in reality. The overwhelming temptation to utter the answer `ijl` is an important manifest of the difficulty of modern artificial intelligence study, i.e., the search on the implicit prior that makes human intelligence excel in daily tasks, not only in natural language processing, but also in other domains such as computer vision. 



A popular school of thought, coming with the success of the data-driven approaches, is that the so-called human reasoning is only an illusion. According to this thought, if we substract the human intelligence by what it gets from data, it would remain nothing. There isn't really a *symbolic* reasoning, but an interplay of analogy to the past.

Today's natural language processing research with machine learning approaches, usually data-driven and data-hungry, see a huge success in modeling daily natural language usage. Models such as GPT series, BERT series are generating texts of complex and coherent patterns that we never could have imagine using machines. Their functionality is based on this idea that we use language based on past experience and the current context. A dream seems to be that, as long as we have enough time and data, our goal of modelling human language would be complete.

The dream, however, is doomed to fail. To my knowledge, current word-embedding technique maps words into vectors, where the vector is supposed to be a semantic representation of the word, within or without its context. The subsequent part of the models proceeds without knowing what the literal is. Abandoning this literal form of words seems to harm nothing according to their principle. Indeed, if usage of words is all about comparing to how they are used in the past, then retrieval of the literal form of the words is just a copy-paste, which we should just agree to hard-code into the network.



The loss of information is going to fail the tasks that need exactly these kinds of information, such as the copycat problem mentioned above. This phenomenon is what I pinpoint as the currently most greatest gap of the current models of NLP research to the reasoning of a real human.



#### The Duality of Information

A word is an organic combination of its semantic and its literal. A line of program is both an instruction and data. A gene is both the representation of a piece of encoded biological information and a piece of DNA material (for most of the living creatures). This duality is at the core of Godel's construction of the contradiction *this statement is not provable* in his proof of the incompleteness theorem, and is also that of Turing in how he solved the halting problem.



#### Problem of Encoding this Duality into Models of Data-Driven Paradigm

One obvious suggestion to improve the current models would be just to encode these literal informations into the model. However, if we think one step further, this turns out to be more difficult than it seems. The goal of encoding these informations is to allow the model to do more human-like reasoning instead of simply interpolating its experience. The manifest of such human-like reasoning is to be able to answer, or intuite, some reasonable answers for questions like copycat problem. 

Unfortunately, this extra set of questions has two distinguish characteristics. First, these questions are not intuitable purely by interpolating past experience because they are rare or even nonexistent in the past. Data for these types of questions are rarely seen in daily life. Possibly some of us have never heard of sufficient examples of question like copycat before. Some of us may never have encountered one. The relevant knowledge of the alphabetic ordering is learnt not by hard-coding genes, but by repeating, and then **understanding** the elementary English session we have had during a young age. All we heard may just be *repeat after me: a, b, c...*. The reality is that we learned from this seemingly innocuous experience so much and so deep, that not only do we pick up the appearance of this sequence but understand its implication of the meaning of *ordering*. In fact, if we redefine for now the alphabetic order as *a, e, i, o, u, b, c, d, f,...*, we as human can still see a fast analogy of the similar situation, e.g., if `aei` is transformed to `aeo`, then `hjk` will be transformed into `hjl`. This instant and temporary new alphabetic order would be so rare that, attempting to extract this information from the past experience seems to be hopeless, yet human reasoning is still capable.

If the problem is just the availability of data, there would be a huge bunch of potential hacks from previous machine learning research that could help us. However, there is one more problem, which is that, these problems are intrinsically difficult and the set is so huge and diverse that making a sufficient sampling from this set will basically be impossible. In fact, all reasoning problems, ranging from the most advanced mathematics to daily puzzles, to big philosophical questions should be included into this set. 

*Hold on. You are saying that current AIs fail because they fail to answer questions that human ourselves are still not capable of answering, this seems not fair at all!*

Well, yes, but no. The problem is that we as human *can* answer all these questions. For example, given enough teaching sessions, most of us can follow step by step how to do a multiplication between any two integers in ten-based representation, with, of course, enough time. This, however, is too difficult for current AI to accomplish. 

I need to emphasize that, here, we are not trying to approximate the multiplication function that receives two numbers as inputs and is expected to output the product of these two numbers. No. What we are talking is that we give a lecture to the AI model in text format. What we expect from the model is that after it reads and analyzes this text, it will then be able to answer a question of multiplication. One of the example input is as follows:

`Here we will define a new operation between two integers, namely a multiplication. The result of this operation between, say, integer a and integer b reads a multiplied by b. To do this, first, ... Then, ... The result of the multiplication would then be .... Now answer this question: what is 43 multiplied by 25?`

Of course, if someone who had never done multiplication before for the first time hears such message, he would possibly be uncapable of finishing this. We should not expect the program to response immediately the correct result either. However, what a normal human does is that he then would try to learn this calculation by following the instruction, with some failure and mistake and confusion. He would write back something like

`Let me see. 43 multiplied by 25. So, according to what you said, firstly, we multiply the first digit x and y of these two numbers. To do this single digit multiplication, we add to zero the y value for x times. So, 0+2 is 2, 2+2 is 4, then 6, then 8. And then... But then I am a little bit confused, could you please explain some more about what should follow after this step?`

The conversation would go back and forth like a normal teaching session. 

At the end, the person might not fully grasp the method of multiplication in his mind, even though, as it appears, most of us human actually can. However, what is more important is that this process, unlike some daily conversations, involves an intense usage of new vocabulary and new concepts which would render the statistical based approach impossible. This usage of new concepts requires then a real understanding of the usual language in the semantic domain, which allows for a manipulation of new vocabulary in the literal domain. And more importantly, through this manipulation in the literal domain, the AI model can remap the new concepts into the semantic domain, allowing it to truly understand the concept, instead of just accumulating the statistics of literature corpus.

This, as an example, demonstrates why taking into account the duality is important. 

Existing literature, such as Neural Turing Machine, addresses fast modeling problem with external memory. However, what's not obvious in these models is how they transform the short-term memory into long-term knowledge. 