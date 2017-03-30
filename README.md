# obfus-value

The obfuscation annoations for value.

We knew `proguard` could obfuscate symbols, but it can not obfuscate the value.
Basically, we used to obfuscate values manually. But it's very routine. We should generate an obfuscator for obfuscating constants.

## Usage

Before:

```java
public class Constant {
  public static final String PASSWORD = Base64.decode("cGFzc3dvcmQ="); // Obfuscate "password" manually avoid plain-text after decompiled
}
```

After:

```java
@ObfuValue
public abstract class Constant {
  @ObfuValue("password")
  public String password();
  public static Constanct create() { new ObfusValue_Constant(); }
}

System.out.println(Constant.create().password());
```

Generated:

```java
public class ObfusValue_Constant extends Constant {
  @Override
  public String password() { return Obfucator.decode("cGFzc3dvcmQ="); }
}
```
