Coding conventions serve the following purposes: 

- They create a consistent look to the code, so that readers can focus on content, not layout. 
- They enable readers to understand the code more quickly by making assumptions based on previous experience. 
- They facilitate copying, changing, and maintaining the code.
- They prevent discussions about coding styles.



**Merge requests that do not follow these guidelines will be rejected.**



These guidelines are based on the [C# Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions) and the [Framework Design Guidelines](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/) with some changes.



## Table of contents

[[_TOC_]]

## EditorConfig

A .editorconfig file is used to automatically check for code not following (most of) these guidelines.

Please make sure your coding environment supports [EditorConfig](https://editorconfig.org/).



## API Controllers

All of the API endpoints must follow the REST standard and use the appropriate HTTP response codes.

All of the API endpoints must use singular names: `/api/project/` instead of `/api/projects/`.

Both request- and response- bodies must use resource classes. These classes can be automagically mapped to models using a `ModelMapper`.



* The controller should return a `404 Not Found` status code when a requested resource does not exist. (So not `204 No Content`.)
* The controller should return a `401 Unauthorized` status code when a user is requesting a resource, while not having permission to do so.



## Naming Conventions 

### Capitalization Rules for Identifiers

To differentiate words in an identifier, capitalize the first letter of each word in the identifier. Do not use underscores to differentiate words, or for that matter, anywhere in identifiers. There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:

- PascalCasing
- camelCasing

The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:

`PropertyDescriptor` `HtmlTag`

A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier: `IOStream`

The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples. As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.

`propertyDescriptor` `ioStream` `htmlTag`



✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.

✔️ DO use camelCasing for parameter names.

The following table describes the capitalization rules for different types of identifiers.

| Identifier | Casing | Example                                                      |
| ---------- | ------ | ------------------------------------------------------------ |
| Namespace  | Pascal | `namespace System.Security { ... }`                          |
| Type       | Pascal | `public class StreamReader { ... }`                          |
| Interface  | Pascal | `public interface IEnumerable { ... }`                       |
| Method     | Pascal | `public class Object {`  `public virtual string ToString();`  `}` |
| Property   | Pascal | `public class String {`  `public int Length { get; }`  `}`   |
| Event      | Pascal | `public class Process {`  `public event EventHandler Exited;`  `}` |
| Field      | Pascal | `public class MessageQueue {`  `public static readonly TimeSpan`  `InfiniteTimeout;`  `}`  `public struct UInt32 {`  `public const Min = 0;`  `}` |
| Enum value | Pascal | `public enum FileMode {`  `Append,`  `...`  `}`              |
| Parameter  | Camel  | `public class Convert {`  `public static int ToInt32(string value);`  `}` |



### Capitalizing Compound Words and Common Terms

Most compound terms are treated as single words for purposes of capitalization.

❌ DO NOT capitalize each word in so-called closed-form compound words.

These are compound words written as a single word, such as endpoint. For the purpose of casing guidelines, treat a closed-form compound word as a single word. Use a current dictionary to determine if a compound word is written in closed form.

| Pascal        | Camel         | Not                  |
| ------------- | ------------- | -------------------- |
| `BitFlag`     | `bitFlag`     | `Bitflag`            |
| `Callback`    | `callback`    | `CallBack`           |
| `Canceled`    | `canceled`    | `Cancelled`          |
| `DoNot`       | `doNot`       | `Don't`              |
| `Email`       | `email`       | `EMail`              |
| `Endpoint`    | `endpoint`    | `EndPoint`           |
| `FileName`    | `fileName`    | `Filename`           |
| `Gridline`    | `gridline`    | `GridLine`           |
| `Hashtable`   | `hashtable`   | `HashTable`          |
| `Id`          | `id`          | `ID`                 |
| `Indexes`     | `indexes`     | `Indices`            |
| `LogOff`      | `logOff`      | `LogOut`             |
| `LogOn`       | `logOn`       | `LogIn`              |
| `Metadata`    | `metadata`    | `MetaData, metaData` |
| `Multipanel`  | `multipanel`  | `MultiPanel`         |
| `Multiview`   | `multiview`   | `MultiView`          |
| `Namespace`   | `namespace`   | `NameSpace`          |
| `Ok`          | `ok`          | `OK`                 |
| `Pi`          | `pi`          | `PI`                 |
| `Placeholder` | `placeholder` | `PlaceHolder`        |
| `SignIn`      | `signIn`      | `SignOn`             |
| `SignOut`     | `signOut`     | `SignOff`            |
| `UserName`    | `userName`    | `Username`           |
| `WhiteSpace`  | `whiteSpace`  | `Whitespace`         |
| `Writable`    | `writable`    | `Writeable`          |



### Word Choice

✔️ DO choose easily readable identifier names.

For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.

✔️ DO favor readability over brevity.

The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).

❌ DO NOT use underscores, hyphens, or any other nonalphanumeric characters.

❌ DO NOT use Hungarian notation.

❌ AVOID using identifiers that conflict with keywords of widely used programming languages.



### Using Abbreviations and Acronyms

❌ DO NOT use abbreviations or contractions as part of identifier names.

For example, use `GetWindow` rather than `GetWin`.

❌ DO NOT use any acronyms that are not widely accepted, and even if they are, only when necessary.



### Avoiding Language-Specific Names

✔️ DO use semantically interesting names rather than language-specific keywords for type names.

For example, `GetLength` is a better name than `GetInt`.

✔️ DO use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.

For example, a method converting to `Int64` should be named `ToInt64`, not `ToLong` (because `Int64` is a CLR name for the C#-specific alias `long`). The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).

| C#         | Visual Basic | C++                  | CLR         |
| ---------- | ------------ | -------------------- | ----------- |
| **sbyte**  | **SByte**    | **char**             | **SByte**   |
| **byte**   | **Byte**     | **unsigned char**    | **Byte**    |
| **short**  | **Short**    | **short**            | **Int16**   |
| **ushort** | **UInt16**   | **unsigned short**   | **UInt16**  |
| **int**    | **Integer**  | **int**              | **Int32**   |
| **uint**   | **UInt32**   | **unsigned int**     | **UInt32**  |
| **long**   | **Long**     | **__int64**          | **Int64**   |
| **ulong**  | **UInt64**   | **unsigned __int64** | **UInt64**  |
| **float**  | **Single**   | **float**            | **Single**  |
| **double** | **Double**   | **double**           | **Double**  |
| **bool**   | **Boolean**  | **bool**             | **Boolean** |
| **char**   | **Char**     | **wchar_t**          | **Char**    |
| **string** | **String**   | **String**           | **String**  |
| **object** | **Object**   | **Object**           | **Object**  |

✔️ DO use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.



### Names of Namespaces

As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be. The following template specifies the general rule for naming namespaces:

`<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

The following are examples:

`Fabrikam.Math` `Litware.Security`



✔️ DO prefix namespace names with a company name to prevent namespaces from different companies from having the same name.

✔️ DO use a stable, version-independent product name at the second level of a namespace name.

❌ DO NOT use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived. Organize the hierarchy of namespaces around groups of related technologies.

✔️ DO use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`). If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.

✔️ CONSIDER using plural namespace names where appropriate.

For example, use `System.Collections` instead of `System.Collection`. Brand names and acronyms are exceptions to this rule, however. For example, use `System.IO` instead of `System.IOs`.

❌ DO NOT use the same name for a namespace and a type in that namespace.

For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace. Several compilers require such types to be fully qualified.



#### Namespaces and Type Name Conflicts

❌ DO NOT introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.

There is a very high probability that doing so will lead to type name conflicts in common scenarios. You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).

