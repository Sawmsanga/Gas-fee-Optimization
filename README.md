# Gas-fee-Optimization

1.IMMUTABLE KEYWORD

    It allows you to delcare contract level variable which gets stored in the code rather than storage. However,contrary to a
    standard variable it's not possible to change its value later.With a standard storage variable,every time you read it you
    have to call the SLOAD opcode which costs approximately 2100 gas.However,when you read an immutable variable it just reads
    as a constant from the stack that is done using the PUSH32 opcode which only costs 3 gas.So,if you have a storage variable
    that is not going to change,use the immutable keyword.


2. ARRAYS AS ARGUMENTS

     When you pass an array to an external function,you can either declare it as call data which means it's taken directly from
     the transaction payload which is immutable or memory which means that you can manipulate the array in your code but it takes
     more gas because the EVM has to first copy your code from code data to memory.If you are just going to read this array after
     and don't need to manipulate it,use code data it will cost less gas.

3.MODIFIER

    When you use a modifier the whole code of the modifier is repeated every time it's used.To minimize the deployment cost of
    your contract, instead you can create an internal function with the code of the modifier and call it from the other functions
    who need it.The only downside is that it adds a jumpop when you execute each function but it's a negligible gas cost.

