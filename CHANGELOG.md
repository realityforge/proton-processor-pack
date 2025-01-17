# Change Log

### Unreleased

### [v0.65](https://github.com/realityforge/proton/tree/v0.65) (2025-01-13) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.64...v0.65)

Changes in this release:

* Update the `org.realityforge.javax.annotation` artifact to version `1.1.1`.
* Change `CompileTestUtil.assertNoWarnings()` to fail an assertion if `MANDATORY_WARNING` diagnostics are present (not just `WARNING` diagnostics).

### [v0.64](https://github.com/realityforge/proton/tree/v0.64) (2024-05-31) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.63...v0.64)

Changes in this release:

* When collecting methods, if an abstract method matches an existing abstract method then assume it is a refinement and replace the method in the method list.

### [v0.63](https://github.com/realityforge/proton/tree/v0.63) (2024-05-24) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.62...v0.63)

Changes in this release:

* Sort assertions in `CompileTestUtil.assertCompilesWithoutWarnings()` so that they generate more useful failure messages by asserting on errors, then warnings, and then success.

### [v0.62](https://github.com/realityforge/proton/tree/v0.62) (2024-05-17) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.61...v0.62)

Changes in this release:

* Fix bug introduced in `0.61` where interface methods were collected at incorrectly in some circumstances.

### [v0.61](https://github.com/realityforge/proton/tree/v0.61) (2024-05-17) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.60...v0.61)

Changes in this release:

* Sort assertions in `CompileTestUtil.assertCompilesWithoutWarnings()` so that they generate more useful failure messages by asserting on warnings, then errors and then success.
* Fix bug introduced in `0.60` where interface methods were not collected at all unless they were collected at the end.

### [v0.60](https://github.com/realityforge/proton/tree/v0.60) (2024-05-17) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.59...v0.60)

Changes in this release:

* Add optional parameter `collectInterfaceMethodsAtEnd` to `ElementsUtil.getMethods(...)` so that interface methods can be collected at the end of collecting methods for classes. This is useful in systems that allow users to provide additional extension methods via interfaces.

### [v0.59](https://github.com/realityforge/proton/tree/v0.59) (2022-05-10) · [Full Changelog](https://github.com/spritz/spritz/compare/v0.58...v0.59)

Changes in this release:

* Support passing `Predicate<TypeElement> isValidPredicate` to `AbstractStandardProcessor.processTypeElements(...)` so can override the mechanisms for determining whether an element is "valid enough" to perform annotation processing on.

### [v0.58](https://github.com/realityforge/proton/tree/v0.58) (2022-04-29) · [Full Changelog](https://github.com/spritz/spritz/compare/v0.57...v0.58)

Changes in this release:

* Reinstate simplified `AbstractProcessorTest.outputFilesIfEnabled(Compilation, Filter)` method.

### [v0.57](https://github.com/realityforge/proton/tree/v0.57) (2022-04-27) · [Full Changelog](https://github.com/spritz/spritz/compare/v0.56...v0.57)

Changes in this release:

* Remove support for annotating generated artifacts with `javax.annotation.Generated` prior to Java 9 as we no longer support Java prior to Java 9.

### [v0.56](https://github.com/realityforge/proton/tree/v0.56) (2022-04-27) · [Full Changelog](https://github.com/spritz/spritz/compare/v0.55...v0.56)

Changes in this release:

* Ensure `SynthesizingProcessor` supports source in version `17`.
* Introduce `CompileTestUtil` and `Compilation` classes in the `qa` module to reimplement functionality present in the `com.google.testing.compile:compile-testing` artifact. Rewrite `AbstractProcessorTest` to use `CompileTestUtil` functionality rather than the equivalent code in the `com.google.testing.compile:compile-testing` artifact. Remove the `com.google.testing.compile:compile-testing` artifact and related dependencies. This resulted in simpler code and made it easier to evolve the project to support the latest version of Java.

### [v0.55](https://github.com/realityforge/proton/tree/v0.55) (2022-04-22) · [Full Changelog](https://github.com/spritz/spritz/compare/v0.54...v0.55)

Changes in this release:

* Remove `ElementsUtil.isSynthetic(Element)` and `ElementsUtil.isNotSynthetic(Element)` as it used java internals that are not available in later versions of java. Later versions of java should use `elements.getOrigin( element ).isDeclared()` for equivalent functionality.
* Move to a minimum java version of `17`.

