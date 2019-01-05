### Files and layout
* Use a .h header file extension
* Use a .cpp source file extension
* File description comments for header and source files
  * Don't write a version number or a list of modifications. It is tedious to maintain; do that in Git or other revision control

		//
		// Sample.h or Sample.cpp
		// Project name
		//
		// Description
		//
		// Created by x on date
		// Copyright (c) year organization
		//

* Use an include guard in header files
  * Rationale: To prevent including a header file more than once

		#ifndef SAMPLE_H
		#define SAMPLE_H
		.
		.
		#endif    // SAMPLE_H

* If possible, forward declare classes in header files instead of using an #include (move the #include to the source file) [[1](#ref)]

* No tab characters, indentation is 4 spaces
  * Rationale: Various editors may have different default tabstop widths.
  * use these Vim settings to substitute 4 spaces for a tab keypress [[2](#ref)]

		:set tabstop=4
		:set shiftwidth=4
		:set expandtab

* Pointer declaration: group the asterisk * with the type

		int* pointer;

* Reference declaration: group the ampersand & with the type

		int a {1};
		int& reference {a};

* Use Allman style indentation [[3](#ref)]
  * Rationale: Personal opinion that it is easy to read and to match braces

		if (condition)
		{
			statement;
		}
		else if (condition)
		{
			statement;
		}
		else
		{
			statement;
		}

* Use braces around blocks of code that follow control or conditional statements (e.g., if, else if, else, for, while) <br>
  * Rationale: Unbraced one line control or conditional statements may lead to bugs after a code change or version control merge <br>
  Apple's goto fail SSL bug could have been prevented by following this rule [[4](#ref)]
  * Counterargument: No braces keeps code compact, which can improve readability if an entire code block can be viewed on the screen


### Naming convention
* Use CapWords (UpperCamelCase) for classes, enumerations, and typedefs
* Use camelCase for variables
* Use ALL_CAPS for named constants
* Accessor methods use a get or set prefix
  * not every member needs a getter and setter
* Don't prefix class members with a m_
  * use this->memberVariable to differentiate between a parameter name and a member variable with the same name
  * the compiler should be able to tell the difference in a class initializer list if the parameter and member variable names are the same
* single character names like i, j, k can be used for iterators and loop counters
  * in general, prefer to use a more descriptive name

### Namespaces
* Don't indent namespace blocks
* Don't use using directives and using declarations in header files
  * Rationale: to avoid bringing namespace identifiers into scope for files that include that header, which can lead to name conflicts
  * Instead, use only fully qualified names in a header file (i.e., the word "using" should not be in any header file)
* In .cpp source files, use a using declaration to bring in specific identifiers instead of a using directive that brings the entire namespace into scope

		// Sample.cpp
		.
		.
		.
		// Avoid a using directive
		// using namespace std;

		// Prefer a using declaration
		using std::cout;
		using std::endl;

### Statements
* Use a separate line for each variable declaration or expression statement
* Use named constants or enumerated types instead of literals (magic numbers)
  * a 0 or 1 is OK for initial loop or array counters

		// avoid the hard-coded "6"
		for (int cubeFace {0}; cubeFace < 6; ++cubeFace)    
		{
			...
		}

		// preferred
		namespace
		{
		const int MAX_CUBE_FACES {6};    
		}
		.
		.
		.
		for (int cubeFace {0}; cubeFace < MAX_CUBE_FACES; ++cubeFace)
		{
			...
		}

* Declare local variables as late as possible to minimize scope
* When calling a function that returns a pointer, place it inside a conditional
  * This is similar to the optional binding syntax (if let) in the Swift programming language [[5](#ref)]
  * Rationale: Minimizes the scope of the pointer and avoids dereferencing the pointer outside of the conditional block

		if (SampleClass* samplePointer = getResource())
		{
			samplePointer->doWork();
		}

		// can't dereference samplePointer here



### Functions
* Use the trailing return type style
  * Rationale: Allows for function templates, and the return type can be specified based on a parameter type

		// function declaration
		auto addInts(int a, int b) -> int;

		// function definition
		auto addInts(int a, int b) -> int
		{
			return a + b;
		}

		// can specify return type based on parameter types that are in scope after the parameter list
		auto addDoubles(double a, double b) -> decltype(a + b);

		// template function
		template <typename FirstNumberType, typename SecondNumberType>
		auto addNumbers(FirstNumberType a, SecondNumberType b) -> decltype(a + b);


### Classes
* definitions belong in the source .cpp file, not the header file
  * Rationale: avoid implicitly inlining a member function [[6](#ref)], [[7](#ref)]
* use the <code>explicit</code> keyword for single parameter constructors to prevent an implicit type conversion [[8](#ref)]
  * unless a conversion is needed in a copy initialization
* data members should be private
* prefix get and set accessors with a 'get' or 'set'
  * mark the getters with a <code>const</code> keyword (at the end of the declaration and the definition)
* apply the rule of zero [[9](#ref)]
  * either:
  	* (preferred) don't declare any special member functions (class ctor is OK)
  	* declare one or more special member functions (copy and move ctors, copy and move assignment operators, destructor) and default or delete the rest
  * use STL containers (such as std::array, std::vector, std::string) instead of C-arrays or C-strings [[10](#ref)]
  * use unique_ptr or shared_ptr instead of raw pointers
  * if the class has any virtual functions, either [[11](#ref)]:
  	* (preferred) store dynamically allocated objects of the derived class using shared_ptr
  	* declare a virtual destructor and default or delete the other special member functions
  	* store dynamically allocated objects of the derived class using unique_ptr with a custom deleter
* use initializer lists in constructor definitions
* use the <code>override</code> identifier to mark a function in a derived class as an override of a virtual function from the base class


---

### References <a id="ref"></a>
1. The Chromium Projects C++ Dos and Don'ts [https://www.chromium.org/developers/coding-style/cpp-dos-and-donts](https://www.chromium.org/developers/coding-style/cpp-dos-and-donts#TOC-Forward-declare-classes-instead-of-including-headers)
2. [http://vim.wikia.com/wiki/Converting_tabs_to_spaces](http://vim.wikia.com/wiki/Converting_tabs_to_spaces)
3. [http://en.wikipedia.org/wiki/Indent_style#Allman_style](http://en.wikipedia.org/wiki/Indent_style#Allman_style)
4. Apple’s #gotofail SSL Security Bug was Easily Preventable [http://embeddedgurus.com/barr-code/2014/03](http://embeddedgurus.com/barr-code/2014/03/apples-gotofail-ssl-security-bug-was-easily-preventable/)
5. Swift Language Guide, Optionals [https://developer.apple.com/library/ios/documentation/Swift](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/TheBasics.html)
6. LLVM Coding Standards [http://llvm.org/docs/CodingStandards.html](http://llvm.org/docs/CodingStandards.html#don-t-use-inline-when-defining-a-function-in-a-class-definition)
7. The Chromium Projects C++ Dos and Don'ts [https://www.chromium.org/developers/coding-style/cpp-dos-and-donts](https://www.chromium.org/developers/coding-style/cpp-dos-and-donts#TOC-Stop-inlining-code-in-headers)
8. Standard C++ Foundation Constructors [https://isocpp.org/wiki/faq/ctors#explicit-ctors](https://isocpp.org/wiki/faq/ctors#explicit-ctors)
9. Flaming Dangerzone, Rule of Zero [http://flamingdangerzone.com/cxx11/rule-of-zero/](http://flamingdangerzone.com/cxx11/rule-of-zero/)
10. Sticky Bits, The rule of zero [https://blog.feabhas.com/2015/01/the-rule-of-zero/](https://blog.feabhas.com/2015/01/the-rule-of-zero/)
11. Ponder the use of unique_ptr to enforce the Rule of Zero [https://marcoarena.wordpress.com/2014/04/12/](https://marcoarena.wordpress.com/2014/04/12/ponder-the-use-of-unique_ptr-to-enforce-the-rule-of-zero/)
