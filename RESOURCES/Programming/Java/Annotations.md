 are a form of syntactic metadata that can be added to Java source code
 Here are some of the built-in annotations:
 
 - `@Override` — Checks that the method is an [override](https://en.wikipedia.org/wiki/Method_overriding "Method overriding"). Causes a [compilation error](https://en.wikipedia.org/wiki/Compilation_error "Compilation error") if the method is not found in one of the [parent classes](https://en.wikipedia.org/wiki/Parent_class "Parent class") or implemented [interfaces](https://en.wikipedia.org/wiki/Interface_(Java) "Interface (Java)").
- `@Deprecated` — Marks the method as obsolete. Causes a compile warning if the method is used.
- `@SuppressWarnings` — Instructs the compiler to suppress the [compile time](https://en.wikipedia.org/wiki/Compile_time "Compile time") warnings specified in the annotation parameters.

**Annotations applied to other annotations (also known as "Meta Annotations"):**

- `@Retention` — Specifies how the marked annotation is stored, whether in code only, compiled into the class, or available at runtime through reflection.
- `@Documented` — Marks another annotation for inclusion in the documentation.
- `@Target` — Marks another annotation to restrict what kind of Java elements the annotation may be applied to.
- `@Inherited` — Marks another annotation to be inherited to subclasses of annotated class (by default annotations are not inherited by subclasses).

Here are some other Java annotations:
- `@Inject` — 