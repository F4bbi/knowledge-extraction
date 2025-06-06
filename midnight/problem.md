# The Midnight Mystery: A Data Mining Murder Investigation

## Background

It's a dark and stormy night at the Grand Hotel. Many distinguished guests have gathered for an exclusive gala. At precisely 11:50 PM, a scream pierces the night - one guest has been murdered!

The legendary detective Sherlock Holmes and his assistant Dr. Watson arrive at the scene. They conduct thorough interviews with all surviving guests. Each guest provides information about their whereabouts at the time of the murder and whom they remember seeing.

A crucial piece of evidence is found: a handwritten note clutched in the victim's hand, apparently torn from the murderer during the struggle. The note appears to be written in a distinctive style.

Your task is to help Holmes and Watson identify the most likely suspects.

## Dataset Description

You are provided with `murder_mystery.json` containing:

-   **Metadata**: Case details including victim name, murder time, and the mysterious note
-   **Interrogations**: Interview reports, each containing:
    -   Guest name
    -   Their statement about location and sightings
    -   Interview timestamp

## Your Mission

You must analyze the evidence to identify the prime suspects. Your investigation should follow these steps:

Combine your findings from all analyses to:

1. Identify the most likely murderer
2. Provide evidence supporting your conclusion
3. Explain any alternative suspects and why they were ruled out

**Deliverable**: A final report presenting your conclusion with supporting evidence, and the code.

## Technical Requirements

-   You can use any Python libraries you like, such as: `networkx`, `python-louvain`, `sentence-transformers`, `openai/anthropic` (via OpenRouter)
-   Your code should be well-documented and reproducible
-   Handle API rate limits appropriately

## Evaluation Criteria

-   **Code Quality**: Clean, documented, efficient code
-   **Analysis Depth**: Thoroughness of investigation and use of multiple techniques
-   **Conclusions**: Logical reasoning and evidence-based conclusions

## Hints

-   People may be mistaken as to who they saw. This is less likely so, if, for example, they were playing cards with a guest, rather than just briefly seeing them pass by.
-   Some guests might naturally be more isolated due to their behavior
-   Writing styles can reveal more than just dialect - look for patterns

## Submission

Submit a Jupyter notebook containing:

1. All code with explanations
2. Your final report as a markdown cell

USE ONLY THE API KEY PROVIDED VIA EMAIL

Good luck, detective! The truth is hidden in the data...