There are specific guidelines for avoiding type name conflicts for different categories of namespaces.

- **Application model namespaces**

  Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models. For example, the `System.Windows.Forms` namespace is very rarely used together with the `System.Web.UI` namespace. The following is a list of well-known application model namespace groups:

  `System.Windows*` `System.Web.UI*`

  ❌ DO NOT give the same name to types in namespaces within a single application model.

  For example, do not add a type named `Page` to the `System.Web.UI.Adapters` namespace, because the `System.Web.UI` namespace already contains a type named `Page`.

- **Infrastructure namespaces**

  This group contains namespaces that are rarely imported during development of common applications. For example, `.Design` namespaces are mainly used when developing programming tools. Avoiding conflicts with types in these namespaces is not critical.

- **Core namespaces**

  Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces. Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.

  ❌ DO NOT give types names that would conflict with any type in the Core namespaces.

  For example, never use `Stream` as a type name. It would conflict with `System.IO.Stream`, a very commonly used type.

- **Technology namespace groups**

  This category includes all namespaces with the same first two namespace nodes `(.*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`. It is important that types belonging to a single technology do not conflict with each other.

  ❌ DO NOT assign type names that would conflict with other types within a single technology.

  ❌ DO NOT introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).



### Names of Classes, Structs, and Interfaces