### [v0.54](https://github.com/realityforge/proton/tree/v0.54) (2021-12-16) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.53...v0.54)

Changes in this release:

* Add a `profile` annotation configuration option to enable basic profiling for different stages within the annotation processor. This option must be added to the set of supported annotation processor options in subclasses of `AbstractStandardProcessor`. The API to `AbstractStandardProcessor` also changed so that subclasses must pass a `StopWatch` instance when invoking some API methods.

### [v0.53](https://github.com/realityforge/proton/tree/v0.53) (2021-11-26) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.52...v0.53)

Changes in this release:

* Change the debug message in `debugAnnotationProcessingRootElements()` to be less prone to confusion.
* Change the `processTypeElements(...)` and `performAction(...)` methods to accept a label to use when emitting debug messages.

### [v0.52](https://github.com/realityforge/proton/tree/v0.52) (2021-11-10) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.51...v0.52)

Changes in this release:

* Upgrade the `au.com.stocksoftware.idea.codestyle` artifact to version `1.17`.
* Upgrade the `com.squareup` artifact to version `1.13.0`.
* Add a `AbstractStandardProcessor.debugAnnotationProcessingRootElements(...)` helper method that downstream annotation processors can call to improve debuggability.
* Change the implementation of `AbstractStandardProcessor.getNewTypeElementsToProcess(...)` so that it only returns types for that have been passed to the annotation processor for processing. This avoids the annotation processor from re-generating classes or descriptors for dependencies and eliminates failures during concurrent, incremental compiles. This does necessitate the downstream annotation processors invoking `collectRootTypeNames(RoundEnvironment)` at the start of the `process()` method and `clearRootTypeNamesIfProcessingOver(RoundEnvironment)` at the end of the `process()` method.

### [v0.51](https://github.com/realityforge/proton/tree/v0.51) (2020-05-28) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.50...v0.51)

Changes in this release:

* Add `MemberChecks.mustBeProtected(...)` and `MemberChecks.mustNotBeProtected(...)` helper methods.

### [v0.50](https://github.com/realityforge/proton/tree/v0.50) (2020-05-21) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.49...v0.50)

Changes in this release:

* Fix bug where `GeneratorUtil.overrideMethod(...)` was not passing on the `additionalSuppressions` parameter when generating suppressions.

### [v0.49](https://github.com/realityforge/proton/tree/v0.49) (2020-05-21) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.48...v0.49)

Changes in this release:

* Expose `TypesUtil.hasRawTypes()` helper method.
* Deprecate `ElementsUtil.isElementDeprecated()` helper method and add replacement `ElementsUtil.hasDeprecatedAnnotation()`.
* Expose `ElementsUtil.isDeprecated()` helper method that determines whether the element is effectively deprecated by either being annotated with `@Deprecated` or being enclosed in a deprecated element.
* Expose `TypesUtil.isDeprecated(...)` helper method.

### [v0.48](https://github.com/realityforge/proton/tree/v0.48) (2020-05-19) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.47...v0.48)

Changes in this release:

* Ensure `ElementsUtil.getOverriddenMethod(...)` is public.

### [v0.47](https://github.com/realityforge/proton/tree/v0.47) (2020-05-19) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.46...v0.47)

Changes in this release:

* Add `ElementsUtil.getOverriddenMethod(...)` helper method.

### [v0.46](https://github.com/realityforge/proton/tree/v0.46) (2020-04-07) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.45...v0.46)

Changes in this release:

* Make `MemberChecks.doesMethodNotOverrideInterfaceMethod(...)` public access.

### [v0.45](https://github.com/realityforge/proton/tree/v0.45) (2020-04-07) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.44...v0.45)

Changes in this release:

* Extract the `AbstractProcessorTest.outputFilesIfEnabled(...)` helper method so that downstream projects can update golden files/fixtures even when they are performing custom configuration of the compilation.

### [v0.44](https://github.com/realityforge/proton/tree/v0.44) (2020-03-19) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.43...v0.44)

Changes in this release:

* Add a utility method `AbstractStandardProcessor.isDebugEnabled()` to expose whether the debug state is enabled.

### [v0.43](https://github.com/realityforge/proton/tree/v0.43) (2020-03-19) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.42...v0.43)

Changes in this release:

