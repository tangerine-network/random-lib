# Tangerine Network RNG Library

## Introduction

Tangerine Network provides on-chain randomness through a precompiled contract.
Using a precompiled contract instead of introducing a new OP code ensures that
we are compatible with EVM, and eliminates the need to maintain a separate
toolchain.

The precompiled contract is located at
`0xc327ff1025c5b3d2deb5e3f0f161b3f7e557579a`, which is the first 20 bytes of
`Keccak256Hash("Tangerine Network Random")`. The gas cost for each invocation is 64.

To use the random library, simply include the library file then call `Random.rand()` to get the random number.

## Example

```
import "github.com/tangerine-network/random-lib/RandomLib.sol";

contract UseRandom {
    event Win();
    event Lose();

    function readRand() public view returns (uint256) {
        return Random.rand();
    }

    function bet() public {
        if (Random.rand() % 100 >= 50) {
            emit Win();
        } else {
            emit Lose();
        }
    }
}
```
