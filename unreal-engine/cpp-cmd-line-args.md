# UE4 Command Line Args Notes
- Use `FCommandLine::Get()` to get whole launched command line string
- Use `FParse::Value` to get command line argument value
## Usages / Different notation
### Using equal sign
```bat
:: command
UE4Editor.exe "C:\Project\TestProject.uproject" -game --custom-arg=testValue
```
```cpp
// .cpp
FString ParsedValue;
FParse::Value(FCommandLine::Get(), TEXT("--custom-arg="), ParsedValue)

// Result
// ParsedValue = "testValue"
```
### Using spaces
```bat
:: command
UE4Editor.exe "C:\Project\TestProject.uproject" -game --custom-arg testValue
```
```cpp
// .cpp
FString ParsedValue;
FParse::Value(FCommandLine::Get(), TEXT("--custom-arg"), ParsedValue)

// Result
// ParsedValue = "testValue"
```

## Experiences
- Had a bug where I'm not getting the expected command line arguments because of using different notations on both command and parsing
