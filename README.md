
# STON-Specification
A specification for Strictly Typed Object Notation.

### Advantages over JSON
* Significant Performance Optimization
* Enforces Strict Typing
* Simplifies Schema Enforcement
* Slight Reduction In Data Overhead
* Simplifies Development in Strictly Typed Environments

### Disadvantages
* May be confusing to developers without strict typing experience.

# STON Full-Object Archetype.
A .ston format is similar to JSON, but each type is preceeded with a cast in quotes.

	(s)[]    Array (Strings)
	(#)[]    Array (Numbers)
	(o)[]    Array (Objects)
	(s,s){}  Dictionary <String, String>
	(s,#){}  Dictionary <String, Numeric>
	(s,o){}  Dictionary <String, Object>
	(#,s){}  Dictionary <Number, String>
	(#,o){}  Dictionary <Number, Object>
	(#,#){}  Dictionary <Number, Number>

NOTE: The "#" character represents numeric options (byte, int, long, etc) as 1, 2, 4, 8, 16, 32, or 64.

### Character Representations:

	 s   string
	 o   object
	 
	 1   bit
	 2   dibit
	 4   nibble
	 8   byte
	 16  short
	 32  int
	 64  long


### Notes about STON Formatting

1. Whitespace is trimmed in both keys and values.

2. Backslashes will escape characters, including for forced whitespace and commas.

3. Trailing commas are allowed.


# STON Examples

An array of strings:

	(s)[Hello,Goodbye,Come Again,How are you?,Excellent!,Bravo]
	
An array of bytes (8 bits):
	
	(8)[100,43,75,247,90,61,35]
	
An array of nibbles (4 bites):
	
	(4)[2,15,0,8,3,7,11,13]
	
A Dictionary<string, nibble> rating Meals from 0 to 10.
	
	(s,4){
		Pizza=10,
		Spaghetti=5,
		Soup=7,
	}
	
