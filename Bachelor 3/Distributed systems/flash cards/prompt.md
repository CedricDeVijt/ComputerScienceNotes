# Role and Objective

- Generate 20 new exam questions specific to a given chapter, using the provided course content and drawing inspiration from previous exam question styles to align with the professor’s expected format.

# Process Checklist

- Begin with a concise checklist of planned steps: (1) analyze previous exam questions for style and rigor, (2) extract main concepts and subtopics from the current chapter, (3) ensure a range of question types and coverage, (4) generate questions matching required tone and difficulty, (5) review for overlap and redundancy.

# Instructions

- Accept course content for the given chapter as input.
- Review and analyze previous exam questions for consistency in style, difficulty, and coverage.
- Produce 20 unique, well-structured exam questions directly relevant to the specified chapter, matching the pedagogical intent and assessment criteria observed in the example questions.
- Provide a mix of question types (definition, comparison, application, explanation, analysis) and align question difficulty and tone with previous exams.
- Cover a wide range of subtopics within the chapter to ensure comprehensive coverage, and avoid direct repetition of previously used questions or excessive similarity.

# Context

- Inputs: Course content for the selected chapter and examples of previous exam questions from related chapters.
- Out of scope: Generating grading rubrics or questions unrelated to the specified chapter.

# Output and Validation

- Return a CSV-formatted output, with each row containing two values: the first value should be the exam question and the second value should be the answer to the question.
- After generating questions and answers, verify that each subtopic is addressed, there is appropriate variety, and there are no duplicates or excessive similarities.

# Reasoning Effort

- Set reasoning_effort = medium to ensure thoughtful synthesis appropriate to exam creation, while keeping outputs concise and clear.

# Stop Conditions and Agentic Balance

- Stop after producing exactly 20 well-constructed, relevant question-and-answer pairs for the chapter in CSV format.
- If the chapter content is incomplete, unclear, or ambiguous, pause, escalate, or request clarification before proceeding.

# Old questions:

Exam 2025-07

## Model Based

3 major fault tolerance techniques/measures are commonly followed to ensure robustness when executing RMI . Describe each of these 3 techniques and how they related to the invocation semantics.

## SOA

List and describe the 3 service models commonly used in cloud computing. Provide an example of a service following each of the three models.

## Distributed Storage

Describe the 5 stages involved in the application of map/reduce.
Describe the different operations that take place for each stage.

## Replication

Describe the CAP (aka brewer’s) theorem and its implications.
Present an example of a real setting where CAP theorem could be observed.

## Coordination

Describe the Garcia Molina (aka bully) algorithm used for elections. Provide pseudocode for the functions necessary for proper application of the algorithm. (Provide a table describing each message variable used in the pseudocode)

## DISTRIBUTED SYSTEMS

A) Describe the two types of coupled logical architectures that a distributed system may
follow. Indicate the strengths and weaknesses of each of these types.

## MIDDLEWARE

A) Indicate the main differences between Local Method Invocation and Remote Method
Invocations from the point of view of the used reference, the access and the number of
invocations that are required by the client machine (invoker).
B) Indicate what is the role of the Proxy on the Remote Method Invocation process.
Indicate how the Proxy and the Skeleton are related.

## SERVICE-ORIENTED ARCHITECTURES / CLOUD COMPUTING

A) B) Indicate the difference between the different types of multi-tenancy.
List and describe the three service models commonly used in cloud computing.

- Provide an example of a service following each of the three models.

## WEB SERVICES

A) REST architectures are characterized by several architectural constraints. Explain
each of the following constraints and indicate why each of them is desirable.
a) Client-server model, b) Caching and c) Layering
B) Describe five ways in which REST resources are described from the point of view of
REST URI design.

## MICROSERVICES

A) The Reactive Manifesto is characterized by four architectural traits.
Describe each of these traits and indicate their importance.
B) Indicate why containers are considered a preferable solution over virtual machines
(VM) for the implementations of microservices. Indicate at least one advantages and
one disadvantage of using containers.

## DISTRIBUTED STORAGE

A) Directed Acyclic Graphs (DAGs) have been proposed as a good structure to handle
disrtibuted storage and processing. Indicate how these DAG structures are defined in
the context of disrtibuted storage and processing and what are the advantages of
following this type of structure.
B) Indicate the main difference between Narrow and Wide transformation in Resilient
Distributed Datasets (RDDs). DataFrames.

## COORDINATION

A) Describe the Ricart-Agrawala algorithm and indicate how it compares with respect to
the Ring-based algorithm.
B) Describe the Garcia-Molina (Bully) algorithm and indicate how it compares with
respect to the Chang-Roberts Ring-based algorithm.

## REPLICATION

A) B) Describe the data-centric and client-centric consistency models.
Indicate what are the main advantages and disadvantages of using one over the other.
Describe the Pipelined Random Access Memory (PRAM) consistency model.
Indicate and justify whether the processes below follow the PRAM consistency model.
