# obfus-value

obfuscation annoations for value.

## Usage

Before:

```java
public static final String PASSWORD = Base64.decode("cGFzc3dvcmQ="); // "password"
```

After

```java
@ObfuValue
public static final String PASSWORD = "password";
```