* Add the method `assertDiagnostic(...)` that accepts a compilation, a diagnostic and a message contents to the `AbstractProcessorTest` class. Also added `assertErrorDiagnostic(...)` and `assertWarningDiagnostic(...)` helper methods to make testing the most common diagnostic error messages easy. Deprecated the existing `assertDiagnosticPresent(...)` method as it's functionality has been subsumed by the new methods.

### [v0.42](https://github.com/realityforge/proton/tree/v0.42) (2020-03-18) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.41...v0.42)

Changes in this release:

* Extract the `AbstractStandardProcessor.getNewTypeElementsToProcess()` utility method.

### [v0.41](https://github.com/realityforge/proton/tree/v0.41) (2020-03-04) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.40...v0.41)

Changes in this release:

* Add `AbstractProcessorTest.newSynthesizingProcessor(...)` helper methods that create an annotation processor that will "generate" source in a particular processor round. The generation actually just consists of reading a fixture from the filesystem and passing it to the compiler. This utility is useful when testing annotation processors that defer processing until later rounds based on whether the types that they are acting on are fully resolved or have unknown elements present.

### [v0.40](https://github.com/realityforge/proton/tree/v0.40) (2020-02-16) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.39...v0.40)

Changes in this release:

* Import `TypesUtil` class that contain helper methods that work solely on types.

### [v0.39](https://github.com/realityforge/proton/tree/v0.39) (2020-02-13) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.38...v0.39)

Changes in this release:

* Add some additional debugging when actually performing an action on an `TypeElement`.
* Add `AbstractProcessorTest.assertDiagnosticPresent` method to help when performing explicit staged compiled during testing.

### [v0.38](https://github.com/realityforge/proton/tree/v0.38) (2020-02-13) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.37...v0.38)

Changes in this release:

* Refactor `AbstractStandardProcessor.processTypeElements()` to work when the annotation processor is responsible for processing multiple different top-level types.
* Add helper method `AbstractStandardProcessor.readBooleanOption(...)` that simplifies reading boolean annotation options.
* Cache resolution of annotation properties in `AbstractStandardProcessor.init(...)`.
* Mark `AbstractStandardProcessor.errorIfProcessingOverAndDeferredTypesUnprocessed(...)` as private as should never be invoked by subclasses.
* Add support for a `debug` annotation option that prints out debug messages based on whether types are processed in a round. Add a method `AbstractStandardProcessor.debug(...)` that can be used by downstream libraries to emit debug messages.

### [v0.37](https://github.com/realityforge/proton/tree/v0.37) (2020-02-13) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.36...v0.37)

Changes in this release:

* Fix incorrect annotation name in the `AnnotationsUtil.hasNullableAnnotation(...)` helper method.

### [v0.36](https://github.com/realityforge/proton/tree/v0.36) (2020-02-13) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.35...v0.36)

Changes in this release:

* Change the way that that `AbstractStandardProcessor` handles deferring of unresolved types. Previously the code assumed that the annotation processors would only have a single call to `AbstractStandardProcessor.processTypeElements()` within each annotation processor which meant that there was only one callback that was ever invoked so that deferred types could be added if they have been resolved since the last processor round. However toolkits such as Sting that process multiple different categories of top-level `TypeElement` instances would have get have resolved types from incorrect categories processed in incorrect callbacks. This is a breaking change that will result in rework of downstream libraries.
* Remove the deprecated `AnnotationUtils.getAnnotationValue()` method and rename the `AnnotationUtils._getAnnotationValue()` to `AnnotationUtils.getAnnotationValue()`. This backwards incompatible change was made in this version so all incompatible changes are made in a single release.
* Migrate `GeneratorUtil.getPackageElement(...)` to `ElementsUtil`.
* Migrate `GeneratorUtil.areTypesInDifferentPackage(...)` to `ElementsUtil`.
* Migrate `GeneratorUtil.areTypesInSamePackage(...)` to `ElementsUtil`.
* Add `AnnotationsUtil.hasNullableAnnotation(...)` helper method.
* Move and rename nullability annotation classname constants to `AnnotationsUtil`.

### [v0.35](https://github.com/realityforge/proton/tree/v0.35) (2020-02-13) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.34...v0.35)

Changes in this release:

* Add `ElementsUtil.isSynthetic(Element)` and `ElementsUtil.isNotSynthetic(Element)` helper methods.

### [v0.34](https://github.com/realityforge/proton/tree/v0.34) (2020-02-12) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.33...v0.34)

Changes in this release:

* Expose `GeneratorUtil.ANNOTATION_WHITELIST` as a public field.

