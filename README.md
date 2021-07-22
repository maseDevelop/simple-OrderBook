# 📲 Simple Order Book library
Order book library in Solidity using a modified version of the BokkyPooBahsRedBlackTreeLibrary

Link to original repository for BokkyPooBahsRedBlackTreeLibrary: https://github.com/bokkypoobah/BokkyPooBahsRedBlackTreeLibrary

Link to Modified version: https://github.com/maseDevelop/BokkyPooBahsRedBlackTreeLibrary-Modified

**This has not been tested or audited and was made for Research Purposes **

Orders are stored in a Solidity Mapping:

Mapping -> sell token address -> buy token address -> sorted tree of orders

## Functions

See [contracts/TestBokkyPooBahsRedBlackTree.sol](contracts/TestBokkyPooBahsRedBlackTree.sol) (or the [flattened](flattened/TestBokkyPooBahsRedBlackTree_flattened.sol) version) for an example contract that uses this library.

<br />

### insert
```javascript
function root() internal view returns (uint _key);
```

Returns the root of the tree, or `EMPTY` is the tree is empty.

<br />

### remove

```javascript
function remove(OB storage self,uint _id, address _sell_token, address _buy_token) public;
```

Returns the smallest key in the tree.

Return Value  | Condition
:------------ |:--------
_{first key}_ | Tree has at least one key
`EMPTY`       | Tree empty

<br />

### getFirstOffer

```javascript
function getFirstOffer(OB storage self, address _sell_token, address _buy_token) public view returns(uint)
```

Returns the largest key in the tree.

Return Value | Condition
:----------- |:--------
_{last key}_ | Tree has at least one key
`EMPTY`      | Tree empty

<br />

### getLastOffer

```javascript
function getLastOffer(OB storage self, address _sell_token, address _buy_token) public view returns(uint);
```

Returns the next key in the tree with a value larger than `x`.

Return Value | Condition
:----------- |:--------
_{next key}_ | There exists a key with a value larger than the `x` key
`EMPTY`      | Tree empty
`EMPTY`      | `x` is not an existing key in the tree
`EMPTY`      | `x` is the only key in the tree
`EMPTY`      | `x` is the last key in the tree

<br />

### getNode

```javascript
function getNode(OB storage self, uint _id, address _sell_token, address _buy_token) public view returns (uint price)
```

Returns the previous key in the tree with a value smaller than `x`.

Return Value | Condition
:----------- |:--------
_{prev key}_ | There exists a key with a value smaller than the `x` key
`EMPTY`      | Tree empty
`EMPTY`      | `x` is not an existing key in the tree
`EMPTY`      | `x` is the only element in the tree
`EMPTY`      | `x` is the last element in the tree

<br />

