---
icon: bullseye-arrow
---

# Quickstart

DryRunPlus is a transaction simulation and security analysis tool specifically designed for Sui Network wallets. After receiving a transaction request, it analyzes the transaction using various security strategies, and then returns the results of the simulated transaction and the security analysis to the wallet, helping users assess the risks of the transaction.

## Usage

### Request

Parameters:

- `transaction`: `Transaction` data, must contain `sender`.
- `website`: Optional, string. The website of the DApp that connects to the wallet, if it detects that the site is risky, will share the URL with other security applications for blocking.

```TypeScript
const tx = new Transaction();
// PTB
tx.setSender(userAddress);
try {
    const checkResponse = await fetch('https://api.suisec.tech/dryRunPlus', {
        method: 'POST',
        headers: {
            'Content-Typs': 'application/json',
        },
        body: JSON.stringify({ 
            transaction: JSON.stringify(tx.getData()),
            website: string,  // optional
        })
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
  msg: String | undefined;
}
```

If the transaction analysis shows no risk, the `pass` value is `true`, and `msg` is `undefined`.   
If the transaction analysis shows risk, the `pass` value is `false`, and `msg` displays the risk information.   
`dryRun` is `DryRunTransactionBlockResponse`.
