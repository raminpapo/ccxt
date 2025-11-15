# Documentation: cs/ccxt/static/StarkSharp/StarkSharp.Platform/Platform.cs

## File Metadata

- **Path**: `cs/ccxt/static/StarkSharp/StarkSharp.Platform/Platform.cs`
- **Size**: 1,513 bytes
- **Lines**: 24
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Numerics;
// using StarkSharp.Connectors.Components;
// using StarkSharp.Rpc;
// using StarkSharp.Tools.Notification;

namespace StarkSharp.Platforms
{
    public class Platform
    {
        public enum PlatformName { CryEngine, Unity, Godot, Dotnet }
        public enum PlatformConnectorType { WebGL, Sharpion, HTML5, RPC }
        public virtual void ConnectWallet(string walletType, int id) { }
        public virtual void SendTransaction(string walletType, int id, string contractAddress, string entryPoint, string callData) { }
        // public virtual void SendTransaction(Platform platform, TransactionInteraction transactionInteraction, Action<JsonRpcResponse> successCallback, Action<JsonRpcResponse> errorCallback) { }
        // public virtual void CallContract(ContractInteraction contractInteraction, Action<string> successCallback, Action<string> errorCallback) { }
        public virtual void WaitUntil(int id, Action<string> successCallback, Action<string> failCallback, Func<bool> predicate, Action<int, Action<string>, Action<string>> action) { }
        public virtual bool CheckWalletConnection() { return true; }
        public virtual string GetAccountInformation() { return string.Empty; }
        public virtual void DebugMessage(string message) { }
        // public virtual void PlatformRequest(JsonRpc requestData, Action<JsonRpcResponse> Callback) { }
        // public virtual void PlatformLog(string LogMessage, NotificationType notitype) { }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/StarkSharp/StarkSharp.Platform/Platform.cs`.

**Classes defined**: Platform



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 16
- Comment lines: 7
- Blank lines: 1

### Main Components

**Classes** (1):
- `Platform`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