### [v0.33](https://github.com/realityforge/proton/tree/v0.33) (2020-02-10) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.32...v0.33)

Changes in this release:

* Add some additional utility methods `MemberChecks.must(...)` and `MemberChecks.mustNot(...)`.

### [v0.32](https://github.com/realityforge/proton/tree/v0.32) (2020-02-02) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.31...v0.32)

Changes in this release:

* Make `AnnotationsUtil.findAnnotationValue()` public.
* Deprecate `AnnotationsUtil.getAnnotationValue(...)` in favour of `AnnotationsUtil.getAnnotationValueValue(...)` as a future version of the library will add a `AnnotationsUtil.getAnnotationValue(...)` that returns an `AnnotationValue`.

### [v0.31](https://github.com/realityforge/proton/tree/v0.31) (2020-02-01) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.30...v0.31)

Changes in this release:

* Upgrade the `com.google.truth` artifact to version `0.45`.
* Upgrade the `com.google.testing.compile` artifact to version `0.18-rf`.
* Enhance `ProcessorException` so that it accepts optional `AnnotationMirror` and `AnnotationValue` parameters.

### [v0.30](https://github.com/realityforge/proton/tree/v0.30) (2020-01-29) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.29...v0.30)

Changes in this release:

* Add `AbstractProcessorTest.input(...)` helper method.
* Add `AbstractProcessorTest.assertCompilationUnsuccessful(...)` helper method.

### [v0.29](https://github.com/realityforge/proton/tree/v0.29) (2020-01-29) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.28...v0.29)

Changes in this release:

* Add `ElementsUtil.isElementDeprecated(Element)` helper method.
* Add `ElementsUtil.isEffectivelyPublic(Element)` helper method.
* Add `AbstractStandardProcessor.errorIfProcessingOverAndDeferredTypesUnprocessed()` helper method.

### [v0.28](https://github.com/realityforge/proton/tree/v0.28) (2020-01-29) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.27...v0.28)

Changes in this release:

* Further compatibility fixes by using `TypeMirror.getKind()` rather than `instanceof SomeType`.
* Change the `SuppressWarningsUtil` code so that id a class is a nested class and one of the outer classes are deprecated then the class is considered deprecated.

### [v0.27](https://github.com/realityforge/proton/tree/v0.27) (2020-01-29) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.26...v0.27)

Changes in this release:

* Improve compatibility with other javac compilers by using `TypeMirror.getKind()` to get the kind of the `TypeMirror` rather than using `instanceof DeclaredType` etc as some compiler have `TypeMirror` implement interfaces even if they are not of that type.
* Fix a bug where deprecated methods may not be detected and may not have appropriate suppressions added in `SuppressWarningsUtil`

### [v0.26](https://github.com/realityforge/proton/tree/v0.26) (2020-01-23) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.25...v0.26)

Changes in this release:

* Extract `AbstractProcessorTest.processors()` to simplify getting complete set of processors in downstream projects.
* Extract `AbstractProcessorTest.compiler()` to simplify setup of compiler.
* In the `AbstractStandardProcessor` class, stop emitting duplicate error messages if the error is about an `Element` that was not part of the current compilation round.
* Add a new annotation processor parameter `myprefix.verbose_out_of_round.errors` that controls whether `Element` that were not compiled in the current round that cause errors will produce verbose error messages to make it easier for IDE users to locate the source of the errors.

### [v0.25](https://github.com/realityforge/proton/tree/v0.25) (2020-01-23) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.24...v0.25)

Changes in this release:

* Add `AbstractProcessorTest.buildClasspath(File...)`, `AbstractProcessorTest.describeFailureDiagnostics(Compilation)` and `AbstractProcessorTest.assertCompilationSuccessful(Compilation)` to make it easier for downstream tests to support multi-stage compilations while still generating useful errors when failures occur.

### [v0.24](https://github.com/realityforge/proton/tree/v0.24) (2020-01-23) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.23...v0.24)

Changes in this release:

* Add `AbstractProcessorTest.outputFiles(...)` overloaded method that omits the filter under the assumption that all files are emitted to the target directory. This is useful when building up multi-stage compiles and all output should be written to the target directory so that it can be picked up by a subsequent compile stage

### [v0.23](https://github.com/realityforge/proton/tree/v0.23) (2020-01-23) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.22...v0.23)

Changes in this release:

* Refactor `AbstractProcessorTest.outputFile()` and invoke it from existing test infrastructure.

