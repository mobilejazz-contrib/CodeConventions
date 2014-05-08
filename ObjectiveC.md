### Mobile Jazz 
# Objective-C Code Conventions
---
In this document we describe the basic code conventions to follow when working in a **Objective-C** & **Cocoa** environment. The Mobile Jazz team is encouraged to follow this document in order to conceive and develop similar code.

#Summary
1. Code Basics

	1.1 Word Spacing
	
	1.2 Brakets
	
	1.3 New Lines
	
2. Code Architecture

	2.1 Classes
	
	2.2 Protocols
	
	2.3 Categories
	
	2.4 General Recommendations

3. Xcode Project

4. Repository

---
##1. Code Basics

###1.1 Words spacing


- **Variable declaration**: Always space between type and pointer and no space between pointer and var name. Do `TYPE *var`, never `TYPE* var`, `TYPE * var` nor `TYPE*var`.
- **Statements**: Spaces between the key words and the parentesis. `if (cond) `, `while (cond)`, `for (...)`, `switch (var)`.
- **Operations**: Spaces are optional. Both `valueA + valueB == valueC` and `value+value==valueC` are accepted. Use comon sense to write the most readable code. 
- **Parentesis**: No spacing between parentesis and next char. Do `valueA * (valueB + valueC)`, never `valueA * ( valueB + valueC )`. Nested parentesis should follow the same rule. Do `floor((valueA + valueB)/valueC)` and not `floor( (valueA + valueB)/valueC )`.
- **Method return signature**: Add one space between the dash and the parentesis and no space between the parentesis and the begining of the method name. Do `- (NSInteger)myMethod` and not `-(NSInteger) myMethod`, `-(NSInteger)myMethod` nor `- (NSInteger) myMethod`.
- **Objective-C directives**: Add always one space after any Objective-C directive. Do `@property (nonatomic)` and not `@property(nonatomic)`.
- **Properties**: Add always one coma and one space after each property descriptor. Do `@property (nonatomic, strong)` and not `@property (nonatomic,strong)`. 
- **Indentation**: Use always spaces instead of tabs and with a length of 4 sapces.
 

###1.2 Brakets

Brakets will be placed always in a new line, alone. Opening brakets and closing brakets will be aligned vertically.

`method` declaration:

    - (id)methodWithValue:(int)value
    {
    	// Code here
    }

`if` statement:

    if (condition)
    {
    	// Code here
    }
    
`for` statement:

    for (NSSring *string in array)
    {
    	// Code here
    }
    
`while` statement:

    while (condition)
    {
    	// Code here
    }
    
And the same pattern used on `switch`, `@try` and `@catch`, etc.

The only exception is when using Blocks, that the opening braket will be allowed to be placed in the same line as the block signature.

    void (^myBlock)() = ^{
    
    };

###1.3 New lines

- The goal is to write code the most vertically spaced possible with the minimum number of empty lines. We will add empty lines only when it will help to separate blocks of code semantically.

- Also, use "brakets" as a spacing tool (each braket is placed in a line without any other characters). It Will help us give some additional space.

- In olders times editors used to wrap lines after 80 characters. In Objective-C we won't ever break a single line for this reason.

---
##2. Code Architecture

###2.1 Classes

###2.2 Protocols

###2.3 Categories

###2.4 General Recomendations

---
##3. Xcode Project


---
##4. Repository

