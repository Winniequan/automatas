# PDA
Pushdown Automaton (PDA) Simulator
This program simulates a Pushdown Automaton (PDA) that recognizes the language:
𝐿={𝑎^𝑛𝑏𝑎^2𝑛 ∣ 𝑛≥1}
The PDA accepts strings where:

The string begins with 𝑎^𝑛 (one or more as).
It is followed by exactly one b.
It ends with 𝑎^2𝑛 (twice as many as as in the first segment).

Features
Simulates the PDA using a stack-based approach.
Checks if the input string conforms to the language 𝐿
Provides feedback on whether the string is accepted or rejected.

Prerequisites
anaconda.cloud/jupyterhub
How to Use
Open the pda.ipynb file on anaconda cloud
Run the program using Python:
The program contains test strings (test_strings) for demonstration. Modify the test_strings list to test with  some strings.
Code Structure
The program consists of the following components:

Stack: Used to track the count of a's and ensure the balance between n and 2n.
States:
q0: Processes the initial 𝑎^𝑛 and transitions on the b.
q1: Pushes two as for every a in 𝑎^2𝑛
q2: The accepting state, reached when the stack is empty (except for the marker).

Transition Logic:
Validates the input string against the PDA's rules.
Rejects invalid strings or mismatched patterns.

Example Input and Output
Test Strings:
python
Copy code
test_strings = ["ab", "aabaaa", "aaabaaaaaa", "aaa"]
Sample Output:
plaintext
Copy code
The string 'ab' is accepted by the PDA: True
The string 'aabaaa' is accepted by the PDA: True
The string 'aaabaaaaaa' is accepted by the PDA: True
The string 'aaa' is accepted by the PDA: False

How It Works
Step 1: The PDA processes the first segment 𝑎^𝑛 pushing as onto the stack.
Step 2: It transitions to processing b and pops one a from the stack.
Step 3: In the next segment 𝑎^2n it pushes two as for every a.
Step 4: The PDA pops all as from the stack, ensuring 2𝑛 matches the stack size.
Step 5: The PDA accepts if the stack is empty (only the marker 0 remains).


You can:

Add more test cases to the test_strings list.
Adjust the PDA's logic to handle similar languages.
Limitations
The PDA handles only deterministic input for this specific language.
It does not support additional symbols or generalized patterns outside 𝑎^𝑛𝑏𝑎^2𝑛


