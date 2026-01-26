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

[2 High-level description of the exploratory testing plan	1](#_Toc439194678)

[3 Comparison of exploratory and manual functional testing	1](#_Toc439194679)

[4 Notes and discussion of the peer reviews of defect reports	1](#_Toc439194680)

[5 How the pair testing was managed and team work/effort was
divided	1](#_Toc439194681)

[6 Difficulties encountered, challenges overcome, and lessons
learned	1](#_Toc439194682)

[7 Comments/feedback on the lab and lab document itself	1](#_Toc439194683)

# Introduction

In this lab, the primary focus is to get an idea of what software testing is. Software testing is a critical practice used in software development, as it helps to ensure that systems behave as expected and meet their requirements. Before this lab, our understanding of testing was mainly focused on the idea of verifying correctness through pre defined test cases. However, this lab provided a hands-on experience with multiple testing styles. This includes exploratory testing, manual scripted testing and regression testing by using a simulated ATM system.

# High-level description of the exploratory testing plan

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

# regretion testing

 


# Notes and discussion of the peer reviews of defect reports

Text…

# How the pair testing was managed and team work/effort was divided 

- Fatma and Amielle were assigned to work on the first pair testing for Appendix B. Fatma was testing the different scenerios that would not work and Amielle would do the recording.

# Difficulties encountered, challenges overcome, and lessons learned

Text…

# Comments/feedback on the lab and lab document itself

Text…