### [v0.22](https://github.com/realityforge/proton/tree/v0.22) (2020-01-23) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.21...v0.22)

Changes in this release:

* Extract `AbstractProcessorTest.outputFiles()` to make it easier to emit files into intermediate directories in downstream projects.

### [v0.21](https://github.com/realityforge/proton/tree/v0.21) (2020-01-23) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.20...v0.21)

Changes in this release:

* Extract `AbstractProcessorTest.outputFile()` to make it easier to emit files into intermediate directories in downstream projects.

### [v0.20](https://github.com/realityforge/proton/tree/v0.20) (2020-01-21) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.19...v0.20)

Changes in this release:

* Refactor `AbstractStandardProcessor.performAction` to use generics to support processing arbitrary `Element` subtypes.

### [v0.19](https://github.com/realityforge/proton/tree/v0.19) (2020-01-21) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.18...v0.19)

Changes in this release:

* Address crash that resulted when the `ProcessorException._element`  field referred to a parameter of a method or a constructor.

### [v0.18](https://github.com/realityforge/proton/tree/v0.18) (2020-01-20) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.17...v0.18)

Changes in this release:

* Upgrade the `com.google.truth` artifact to version `0.44`.
* Upgrade the `com.google.testing.compile` artifact to version `0.18`.
* Upgrade the `com.squareup:javapoet` artifact to version `1.12.0`.
* Import the `IOUtil` util class from downstream projects.

### [v0.17](https://github.com/realityforge/proton/tree/v0.17) (2020-01-20) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.16...v0.17)

Changes in this release:

* Emit a stack trace when an `IOException` occurs. Previously the code would just emit the message component of the IO error which made tracking down the root cause difficult. The code also crashed if there was no message supplied to the `IOException`.

### [v0.16](https://github.com/realityforge/proton/tree/v0.16) (2020-01-15) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.15...v0.16)

Changes in this release:

* Extract `JsonUtil` and `ResourceUtil` from downstream libraries. Basic utilities for emitting files and resources from an annotation processor.

### [v0.15](https://github.com/realityforge/proton/tree/v0.15) (2020-01-15) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.14...v0.15)

Changes in this release:

* Add `AbstractProcessorTest.inputs(String... classnames)` for building up a set of input fixtures.
* Add `AbstractProcessorTest.assertSuccessfulCompile(...)` method variant that accepts a predicate for selecting which files to save to the filesystem.

### [v0.14](https://github.com/realityforge/proton/tree/v0.14) (2020-01-13) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.13...v0.14)

Changes in this release:

* Expose `AbstractStandardProcessor.deferElement(...)` so that annotation processors can schedule elements for processing in the next processing round.
* Expose `AbstractStandardProcessor.performAction(...)` so that subclasses can perform the same error recovery actions as the base class.

### [v0.13](https://github.com/realityforge/proton/tree/v0.13) (2020-01-12) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.12...v0.13)

Changes in this release:

* Add `SuperficialValidation.validateType(...)` and `SuperficialValidation.validateTypes(...)` helper methods.

### [v0.12](https://github.com/realityforge/proton/tree/v0.12) (2020-01-09) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.11...v0.12)

Changes in this release:

* Add `MemberChecks.mustNotHaveAnyTypeParameters(...)` helper method.

### [v0.11](https://github.com/realityforge/proton/tree/v0.11) (2020-01-05) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.10...v0.11)

Changes in this release:

* Replace `ElementsUtil.isEnclosedInNonStaticClass(TypeElement)` with easier to understand `ElementsUtil.isNonStaticNestedClass(TypeElement)` method.

### [v0.10](https://github.com/realityforge/proton/tree/v0.10) (2020-01-05) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.09...v0.10)

Changes in this release:

* Add an overloaded `AbstractStandardProcessor.toFilename(...)` method that accepts a prefix and postfix parameter to simplify deriving file names for expected files that are derived from input classes.
* Change the default behaviour of `AbstractStandardProcessor` to emit all files generated from annotation processor except `.class` files. Subclasses that override `AbstractStandardProcessor.emitGeneratedFile()` will need to invoke super method otherwise `.class` files will begin to be emitted.
* Add `ElementsUtil.isEnclosedInNonStaticClass(TypeElement)` helper method.

### [v0.09](https://github.com/realityforge/proton/tree/v0.09) (2019-12-30) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.08...v0.09)

Changes in this release:

