---
_layout: landing
---

# James Consulting Core Library

The **James Consulting Core Library** is a collection of essential utilities, constants, and helpers designed to accelerate .NET application development. It provides reusable components for common tasks, helping teams build robust, maintainable, and scalable solutions faster.

## Features

- Common constants and configuration helpers
- Utility methods for strings, enums, streams, and objects
- Extensions for reflection and diagnostics
- Designed for performance and reliability
- Well-documented API

## Installation

Install via NuGet:

```shell
Install-Package JamesConsulting.Core
```
Or with .NET CLI:
```shell
dotnet add package JamesConsulting.Core
```

## Usage Examples

Round-trip a string to bytes and back:
```csharp
using JamesConsulting;

var bytes = "Test".GetBytes();
var roundTrip = bytes.GetString(); // "Test"
```

Convert a name to title case:
```csharp
using JamesConsulting;

var title = "rudy james".ToTitleCase(); // "Rudy James"
```

Truncate a string:
```csharp
using JamesConsulting;

var truncated = "testing".Truncate(4); // "test"
```

Get an enum member description:
```csharp
using System.ComponentModel;
using JamesConsulting;

private enum MyOptions
{
    [Description("Testing")] With,
    Without
}

var desc1 = MyOptions.With.GetDescription();    // "Testing"
var desc2 = MyOptions.Without.GetDescription(); // "Without"
```

Check if a stream contains an executable header:
```csharp
using System.IO;
using System.Text;
using JamesConsulting.IO;

using var ms = new MemoryStream();
using var writer = new BinaryWriter(ms, Encoding.UTF8, leaveOpen:true);
writer.Write('M');
writer.Write('Z');
writer.Flush();
var isExe = ms.IsExecutable(); // true
```

Convert a string to a SecureString and back:
```csharp
using JamesConsulting.Security;

var secure = "secret".ToSecureString();
var plain = secure.ConvertToString(); // "secret"
```

Serialize an object to a JSON stream and deserialize:
```csharp
using System.IO;
using JamesConsulting;
using JamesConsulting.IO;

var obj = new { Name = "Rudy", Value = 3 };
using var ms = new MemoryStream();
obj.SerializeToJsonStream(ms);
var clone = ms.Deserialize<dynamic>();
```

For full API documentation, browse the navigation menu or explore the generated API reference.