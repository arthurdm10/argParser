## Dependencies
* fmtlib: https://github.com/fmtlib/fmt

## Example
```c++
#include "argparser.h"

int main(int argc, char **argv)
  auto argParser = ArgParser("This is the program description");

	argParser.addArg("arg1", "This is a required argument", true);
	argParser.addArg("arg2", "Another required argument", true);
	argParser.addArg("arg3", "This is an optinal argument", false);
	argParser.addArg("arg4", "Another optinal argument", false);

	argParser.parseArguments(argc, argv);

	//get argument as a string
	auto arg1 = argParser.get("arg1");
	std::cout << arg1 << "\n";

	//get as an int
	auto arg2 = argParser.get<int>("arg2");
	std::cout << arg2 << "\n";

	if (argParser.isSet("arg3")) {
		auto arg3 = argParser.get<double>("arg3");
		std::cout << arg3 << "\n";
	}

	if (argParser.isSet("arg4")) {
		auto arg4 = argParser.get<char>("arg4");
		std::cout << arg4 << "\n";
	}
}

```

```
./sample --help

This is the program description
        --help: Display this message

[::] Required arguments
         --arg1: This is a required argument

         --arg2: Another required argument

[::] Optional arguments
         --arg3: This is an optinal argument

         --arg4: Another optinal argument

```
