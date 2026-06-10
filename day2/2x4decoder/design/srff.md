
<img width="1223" height="564" alt="Screenshot 2026-06-10 210642" src="https://github.com/user-attachments/assets/892f617b-6415-4101-9c71-6216019a575d" />

<img width="1080" height="509" alt="WhatsApp Image 2026-06-10 at 9 15 52 PM" src="https://github.com/user-attachments/assets/cced4dea-58dc-4b3b-b98d-0cf8fa599f6e" />
An SR flip-flop may power up in an undefined state because the output can randomly become either Set (Q = 1) or Reset (Q = 0). To ensure that the flip-flop starts in a known state, two additional asynchronous inputs called Preset (PR) and Clear (CLR) are provided. These inputs can force the output to a desired state regardless of the clock signal.
Operation of Preset and Clear:
PR = 1, CLR = 1 (Normal Operation)
Preset and Clear are inactive.
The flip-flop operates normally according to the S, R, and Clock inputs.
PR = 0, CLR = 1 (Preset Active)
The flip-flop is forced into the Set state.
Output: Q = 1, Q̅ = 0.
PR = 1, CLR = 0 (Clear Active)
The flip-flop is forced into the Reset state.
Output: Q = 0, Q̅ = 1.
PR = 0, CLR = 0 (Invalid Condition)
Both outputs may become the same value.
This condition is not allowed because it violates the complementary nature of the outputs.