* Extract `AbstractStandardProcessor.errorIfProcessingOverAndInvalidTypesDetected()` to simplify reuse in subclasses.
* Expose `ElementsUtil.getTopLevelElement(Element)` that returns the top-level class, interface, enum, etc within a package that contained the specified `Element`.
* Expose `AbstractStandardProcessor.processTypeElements(...)` helper methods to make subclassing easier.
* Remove `AbstractStandardProcessor.process()` method and instead require that it is implemented in subclasses.

### [v0.08](https://github.com/realityforge/proton/tree/v0.08) (2019-12-30) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.07...v0.08)

Changes in this release:

* Add several overloaded methods to `MemberChecks` that assume a `null` value for `alternativeSuppressWarnings`.
* Add an overloaded method `MemberChecks.mustReturnAnInstanceOf(...)` that accepts a `TypeMirror` for the expected type.
* Add an overloaded methods `ElementsUtil.isWarningNotSuppressed(...)` and `ElementsUtil.isWarningSuppressed(...)` that assume a `null` value for `alternativeSuppressWarnings`.

### [v0.07](https://github.com/realityforge/proton/tree/v0.07) (2019-12-29) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.06...v0.07)

Changes in this release:

* Decouple `GeneratorUtil` from `com.google.auto:auto-common`.
* Change the `GeneratorUtil.getPackageElement(...)` to take an `Element` so can retrieve the package of any element rather than just a`TypeElement`.
* Decouple `AnnotationsUtil` from `com.google.auto:auto-common`. This involved importing and reimplementing `AnnotationsUtil.getAnnotationValuesWithDefaults()` from `auto-common`. The original `auto-common`
* Expose `AbstractStandardProcessor.reportError(...)` method as protected access so subclasses can invoke.
* Add `AbstractStandardProcessor.emitTypeSpec(...)` helper method as it appeared in all downstream classes. In the future it will also make it possible for the toolkit to track processing statistics.
* Decouple `AbstractStandardProcessor` from `com.google.auto:auto-common`.
* Remove unused dependencies `com.google.auto:auto-common` and `com.google.guava:guava`.
* Add `ElementsUtil.isWarningNotSuppressed(...)` utility method to compliment `ElementsUtil.isWarningSuppressed(...)` as the first form is that which is usually used in downstream libraries.
* Introduce several `AbstractProcessorTest.assertCompilesWith*(...)` helper methods to aid testing annotation processors using common test patterns.
* Add a template method `AbstractProcessorTest.getFixtureKeyPart()` that makes it possible to customize the property used to retrieve the fixture dir.

### [v0.06](https://github.com/realityforge/proton/tree/v0.06) (2019-12-25) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.05...v0.06)

Changes in this release:

* Rename library to `proton` and define a separate module named `core` that contains the same contents as was previously in the `proton-processor-pack` artifact.
* Introduce a `qa` module the contains the base class we use to test the annotation processors.

### [v0.05](https://github.com/realityforge/proton/tree/v0.05) (2019-12-25) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.04...v0.05)

Changes in this release:

* Extract the logic for determining whether unresolved types are processed into `AbstractStandardProcessor.shouldDeferUnresolved()` so that subclasses can override the behaviour.

### [v0.04](https://github.com/realityforge/proton/tree/v0.04) (2019-12-24) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.03...v0.04)

Changes in this release:

* Add missing variant of `SuppressWarningsUtil.addSuppressWarningsIfRequired(...)` for FieldSpec.Builder types.
* Add variants of `SuppressWarningsUtil.addSuppressWarningsIfRequired(...)` for ParameterSpec.Builder type.

### [v0.03](https://github.com/realityforge/proton/tree/v0.03) (2019-12-24) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.02...v0.03)

Changes in this release:

* Make the `AnnotationsUtil.getRepeatingAnnotations(...)` utility method public.

### [v0.02](https://github.com/realityforge/proton/tree/v0.02) (2019-12-24) · [Full Changelog](https://github.com/realityforge/proton/compare/v0.01...v0.02)

Changes in this release:

* Introduce `AnnotationsUtil.getRepeatingAnnotations(...)` utility.

### [v0.01](https://github.com/realityforge/proton/tree/v0.01) (2019-12-24) · [Full Changelog](https://github.com/realityforge/proton/compare/5d8d0136c796a3732c5d74715aa5e01764a9eaa9...v0.01)

Changes in this release:

‎🎉 Initial project release ‎🎉
