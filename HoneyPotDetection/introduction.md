---
icon: bullseye-arrow
---

# Introduction

`HoneyPotDetection` is a JavaScript/TypeScript library for identifying  identifying HoneyPots. 

## Installation

```bash
npm install suihoneypot
```

## Usage

```TypeScript
import { isHoneyPot } from 'suihoneypot';

const ca: string = "0x566923c3995f64c3f861e694da52cdc79d8b968bfcdb7f8a275c19c73fd9b99d::brett::BRETT"
const res = await isHoneyPot(ca);
console.log(res);
```

- Github: [https://github.com/SuiSec/HoneyPotDetectionOnSui](https://github.com/SuiSec/HoneyPotDetectionOnSui)    
- NPM: [https://www.npmjs.com/package/suihoneypot](https://www.npmjs.com/package/suihoneypot)    