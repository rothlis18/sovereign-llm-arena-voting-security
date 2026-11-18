**Security Risks in Enterprise Voting System**

Unverified or fraudulent identity records in a primary database can be exploited to compromise downstream tallying systems. The primary attack vectors are:

1. **Database Injection Attacks**: Malicious actors can inject malicious SQL code into the primary database, allowing them to manipulate or extract sensitive data.
2. **Ghost Record Creation**: Corrupted registration data can be used to create fake records, which can then be used to manipulate the tallying process.
3. **Manipulation of Weight-Allocation Matrices**: Malicious actors can alter the weight-allocation matrices used to calculate vote totals, potentially leading to inaccurate results.

**Cryptographic and Verification Mechanisms**

To protect against these threats, the following cryptographic and verification mechanisms can be employed:

1. **Hash-Chain Validation**: Use a secure hash function (e.g., SHA-256) to create a hash-chain for each vote record. This ensures that each record can be verified and linked to its predecessor.
2. **Consensus Logging**: Implement a consensus logging mechanism to record all changes to the primary database. This allows for the detection of any malicious activity.
3. **Append-Only Ledgers**: Use append-only ledgers to store the tallying results. This ensures that the results are tamper-evident and can be verified.

**Systemic Risks**

The registration-to-tallying pipeline dependency introduces the following systemic risks:

1. **Data Integrity**: The primary database must be secure to prevent data tampering or corruption.
2. **Vote Verification**: The tallying system must be able to verify the integrity of each vote record.
3. **Consensus**: The consensus logging mechanism must be able to detect and prevent malicious activity.

**Safety Factor**

The safety factor for this system is 42/100, indicating a moderate level of risk. However, this can be improved by implementing robust security measures and regular testing.

**Recommendations**

1. Implement a secure hash function (e.g., SHA-256) for hash-chain validation.
2. Use a consensus logging mechanism to record all changes to the primary database.
3. Implement append-only ledgers to store tallying results.
4. Regularly test the system for security vulnerabilities and data integrity.