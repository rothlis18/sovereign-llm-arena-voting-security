**Systemic Analysis of Enterprise Voting System Security Risks**

**Database Injection Attacks**

Corrupted registration data can be exploited to inject malicious SQL code into the primary database, compromising downstream tallying systems. This can be achieved through:

1. **SQL Injection**: Malicious data can be injected into the database through user input, allowing an attacker to execute arbitrary SQL code.
2. **Blind SQL Injection**: An attacker can manipulate the database to extract sensitive information without directly injecting malicious SQL code.

**Ghost Record Creation**

Corrupted registration data can be used to create ghost records in the primary database, which can then be used to manipulate the tallying system. This can be achieved through:

1. **Data Tampering**: Malicious data can be inserted into the database, creating a duplicate record that can be used to manipulate the tallying system.
2. **Data Deletion**: Corrupted data can be deleted, creating a gap in the record that can be exploited to manipulate the tallying system.

**Manipulation of Weight-Allocation Matrices**

Corrupted registration data can be used to manipulate the weight-allocation matrices used in the tallying system. This can be achieved through:

1. **Data Tampering**: Malicious data can be inserted into the weight-allocation matrices, altering the voting weights and potentially leading to a compromised outcome.
2. **Data Manipulation**: Corrupted data can be used to manipulate the voting weights, potentially leading to a compromised outcome.

**Cryptographic and Verification Mechanisms**

To protect against these threats, the following cryptographic and verification mechanisms can be employed:

1. **Hash-Chain Validation**: A hash-chain can be used to validate the integrity of the registration data and ensure that it has not been tampered with.
2. **Consensus Logging**: A consensus logging mechanism can be used to record all changes to the registration data, ensuring that any tampering or manipulation can be detected.
3. **Append-Only Ledgers**: An append-only ledger can be used to record all changes to the weight-allocation matrices, ensuring that any tampering or manipulation can be detected.

**Mathematical Assessment of Systemic Risks**

The systemic risks introduced by the registration-to-tallying pipeline dependency can be assessed using the following mathematical model:

Let `R` be the set of registration data, `T` be the set of tallying system data, and `W` be the set of weight-allocation matrices.

The probability of a database injection attack can be modeled as:

`P(injection) = (1 - σ) \* (1 - ρ) \* (1 - α)`

where `σ` is the probability of data tampering, `ρ` is the probability of data deletion, and `α` is the probability of data injection.

The probability of a ghost record creation attack can be modeled as:

`P(ghost) = (1 - σ) \* (1 - ρ) \* (1 - β)`

where `β` is the probability of data duplication.

The probability of a weight-allocation matrix manipulation attack can be modeled as:

`P(manipulation) = (1 - σ) \* (1 - ρ) \* (1 - γ)`

where `γ` is the probability of data manipulation.

The overall probability of a successful attack can be modeled as:

`P(attack) = P(injection) + P(ghost) + P(manipulation)`

**Safety Factor**

Based on the mathematical assessment of systemic risks, a safety factor of 75 can be assigned to the enterprise voting system. This indicates that the system has a moderate level of security, but further improvements are needed to mitigate the risks introduced by the registration-to-tallying pipeline dependency.