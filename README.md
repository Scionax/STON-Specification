
# STON-Specification
A specification for Strictly Typed Object Notation.

### Advantages over JSON
* Significant Performance Optimization
* Enforces Strict Typing
* Simplifies Schema Enforcement
* Greater Flexibilty
* Slight Reduction In Data Overhead
* Simplifies Development in Strictly Typed Environments

### Disadvantages
* May be confusing to developers without strict typing experience.


# STON Files
A basic STON implementation would include just the .ston file type, which can stand alone and fulfill all strict typing requirements.

However, a complete implementation would include every STON file type (.array, .map, .dict, etc.) for its full benefit.

Using these STON files allows code to eliminate additional tags and lookups, and are useful particularly in application development, configurations, user settings, dictionaries, and APIs.


### STON Array Files.
These files have no tags or delimiters directly in the code; just the array bytes due to fixed length.
Editors can optionally choose to show delimiters (or a GUI) if they're removed on save.
Since this is an array, editors will not allow changing the count.

	.array1:   An array of booleans.
	.array2:   An array of dibits (2 bits).
	.array4:   An array of nibbles (4 bits).
	.array8:   An array of bytes (8 bits).
	.array16:  An array of shorts (16 bits).
	.array32:  An array of integers (32 bits).
	.array64:  An array of longs (64 bits).

### STON List Files.
Identical behavior to arrays, except these are not fixed in length. Editors can modify the count.

	.list1:   A List<bool>.
	.list2:   A List<dibit>.
	.list4:   A List<nibble>.
	.list8:   A List<byte>.
	.list16:  A List<short>.
	.list32:  A List<int>.
	.list64:  A List<long>.

### STON Immutable Array Files.
Identical to Arrays, except these are immutable. Editors should disallow modification of the file. Considered read-only.

	.imm1:   An Immutable Array<bool>.
	.imm2:   An Immutable Array<dibit>.
	.imm4:   An Immutable Array<nibble>.
	.imm8:   An Immutable Array<byte>.
	.imm16:  An Immutable Array<short>.
	.imm32:  An Immutable Array<int>.
	.imm64:  An Immutable Array<long>.

### STON Delimited List Files.
These files are nearly identical to those above, but have delimiters (and longer read times) due to the dynamic sizing of the mapped types.

	.array:  An array of strings.
	.arrayo: An array of objects.
	.list:   A List<string>.
	.list:   A List<objects>.
	.imm:    An Immutable Array<string>.
	.immo:   An Immutable Array<objects>.
	
### STON Dictionaries <string, MAPTYPE>
Stored as a Key-Value pair (e.g. Key=Value) with Equal Sign (=) as a key delimiter and Newline as entry delimiter. Ordered Dictionary.

	.dict:    A <string, string> Dictionary.
	.dicto:   A <string, object> Dictionary.
	.dict1:   A <string, bool> Dictionary.
	.dict2:   A <string, dibit> Dictionary.
	.dict4:   A <string, nibble> Dictionary.
	.dict8:   A <string, byte> Dictionary.
	.dict16:  A <string, short> Dictionary.
	.dict32:  A <string, int> Dictionary.
	.dict64:  A <string, long> Dictionary.

### STON Dictionaries <numeric, MAPTYPE>
Identical to .dict files, except key is numeric, and value is assigned to MAPTYPE.

	.map2_:   A <dibit, MAPTYPE> Dictionary>.
	.map4_:   A <nibble, MAPTYPE> Dictionary>.
	.map8_:   A <byte, MAPTYPE> Dictionary.
	.map16_:  A <short, MAPTYPE> Dictionary.
	.map32_:  A <int, MAPTYPE> Dictionary.
	.map64_:  A <long, MAPTYPE> Dictionary.

MAPTYPE is assigned based on the prefix of the filename. (e.g. map8_s is <byte, string>, map8_o is <byte, object>)

	 s   string
	 o   object
	 2   dibit
	 4   nibble
	 8   byte
	 16  short
	 32  int
	 64  long

### STON Full-Object Archetype.
The full .ston file that encorporates all of the previous types into a single object. Similar to JSON styling, but with strong typing.

	.ston
		{s   }   Dictionary (String)
		{#   }   Dictionary (Numeric)   // # is equal to 1, 2, 4, 8, 16, or 32
		{o   }   Dictionary (Objects)
		[s   ]   Array (String)
		[#   ]   Array (Numeric)        // # is equal to 1, 2, 4, 8, 16, or 32
		[o   ]   Array (Objects)
		[ls  ]   List (String)
		[l#  ]   List (Numeric)         // # is equal to 1, 2, 4, 8, 16, or 32
		[lo  ]   List (Objects)
		[fs  ]   Fixed Array (String)
		[f#  ]   Fixed Array (Numeric)  // # is equal to 1, 2, 4, 8, 16, or 32
		[fo  ]   Fixed Array (Objects)
		<m#  ?>  Map (to Strings)       // # is equal to 1, 2, 4, 8, 16, or 32; ? is equal the MAPTYPE character.
		<m#  ?>  Map (to Objects)       // # is equal to 1, 2, 4, 8, 16, or 32; ? is equal the MAPTYPE character.
