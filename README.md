Git hook to prevent commits containing temporary or debug code.

Any comment beginning with ```//!!! ``` will prevent code from being commited. (Thanks [Ed George](https://github.com/ed-george) for the syntax suggestion)

#Example

In the case of the following function:

```
bool hasErrorOccurred(){
	// Logic to determine whether error has occurred
} 
```

The developer may be tempted to modify the code in order to test the application:

```
bool hasErrorOccurred(){
	return true;
	// Logic to determine whether error has occurred
} 
```

Flagging this code as temporary will prevent it from being accidentally committed:

```
bool hasErrorOccurred(){
	//!!! It would be a bad idea to commit this!
	return true;
	// Logic to determine whether error has occurred
} 
```

#Supported languages

Any language that defines a comment as starting with ```//``` can be supported, although the file extension must be added to the shell script.

Currently: C, C++, Objective-C, Objective-C++, Swift, Java

#Installation

Be aware that you can only have a single pre-commit script, so you should check for the existance of ```.git/hooks/pre-commit``` to ensure that you are not overwriting your existing script.

```
cd your_project_root
curl https://raw.githubusercontent.com/SteveBarnegren/DontCommit/master/pre-commit -o .git/hooks/pre-commit && chmod u+x .git/hooks/pre-commit
```