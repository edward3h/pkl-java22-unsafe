# pkl-lang bug on Java 22

Minimal Gradle build to demonstrate a bug with Pkl on Java 22.

Ensure `$JAVA_HOME` points to Java 22.

Run `./gradlew build --stacktrace`.

```shell
Execution failed for task ':genJava'.
### SNIP
Caused by: java.lang.ExceptionInInitializerError: Exception java.lang.NoSuchMethodError: 'void sun.misc.Unsafe.ensureClassInitialized(java.lang.Class)' [in thread "Execution worker Thread 2"]
        at org.pkl.thirdparty.truffle.api.library.LibraryFactory.ensureLibraryInitialized(LibraryFactory.java:384)
        at org.pkl.thirdparty.truffle.api.library.LibraryFactory.getUncached(LibraryFactory.java:364)
        at org.pkl.thirdparty.truffle.api.library.LibraryFactory.<init>(LibraryFactory.java:210)
        at org.pkl.thirdparty.truffle.api.interop.InteropLibraryGen.<init>(InteropLibraryGen.java:178)
        at org.pkl.thirdparty.truffle.api.interop.InteropLibraryGen.<clinit>(InteropLibraryGen.java:169)
        at org.pkl.thirdparty.truffle.api.library.LibraryFactory.loadGeneratedClass(LibraryFactory.java:791)
        at org.pkl.thirdparty.truffle.api.library.LibraryFactory.resolveImpl(LibraryFactory.java:740)
        at org.pkl.thirdparty.truffle.api.library.LibraryFactory.resolve(LibraryFactory.java:733)
        at org.pkl.thirdparty.truffle.api.interop.InteropLibrary.<clinit>(InteropLibrary.java:2941)
        at org.pkl.thirdparty.truffle.polyglot.PolyglotValueDispatch.<clinit>(PolyglotValueDispatch.java:170)
        at org.pkl.thirdparty.truffle.polyglot.PolyglotImpl.initialize(PolyglotImpl.java:166)
        at org.pkl.thirdparty.graalvm.polyglot.impl.AbstractPolyglotImpl.setConstructors(AbstractPolyglotImpl.java:288)
        at org.pkl.thirdparty.graalvm.polyglot.Engine$1.loadAndValidateProviders(Engine.java:1107)
        at org.pkl.thirdparty.graalvm.polyglot.Engine$1.run(Engine.java:1067)
        at org.pkl.thirdparty.graalvm.polyglot.Engine$1.run(Engine.java:1061)
        at org.pkl.thirdparty.graalvm.polyglot.Engine.initEngineImpl(Engine.java:1061)
        at org.pkl.thirdparty.graalvm.polyglot.Engine$ImplHolder.<clinit>(Engine.java:143)
        at org.pkl.thirdparty.graalvm.polyglot.Engine.getImpl(Engine.java:367)
        at org.pkl.thirdparty.graalvm.polyglot.Engine$Builder.build(Engine.java:665)
        at org.pkl.core.runtime.VmUtils.<clinit>(VmUtils.java:74)

```