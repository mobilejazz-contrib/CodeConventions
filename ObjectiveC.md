### Mobile Jazz 
# Objective-C Code Conventions
---
In this document we describe the basic code conventions to follow when working in a **Objective-C** & **Cocoa** environment. The Mobile Jazz team is encouraged to follow this document in order to conceive and develop similar code.

Mainly, we are going to follow the [Coding Guidelines for Cocoa](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html#//apple_ref/doc/uid/10000146-SW1). However, in this document we are going to describe the main guidelines to follow so you can understand fast what and what not to do.

#Summary
1. Code Basics

	1.1 Word Spacing
	
	1.2 Brakets
	
	1.3 New Lines
	
	1.4 Names
	
2. Code Architecture

	2.1 Classes
	
	2.2 Protocols
	
	2.3 Categories
	
	2.4 General Recommendations

3. Xcode Project

4. Repository

5. Useful tools

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

###1.4 Names

Objective-C is a verbose language. Variables, methods, constants and any other named word will have an understandeable and readable name.

- **Be Verbose**: Names must apport semantic meaning of what the attribute, method, constant, etc. does. Do `myVeryImportantVariableKey` and not `impVarKey`.

- **Variable Names**: Start with a lowercase, without underlines (nor dashes or spaces, of curse), and with an uppercase at first letter of each word. Do `myVariable` and not `myvariable`, `my_variable` or `MyVariable`.

- **MethodNames**: As Variable Names, start with a lowercase, without underlines and with a capital letter for each first word letter. Arguments might have a prefix as *with*, *from* or *at*. Use common sense to build a readable method name.

- **Constants**: Constants start with capital letter and may have a prefix describing the procedence of the constant value and a suffix describing the semantic of the constant. For example, for a dictinary key to access a number value do `NSString * const MJDictionaryNumberKey = @"number";` and not `NSString * const number = @"number";`. Do not prefix constants with a `k` letter.

- **Enumerations**: Follow the same guidelines as constants.

---
##2. Code Architecture

###2.1 Classes

###2.2 Protocols

###2.3 Categories

###2.4 General Recomendations

#### Arrays and Dictionaries

You should **always** use modern Objective-C notation for accessing array and dictonary items.

**For example:**
```objc
array[idx] = value;
value = array[idx];

dictonary[key] = value;
value = dictonary[key]
```

**Not:**
```objc
[arr setObject:value atIndexedSubscript:idx];
value = [array objectAtIndex:idx];

[dictonary setValue:value forKey:key];
value = [dictonary objectForKey:key];
```

#### Dot-Notation Syntax

Dot-notation should **always** be used for accessing and mutating properties. Bracket notation is preferred in all other instances.

**For example:**
```objc
view.backgroundColor = [UIColor orangeColor];
[UIApplication sharedApplication].delegate;
```

**Not:**
```objc
[view setBackgroundColor:[UIColor orangeColor]];
UIApplication.sharedApplication.delegate;
```

#### Singletons

Singleton objects should use a thread-safe pattern for creating their shared instance.
```objc
+ (instancetype)sharedInstance 
{
   static id sharedInstance = nil;

   static dispatch_once_t onceToken;
   dispatch_once(&onceToken, ^{
      sharedInstance = [[self alloc] init];
   });

   return sharedInstance;
}
```
This will prevent [possible and sometimes prolific crashes](http://cocoasamurai.blogspot.com/2011/04/singletons-your-doing-them-wrong.html).

---
##3. Xcode Project

* The project should have 0 warnings.
* The physical files should be kept in sync with the Xcode project files in order to avoid file sprawl. Any Xcode groups created should be reflected by folders in the filesystem. Code should be grouped not only by type, but also by feature for greater clarity.
* Evaluate third-party dependencies before adding them. 

---
##4. Repository

---
##5. Useful tools
You can use this [XCode plugin](https://github.com/benoitsan/BBUncrustifyPlugin-Xcode) to format your code using [Uncrustify](https://github.com/bengardner/uncrustify).

You can use the following [uncrustify config file](https://github.com/mobilejazz/CodeConventions/tree/master/ObjectiveC) to format your files using the Mobilejazz code conventions.

