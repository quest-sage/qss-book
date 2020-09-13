---
description: An introduction to the QSS programming language.
---

# Overview

QSS, the Quest Sage scripting language, is a domain-specific programming language \(DSL\) designed to enable dynamic scripting in the Quest Sage virtual tabletop. This manual to QSS assumes some level of familiarity with programming in general.

## Goals

QSS aims to solve several programming challenges for making virtualisations of tabletop games.

### Hooks

While traditional programming languages \(such as C, Java, Go, Rust...\) are good at computing predefined lists of instructions, they do not \(trivially and idiomatically\) support dynamic changes to these instructions. This, however, is one of the core principles behind tabletop game design: the ability to bend the rules in certain scenarios! We will explore an example here to explain our reasoning.

For example, imagine an item which gives the wearer a higher chance to dodge an attack. To implement this, you could look at the code that determines whether an attack hits, and add a check to see if the target is wearing this item. But then, what if there were several types of item? What if they all helped in very slightly different ways? The function quickly becomes bloated, and ends up eventually becoming unreadable. Or what if the function you want to edit is in a place that you _can't_ edit, such as in a public package?

QSS solves these problems using a principle called 'hooks', which allow you to modify pre-existing functions. We will cover them in detail in a part of this manual. This is \(probably\) the most notable feature of the programming language, since we based its core design around this concept.

### Appends

Hooks allow you to modify a function, and 'appends' allow you to modify data structures. They offer the ability to add extra data to a structure. For example, if you're making an ultra-realistic ruthless game and each character needs to keep track of their core body temperature or oxygen levels, you could 'append' this information to characters.

### Implicit Asynchronicity

QSS functions don't have to execute all at once: for example, they can wait for the user to input something, or sleep until another function wakes it up.

### Type Safety

One of the consequences of having such dynamic code that can be changed with hooks is that there is an increased need to know exactly what types of variables functions are allowed to input and output. You can't just go to the source code of the function to see, because other people could just hook into the function and return their own data!

QSS therefore has a 'strongly typed' system that makes the language more reminiscent of Java, Rust or Haskell as opposed to something like Python or PHP.

### Internationalisation

QSS has the distinct data types `String` and `Text`. The `String` data type is more like what you are probably familiar with, and the `Text` data type focuses heavily on dynamic translations. This is all handled "under-the-hood", allowing programmers to focus on actually programming rather than future-proofing for language support.

## Anti-Goals

There are a number of things that QSS does not intend to offer.

### Runtime Speed

QSS prioritises ergonomics and the aforementioned features over runtime speed. This is not to say that QSS is a slow language, but this is not the main focus of the language.

### Compile Time Structures

Macros and compile time optimisation are largely absent from QSS, as these features are more geared towards systems programming than something like Quest Sage. They would just add to the language's bloat and increase the steepness of the learning curve.

