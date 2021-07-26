---
title: "Troubleshoot Java Runtime Errors"
layout: single
cover: false
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'posts'
comments: true
category: blog
date: 2021-07-26 17:33:11 EDT
---


## `java.lang.NoSuchMethodError`

This is a very common error when the runtime class doesn't match with the complied time classes. It is usually caused by mismatched runtime dependencies. If it's a maven/gradle based project, you can figure it out by building the dependency tree to understand which version is actually pulled in and used in runtime.

For gralde, the command is - `./gradlew dependencies`

However, the dependency tree approach only works if all the dependencies are managed correctly, i.e. all external dependencies are declared via maven or gradle. If there is a bad library which encloses its dependent into its own jar, it will make the troubleshooting much harder. This is something really bad and every library should avoid doing it.

If you are sure everything looks good in the dependency tree but you still see runtime errors, you should check if any classes have multiple versions and could have caused the problem. To check it, you can do:

### Using the `verbose` parameter to show the detail information about where a class is loaded:
```bash
java -verbose:class <other args>
```

The output is like:

```bash
[2.209s][info][class,load] org.springframework.security.authentication.AuthenticationTrustResolverImpl source: jar:file:/home/gary/java/spring/spring-boot-playground/build/libs/spring-boot-playground-0.0.1.jar!/BOOT-INF/lib/spring-security-core-5.2.8.RELEASE.jar!/
[2.210s][info][class,load] org.springframework.security.core.CredentialsContainer source: jar:file:/home/gary/java/spring/spring-boot-playground/build/libs/spring-boot-playground-0.0.1.jar!/BOOT-INF/lib/spring-security-core-5.2.8.RELEASE.jar!/
```

## Using the IDE feature to find the offending classes

Intellij does a great job helping you locate the class files in the project, if there are multiple versions loaded, you can see them in the search (using `Shift`+`Shift` to show the global search dialog.)

## How to read the `NoSuchMethodError` error message

Here is a sample error message:

```
java.lang.NoSuchMethodError:
com.sun.tools.doclets.formats.html.SubWriterHolderWriter.printDocLinkForMenu(
    ILcom/sun/javadoc/ClassDoc;Lcom/sun/javadoc/MemberDoc;
    Ljava/lang/String;Z)Ljava/lang/String;
at com.sun.tools.doclets.formats.html.AbstractExecutableMemberWriter.writeSummaryLink(
    AbstractExecutableMemberWriter.java:94)
```

It could be quite confusing to figure out what does `ILcom/sun/javadoc/ClassDoc;Lcom/sun/javadoc/MemberDoc;Ljava/lang/String;Z)` mean. To understand it, we need to understand how JVM represents the type of class, instance or variables. According to [JVM: Field Descriptors](https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-4.html#jvms-4.3.2), here is the table which shows the FiledType characters:

```
Character     Type          Interpretation
------------------------------------------
B             byte          signed byte
C             char          Unicode character
D             double        double-precision floating-point value
F             float         single-precision floating-point value
I             int           integer
J             long          long integer
L<classname>; reference     an instance of class
S             short         signed short
Z             boolean       true or false
[             reference     one array dimension
```

Based on the table, we can translate the parameters in the error message above to:

- `I` -> `int`
- `Lcom/sun/javadoc/ClassDoc;` -> `com.sun.javadoc.ClassDoc`
- `Lcom/sun/javadoc/MemberDoc;` -> `com.sun.javadoc.MemberDoc`
- `Ljava/lang/String;` -> `java.lang.String`
- `Z` -> `boolean`

Or:  `printDocLinkForMenu(int, ClassDoc, MemberDoc, String, boolean)`

## Reference:

- [Java command options](https://docs.oracle.com/en/java/javase/11/tools/java.html#GUID-3B1CE181-CD30-4178-9602-230B800D4FAE)
- [JVM Field Descriptors](https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-4.html#jvms-4.3.2)
- [StackOverflow Answer - Interpreting NoSuchMethodError message](https://stackoverflow.com/a/2945933/958071)