The naming guidelines that follow apply to general type naming.

✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.

This distinguishes type names from methods, which are named with verb phrases.

✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.

Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.

❌ DO NOT give class names a prefix (e.g., "C").

✔️ CONSIDER ending the name of derived classes with the name of the base class.

This is very readable and explains the relationship clearly. Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`. However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.

✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.

For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names. As with other type names, avoid abbreviations.

✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.



#### Names of Generic Type Parameters

✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.

✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

✔️ DO prefix descriptive type parameter names with `T`.

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
  TSession Session { get; }
}
```

✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.

For example, a parameter constrained to `ISession` might be called `TSession`.



#### Names of Common Types

✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.

| Base Type                                                    | Derived/Implementing Type Guideline                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `System.Attribute`                                           | ✔️ DO add the suffix "Attribute" to names of custom attribute classes. |
| `System.Delegate`                                            | ✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.  ✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.  ❌ DO NOT add the suffix "Delegate" to a delegate. |
| `System.EventArgs`                                           | ✔️ DO add the suffix "EventArgs."                             |
| `System.Enum`                                                | ❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.  ❌ DO NOT add the suffix "Enum" or "Flag." |
| `System.Exception`                                           | ✔️ DO add the suffix "Exception."                             |
| `IDictionary`  `IDictionary`                                 | ✔️ DO add the suffix "Dictionary." Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows. |
| `IEnumerable`  `ICollection`  `IList`  `IEnumerable`  `ICollection`  `IList` | ✔️ DO add the suffix "Collection."                            |
| `System.IO.Stream`                                           | ✔️ DO add the suffix "Stream."                                |
| `CodeAccessPermission IPermission`                           | ✔️ DO add the suffix "Permission."                            |



#### Naming Enumerations

Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.). However, there are additional guidelines that apply specifically to enums.

✔️ DO use a singular type name for an enumeration unless its values are bit fields.

✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.

❌ DO NOT use an "Enum" suffix in enum type names.

❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.

❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).



### Names of Type Members

Types are made of members: methods, properties, events, constructors, and fields. The following sections describe guidelines for naming type members.



#### Names of Methods

Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases. Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.

✔️ DO give methods names that are verbs or verb phrases.

```csharp
public class String {
  public int CompareTo(...);
  public string[] Split(...);
  public string Trim();
}
```



#### Names of Properties

Unlike other members, properties should be given noun phrase or adjective names. That is because a property refers to data, and the name of the property reflects that. PascalCasing is always used for property names.

✔️ DO name properties using a noun, noun phrase, or adjective.

❌ DO NOT have properties that match the name of "Get" methods as in the following example:

```csharp
public string TextWriter { get {...} set {...} } public string GetTextWriter(int value) { ... }
```

This pattern typically indicates that the property should really be a method.

✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".

✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`). Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.

✔️ CONSIDER giving a property the same name as its type.

For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:

```csharp
public enum Color {...}
public class Control {
  public Color Color { get {...} set {...} }
}
```

❌ DO NOT include the class name in the name of the properties unless it is needed to clarify the meaning of the property. For example, use `Email` instead of `UserEmail`.



#### Names of Events

Events always refer to some action, either one that is happening or one that has occurred. Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.

✔️ DO name events with a verb or a verb phrase.

Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.

✔️ DO give events names with a concept of before and after, using the present and past tenses.

For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.

❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events. Use present and past tenses as just described.

✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:

```csharp
public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);
```

✔️ DO use two parameters named `sender` and `e` in event handlers.

The sender parameter represents the object that raised the event. The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.

✔️ DO name event argument classes with the "EventArgs" suffix.



#### Names of Fields

✔️ DO use PascalCasing in static, public and protected field names.

✔️ DO use camelCasing in private and internal field names.

✔️ DO name fields using a noun, noun phrase, or adjective.

❌ DO NOT use a prefix for field names.

For example, do not use "g\_" or "s\_" to indicate static fields.



### Naming Parameters

Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.

✔️ DO use camelCasing in parameter names.

✔️ DO use descriptive parameter names.

✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.



## Layout Conventions 

Good layout uses formatting to emphasize the structure of your code and to make the code easier to read. 

Use the following convention:

- Indent using tabs.
  
- An indent has a width of four spaces.
  
- Unix style line endings must be used in all files (lf).
  
- Write only one statement per line. 
  
- Write only one declaration per line. 
  
- If continuation lines are not indented automatically, indent them one tab stop (four spaces). 
  
- Add at least one blank line between method definitions and property definitions. 
  
- Use parentheses to make clauses in an expression apparent, as shown in the following code. 
  
     ```csharp
     if ((val1 > val2) && (val1 > val3))
     {
       // Take appropriate action.
     }
     ```



## Code Documentation Conventions

Make use of documentation comments for classes and methods.

The documentation comment for methods must include a summary, a description for all the parameters and a description of the return value when applicable.

```csharp
/// <summary>
///
/// </summary>
/// <param name="id"></param>
/// <returns></returns>
```



The following tags can be used:

|               |                |                 |          |
| ------------- | -------------- | --------------- | -------- |
| \<c>          | \<para>        | \<see>*         | \<value> |
| \<code>       | \<param>*      | \<seealso>*     |          |
| \<example>    | \<paramref>    | \<summary>      |          |
| \<exception>* | \<permission>* | \<typeparam>*   |          |
| \<include>*   | \<remarks>     | \<typeparamref> |          |
| \<list>       | \<inheritdoc>  | \<returns>      |          |

(* denotes that the compiler verifies syntax.)



If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively. This encoding is shown in the following example.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```



### Commenting Conventions 

- Place the comment on a separate line, not at the end of a line of code. 
  
- Begin comment text with an uppercase letter. 
  
- End comment text with a period. 
  
