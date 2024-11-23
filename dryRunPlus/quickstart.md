---
icon: bullseye-arrow
---

# Quickstart

DryRunPlus is a transaction simulation and security analysis tool specifically designed for Sui Network wallets. After receiving a transaction request, it analyzes the transaction using various security strategies, and then returns the results of the simulated transaction and the security analysis to the wallet, helping users assess the risks of the transaction.

## Usage

### Request

```TypeScript
const tx = new Transaction();
// PTB
tx.setSender(userAddress);
try {
    const checkResponse = await fetch('https://api.suisec.tech/', {
        method: 'POST',
        headers: {
            'Content-Typs': 'application/json',
        },
        body: JSON.stringify({ transaction: JSON.stringify(tx.getData()) })
    });

    if (!checkResponse.ok) {
        throw new Error(`HTTP error! status: ${checkResponse.status}`);
    }
} catch (error) {
    console.log(error)
}
```

### Response

```TypeScript
export interface Response {
  dryRun: DryRunTransactionBlockResponse;
  pass: boolean;
  msg?: String;
}
```