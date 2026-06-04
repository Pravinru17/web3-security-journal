# Day 4 Security Notes

## Topic 1: Custom Errors

### Why Use Custom Errors?

Traditional approach:

require(owner == msg.sender, "Not owner");

Optimized approach:

error NotOwner();

if (owner != msg.sender) {
revert NotOwner();
}

### Benefits

* Lower gas costs
* Cleaner code
* Better scalability

### Best Practice

Prefer custom errors over require strings for production contracts.

---

## Topic 2: Insecure Randomness

### Unsafe Sources

* block.number
* block.timestamp
* blockhash

These values are predictable.

### Attack Risk

An attacker can:

* read blockchain data
* reproduce calculations
* predict outcomes

### Secure Alternatives

* Chainlink VRF
* Commit-Reveal
* Oracle-based randomness

### Security Principle

Randomness on-chain is difficult.

Assume public blockchain data is predictable.
