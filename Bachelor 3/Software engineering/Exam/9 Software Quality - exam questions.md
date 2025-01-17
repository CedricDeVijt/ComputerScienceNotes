## You should know the answers to these questions

### Why is software quality more important than it was a decade ago?

Software is now ubiquitous, with critical dependencies in areas such as health, finance, and infrastructure. Failures can result in lawsuits, financial loss, or even endanger lives. As society's reliance on software grows, so does the cost of poor quality.

### Can a correctly functioning piece of software still have poor quality? Why?

Yes, software can function as specified yet exhibit poor quality if it lacks attributes such as maintainability, usability, or efficiency. For instance, it may be difficult to modify or require excessive resources.

### If quality control can’t guarantee results, why do we bother?

Quality control eliminates coincidence and makes achieving quality repeatable. It reduces risks, improves reliability, and helps ensure intermediate steps meet standards.

### What’s the difference between an external and an internal quality attribute? And between a product and a process attribute?

- **External vs. Internal**: External attributes relate to the system's behavior in its environment (e.g., usability), while internal attributes pertain to the software's description (e.g., code complexity).
- **Product vs. Process**: Product attributes describe the final deliverable, whereas process attributes describe the development method.

### What’s the distinction between correctness, reliability, and robustness?

- **Correctness**: Conformance to specifications.
- **Reliability**: The probability of the software operating as expected over time.
- **Robustness**: The system’s ability to handle unspecified or abnormal circumstances.

### How can you express the “user friendliness” of a system?

User-friendliness can be measured by the time users need to learn the system. This includes considerations for different user types, such as novices and experts.

### Can you name three distinct refinements of “maintainability”? What do each of these names mean?

1.  **Repairability**: Effort required to fix defects.
2.  **Adaptability**: Effort required to adjust to changing requirements.
3.  **Portability**: Effort required to transition to new platforms.

### What is meant with “short time to market”? Can you name 3 related quality attributes and provide definitions for each of them?

- **Short time to market**: Rapid delivery of features from specification to production.
  Related attributes:
  1.  **Productivity**: Output relative to resources.
  2.  **Timeliness**: Adherence to schedules.
  3.  **Visibility**: Transparency of process and project status.

### Name four things which should be recorded in the review minutes.

1.  What was reviewed.
2.  Who participated.
3.  Findings and conclusions.
4.  Decisions made (e.g., accepted, conditionally accepted, or rejected).

### Explain briefly the three items that should be included in a quality plan.

1.  Desired product qualities and their assessment.
2.  Organizational standards to be applied.
3.  Quality assessment process (e.g., quality reviews).

### What’s the relationship between ISO9001, CMMI standards and an organization’s quality system? How do you get certified?

ISO9001 and CMMI define frameworks for quality management and maturity. Organizations adopt these standards to structure their quality systems. Certification requires audits by external accreditation bodies.

### Can you name and define the 5 levels of CMMI?

1.  **Initial**: Processes are ad hoc.
2.  **Managed**: Formal processes exist but are reactive.
3.  **Defined**: Processes are proactive and institutionalized.
4.  **Quantitatively Managed**: Data-driven improvements.
5.  **Optimizing**: Continuous process refinement.

### Where would “use-cases” as defined in chapter 3 fit in the table of core process areas (p. 32)? Motivate your answer shortly.

Use-cases fit in **Requirements Management (REQM)** at Level 2. They ensure requirements are traced and aligned with the system's goals.

---

## You should be able to complete the following tasks

### Given a piece of code and a coding standard, review the code to verify whether the standard has been adhered to.

Use checklists and conventions, such as formatting, naming standards, and comments, as specified in the coding guidelines (e.g., Java Code Conventions).

---

## Can you answer the following questions?

### Given the Quality Attributes Overview table, argue why the crosses and blanks occur at the given positions.

External attributes like usability require user interaction, whereas internal attributes like verifiability rely on the product’s description. The distribution aligns with their nature.

### Why do quality standards focus on process and internal attributes instead of the desired external product attributes?

Processes and internal attributes are controllable during development, ensuring consistent quality. External attributes emerge only after the product is operational.

### Why do you need a quality plan? Which topics should be covered in such a plan?

To define desired qualities, set standards, and plan assessments. Topics: attributes, standards, and assessment processes.

### How should you organize and run a review meeting?

- Involve 3-5 reviewers.
- Prepare with checklists.
- Limit meetings to under 2 hours.
- Record minutes summarizing findings and decisions.

### Why are coding standards important?

They ensure consistency, improve maintainability, and reduce errors.

### What would you include in a documentation review checklist?

- Completeness of scope.
- Consistency of data models.
- Traceability of requirements.
- Feasibility assessments.

### How often should reviews be scheduled?

Regularly, based on milestones or stages in the development lifecycle.

### Could you create a review check-list for ATAM?

Yes, include architecture decisions, trade-off analyses, and alignment with quality attributes.

### Would you trust software from an ISO 9000 certified company? And if it were CMMI?

ISO9000 ensures process quality but not product quality. CMMI certification indicates higher process maturity.

### You are supposed to develop a quality system for your organization. What would you include?

Standards, guidelines, review processes, training, and metrics for quality assessment.

### Where would “testing” fit in the table of core process areas (p. 32)? Does it cover a single row or not? Argue why (not)?

Testing spans multiple rows: **Verification** (internal), **Validation** (external), and supports Quality Assurance.
