# Reproducible of Languagetool 6.6 error

This project is reproducible to the error.

This works well for LanguageTool 6.5, and it raises an error when increment LT version. 

it is because LT 6.5 published `languagetools-parent` on Maven central, but LT 6.6 don't.

See https://repo1.maven.org/maven2/org/languagetool/languagetool-parent/


## Command to reproduce
```shell
 ./gradlew dependencies
```

## Log of the error

```log
Configuration on demand is an incubating feature.

> Task :dependencies

------------------------------------------------------------
Root project 'languagetool-reproduce-lt6-6-pom-error'
------------------------------------------------------------

annotationProcessor - Annotation processors and their dependencies for source set 'main'.
No dependencies

compileClasspath - Compile classpath for source set 'main'.
\--- org.languagetool:languagetool-core:6.6 FAILED

compileOnly - Compile-only dependencies for the 'main' feature. (n)
No dependencies

default - Configuration for default artifacts. (n)
No dependencies

implementation - Implementation dependencies for the 'main' feature. (n)
\--- org.languagetool:languagetool-core:6.6 (n)

mainSourceElements - List of source directories contained in the Main SourceSet. (n)
No dependencies

runtimeClasspath - Runtime classpath of source set 'main'.
\--- org.languagetool:languagetool-core:6.6 FAILED

runtimeElements - Runtime elements for the 'main' feature. (n)
No dependencies

runtimeOnly - Runtime-only dependencies for the 'main' feature. (n)
No dependencies

testAnnotationProcessor - Annotation processors and their dependencies for source set 'test'.
No dependencies

testCompileClasspath - Compile classpath for source set 'test'.
\--- org.languagetool:languagetool-core:6.6 FAILED

testCompileOnly - Compile only dependencies for source set 'test'. (n)
No dependencies

testImplementation - Implementation only dependencies for source set 'test'. (n)
No dependencies

testRuntimeClasspath - Runtime classpath of source set 'test'.
\--- org.languagetool:languagetool-core:6.6 FAILED

testRuntimeOnly - Runtime only dependencies for source set 'test'. (n)
No dependencies

(n) - A dependency or dependency configuration that cannot be resolved.

A web-based, searchable dependency report is available by adding the --scan option.

BUILD SUCCESSFUL in 567ms
1 actionable task: 1 executed
```

## Conditions

There is ivy configuration for repository.

```gradle
    // 'repository' for getting docbook xsd
    ivy {
        url = 'https://docbook.org/xml'
        patternLayout {
            artifact '[revision]/[module]-[revision].[ext]'
        }
        content {
            includeGroup 'docbook'
        }
        metadataSources {
            artifact()
        }
    }
```