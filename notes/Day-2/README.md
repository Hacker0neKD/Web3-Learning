## Day 2: Solidity Basics

Solidity boilerplate (or the “shebang line”) typically starts like this:

```solidity
pragma solidity // 1. Enter solidity version here
// 2. Create contract here
```

In Solidity, all code begins with the `contract` keyword:

```solidity
contract HelloWorld {

    // code here

}
```

---

### Version Pragma

All Solidity code should start with a **version pragma** — a declaration specifying which version of the Solidity compiler should be used.

```solidity
pragma solidity >=0.5.0 <0.6.0;

// This is the syntax for defining the Solidity version

//------------------------------------------------
// Operators:

// Greater Than (>) → version should be greater than 0.5.0

// Less Than (<) → version should be less than 0.6.0

// Semicolon (;) → indicates the end of the statement
```

---

### Challenge

> Create an empty Solidity contract Without AI

```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.5.0 <0.6.0; // Version

contract ZombieFactory {

    // code here

}
```
---
## Variables & Data Types

### State Variables

State variables are variables that are **permanently stored on the blockchain** (contract storage).
They are declared inside a contract but outside of functions.

* Stored on-chain
* Persist between function calls
* Gas expensive (because they use storage)

**Example:**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StateExample {

    uint public count = 10; // State variable
    string public name = "Zombie"; // State variable

}
```

---

### Dynamic Variables

Dynamic variables are variables whose **size or value can change during execution**.
They are commonly used with arrays, strings, or memory-based variables inside functions.

* Not fixed in size
* Can grow or shrink
* Often used in **memory** or **calldata**
* Cheaper than storage when used locally

**Example:**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DynamicExample {

    uint[] public numbers; // Dynamic array (state variable)

    function addNumber(uint _num) public {
        numbers.push(_num); // Dynamically adds values
    }

    function getNumbers() public view returns (uint[] memory) {
        return numbers; // Returns dynamic array
    }
}
```

---

### Key Differences

| Feature          | State Variable       | Dynamic Variable                |
| ---------------- | -------------------- | ------------------------------- |
| Storage Location | Blockchain (storage) | Memory / Calldata / Storage     |
| Lifetime         | Permanent            | Temporary (if inside functions) |
| Gas Cost         | High                 | Lower (if memory-based)         |
| Size             | Fixed or dynamic     | Usually dynamic                 |

---

### Combined Example

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Example {

    // State Variables
    uint public total = 0;
    uint[] public values; // Dynamic state variable

    function addValue(uint _val) public {

        // Dynamic Variable (local - memory)
        uint temp = _val * 2;

        values.push(temp); // Updating dynamic array
        total += temp;
    }
}
```

---

### Summary

* **State variables** → Stored permanently on blockchain
* **Dynamic variables** → Flexible size, often used in arrays, strings, or inside functions
* You can also have **dynamic state variables** like dynamic arrays (`uint[]`)

This combination is very common in real-world smart contracts.

1. **Local Variables**
   These variables are defined inside the contract and are only accessible within that contract.

2. **Global Variables**
   These variables are defined at the file level (outside contracts). They can be accessed across multiple contracts within the same file, such as `contract_1` and `contract_2`.

---

### Integer Types

* **Unsigned Integers (`uint`)**
  Store only positive values (no negative numbers).
  Examples: `uint8`, `uint16`, `uint32`, `uint256`

* **Signed Integers (`int`)**
  Can store both positive and negative values.

> **Note:** If no size is specified, Solidity defaults to `uint256`.

---

### Challenge

> Assign the number `16` to `zombieDna` using an unsigned integer.

```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.5.0 <0.6.0; // Version

contract ZombieFactory {

    uint dnaDigits = 16;

}
```

---

### Common Solidity Data Types

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DataTypes {

    uint256 public num = 10; // Unsigned integer
    int public num2 = 12; // Signed integer
    bool public isActive = true; // Boolean (true/false)

    address public myAddress = 0x123; // Blockchain address

    uint8[] public dynamicArray; // Dynamic array
    uint8[2] public fixedArray; // Fixed-size array

    // Custom data type using struct
    struct Person {
        uint age;
        string name;
    }

    // Using the custom data type
    Person public person = Person(26, "Kuldeep");

}
```

---

### Structs (Custom Data Types)

* Structs allow you to create your own data types.
* They can hold multiple values of different types in a single structure.
* Useful for organizing related data.

**Example:**
The `Person` struct combines `age` and `name` into one custom type.
