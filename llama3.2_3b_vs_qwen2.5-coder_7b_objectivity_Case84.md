**Systemic Analysis of Enterprise Voting System Security Risks**

**Primary Database Vulnerabilities**

Unverified or fraudulent identity records in the primary database can be exploited to compromise downstream tallying systems. This is due to the lack of robust identity verification mechanisms, allowing attackers to create or manipulate identity records, leading to:

1. **Database Injection Attacks**: Malicious actors can inject malicious SQL code into the primary database, allowing them to extract or modify sensitive data, including voter registration information.
2. **Ghost Record Creation**: Attackers can create fake voter registration records, which can be used to manipulate the tallying process or create the illusion of a legitimate vote.
3. **Weight-Allocation Matrix Manipulation**: Corrupted registration data can be used to manipulate the weight-allocation matrix, which determines the voting power of each voter. This can lead to a biased outcome, where certain groups or individuals have disproportionate influence over the election result.

**Cryptographic and Verification Mechanisms**

To protect against these threats, the following cryptographic and verification mechanisms can be employed:

1. **Hash-Chain Validation**: Implement a hash-chain validation mechanism to ensure the integrity of the primary database. This involves creating a digital fingerprint of each record and verifying that it has not been tampered with.
2. **Consensus Logging**: Implement a consensus logging mechanism to ensure that all nodes in the tallying system agree on the state of the system. This can be achieved through the use of distributed ledger technology, such as blockchain.
3. **Append-Only Ledgers**: Implement an append-only ledger to ensure that all transactions are immutable and tamper-proof.

**Systemic Risks**

The registration-to-tallying pipeline dependency introduces the following systemic risks:

1. **Scalability**: As the number of voters increases, the primary database and tallying system must scale to accommodate the increased load. Failure to do so can lead to performance issues and security vulnerabilities.
2. **Interdependence**: The primary database and tallying system are interdependent, meaning that any failure in one system can have a cascading effect on the other. This increases the risk of a systemic failure.
3. **Material Scarcity**: The availability of voting materials, such as ballots and voting machines, can become a bottleneck in the system. This can lead to delays and security vulnerabilities.

**Safety Factor**

Given the potential risks and vulnerabilities identified in this analysis, a safety factor of 20 is recommended to ensure the integrity and security of the enterprise voting system. This safety factor can be achieved through the implementation of robust identity verification mechanisms, cryptographic and verification mechanisms, and a distributed ledger technology-based consensus logging system.