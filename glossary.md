# Glossary


## Subjekt 

- **Suite**: A global objects containing Parameters, Macros, Subjects and a Configuration.
- **Parameter**: a set of values identified by a unique name. 
- **Macro**: a function that takes a set of arguments and returns a set of possible values. 
- **DefinedParameter**: a Parameter fixed to one of its possible values.
- **DefinedMacro**: a Macro fixed to one of its possible values.
- **Resolvable**: an object that, fixed a Context, can be resolved to a single value.
- **Context**: one of the fixed set of DefinedParameters and DefinedMacros from the possible permutations of Parameters 
and Macros values.
- **Instance**: a Resolvable that has been resolved to a single value by fixing the Context.
- **Subject**: a conceptual unit that contains Resolvables. It encapsulates the configuration and behavior required to 
generate results in the form of ResolvedSubjects.
- **ResolvedSubject**: a result obtained from a Subject by transforming its Resolvables into Instances (i.e. by fixing 
a Context).
- **ResolvedSuite**: a collection of ResolvedSubjects obtained resolving all Subjects in a Suite.
- **Configuration**: a set of values that can be used to configure the generation.

- **Exporter**: a domain entity which converts a ResolvedSuite into a given format.
- **Result**: a domain object that represents the result produced by an Exporter.
- **Source**: a domain object that provides all the Suite's data.
- **SuiteFactory**: a domain entity that creates a Suite from a Source.
- **Module**: a library providing a set of Parameters and DefinedMacros.
- **Mapper**: a domain entity that applies a conversion to a ResolvedSuite (e.g. code linter).

## API

- **User**: a person who interacts with the API.
- **Source**: a configuration object that can be saved and edited.
- **Result**: an entity that represents the result of the Source elaboration.
- **UserRegistry**: an entity which manage users' repository.
- **SourceRegistry**: an entity which manage source' repository.
- **AuthenticationService**: an entity which manage users' authentication.
- **GenerationService**: an entity which manage the Source elaboration.
- **UserEvent**: an event that is triggered by an action involving the User in UserRegistry (e.g. creation, etc.).
- **AuthenticationEvent**: an event that is triggered by an action involving Authentication in UserRegistry (e.g. login, logout).
- **SourceEvent**: an event that is triggered by an action involving the SourceRegistry (e.g. creation, update, etc.).
- **GenerationEvent**: an event that is triggered by a request for a Source elaboration.

```plantuml
@startuml
object Suite 
object ResolvedSuite

object Subject
object ResolvedSubject

object Resolvable
object Instance

object Parameter
object DefinedParameter

object Macro
object DefinedMacro

Suite -> ResolvedSuite
Subject -> ResolvedSubject :n 
Resolvable -> Instance : n

Parameter -> DefinedParameter : n
Macro -> DefinedMacro : n

hide empty members
@enduml
```