> # DACH （DASH CAR CHAIN）
>

**DACH** is a blockchain global open source project developed by DAG foundation in Singapore. DAG foundation adheres to the concept of combination of network and entity, integration of industry and finance, breaks through the industrial layout of upstream and downstream of cars market, redefines and creates a new industrial vehicle ECO. 

**DACH** is a decentralized vehicle ecological data service platform based on the characteristics of blockchain, such as transparency, trustworthiness and irreversibility. DACH Smart Contracts for security and utility tokens.

------

### DACH Ethereum & EOSIO Smart Contract info


| Contract | Contract Address                           | Burned | Total issue amount | Actual circulation   |
| -------- | :----------------------------------------- | ------ | ------------------ | -------------------- |
| 2.0      | 0x0b52599ddec843315224a179ae243eb47c1792ed | 90%    | 3,913,000,000      | 391,300,000          |
| 3.0      | dach3iotzeus                               | 0%     | 39,000,000         | Same as total amount |



- DACH 2.0 -- ERC-20 token used for staking and burning.

- DACH 3.0 -- EOSIO token used for business and internet of things IOT.

*Note: DACH is the token of the Erasure Protocol and the Numerai Tournament.*



### Ecological topology

- Validated Statistics
  - DACH circulating supply and stake
  - Etherscan token tracker
  - Coingecko token tracker



- Development Install dependencies: 

  yarn install

  

- Compile contracts: 

  yarn compile



Specification ERC-20

```
function approve(address _spender, uint256 _value);
function transfer(address _to, uint256 _value);
function transferFrom(address _from, address _to, uint256 _value);

function totalSupply();
function balanceOf(address _owner);
function allowance(address _owner, address _spender);

event Transfer(address indexed _from, address indexed _to, uint256 _value);
event Approval(address indexed _owner, address indexed _spender, uint256 _value);
```



Refer to ERC-20 standard for detailed specification.

*Note: DACH deviates from ERC-20 in the implementation of the approve() function to prevent the ERC-20 approve race condition.*

The approve() function is limited to changing the allowance from zero or to zero.

In order to change the allowance from a non-zero value to a different non-zero value in a single transaction. The user must use the change Approval() function.

```
function change Approval(address _spender, uint256 _oldValue, uint256 _newValue);
```


Sets the approval to a new value while checking that the previous approval value is what we expected.

```
_spender is the address of the contract.
_oldValue is the current amount the contract is allowed to spend.
_newValue is the new amount to allow the contract to spend.
```

**Burning**

The mint() and numeraiTransfer() functions have been repurposed from their initial use in order to support native token burns as implemented in OpenZeppelin's ERC20Burnable.

Note: The caller must check the return values of these functions as they return false on failure.

```
/**

 * @dev Destoys `amount` tokens from `msg.sender`, reducing the total supply.
   *
 * Emits a `Transfer` event with `to` set to the zero address.
   *
 * Requirements:
 * - `account` must have at least `amount` tokens.
     */
     function mint(uint256 _value);
      => function burn(uint256 amount);

/**

 * @dev Destoys `amount` tokens from `account`.`amount` is then deducted
 * from the caller's allowance.
   *
 * Emits an `Approval` event indicating the updated allowance.
 * Emits a `Transfer` event with `to` set to the zero address.
   *
 * Requirements:
 * - `account` must have at least `amount` tokens.
 * - `account` must have approved `msg.sender` with allowance of at least `amount` tokens.
     */
     function numeraiTransfer(address _to, uint256 _value);
      => function burnFrom(address account, uint256 amount);
     Custody for Numerai Tournament
     Numerai performs custody of the token for participants in the Numerai Tournament. This removes participation barriers as users no longer need to pay for gas or manage their own private keys. The withdraw() function can be used by Numerai to transfer tokens from the first 1 million accounts (0x00...00000000 to 0x00...000F4240).

function withdraw(address _from, address _to, uint256 _value);
```

------

### Deprecated Features

All other contract methods belong to the following features which have been disabled as a part of the DACH 2.0 upgrade.

- Multisignature

- Emergency Stops

- Minting

- Upgradeability
