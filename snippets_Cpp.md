cpp.snippets file:

```


	extends c

	###########################################################################
	#                             Snippets                                    #
	###########################################################################
	# $0 is the last tabstop
	# ${1:default} tabstop 1 with default value
	# '!p' is python completion
	# '!v' is vimScript completion



	###########################################################################
	snippet mbh "MB header file"
	//
	//  File: `!p snip.rv = fn`
	//  Description: ${0:Enter description of code}
	//  Created: `!v strftime("%c")`
	//  Copyright MB
	//
	//==================================================================

	#ifndef ${1:`!p
	if not snip.c:
		import string
		name = re.sub(r'[^A-Za-z0-9]+','_', snip.fn).upper()
		snip.rv = ('%s' % (name,)).upper()
	else:
	    snip.rv = snip.c`}
	#define $1

	#include <memory>  // unique_ptr

	//==================================================================
	class ${2:`!p snip.rv = snip.basename`}
	{
	public:
		explicit $2(int param);
		explicit $2(): $2( 0 ){}      	// delegating ctor

		// copy ctor, copy assignment operator,
		// move ctor, move assignment operator, and
		// destructor are not declared
		// If you declare one or more, default the rest

		// dtor
		//virtual ~$2() = default;
		// copy ctor
		//$2(const $2&) = default;            
		// assignment operator
		//$2& operator=(const $2&) = default;     
		// move ctor
		//$2($2&& ) = default;            
		// move assignment op
		//$2& operator=($2&& ) = default;     

		virtual auto getValue1() const -> int;

	private:
		int value1 {0};
		std::unique_ptr<int> value2;
	};

	#endif /* $1 */
	endsnippet


	###########################################################################
	snippet mbc "MB cpp file"
	//
	//  File: `!p snip.rv = fn`
	//  Description: ${0:Enter description of code}
	//  Created: `!v strftime("%c")`
	//  Copyright MB
	//
	//==================================================================

	#include "${1:`!p snip.rv = snip.basename + '.h'`}"

	namespace   
	{

	}


	//==================================================================
	${2:`!p snip.rv = snip.basename`}::$2(int param = 0)
	    :value1{param},
		value2{std::make_unique<int>(0)}
	{

	}

	//==================================================================
	auto $2::getValue1() const -> int
	{
	    return value1;
	}

	endsnippet


	###########################################################################
	snippet forl "for loop"
	for (int ${1:loopVar}{0}; $1<${2:limit}; ++$1)
	{
		${0}
	}
	endsnippet

	###########################################################################
	snippet forr "c++11 range for loop"
	for (const auto& ${1:refval}: ${2:arr})
	{
		${0:total += refval;}
	}
	endsnippet

	###########################################################################
	snippet fore "c++11 for_each"
	// #include <algorithm>, #include <iterator>, range of seq doesn't have to be begin and end
	std::for_each( std::begin(${1:sequence}), std::end($1), ${0:fcn_to_apply_to_range} );
	endsnippet

	###########################################################################
	snippet enumc "c++11 enum class"
	// #include <cstdint> for uint8_t
	// access with Enum_name::enum1
	enum class ${1:Enum_name} : ${2:uint8_t}        
	{
	    ${0:enum1},

	};
	endsnippet

	###########################################################################
	snippet lambda "c++11 lambda"
	// capture can be: blank, this, a var a by value, &a var a by ref
	//	&  all auto vars in body by ref, =  all auto vars in body by value
	${1:auto ${2:lambdafcn} = }[ ${3:capture,} ]( ${4:opt fcn_params_decl,} ){ ${0:return stmt;} }${5:( opt fcn_params)};
	endsnippet


	###########################################################################
	snippet func "trailing return type fcn"
	auto ${1:funcName}(double a, double b) -> decltype(a + b);
	endsnippet

	###########################################################################
	snippet templatefunc "trailing return type fcn template"
	template <typename ${1:type1}, typename ${2:type2}>
	auto addNumbers($1 a, $2 b) -> decltype(a + b);
	endsnippet


	###########################################################################
	snippet wrap{} "wrap block with {}, visual select, tab, trigger"
	{
	    ${0:${VISUAL:...}}
	}
	endsnippet


	###########################################################################
	snippet mbhp "MB header with ptr to implementation (pimpl)"
	//
	//  File: `!p snip.rv = fn`
	//  Description: ${0:Enter description of code}
	//  Created: `!v strftime("%c")`
	//
	//  Copyright MB
	//
	//==================================================================

	#ifndef ${1:`!p
	if not snip.c:
		import string
		name = re.sub(r'[^A-Za-z0-9]+','_', snip.fn).upper()
		snip.rv = ('%s' % (name,)).upper()
	else:
	    snip.rv = snip.c`}
	#define $1

	#include <memory>  // unique_ptr

	//==================================================================
	class ${2:`!p snip.rv = snip.basename`}
	{
	public:
		explicit $2(int sz);
		explicit $2(): $2( 512 ){}      	// delegating ctor

		// copy ctor, copy assignment operator,
		// move ctor, move assignment operator, and
		// destructor are not declared
		// If you declare one or more, default the rest

		// dtor
		//virtual ~$2() = default;
		// copy ctor
		//$2(const $2&) = default;            
		// assignment operator
		//$2& operator=(const $2&) = default;     
		// move ctor
		//$2($2&& ) = default;            
		// move assignment op
		//$2& operator=($2&& ) = default;     

		virtual auto getSize_buf() const -> size_t;


	private:
		class Impl; 			// forward decl of implementation

		std::unique_ptr<Impl, void (*)(Impl*)> pImpl;   
		// custom deleter is a function that takes a pointer to Impl, returns void

	};

	#endif /* $1 */
	endsnippet


	###########################################################################
	snippet mbcp "MB cpp with ptr to implementation (pimpl)"
	//
	//  File: `!p snip.rv = fn`
	//  Description: ${0:Enter description of code}
	//  Created: `!v strftime("%c")`
	//
	//  Copyright MB
	//
	//==================================================================

	#include "${1:`!p snip.rv = snip.basename + '.h'`}"

	namespace          
	{

	}

	//==================================================================
	class $2::Impl
	{
	public:
		size_t size_buf = 512;
		Impl( size_t sb ) :size_buf{ sb }
		{

		}

		auto getSize_b() -> size_t
		{
			return size_buf;
		}

	};

	//==================================================================
	${2:`!p snip.rv = snip.basename`}::$2(int sz=512)
		:pImpl{
				new Impl{ sz },
				[](Impl* impl){ delete impl; }	// custom deleter lambda
			}
	{

	}

	//==================================================================
	auto $2::getSize_buf() const -> size_t
	{
		return pImpl->getSize_b();
	}

	endsnippet


```
