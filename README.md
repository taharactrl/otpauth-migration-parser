# OTP Authenticator Migration URL Parser

This is a parser for Google Authenticator Account Export QR Code data.

## Installation

```sh
npm install --save otpauth-migration-parser
```

## Usage

```js
const parser = require("otpauth-migration-parser");

// otp account migration data uri from Google Authenticator's QR Code
const dataUri = "otpauth-migration://offline?data=xxxxxxxxxxxxxxxxx";

async () => {
  // parser is a Promise function
  const parsedDataList = await parser(dataUri);
  for (let otpSecretInfo of parsedDataList) {
    console.log(otpSecretInfo);
    /* =>
      {
        secret: 'xxxxxxxxxxxxxxxxxxxxxxxxxxx',
        name: 'sample',
        issuer: 'sample',
        algorithm: 'sha1',
        digits: 6,
        type: 'totp',
        counter: Long { low: 0, high: 0, unsigned: false }
      }
    */
  }
};
```
