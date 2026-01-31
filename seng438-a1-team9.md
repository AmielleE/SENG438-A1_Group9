# SENG 438 - Software Testing, Reliability, and Quality
## Lab Report \#1 – Introduction to Testing and Defect Tracking

| Group: 9      |
|-----------------|
| Amielle El Makhzoumi           |   
| Fatma Alzubaidi              |   
| Josral Frederick               |   
| Faris Janjua                |   
| Erioluwa Olubadejo                |  


# Table of Contents

- [Introduction](#introduction)
- [High-level description of the exploratory testing plan](#high-level-description-of-the-exploratory-testing-plan)
- [Comparison of exploratory and manual functional testing](#comparison-of-exploratory-and-manual-functional-testing)
- [Notes and discussion of the peer reviews of defect reports](#notes-and-discussion-of-the-peer-reviews-of-defect-reports)
- [How the pair testing was managed and team work/effort was divided](#how-the-pair-testing-was-managed-and-team-work-effort-was-divided)
- [Difficulties encountered, challenges overcome, and lessons learned](#difficulties-encountered-challenges-overcome-and-lessons-learned)
- [Comments/feedback on the lab and lab document itself](#commentsfeedback-on-the-lab-and-lab-document-itself)

# Introduction

In this lab, the objective was to build experience with software testing and defect tracking using an ATM application simulator. Prior to this lab, our understanding of testing was primarily centered around manual functional testing, where we follow a set standard of predefined test cases and verify that the actual behaviour matches the expected behaviour. As a result, our hands on experience with exploratory testing, in terms of designing test ideas in real time and using requirements to intentionally test edge cases, was limited.

Through this lab assignment, we as a group practiced three testing approaches. Exploratory testing to discover defects through guided experiments, manual scripted testing using the Appendix C test suite to systematically verify expected behaviour, and regression testing by rerunning previously reported issues through version 1.1 to determine which defects were resolved and which were still present. We also gained experience documenting these bugs using Jira, focusing on reproducibility, expected vs. actual outcomes, and version tracking.

# High-level description of the exploratory testing plan

Based on the requirements outlined in Appendix B, our exploratory testing focused on verifying core ATM functionalities such as authentication, withdrawals, deposits, transfers, balance inquiries, and system control operations. We aimed to broadly test most system features rather than overly testing a single function. Our test scenarios were derived from both normal user flows, like valid login followed by a withdrawal or deposit, and exceptional cases, such as invalid PIN entries, insufficient account balance, canceling transactions at various stages, and attempting invalid withdrawal amounts. Boundary conditions such as withdrawing the maximum available cash, performing multiple transactions in one session, and system shutdown behavior were also explored. Testing was conducted randomly to allow unexpected behaviors and defects to be discovered naturally.

In summary, our approach focused on maximizing coverage of both standard and exceptional scenarios, ensuring that the ATM system behaves correctly under typical use while also handling edge cases robustly. This approach also provided valuable input for regression testing and defect tracking in Jira

# Comparison of exploratory and manual functional testing
Both exploratory testing and manual scripted testing helped us evaluate the ATM simulation, but they differed in how test cases were produced, the predictability of a process, and the kinds of defects each method revealed.
In exploratory testing, we created and ran tests on the spot, using the requirements in Appendix B and our observations to guide us. This meant we could quickly try new scenarios when something unexpected happened, like a very large deposit amount or an unusual PIN entry. Exploratory testing was especially useful for catching issues that weren’t part of the standard scripts, such as:

- System freezing or crashing when unrealistic deposit amounts were entered
- Instability when using very long PINs or random card numbers
- Incorrect money movement during withdrawals, deposits, or transfers

In manual functional testing, we followed the test cases in Appendix C step by step. Everything had clear starting points, inputs, and expected results, which made testing predictable and repeatable. This approach was great for confirming that the ATM behaved correctly under normal conditions, such as:

- Rejecting unreadable or invalid cards
- Handling incorrect PIN entries and retaining the card after three failed attempts
- Generating receipts and updating balances accurately

Some defects, like transaction accuracy issues, appeared in both testing approaches, confirming they were genuine problems rather than isolated edge cases. Exploratory testing excelled at uncovering unexpected issues and edge cases, though it required careful documentation to maintain reproducibility. Manual functional testing, on the other hand, provided consistent verification of the system against specified requirements. Using both methods together gave the most complete picture: exploratory testing revealed new problems, while manual testing ensured baseline functionality was correct.

Overall, exploratory testing helped us discover unexpected failures and validate system robustness, while manual scripted testing confirmed the system met all the expected requirements. Together, they gave us confidence that we thoroughly tested the ATM application.

# Notes and discussion of the peer reviews of defect reports

During the peer review process, our group collectively examined all entries and defect reports in Jira. We noticed that some entries did not enough detail regarding the initial state of the system, the exact inputs required to reproduce the error, or clear descriptions of the observed behaviour. In certain cases, a single defect could have been broken down into multiple issues due to overlapping functionalities or complexity, which highlighted the need for careful organization when reporting bugs.

Through the review, we also observed that some functionalities could still fail under exploratory testing scenarios even though they were passing in the manual function tests. For example, transfer and deposit features sometimes behaved unexpectedly when tested with extreme inputs, which would not have been caught by strictly scripted tests. This reinforced the value of pairing exploratory testing with the structured manual test suite to ensure coverage of both expected and edge-case behaviours.

Additionally, we found that simply trying to "break" the ATM during testing was highly effective for uncovering hidden defects, such as the system freezing after entering unrealistically large deposit amounts. These issues were not immediately apparent in the MFT and demonstrate the importance of simulating realistic misuse scenarios. Overall, while most entries were well-documented and informative, the peer review process helped us refine descriptions, ensure reproducibility, and confirm whether issues persisted in version 1.1. This collaborative review strengthened both the quality of our reports and our understanding of how defects impact system functionality.

# How the pair testing was managed and team work/effort was divided 
Pair 1: Fatma & Amielle
- Fatma executed edge cases and non-standard scenarios.
- Amielle recorded results, including steps, expected outcomes, and actual outcomes.

Pair 2: Josral, Faris & Erioluwa
- Focused on normal user flows, withdrawals, deposits, and transfers.
- Team members rotated between testing and noting bugs in Jira to balance workload.

Regression Testing: Each member re-tested their previous exploratory and MFT scenarios on version 1.1 to identify resolved and remaining defects.

# Difficulties encountered, challenges overcome, and lessons learned

Challenges:
- Working with Jira for the first time.
- Documenting steps clearly enough to reproduce defects consistently.
- Managing overlapping defects across testers to avoid duplicate Jira entries.
- Handling unexpected system freezes during exploratory testing.

Lessons Learned:
- Explicit task assignment improves team efficiency.
- Exploratory testing is very important for finding edge-case defects.
- Maintaining consistent Jira fields ensures accurate regression testing.
- Understanding requirements before testing saves significant effort.

# Comments/feedback on the lab and lab document itself
The lab provided a realistic introduction to software testing and defect tracking using industry-standard tools like Jira. Using both exploratory and manual testing provided a comprehensive view of system behaviour. We all feel that we will be using the knowledge from this lab in other courses and in our future experiences.

The documentation was clear, but clearer instructions for regression testing would further improve efficiency. The markdown format worked well for organizing content but limited more dynamic formatting.