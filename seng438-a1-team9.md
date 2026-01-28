>   **SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report \#1 – Introduction to Testing and Defect Tracking**

| Group: 9      |
|-----------------|
| Amielle El Makhzoumi           |   
| Fatma Alzubaidi              |   
| Josral Frederick               |   
| Faris Janjua                |   
| Erioluwa Olubadejo                |  


**Table of Contents**

(When you finish writing, update the following list using right click, then
“Update Field”)

[1 Introduction	1](#_Toc439194677)
In this lab, the objective was to build experience with software testing and defect tracking using an ATM application simulator. Prior to this lab, our understanding of testing was primarily centered around manual functional testing, where we follow a set standard of predefined test cases and verify that the actual behaviour matches the expected behaviour. As a result, our hands on experience with exploratory testing, in terms of designing test ideas in real time and using requirements to intentionally test edge cases, was limited.

Through this lab assignment, we as a group practiced three testing approaches. Exploratory testing to discover defects through guided experiments, manual scripted testing using the Appendix C test suite to systematically verify expected behaviour, and regression testing by rerunning previously reported issues through version 1.1 to determine which defects were resolved and which were still present. We also gained experience documenting these bugs using Jira, focusing on reproducibility, expected vs. actual outcomes, and version tracking.


[2 High-level description of the exploratory testing plan	1](#_Toc439194678)
Our exploratory testing was guided by the high level requirements in Appendix B. We focused on validating core requirements:
- Withdrawals are dispensed in multiples of 20.
- Invalid PIN handling, including reentry and card retention after failing three times.
- Cancel should abort a transaction at many stages and return the user to a safe state.
- Deposits must require envelope insertion and should not be credited if the envelope step is skipped.
- The ATM must not shut down during an active session.
- A receipt must print after a transaction.
- Logs should record activity without including PIN values.

During exploration, we also checked common input validation such as an unusually long PIN input or an unrealistic cash amount, to ensure the system fails rather than freezing or crashing.

Our approach consisted of a broad coverage strategy. We tested major features such as authentication, withdrawal, deposit, transfer, inquiry, cancel behaviour, and system start/stop, rather than exhaustively testing one feature, using both of the following:
- Normal user flows: valid login, transaction, receipt, end session.
- Exceptional and boundary cases: invalid inputs, extreme values, invalid accounts, insufficient funds, and canceling during a transaction.

We generated test cases by combining:
- Good path scenarios to confirm baseline functionality.
- Edge cases that usually reveal defects: very large inputs, unusual PIN lengths, invalid cards, and verifying money movement accuracy.

The major exploratory scenarios we executed were as follows:
1. Invalid card input: non numerical values were rejected appropriately, and many random numbers were handled; however, some cases led to unstable states.
2. Invalid PIN entries: standard incorrect PIN attempts behaved as expected when completed in normal ranges.
3. Withdrawal amount coherence with selected option: some withdrawal processes worked; however, we also observed cases where the selected amount did not match the amount that was dispensed.
4. Withdrawal deduction accuracy: we observed inconsistent behaviour where the balance changed correctly, but the dispensed/selected amounts did not correlate as expected.
5. Withdrawing from an unavailable account: for example, Money Market on card 1 and Savings on card 2. The system behaved correctly and prevented invalid account usage.
6. Withdrawing an amount larger than the account’s balance: the system displayed an appropriate message and prevented the withdrawal, working as expected.
7. Deposit accuracy in updating balance: we observed incorrect balance math, where deposits appeared to update inconsistently and could be off by $10 compared to the amount entered.
8. An unrealistic deposit amount: entering an extreme deposit amount caused a frozen blank screen, making the system unstable.
9. Transfer accuracy between accounts: transfers showed incorrect accounting. The amount was $0.50 less than the value entered.
10. Transfer from an unavailable account to an available one: the system prevented invalid account usage and behaved as expected.



We came across several bugs during exploratory testing for version 1.0:
1. The system accepts an unreasonably long PIN input (22 digits), which raises concerns about the application’s security and validation.
2. Using a random card number with a very long PIN can lead to a blank green screen, and the program freezes.
3. Withdrawal amount mismatch: selecting $20 can result in $40 being dispensed.
4. Deposit amount mismatch: entering $20 may only increase the user’s balance by $10.
5. Entering a very large deposit number freezes the system.
6. Transfer mismatch: transferring $20 from Checking to Savings results in $19.50 being transferred.


After repeating the important checks on version 1.1, we observed some fixes and some remaining issues. Some of the discoveries we made were as follows:
- Transferring accuracy appeared fixed in version 1.1.
-Unstable PIN behaviour still appeared unfixed.
- An unrealistic deposit amount still appeared to not be fixed.
- The logic error with deposits persisted in version 1.1.



[3 Comparison of exploratory and manual functional testing	1](#_Toc439194679)
Both exploratory testing and manual scripted testing helped us evaluate the ATM simulation, but they differed in how test cases were produced, the predictability of a process, and the kinds of defects each method revealed.

In exploratory testing, we created and executed tests dynamically based on the requirements listed in the Appendix, as well as our observations of the system. This allowed us to quickly branch into fresh scenarios when an unexpected event occurred, such as unrealistic deposit amounts after noticing input validation weaknesses.

In manual functional testing, we followed a predefined test case set listed in Appendix C, each with clear starting states, inputs, and the results our system expects. This made the execution more systematic to repeat on a consistent basis.

Exploratory testing was effective at revealing defects related to input validation and edge cases, such as:

- System freezing after an unrealistic deposit amount
- Unstable behaviour after unusual authentication inputs, like a random card or very long PIN
- Incorrect money movement, such as incorrect transfer/withdraw/deposit amounts

Manual functional testing, we found, was effective at validating expected behaviours for the standard use cases, and it also revealed failures that are tied directly to specified requirements. We noticed this in test case #6, where rejecting an unreadable card failed when a non-existent card was still accepted and prompted for a PIN, which contradicts the expected behaviour of our system to immediately reject.

Manual scripted testing was more efficient for verifying baseline correctness across multiple features because the steps were already set, and expected outputs are absolute. Alongside, it also improved repeatability because two testers can run the same test and reach the same conclusion about a pass or a fail. Exploratory testing required more judgement and more note taking. This is due to test cases not being predetermined. However, it was efficient for uncovering higher-impact defects that wouldn’t necessarily be covered by the scripted suite.

When considering coverage and limitations, exploratory testing provided stronger coverage of unknown unknowns, however, it can be inconsistent between testers unless the steps are carefully documented upon discovery. Manual functional testing provided dependable coverage for the encoded Appendix C requirements; however, it is limited to what the script contains. For instance, the scripted test suite doesn’t deeply advocate extremely large numeric inputs; exploratory testing revealed there to be bugs in those areas.

As seen, some bugs were experienced in both approaches. For example, transaction accuracy issues that arose during exploration were also reflected in scripted outcomes. This overlap provided aid in confirming that certain bugs were not solo edge cases, but could also appear during more structured testing.

Overall, exploratory testing was more valuable for the discovery of unexpected failures and issues in validation, whereas manual functional testing was strongest for consistent requirement verification and repeatable pass or fail reporting.


[4 Notes and discussion of the peer reviews of defect reports	1](#_Toc439194680)

[5 How the pair testing was managed and team work/effort was
divided	1](#_Toc439194681)

[6 Difficulties encountered, challenges overcome, and lessons
learned	1](#_Toc439194682)

[7 Comments/feedback on the lab and lab document itself	1](#_Toc439194683)

# Introduction

In this lab, the primary focus is to get an idea of what software testing is. Software testing is a critical practice used in software development, as it helps to ensure that systems behave as expected and meet their requirements. Before this lab, our understanding of testing was mainly focused on the idea of verifying correctness through pre defined test cases. However, this lab provided a hands-on experience with multiple testing styles. This includes exploratory testing, manual scripted testing and regression testing by using a simulated ATM system.

# High-level description of the exploratory testing plan card 1

Requirements based on Appendix B: (this is version 1.0)
- Withdrawals must be in multiples of $20 - will not allow decimals, must be and integer
- Cancel should work at many stages - works
- 3 wrong PINs → card retained - will display "card has been retained" and reprompt to insert card
- Deposit requires envelope insertion - It works.
- Deposit is not credited if envelope isn’t inserted - It works.
- ATM must not shut down during a customer session - it has not shut down so far.
- Receipt must be printed for successful transactions - Yes, it does that.
- ATM logs actions (no PINs in logs) - No pins in logs
- 4 number PIN - actually allows 22 numbers - DEFECT
- No letters in card number - working
- Entering PIN - Will display a blank green page when using random card number, and a long PIN. blank screen, cant go back, cant clear - DEFECT

1. Inserting a false card (entering non-numerical values or random numbers) - Both work
2. Entering an random/incorrect PINs - Theres no defect when done right..
3. Checking to see if the chosen withdraw amount the same as the actual amount - IT works
4. Checking to see if the chosen withdraw amount is the amount deducted from the account - DEFECT - It takes back the correct amount from the balance, but the numbers don't correlate with the ones that are put in.
5. Trying to withdraw money from a unavailable account (Money Market for Card 1 and Savings for Card 2)  - It works
6. Trying to withdraw more money than you have in the account - it works
7. Checking to see if the chosen deposit amount is accurately reflected in the balance -DEFECT -  it only deposits into the total balance but not the available, also the math is wrong, its always $10 less than what you put.
8. Checking to see what happens if an unrealistic deposit amount is entered -DEFECT -  Blank screen appears and the whole system crashes. 
9. Checking to see if the amount transferred from one account to another is accurate - DEFECT -  it's not accurate, it always takes $.50 less than what you put in.
10. Checking to see if you could transfer money from an unavailable account to an available account - it works 

High-level plan:
Based on the requirements outlined in Appendix B, our exploratory testing focused on verifying core ATM functionalities such as authentication, withdrawals, deposits, transfers, balance inquiries, and system control operations. We aimed to broadly test most system features rather than exhaustively testing a single function. Test scenarios were derived from both normal user flows (e.g., valid login followed by a withdrawal or deposit) and exceptional cases (e.g., invalid PIN entries, insufficient account balance, canceling transactions at various stages, and attempting invalid withdrawal amounts). Boundary conditions such as withdrawing the maximum available cash, performing multiple transactions in one session, and system shutdown behavior were also explored. Testing was conducted without predefined scripts to allow unexpected behaviors and defects to be discovered naturally.

version 1.1: 
1. ATM should reject insufficient funds - defect solved
2. 4 number PIN - DEFECT in progress
3. Entering PIN - Will display a blank green page when using random card number, and a long PIN. blank screen, cant go back, cant clear - DEFECT IN PROGRESS
4.Checking to see if the chosen withdraw amount is the amount deducted from the account- DEFECT RESOLVED
5.Checking to see if the chosen deposit amount is accurately reflected in the balance  - DEFECT IN PROGRSS (.10 less in savings and checking)
6.Checking to see what happens if a unrealistic deposit amount is entered - DEFECT IN PROGRESS
7.Checking to see if the amount transferred from one account to another is accurate - SOLVED

# card 2
version 1.0:

version 1.1: 
- it works
- 3 wrong PINs → card retained - will display "card has been retained" and reprompt to insert card
- Deposit requires envelope insertion - It works.
- Deposit is not credited if envelope isn’t inserted - It works.
- ATM must not shut down during a customer session - it has not shut down so far.
- Receipt must be printed for successful transactions - Yes, it does that.
- 4 number PIN - system crashes if it's too much numbers
- No letters in card number - DEFECT allows letters
- Entering PIN - Will display a blank green page when using random card number, and a long PIN. blank screen, cant go back, cant clear - DEFECT
 









# Comparison of exploratory and manual functional testing
Manual functional test case #: (this is version 1.0)
1. it works
2. it works
3. it works
4. it works
5. it works
6. DEFECT, because tested card 80 is asking for PIN, and not ejecting card right away. (100 is accepted 7987498729 is not.)
7. it works
8. it works (some transaction are not correct but it still does the transaction)
9. it works
10. it works
11. it works (says PIN is incorrect)
12. it works
13. it works 
14. DEFECT (repeated from earlier where you enter $20 and its $40)
15. it works
16. 
17. it works
18. it works
19.it works
20. it works
21. it works 
22. it works
23. it works 
24. it works 
25. it works 
26. it works
27. it works
28. it works
29. DEFECT (same as earlier, it adds .38 to original amount but everything else is good)
30.it works
31. it works
32. it works
33. it works
34. it works 
35. it works
36. it works
37. MNI DEFECT (prompts user twice, ask if it counts as defect)
38. it works 
39. MINI DEFECT (promt twice)
40. MINI DEFECT (same as 39)

# Manual Function: version 1.1
1. it works
2. it works
3. it works
4. it works
5. it works
6. DEFECT (same reason as last, ask in class)
7. it works
8. it works 
9. it works
10. it works
11. it works
12. it works 
13. it works
14. it works 
15. it works
16. 
17. it works
18. it works 
19. it works 
20. it works
21. it works
22. it works
23. it works
24. it works
25. it works
26. it works
27. it works
28. it works
29. it works
30. it works
31. it works
32. it works 
33. it works
34. it works 
35. it works
36. it works 
37. MINI DEFECT (prompts user twice, ask if it counts as defect)
38. it works 
39. MINI DEFECT
40. MINI DEFECT

-   Note that you need to submit a report generated by your defect tracking
    system, containing all defects recorded in the system.

# card 2

version 1.0: 

version 1.1: 
 1. it works 
 2. it works 
 3. it works
 4. it works 
 5.it works 
 6. it works
 7.DEFECT, I put the wrong pin first, then i put the right one and it only worked after 2 tries.
 8. it works
 9.it works
 10. it works
 11. mini defect
 12.it works
 13.it works
 14. it works
 15.it works 
 16. it works 
 17.it works 
 18.it works
 19.it works
 20.Defect, it says to enter valid account
 21.defect
 22.defect
 23.it works
 24.it works
 25.it works
 25.it works
 26.it works
 27.it works
 28.defect, it says invalid account type
 29.defect
 30.it works
 31.it works
 32.it works
 33.it works
 34.it works
 35. it works
 36.mini defect, works after second try
 37.mini defect
 38.mini defect
 39. is accepted
 40.works

 


# Notes and discussion of the peer reviews of defect reports

Text…

# How the pair testing was managed and team work/effort was divided 

- Fatma and Amielle were assigned to work on the first pair testing for Appendix B. Fatma was testing the different scenerios that would not work and Amielle would do the recording.

# Difficulties encountered, challenges overcome, and lessons learned
# Comments/feedback on the lab and lab document itself

Text…
