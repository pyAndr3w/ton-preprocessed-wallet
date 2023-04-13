## ton-preprocessed-wallet

[![License](https://img.shields.io/badge/license-MIT-brightgreen)](https://opensource.org/licenses/MIT)
[![FunC](https://img.shields.io/badge/made%20with-FunC-brightgreen)](https://ton.org/docs/#/func)
[![Fift](https://img.shields.io/badge/made%20with-Fift-brightgreen)](https://newton-blockchain.github.io/docs/fiftbase.pdf)
[![toncli](https://img.shields.io/badge/for%20use%20with-toncli-brightgreen)](https://github.com/disintar/toncli)
[![TON](https://img.shields.io/badge/based%20on-TON-blue)](https://ton.org/)

<center><h1>Actual version is <a href="https://github.com/pyAndr3w/ton-preprocessed-wallet-v2">ton-preprocessed-wallet-v2</a></h1></center>

TON based wallet smart contract whose input is a preprocessed [c5 register](https://ton.org/docs/tvm.pdf#page=11).

This approach saves gas, as All processing is done **offchain**. _(onchain only check seqno and signatures)_

Also, with this approach, you can update the version of the contract without changing the wallet address (i.e. `set_code` is also written to the [c5 register](https://ton.org/docs/tvm.pdf#page=11))

The message body is assemble using the following [TL-B](https://github.com/tonstack/ton-docs/blob/main/TL-B/README.md) scheme:\
`msg_body$_ sig:bits512 subwallet_id:uint32 valid_until:uint32 seq_no:uint32 actions:^OutList = MsgBody`

OutList is assemble using [the standard TL-B scheme for c5 register](https://github.com/newton-blockchain/ton/blob/master/crypto/block/block.tlb#L368:L381).
