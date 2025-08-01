# BMC-Anvil

This GitHub Organization holds all repositories related to BareMetalCode's Anvil project.

## Repository organization

Momentarily, GitHub does not support folders, therefore, nesting related repositories is not possible.<br>
With many repositories this creates a bit of a confusing view.

A workaround is to use a _pseudo-qualified-names_ approach.<br>
Organizing repositories could be done by naming them like:

- [...]
- `com.project.topic.subtopicA.suptopicB.xxx.actual_name_of_repo`
- [...]
- com.project.templates.gradle.parent_config
- com.project.templates.gradle.spring_config
- com.project.templates.maven.parent_config
- com.project.templates.maven.quarkus_config

Which will make it clear(er) at a glance... (I wished, though...)

After renaming many repos, I find that this approach is evidently not a better solution than actually having folders support, but a little clearer
view of relations between repositories.

I'm super happy though... it is organized, kind of weird to read... 
