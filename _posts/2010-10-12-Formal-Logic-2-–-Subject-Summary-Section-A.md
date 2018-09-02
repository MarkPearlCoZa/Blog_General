---
layout: post
title: Formal Logic 2 – Subject Summary Section A
tags: 
category: General
---
Outcomes of the Section
(Atomic Sentences)

Understand the concept of formal first-order languages
Know the syntax of FOL: predicate symbols, individual constants, function symbols.
Get acquainted with examples of first-order languages: the blocks language, the language of arithmetic
(Logic of Atomic Sentences)

Understand logical validity of arguments
Know how to show that arguments are valid
Understand the basic properties of the identity predicate: reflexivity, principle of the substitutability of identical’s
Understand the basic properties of other predicate symbols (transitivity, reflexivity, symmetry, inverse relations)
Able to construct informal proofs
Able to use Fitch and construct formal proofs
Know how to show that arguments are not valid: the method of counterexamples
(Boolean Connectives)

Understand the syntax, semantics and truth table of Boolean connectives
Know the formation rules for sentences of FOL using ¬, ^, ?
Be able to translate sentences from English into FOL using Boolean connectives
Understand the expressive power of the Boolean connectives: “ Neither…nor” and “not both … and”
Be able to express complicated statements using the blocks language and the Boolean connectives
(Logic of Boolean Connectives)

Understand the logical truth, tautologies, and TW-necessities
Understand the tautological equivalence, consequence, and validity
Able to apply the method of truth tables
Understand and able to show tautological equivalences: De Morgan’s Law and other equivalent transformations
Able to transform formula to negation, conjunctive and disjunctive normal forms.
(Methods of Proof for Boolean Logic)

Able to show that arguments are valid by informal proofs
Understand the basic properties of ^ and ?
Understand the construction of formal rules for ^ and ?
Able to use proof by cases and proof by contradiction in informal proofs
Understand the concept of inconsistent premises
(Formal Proofs and Boolean Logic)

Have mastered the basic properties of the “not” symbol
Understand indirect proof and formal proofs with ¬
Understand and able to construct formal proofs involving introduction and elimination of ^, ?, ¬  and therefore
Understand and able to use subproofs correctly
(Conditionals)

Understand the construction of truth tables for ? and ?
Able to translate from English to FOL using the conditionals
Understand conversational implicature
Know and able to apply rules fro formal proofs involving ? and ?
Understand the definition and proof of truth-functional completeness for ^, ? and ¬
(The Logic of Conditionals)

Be able to use the informal methods of proof discussed
Be able to use formal rules of proof for ? and ?
Understand valid arguments
Atomic Sentences
For a brief summary of First-order logic read the wiki.

Take the claim…

 

image

 

Atomic sentences correspond to the simplest declarative sentences of English, and often consist of names and predicates. If I were to translate the atomic sentence “Claire gave Scruffy” to FOL translation it could look like Gave(Claire, Scruffy)

The order of names in an atomic sentence is important. Gave(Claire, Scruffy) is different from Gave(Scruffy, Claire).

A Claim is something that is either True or False.

FOL consists of predicate symbols, individual constants & function symbols.

Perspective

With Tarski’s World, it is interesting that some claims will be constant (i.e. regardless of the perspective they will either always be true or always be false), while other claims validity can vary depending of the perspective of the world (i.e. Left(A,B) is relative to which way the world is being viewed).

2010-10-05 06-06-48 AM

Compare the above picture of tarski’s world with the one below, the only thing that has changed is that the perspective of the world has changed. Yet by changing the perspective, some of the sentences validity has changed from true to false.

2010-10-05 06-06-30 AM 

The Logic of Atomic Sentences
An argument is a group of propositions or a set of statements of which one (the conclusion) is meant to follow from the others (premises).

Validity
An argument is logically valid if and only if it takes a form that makes it impossible for the premises to be true and the conclusion to be false. Validity requires that there be no possible circumstance in which the premises would be true and the conclusion false.

An example of a valid argument would be the following…

All people studying COS261 are students
Mark is studying COS261
Therefore Mark is a student –>
Soundness
A deductive argument is sound if and only if it is both valid, and all of its premises are actually true.

If we took the above example, and Mark was actually not studying COS261, then while the argument might be valid, it would not be sound.

Methods of Proof
Informal Proof – expresses in English the same argument that a formal proof would express in a language of logic (may leave out some obvious steps)

Formal Proof – expresses an argument in a language of logic.

There are a few proof rules one needs to know that can be applied to atomic sentences, including…


Remember

There are four important principles that hold of the identity relation

= Elim: if b – c, then whatever holds of b holds of c. This is also known as the indescernibility of identicals
= Intro: Sentences of the form b = b are always true (in FOL). This is also known as the reflexivity of identity
Symmetry of Identity: If b = c, then c = b
Transitivity of Identity: If a = b and b = c, then a = c
 

Formal Proofs
There are two rules in the system f corresponding to each connective and to each quantifier…

Introduction Rule
Elimination Rule
The Fitch bar indicates the division between the claims that are assumed and those that allegedly follow from them…

In a formal proof in f, the premises are written above the horizontal Fitch bar, and the subsequent steps (intermediate and ultimate conclusion) are written below the Fitch bar. (See Wiki Fitch for more info)

Each step in a formal proof must be entered in accordance with some precisely stated rule of the formal system of rules. By applying a rule to some previous line or lines in a proof, we provide justification for entering a new step in a proof.

Identity Rules

a) Identity Introduction (= Intro) – this rule says that you may enter a sentence of the form n = n at any point you wish.

