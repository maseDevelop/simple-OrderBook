# 📲 Simple Order Book library
Order book library in Solidity using a modified version of the BokkyPooBahsRedBlackTreeLibrary

Link to original repository for BokkyPooBahsRedBlackTreeLibrary on which the lib is based on: https://github.com/bokkypoobah/BokkyPooBahsRedBlackTreeLibrary

Link to Modified version: https://github.com/maseDevelop/BokkyPooBahsRedBlackTreeLibrary-Modified

**This has not been tested or audited and was made for research purposes - just used to spark an idea **

Orders are stored in a Solidity Mapping:

Mapping -> sell token address -> buy token address -> sorted tree of orders

## Functions

<br />

### insert
```javascript
function root() internal view returns (uint _key);
```
Insert the key `id` into the tree based on key `price`.

Transaction | Condition
:---------- |:--------
_success_   | `id` has been successfully inserted into the tree
_failure_   | `id` already exists in the tree

<br />

### remove

```javascript
function remove(OB storage self,uint _id, address _sell_token, address _buy_token) public;
```

removes value from tree

Transaction | Condition
:---------- |:--------
_success_   | `key` has been successfully removed from the tree
_failure_   | `key` does not exist in the tree

<br />

### getFirstOffer

```javascript
function getFirstOffer(OB storage self, address _sell_token, address _buy_token) public view returns(uint)
```

Returns the smallest price value currently held in tree.

Return Value  | Condition
:------------ |:--------
_{first key}_ | Tree has at least one key
`EMPTY`       | Tree empty

<br />

### getLastOffer

```javascript
function getLastOffer(OB storage self, address _sell_token, address _buy_token) public view returns(uint);
```

Returns the largest price value currently held in tree.

Return Value  | Condition
:------------ |:--------
_{last key}_ | Tree has at least one key
`EMPTY`       | Tree empty

<br />

### getNode

```javascript
function getNode(OB storage self, uint _id, address _sell_token, address _buy_token) public view returns (uint price)
```

Gets the price stored at a particular node

Returns the node information if `key` exists in the tree. All `uint` values will be set to `EMPTY` if `key` does not exist in the tree.

<br />

