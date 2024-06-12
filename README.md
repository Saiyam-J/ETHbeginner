# MyToken Smart Contract

MyToken is a simple ERC20-like smart contract implemented in Solidity. This contract allows for the creation of a custom token named "EtherNova" with the abbreviation "ETN". It provides basic functionalities to mint and burn tokens, as well as to keep track of balances associated with different addresses.

## Contract Details

### Public Variables

- **tokenName**: The name of the token, set to "EtherNova".
- **tokenAbbrv**: The abbreviation of the token, set to "ETN".
- **totalSupply**: The total supply of the token, initialized to 0.

### Mapping

- **balances**: A mapping from addresses to their respective token balances.

## Functions

### `mint`

The `mint` function allows for the creation of new tokens. It takes two parameters: an address and a value. The function increases the total supply by the specified value and credits the balance of the given address.

```solidity
function mint (address _addr, uint _value) public {
    totalSupply += _value;
    balances[_addr] += _value;
}
```

### `burn`
The `burn` function allows for the destruction of existing tokens. It takes two parameters: an address and a value. The function decreases the total supply by the specified value and deducts the balance of the given address. The function includes a check to ensure that the balance of the address is greater than or equal to the value to be burned.

```solidity
Copy code
function burn (address _addr, uint _value) public {
    if (balances[_addr] >= _value) {
        totalSupply -= _value;
        balances[_addr] -= _value;
    }
}
```
## Requirements
- The contract stores the token details (name, abbreviation, total supply) as public variables.
- The contract maintains a mapping of addresses to balances.
- The mint function increases the total supply and the balance of a specified address.
- The burn function decreases the total supply and the balance of a specified address, with a check to ensure the balance is sufficient.
