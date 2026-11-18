To analyze the security risks in an enterprise voting system where unverified or fraudulent identity records in a primary database can be exploited to compromise downstream tallying systems, we must first understand the mechanics of such a system.

The registration-to-tallying pipeline is a linear process where input data (registrations) is transformed into output data (tallies). Each step in this pipeline introduces potential vulnerabilities. The integrity of the output is only as strong as the weakest link in the chain.

1. **Database Injection Attacks**: If an attacker can inject false or altered data into the primary database, this can lead to compromised tallies. This can be achieved through SQL injection or other forms of data manipulation.

2. **Ghost Record Creation**: An attacker could create duplicate or fake records in the registration database, which would then appear as legitimate votes in the tallying system.

3. **Manipulation of Weight-Allocation Matrices**: If the weight-allocation matrices are manipulated, votes from certain groups could be undervalued or overvalued, skewing the results.

To mitigate these threats, cryptographic and verification mechanisms are essential:

- **Hash-Chain Validation**: Implementing a hash-chain for each record can ensure the integrity of the data. Any alteration to a record would break the hash-chain, making the tampering detectable.

- **Consensus Logging**: Use a consensus protocol to log all transactions. This ensures that all parties agree on the state of the system, making it difficult for an attacker to manipulate the data without consensus.

- **Append-Only Ledgers**: Implement an append-only ledger system, where each entry is cryptographically linked to the previous one, ensuring the immutability of the data.

The systemic risks introduced by the dependency of the registration-to-tallying pipeline can be quantified by assessing the probability of a successful attack and the potential impact on the outcome. However, without specific data on the system's architecture and the attackers' capabilities, this assessment remains theoretical.

To provide a mathematical assessment, we would need to model the system as a complex network with nodes representing data points and edges representing dependencies. The safety factor would then be derived from the resilience of this network to attacks, which could be modeled as attempts to break the connections or corrupt the nodes.

Without loss of generality, let's assume a simplified model where the probability of a successful attack is inversely proportional to the number of cryptographic protections in place. If we assign a base risk factor of 50 (arbitrary and illustrative), we could then adjust this factor based on the number of protections implemented:

- Hash-chain validation: +20
- Consensus logging: +15
- Append-only ledgers: +10

Total safety factor: 50 + 20 + 15 + 10 = 95

This calculation is highly simplified and serves only as a rough estimate. A comprehensive analysis would require a detailed understanding of the system's architecture, the attackers' capabilities, and the specific cryptographic protections in place.