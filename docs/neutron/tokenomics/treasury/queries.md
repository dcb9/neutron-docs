# Queries

This contract accepts these query msgs:

```rust
pub enum QueryMsg {
    /// The contract's configuration
    Config {}, // returns `Config`

    /// The contract's pause info
    PauseInfo {}, // returns `PauseInfoResponse`
}
```

## Config

Returns the current config for Treasury contract:

```rust
pub struct Config {
    /// Denom in which Treasury holds it's funds.
    pub denom: String,

    /// The address of the Neutron DAO. It's capable of pausing and unpausing the contract.
    pub main_dao_address: Addr,

    /// The address of the DAO guardian. The security DAO is capable only of pausing the contract.
    pub security_dao_address: Addr,
}
```

## PauseInfo

Returns the current pause info for the Treasury contract:

```rust
pub enum PauseInfoResponse {
    /// Contract is paused until `until_height` block is reached
    Paused { until_height: u64 },

    /// Contract is not paused
    Unpaused {},
}
```