# JAVA_FLOW.md

# What

This flow is the selected one for java projects whether they are libraries or containerized applications.

# Why

Self explanatory.

# How

Each one of the actions is also self-descriptive, and if there are more insights required, they will be documented shortly as comments in the actions
themselves.

The actions used by this flow are:

- [Set up Java (get the JDK)](../actions/common/semver)
- Set up Maven (get the wrapper, setup config)
- Set up Dependency cache
- Run Static Analysis (Checkstyle / Sonar / Qodana / etc.)
- Build and Test
- Set up SemVer and Git-Tag
- Set up Project Version
- Deploy JAR Library
- Deploy Docker Container

```mermaid
stateDiagram-v2
    direction LR
%% Nodes
    preProcessing: Pre-Processing Flow
    javaFlow: JAVA Flow
    postProcessing: Post-Processing Flow
    action0: Set up Java (get the JDK)
    action1: Set up Maven (get the wrapper, set up config)
    action2: Set up Dependency cache
    action3: Run Static Analysis (Checkstyle / Sonar / Qodana / etc)
    action4: Build and Test
    action5: Set up SemVer and Git-Tag
    action6: Set up Project Version
    action7: Deploy JAR Library
    action8: Deploy Docker Container
%% Pipeline Sequence    
    [*] --> preProcessing
    preProcessing --> javaFlow
    javaFlow --> postProcessing
    postProcessing --> [*]
%% Flow    
    state javaFlow {
        direction TB
        state selector <<choice>>
        [*] --> action0
        action0 --> action1
        action1 --> action2
        action2 --> action3
        action3 --> action4
        action4 --> action5
        action5 --> action5: Create a version and push the tag.\n Retry in case of a tag collision.
        action5 --> action6
        action6 --> selector
        selector --> action7: buildType == JAR
        selector --> action8: buildType == DOCKER / NATIVE
        action7 --> [*]
        action8 --> [*]
    }


```