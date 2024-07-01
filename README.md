### Overview

This PowerShell script demonstrates advanced techniques including shellcode injection, dynamic function invocation, and PowerShell script obfuscation. Let's break down its components:


### Native Function Lookup and Invocation

#### `LookupFunc` Function

This function is responsible for dynamically locating and invoking native functions from the Windows API (`kernel32.dll`). Here's how it works:

- It first retrieves the `Microsoft.Win32.UnsafeNativeMethods` type from the loaded assemblies.
- Using reflection, it finds methods like `GetProcAddress` and `GetModuleHandle`.
- It attempts to invoke `GetProcAddress` to retrieve the memory addresses of functions like `VirtualAlloc`, `CreateThread`, and `WaitForSingleObject` from `kernel32.dll`.

#### `getDelegateType` Function

This function is used to create a custom delegate type dynamically. It defines a delegate that matches the signature of the native functions being invoked.

### Shellcode Execution

- **VirtualAlloc**: Allocates memory in the process's virtual address space to store and execute shellcode.
- **CreateThread**: Creates a new thread in the process, starting execution at the address of the allocated shellcode.
- **WaitForSingleObject**: Waits indefinitely for the created thread to finish executing.

### PowerShell Script Obfuscation

#### `Invoke-PsPayCrypt` Function

This function handles the obfuscation of PowerShell scripts:

- If no script path is provided, it prompts the user to enter a path or uses a default path.
- It reads the contents of the specified PowerShell script file (`$Path`), converts it to Base64, and then sorts and shuffles the Base64 string to obfuscate it.
- Generates random variables (`$Var1` and `$Var2`) and constructs an obfuscated PowerShell script that decodes and executes the Base64-encoded script content.
- Saves the obfuscated script to a file with a randomly generated name.
- Use this to obfuscate shellcode.

### Conclusion

This script showcases how PowerShell can be used for both offensive (shellcode injection) and defensive (script obfuscation) purposes, illustrating the flexibility and power of the language in automation, administration, and unfortunately, exploitation contexts.


## With PsPayCrypt:
![image](https://github.com/EvilBytecode/Shellcode-Loader/assets/151552809/599e1cb0-b05f-48ee-9edb-22ee3c2f878d)

## Without
![image](https://github.com/EvilBytecode/Shellcode-Loader/assets/151552809/2b56a290-d287-4289-a8fb-1b1df11e084e)


