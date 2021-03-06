# b70

Payment protocol (BIP70) for bcoin.

## Usage

``` js
const b70 = require('b70');
const {Address} = require('bcoin');

// Create a payment request.
const req = new b70.PaymentRequest({
  version: 1,
  paymentDetails: {
    network: 'testnet',
    paymentUrl: 'http://bcoin.io/payment',
    memo: 'foobar',
    time: Math.floor(Date.now() / 1000),
    expires: Math.floor(Date.now() / 1000) + 3600,
    outputs: [
      { value: 10000, address: new Address() },
      { value: 50000, address: new Address() }
    ],
    merchantData: { foo: 'bar' }
  }
});

// Sign it.
req.setChain([crt]); // Certificate Chain
req.sign(key); // PEM/DER formatted private key

// Serialize to protobuf format.
const raw = req.toRaw();
```

## Contribution and License Agreement

If you contribute code to this project, you are implicitly allowing your code
to be distributed under the MIT license. You are also implicitly verifying that
all code is your original work. `</legalese>`

## License

- Copyright (c) 2017, Christopher Jeffrey (MIT License).

See LICENSE for more info.
