---
-api-id: M:Windows.Data.Json.JsonObject.GetNamedString(System.String,System.String)
-api-type: winrt method
---

<!-- Method syntax
public string GetNamedString(System.String name, System.String defaultValue)
-->

# Windows.Data.Json.JsonObject.GetNamedString

## -description
Gets the [String](https://msdn.microsoft.com/library/system.string.aspx) value with the specified name, or the provided default value if no such named value is found.

## -parameters
### -param name
The name.

### -param defaultValue
The default value to use if the JSON property is not found.

## -returns
The [String](https://msdn.microsoft.com/library/system.string.aspx) with the specified *name*, or if this value wasn't found, the *defaultValue* is returned.

## -remarks
This method should always used with a try/catch block because it throws an exception if the name is not found.

## -examples

## -see-also
[GetNamedString(String)](jsonobject_getnamedstring_409995224.md)