### Background and Rationale

---

The current system allows us to create a transaction and issue it to the bank immediately. In the context of introducing transactions that are created as a result of a round-up, there will be potentially a lot of transactions worth a few cents issued to the bank.

In order to avoid spamming the user's bank account with a lot of low volume transactions, we want to "batch" those transactions into a single higher volume transactions.

*Note*: A round-up is when we take a users bank transaction e.g. a purchase of $3.67 at Blue Bottle Coffee, and round it up to the nearest whole dollar to invest, which in this example would be $0.33 into their batch. 

### User Story

---

*As a User, I want Donut to batch my low volume transactions together, so that my bank account is not spammed with a lot of low volume transactions.*

### Acceptance criteria (AC)

---

- A **Batch** can be either *dispatched* or *un-dispatched*
    - A **Batch** is *dispatched* if it resulted in a **Transaction** being sent to the bank.
    - A **Batch** is un-dispatched if it didn't send a **Transaction** to the bank
- There is exactly one *un-dispatched* **Batch** at any point of time
- A **Batch** contains an accrued amount, with an initial value of 0
- A **User** can send low volume amounts to a **Batch** and the accrued amount of the **Batch** increases
- Once the accrued amount of the **Batch** goes above the threshold of 100, it gets *dispatched.* The created T**ransaction** has a an amount equal to the accrued amount of the **Batch**
- An history of all **Batches**, *dispatched* or *un-dispatched* must be kept

### Example

---

- **Batch** 1 contains an accrued amount of 50 and is *un-dispatched*
- **User** sends a transaction of 40 → **Batch** 1 now contains an accrued amount of 90
- **User** sends a transaction of 20 → **Batch** 1 now contains  an accrued amount of 110, it gets *dispatched* and creates a **Transaction** of 110. Batch 2 is created and is *un-dispatched* with an accrued amount of 0.
- **User** send a transaction of 20 → **Batch** 2 now contains an accrued amount of 20

### Other important details
---

- **PR Review version**

Your task consists of reviewing a pull-request that aims implementing this user story. Keep in mind that all AC of this story have to be met and that the system is subject to concurrent request (~50 requests per second). Do not forget to implement tests!

- **Boilerplate version and submission**

Your task consists of implementing this user story.

**Follow these instructions to submit your challenge.**
- Create a private Github repository
- Write your Code on a separate branch
- Commit your Changes
- Issue a Pull Request
- Invite us (Github: "lukaskai", "cidyuk") as a Collaborator to Your Repository
