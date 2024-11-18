
# DFA Implementation for Pattern Matching `aa*bacaa*`

This repository contains a Python implementation of a Deterministic Finite Automaton (DFA) that matches strings following the regular expression `aa*bacaa*`. 

## Overview

A **Deterministic Finite Automaton (DFA)** is a theoretical machine used to recognize patterns in input strings. This implementation simulates a DFA that matches strings conforming to the following pattern:

### Pattern: `aa*bacaa*`

- Starts with one `a`, followed by zero or more `a`s.
- Followed by a single `b`.
- Then a single `a`, followed by a `c`.
- Ends with one `a`, followed by zero or more `a`s.

### DFA State Diagram

The DFA processes input strings and transitions between the following states:

- **`S0`**: Start state, expects the first `a`.
- **`S1`**: Matches the leading `a` and additional `a`s.
- **`S2`**: Matches the `b` after the `a`s.
- **`S3`**: Matches the `a` after the `b`.
- **`S4`**: Matches the `c`.
- **`S5`**: Accepts the final `a` and any subsequent `a`s (accept state).
- **`TRAP`**: Reject state for invalid inputs.

### Transition Rules

- Any invalid input or sequence transitions the DFA to the `TRAP` state.
- The string is **accepted** if the DFA ends in the `S5` state after processing all input characters.

## Features

- Simulates a DFA with six states (`S0` to `S5` and `TRAP`).
- Processes strings character by character.
- Determines whether a given string matches the pattern.

## Usage

Prerequisites
anaconda.cloud/jupyterhub
How to Use
Open the pda.ipynb file on anaconda cloud
Run the program using Python:

### Running the Code

Test the DFA with input strings: Modify the input string in the main section of the script to test specific cases.
Example:
print(dfa.is_accepted("aabacaa"))  # Expected output: True
Example Input and Output
Input String	Accepted?	Explanation

aabacaa	 True Matches the pattern
aaabacaaa	True Matches the pattern
aabaca	False	Missing the final c and a part
baca	False	Does not start with a
aaacaa	False No	Missing b and c
aabac	False No	Missing final a
DFA Implementation
The DFA is implemented as a Python class with the following methods:

transition(input_char): Defines the transitions between states based on the current state and input character.
is_accepted(input_string): Processes an input string and determines if it matches the pattern.
Code Example
Here is an example usage of the DFA class:

dfa = DFA()
print(dfa.is_accepted("aabacaa"))  # Output: True
print(dfa.is_accepted("baca"))     # Output: False

How It Works
The DFA starts in the S0 state.
Each input character triggers a transition based on the current state.
If an invalid character or sequence is encountered, the DFA transitions to the TRAP state.
The string is accepted only if the DFA ends in the S5 state.
Customization
To modify the DFA for a different pattern:

Update the transition method to define new states and transitions.
Add or update test cases in the main section.



### NFA
# NFA Implementation for Regular Expression `aa*b(ca* + acaa*)`

This repository contains a Python implementation of a Non-deterministic Finite Automaton (NFA) designed to process input strings and verify whether they conform to the regular expression:

aab(ca + acaa*)

## Regular Expression Breakdown

1. **`aa*`**: The string starts with at least two `a`s, followed by zero or more `a`s.
2. **`b`**: A single `b` is required after the `aa*`.
3. **`ca*`**: Followed by a `c` and zero or more `a`s.
4. **`+`**: OR
5. **`acaa*`**: An `a`, followed by `c`, then one or more `a`s.

## Features

- Implements an NFA to evaluate strings against the specified regular expression.
- Allows non-deterministic transitions where a single input can lead to multiple possible states.
- Includes functionality to check if a string is accepted by the NFA.

### States

1. **`S0`**: Start state.
2. **`S1`**: Handles the `aa*` portion (at least two `a`s).
3. **`S2`**: Accepts a single `b` after `aa*`.
4. **`S3`**: Prepares for `c` in either `ca*` or `acaa*`.
5. **`S4`**: Handles `c` and transitions to either `ca*` or `acaa*`.
6. **`S5`**: Accepting state (final state).
7. **`TRAP`**: Trap state for invalid inputs.

### Transitions

The NFA transitions allow multiple possible states:
- `S0` → `S1` on `a`
- `S1` → `S1` on `a`, `S2` on `b`
- `S2` → `S3` on `a`
- `S3` → `S4` on `c`
- `S4` → `S5` on `a`
- `S5` → `S5` on `a`
- Any invalid transitions lead to the trap state `TRAP`.

### Acceptance

A string is accepted if, after processing all input, one or more of the current states is the accepting state (`S5`).

## Usage

Prerequisites
anaconda.cloud/jupyterhub
How to Use
Open the pda.ipynb file on anaconda cloud
Run the program using Python:
Enter a string to check: aaaabca
The program will output whether the string is ACCEPTED or REJECTED by the NFA.

Example Input and Output
Example 1:
Input: aaaaabca
Output:The string 'aaaaabca' is ACCEPTED by the NFA.
Example 2:
Input: abac
Output: The string 'abac' is REJECTED by the NFA.

NFA Class
The NFA class includes:

States: Set of all possible states, including the trap state.
Transitions: A dictionary defining valid transitions, where each input may lead to multiple states.
Start State: Initial state of the NFA (S0).
Accepting State: Final state where the input is accepted (S5).
Method: process_input
Starts with the initial state (S0).
Tracks all possible current states.
For each input character, determines all possible next states.
After processing all characters, checks if any current states are the accepting state (S5).
Examples of Accepted Strings
The following strings are valid for the regular expression aa*b(ca* + acaa*):

aabca
aaaabacaaa
aaabca
aaaaaaabca
aaaabacaaaa
Invalid strings will be rejected.

Customization
To modify the NFA:

Adjust the transitions dictionary to change state transitions or add additional states.
Update the start or accept states as needed.
Examples of Accepted and Rejected Strings
Accepted Strings:
aaaabca
aaaaaaabacaaa
aabacaaa
aaaaabacaaaa
Rejected Strings:
abc
aabc
abab

Pushdown Automaton (PDA) 𝐿={𝑎^𝑛𝑏𝑎^2𝑛 ∣ 𝑛≥1}
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


