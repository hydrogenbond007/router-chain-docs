---
title: Handling the Acknowledgment on the Source Chain
sidebar_position: 2
---

Once the read request is executed on the destination chain, the requested data is sent along with an acknowledgment to the source chain. To handle the acknowledgment, developers need to include a `handle_crosstalk_ack()` function in their contract. This function will have three parameters, namely:

```javascript
fn handle_crosstalk_ack(
    &self,
    event_identifier: u64,
    exec_flags: Vec<bool>,
    exec_data: Vec<Vec<u8>>,
)
```

### 1. event_identifier

This is the same nonce you receive while calling the `read_query_to_dest()` function on the source chain Gateway contract. Using this nonce, you can verify whether a particular request was executed on the destination chain.

### 2. exec_flags

Since multiple payloads can be sent to multiple contract addresses on the destination chain, the `exec_flags` is an array of boolean values that tells you the status of the individual calls.

### 3. exec_data

The `exec_data` parameter is an array of bytes that provides the return values from every read call included in the read request. Based on the application's requirement, this data can be decoded and processed on the source chain.

<br/>

> **Note:** More details about this function can be found [here](../../understanding-crosstalk/near_guides/handleCrossTalkAck).
