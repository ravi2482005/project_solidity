# project_solidity

// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       What to do:
     Contract contains:
     1. public variables storing details about dummy coin (Token Name, Token Abbrv., Total Supply)
     2.  mapping function [addresses to balances (address => uint)]
     3. a mint function taking two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here
    string public tokenName = "Token";
    string public tokenAbbriv = "Tok";
    uint256 public totalSupply = 0;

    // mapping variable here
    mapping (address => uint) public balances;

    // mint function
    function mint (address _address , uint256 _value) public {
       totalSupply += _value;
       balances[_address] += _value;
    }
    // burn function
    function burn (address _address , uint256 _value) public {
       if (balances[_address] >= _value) {
       totalSupply -= _value;
       balances[_address] -= _value;
       }
    }
}
