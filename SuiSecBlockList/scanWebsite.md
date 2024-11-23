---
icon: bullseye-arrow
---

# Scan Website

## Usage

```TypeScript
import { SuiSecBlocklist } from "suisecblocklist";

const blocklist = new SuiSecBlocklist();

// 1. Fetch the domainlist and persist it in the storage
blocklist.fetchDomainlist();

// 2. Re-refetch the domainlist every 5 minutes
setInterval(() => blocklist.fetchDomainlist(), 1000 * 60 * 5);

// 3. Once you have a domainlist object saved, you can execute lookups
const action = blocklist.scanDomain("https://scam-website.io");

if (action === Action.BLOCK) {
  // block the domain
}
```