b) Identity Elimination (= Elim) – this rule tells you that you can substitute m for n wherever you like, provided that you have the sentence n = m.

c) Reiteration (Reit) – this rule tells us that at any point in a proof, you may enter any sentence that occurs on some previous accesible line.

Constructing Proofs in Fitch

Section 2.4 runs through the basic construction of a proof in Fitch (see diagram below).

image

Demonstrating Nonconsequence
The proof of nonconsequence means that a conclusion does not follow from the premises (i.e. the argument is invalid).

In a nonconsequence proof a counter example needs to be shown.

The Boolean Connectives
This section covers three connectives ¬, ^, ?

¬ - Negation Symbol
^ - Conjunction Symbol
? - Disjunction Symbol
The symbol of logical equivalence (<=> ) is not part of FOL. When you write p <=> Q , you are talking about a language of first order logic.

The Logic of Boolean Connectives
This section discusses what truth tables can tell us about three related logical notions, which are…

Logical Consequence
Logical Equivalence
Logical Truth
Tautologies and logical truth
Logical Truth or Necessity – A sentence that is a logical consequence of any set of premises. That is, no matter what the premises may be, it is impossible for the conclusion to be false (e.g. a = a)

Logical Possibility – A sentence or claim is logically possible if there is a possible circumstance in which it is true.

Logical and Tautological Equivalence
Logical Equivalence – two sentences are logically equivalent if they have the same truth values in all possible circumstances

Tautological Equivalence – S & S’ are tautologically equivalent if and only if every row of the joint truth table assigns the same values to S and S’

Logical and Tautological Consequence
Logical Consequence – A sentence S is a logical consequence of a set of premises if it is impossible for the premises all to be true while the conclusion is false

Tautological Consequence – Q is a tautological consequence of a set of premises P1…Pn, if and only if every row in a truth table that assigns T to P1..Pn also assigns T to Q.

Methods of Proof for Boolean Logic
There are three methods that you can use in informal proofs…

Conjunction elimination – From P ^ Q, infer P (or infer Q)
Conjunction introduction – From P and Q, infer P ^ Q
Disjunction introduction – From P, infer P ? Q (or infer Q ? P)
Proof by Cases

If you know that a disjunction is true and if you know that some sentence P follows from each of the disjuncts, then you may conclude P

Indirect Proof (Proof by Contradiction)

If we manage to prove a contradiction from some premise, then the premise itself must be false.

Arguments with inconsistent premises

If a set of premises is inconsistent, any argument having those premises is valid. The reason is that, if the premises are inconsistent, there is no possible circumstance in which they are all true. So no matter what the conclusion is, there is no possible circumstance in which the premises are all true and the conclusion is false.

But no such argument is sound, since a sound argument is not only valid, but has true premises. We know that if you can derive a contradiction from a set of premises, the set is inconsistent. We may not know at the start that our premise are inconsistent, but if we derive from them, we have established that they are inconsistent. If a set of premise, or assumptions, is inconsistent, it is important to know this.

Formal Proofs and Boolean Logic
The deductive system, f known as a system of natural deduction uses introduction and elimination rules.

If the conclusion (i.e. the last line) of Fitch style proof has only one bar on its left side as it should, then it depends only on the premises of the whole argument and not on the various additional assumptions that might appear at the beginnings of other vertical bars.

Conjunction Elimination – Removes a conjunct from a previous line containing a conjunction.
Conjunction Introduction – Introduces a new conjunction on any line of a proof by citing each of the conjuncts from prior lines. These conjuncts must be alone on the line cited. This rule allows one to conjunct any number of previously established statements in order.
Disjunction Introduction – The rule allows one to construct any disjunction using previous results as one of its disjuncts.
Disjunction Elimination – This is the formal rule that corresponds to the method of proof by cases. It incorporates the formal device of a subproof. A subproof involves the temporary use of an additional assumption, which functions in a subproof. A subproof involves the temporary use of an additional assumption, which functions in a subproof the way the premises do in the main proof under which it is subsumed.
Negation Elimination – It means that if you have double negation of a sentence, then you are entitled to claim the sentence.
Negation Introduction – Assume the opposite of what you want to proove. Derive a contradiction as the last line of the subproof. Then claim the denial of the sentence you assumed when you started the subproof.
Elimination – It means that if you have managed to derive the contradiction, then you are entitled to insert any arbitrary sentence.
Strategy and Tactics of Proofs

Understand what sentences are saying
Decide whether you think the conclusion follows from the premises
If you think it does not follow, or are not sure, try find a counterexample
If you think it does follow, try to give an informal proof
If a formal proof is called for, use the informal proof to guide you in finding one
In giving consequence proofs, both formal and informal, don’t forget the tactic of working backwards
In working backwards always check that your intermediate goals are consequences of the available information
Conditionals
This section introduces conditionals and biconditionals ? and ?

? = ¬P ? Q

? = (¬P ? Q)^(¬Q ? P)

The Logic of Conditionals
There are a number of questions that need to be done on this section, refer to the textbook.

Conditional Elimination – Means that if you have both a conditional P –> Q, and its antecedant, P, then you are entitled to claim its consequence, Q. (Called Modus Ponens)

Biconditional Elimination – Means if you have both a biconditional and one of its two sides, then you are entitled to claim the other of the two sides.

Biconditional Introduction – Means if you have two of the right sorts of sub proofs (i.e. one starting with the left side of the biconditional and ending with its right side and the other starting with its right side and ending with the left side, then you are entitled to claim a biconditional

See page 206 and 209 of Textbook for Diagrams