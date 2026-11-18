To address the security risks in an enterprise voting system where unverified or fraudulent identity records in a primary database can be exploited to compromise downstream tallying systems, we must first understand the mechanics of such exploitation and the defenses against it.

### Registration-to-Tallying Pipeline Dependency

The registration-to-tallying pipeline can be modeled as a series of nodes:
1. **Registration Node (R)**: Where identity records are created and verified.
2. **Tallying Node (T)**: Where votes are counted and aggregated.

### Failure Probabilities and Impact

- **P(R)**: Probability of a compromised registration record.
- **P(T|R)**: Probability that a compromised record affects the tallying system.
- **I(T)**: Impact of a compromised record on the tallying system.

### Mathematical Framework

The systemic risk (R) can be modeled as:
\[ R = P(R) \times P(T|R) \times I(T) \]

### Quantification of Variables

- **P(R)**: Assume a false registration rate of 0.1% (P(R) = 0.001).
- **P(T|R)**: Assume a 50% chance that a compromised record affects the tallying (P(T|R) = 0.5).
- **I(T)**: Assume that a single ghost record can affect 10,000 votes (I(T) = 10,000).

### Calculation

\[ R = 0.001 \times 0.5 \times 10,000 = 5 \]

This means that for every 100,000 registration records, there is a 5% chance that a compromised record affects 10,000 votes.

### Mitigation Strategies

- **Hash-chain validation**: Ensures that each record in the registration database is a one-way hash of the previous record, preventing tampering.
- **Consensus logging**: Uses a distributed consensus protocol to validate and log changes to the registration database.
- **Append-only ledgers**: Ensures that the registration database is immutable and can only be appended to, preventing deletion or alteration of records.

### Safety Factor

Given the systemic risk of 5%, a safety factor of 50 would imply that the system can tolerate a 0.1% chance of a compromised record affecting the tallying system. This aligns with the quantified risk, assuming a risk tolerance threshold of 0.1%.

### Conclusion

The systemic risk introduced by the registration-to-tallying pipeline dependency is quantifiable and can be mitigated through robust cryptographic and verification mechanisms. The proposed safety factor of 50 is justified by the mathematical assessment of the systemic risks, ensuring a high level of security and integrity in the voting system.