- Insert one space between the comment delimiter (//) and the comment text, as shown in the following example. 
  
     ```csharp
  // The following declaration creates a query. It does not run
  // the query.
  ```
  
- Do not create formatted blocks of asterisks around comments. 



## Language Guidelines 

### Literals

Use literals instead of object types unless a specific function of the object type is required.



### Return statements

Return statements may be written wherever. No need to store the return value until the end of a method.



### Switch statements

Avoid the use of if-else if-else chains. Use `switch` statements instead.



### String Data Type 

- Use string interpolation to concatenate short strings, as shown in the following code. 
  
     ```csharp
  string displayName = $"{nameList[n].LastName}, {nameList[n].FirstName}";
  ```
  
- To append strings in loops, especially when you are working with large amounts of text, use a `System.Text.StringBuilder` object. 
  
     ```csharp
     var phrase = "lalalalalalalalalalalalalalalalalalalalalalalalalalalalalala";
     var manyPhrases = new StringBuilder();
     for (var i = 0; i < 10000; i++)
     {
       manyPhrases.Append(phrase);
     }
     //Console.WriteLine("tra" + manyPhrases);
     ```



### Implicitly Typed Local Variables

Avoid the use of implicitly typed local variables.

(Do not use `var` when assigning a variable)

(Except for anonymous types)



### Unsigned Data Type 

In general, use `int` rather than unsigned types. The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`. 



### Arrays 

Use the concise syntax when you initialize arrays on the declaration line. 

```csharp
// Preferred syntax.
string[] vowels1 = { "a", "e", "i", "o", "u" };

// If you specify an array size, you must initialize the elements one at a time.
string[] vowels3 = new string[5];
vowels3[0] = "a";
vowels3[1] = "e";
// And so on.
```



### Delegates 

Use the concise syntax to create instances of a delegate type. 

```csharp
// First, in class Program, define the delegate type and a method that 
// has a matching signature.

// Define the type.
public delegate void Del(string message);

// Define a method that has a matching signature.
public static void DelMethod(string str)
{
  Console.WriteLine("DelMethod argument: {0}", str);
}
```

```csharp
// In the Main method, create an instance of Del.

// Preferred: Create an instance of Del by using condensed syntax.
Del exampleDel2 = DelMethod;

// The following declaration uses the full syntax.
Del exampleDel1 = new Del(DelMethod);
```



### try-catch and using Statements in Exception Handling 

- Use a `try-catch` statement for most exception handling. 
  
     ```csharp
  static string GetValueFromArray(string[] array, int index)
  {
    try
    {
      return array[index];
    }
    catch (System.IndexOutOfRangeException ex)
    {
      Console.WriteLine("Index is out of range: {0}", index);
      throw;
    }
  }
  ```
  
- Simplify your code by using the C# `using` statement. If you have a `try-finally` statement in which the only code in the `finally` block is a call to the `System.IDisposable.Dispose` method, use a `using` statement instead. 
  
     ```csharp
     // This try-finally statement only calls Dispose in the finally block.
     Font font1 = new Font("Arial", 10.0f);
     try
     {
       byte charset = font1.GdiCharSet;
     }
     finally
     {
       if (font1 != null)
       {
         ((IDisposable)font1).Dispose();
       }
     }
     
     // You can do the same thing with a using statement.
     using (Font font2 = new Font("Arial", 10.0f))
     {
       byte charset = font2.GdiCharSet;
     }
     ```



### Operators

All operators are allowed, except for the conditional if-else (? :) operator (single line if-else-statement).

#### Allowed operators

| Operators                                                    | Category or name                                             |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [x.y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#member-access-expression-), [x?.y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-), [x?\[y\]](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-), [f(x)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#invocation-expression-), [a\[i\]](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#indexer-operator-), [x++](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#increment-operator-), [x--](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#decrement-operator---), [new](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/new-operator), [typeof](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/type-testing-and-cast#typeof-operator), [checked](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/checked), [unchecked](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/unchecked), [default](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/default), [nameof](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/nameof), [delegate](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/delegate-operator), [sizeof](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/sizeof), [stackalloc](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/stackalloc), [x->y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/pointer-related-operators#pointer-member-access-operator--) | Primary                                                      |
| [+x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#unary-plus-and-minus-operators), [-x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#unary-plus-and-minus-operators), [!x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-negation-operator-), [~x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#bitwise-complement-operator-), [++x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#increment-operator-), [--x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#decrement-operator---), [^x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#index-from-end-operator-), [(T)x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/type-testing-and-cast#cast-operator-), [await](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/await), [&x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/pointer-related-operators#address-of-operator-), [*x](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/pointer-related-operators#pointer-indirection-operator-), [true and false](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/true-false-operators) | Unary                                                        |
| [x..y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#range-operator-) | Range                                                        |
| [switch](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-8#switch-expressions) | `switch` expression                                          |
| [x * y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#multiplication-operator-), [x / y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#division-operator-), [x % y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#remainder-operator-) | Multiplicative                                               |
| [x + y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#addition-operator-), [x – y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#subtraction-operator--) | Additive                                                     |
| [x << y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#left-shift-operator-), [x >> y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#right-shift-operator-) | Shift                                                        |
| [x < y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/comparison-operators#less-than-operator-), [x > y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/comparison-operators#greater-than-operator-), [x <= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/comparison-operators#less-than-or-equal-operator-), [x >= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/comparison-operators#greater-than-or-equal-operator-), [is](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/type-testing-and-cast#is-operator), [as](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/type-testing-and-cast#as-operator) | Relational and type-testing                                  |
| [x == y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/equality-operators#equality-operator-), [x != y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/equality-operators#inequality-operator-) | Equality                                                     |
| `x & y`                                                      | [Boolean logical AND](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-and-operator-) or [bitwise logical AND](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#logical-and-operator-) |
| `x ^ y`                                                      | [Boolean logical XOR](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-exclusive-or-operator-) or [bitwise logical XOR](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#logical-exclusive-or-operator-) |
| `x | y`                                                      | [Boolean logical OR](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-or-operator-) or [bitwise logical OR](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#logical-or-operator-) |
| [x && y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#conditional-logical-and-operator-) | Conditional AND                                              |
| [x \|\| y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#conditional-logical-or-operator-) | Conditional OR                                               |
| [x ?? y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/null-coalescing-operator) | Null-coalescing operator                                     |
| [x = y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/assignment-operator), [x += y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment), [x -= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment), [x *= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment), [x /= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment), [x %= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment), [x &= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#compound-assignment), [x \|= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#compound-assignment), [x ^= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#compound-assignment), [x <<= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#compound-assignment), [x >>= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#compound-assignment), [x ??= y](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/null-coalescing-operator), [=>](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-operator) | Assignment and lambda declaration                            |



#### Banned operators

To avoid readability issues for some developers, single line if-else-statements (conditional operators) are banned.

| Operators                                                    | Category or name     |
| ------------------------------------------------------------ | -------------------- |
| [c ? t : f](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator) | Conditional operator |



#### && and &#124;&#124; Operators 

To avoid exceptions and increase performance by skipping unnecessary comparisons, use `&&` instead of `&` and `||` instead of `|` when you perform comparisons, as shown in the following example. 

```csharp
Console.Write("Enter a dividend: ");
int dividend = Convert.ToInt32(Console.ReadLine());

Console.Write("Enter a divisor: ");
int divisor = Convert.ToInt32(Console.ReadLine());

// If the divisor is 0, the second clause in the following condition
// causes a run-time error. The && operator short circuits when the
// first expression is false. That is, it does not evaluate the
// second expression. The & operator evaluates both, and causes 
// a run-time error when divisor is 0.
if ((divisor != 0) && (dividend / divisor > 0))
{
  Console.WriteLine("Quotient: {0}", dividend / divisor);
}
else
{
  Console.WriteLine("Attempted division by 0 ends up here.");
}
```



### New Operator 

- Use explicit typing when doing object instantiation, as shown in the following declaration. 
  
     ```csharp
  ExampleClass instance1 = new ExampleClass();
  ```
  
- Use object initializers to simplify object creation. 

     ```csharp
     // Object initializer.
     var instance3 = new ExampleClass { Name = "Desktop", ID = 37414, 
       Location = "Redmond", Age = 2.3 };
     
     // Default constructor and assignment statements.
     var instance4 = new ExampleClass();
     instance4.Name = "Desktop";
     instance4.ID = 37414;
     instance4.Location = "Redmond";
     instance4.Age = 2.3;
     ```



### Event Handling 

If you are defining an event handler that you do not need to remove later, use a lambda expression. 

```csharp
public Form2()
{
  // You can use a lambda expression to define an event handler.
  this.Click += (s, e) =>
    {
      MessageBox.Show(
        ((MouseEventArgs)e).Location.ToString());
    };
}
```

```csharp
// Using a lambda expression shortens the following traditional definition.
public Form1()
{
  this.Click += new EventHandler(Form1_Click);
}

void Form1_Click(object sender, EventArgs e)
{
  MessageBox.Show(((MouseEventArgs)e).Location.ToString());
}
```



### Static Members 

Call `static` members by using the class name: *ClassName.StaticMember*. This practice makes code more readable by making static access clear. Do not qualify a static member defined in a base class with the name of a derived class. While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class. 



### LINQ Queries 

- Use meaningful names for query variables. The following example uses `seattleCustomers` for customers who are located in Seattle. 
  
     ```csharp
  string[] seattleCustomers = from customer in customers
              where customer.City == "Seattle"
              select customer.Name;
  ```
  
- Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing. 
  
     ```csharp
  var localDistributors =
    from customer in customers
    join distributor in distributors on customer.City equals distributor.City
    select new { Customer = customer, Distributor = distributor };
  ```
  
- Rename properties when the property names in the result would be ambiguous. For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor. 
  
     ```csharp
  var localDistributors2 =
    from customer in customers
    join distributor in distributors on customer.City equals distributor.City
    select new { CustomerName = customer.Name, DistributorID = distributor.ID };
  ```
  
- Use explicit typing in the declaration of query variables and range variables. 
  
     ```csharp
  string[] seattleCustomers = from customer in customers
              where customer.City == "Seattle"
              select customer.Name;
  ```
  
- Align query clauses under the `from` clause, as shown in the previous examples. 
  
- Use `where` clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data. 
  
     ```csharp
  Customer[] seattleCustomers2 = from customer in customers
              where customer.City == "Seattle"
              orderby customer.Name
              select customer;
  ```
  
- Use multiple `from` clauses instead of a `join` clause to access inner collections. For example, a collection of `Student` objects might each contain a collection of test scores. When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score. 
  
     ```csharp
     // Use a compound from to access the inner sequence within each element.
     var scoreQuery = from student in students
              from score in student.Scores
              where score > 90
              select new { Last = student.LastName, score };
     ```
