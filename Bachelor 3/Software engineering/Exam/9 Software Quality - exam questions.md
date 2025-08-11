## You should know the answers to these questions

### Why is software quality more important than it was a decade ago?

Software quality is more important today than a decade ago due to the increasing reliance on digital systems in everyday life, business, and critical infrastructure. Higher customer expectations, security threats, and the complexity of modern software demand greater reliability, faster updates, and seamless user experiences.

### Can a correctly functioning piece of software still have poor quality? Why?

Yes. It can meet functional requirements yet fail in non-functional areas (e.g., maintainability, usability, portability), leading to inefficiency, difficulty in updates, or poor user experience.

### If quality control can’t guarantee results, why do we bother?

Quality control helps minimize errors and improve consistency, even if it can't guarantee perfect results. It ensures products or services meet established standards, reducing the likelihood of defects and increasing customer satisfaction.

### What’s the difference between an external and an internal quality attribute? And between a product and a process attribute?

- **External vs. Internal**: External attributes relate to the system's behavior in its environment (e.g., usability), while internal attributes pertain to the software's description (e.g., understandability).
- **Product vs. Process**: Product attributes describe the final deliverable, whereas process attributes describe the development method.

### What’s the distinction between correctness, reliability, and robustness?

- Correctness: system matches its specification (absolute).
- Reliability: probability it behaves as expected over time (relative).
- Robustness: reasonable behavior under unspecified or abnormal conditions (vague).

### How can you express the “user friendliness” of a system?

By measuring the time needed for users to learn the system, considering the target audience (novices, experts, operators, etc.).

### Can you name three distinct refinements of “maintainability”? What do each of these names mean?

- Repairability: effort to fix defects. (= corrective maintenance)
- Adaptability (Evolvability): effort to meet new requirements. (= perfective maintenance)
- Portability: effort to move to a different environment. (= adaptive maintenance)

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

1. Desired product qualities & assessment methods.
2. Applicable organizational standards.
3. Quality assessment process (e.g., reviews).

### What’s the relationship between ISO9001, CMMI standards and an organization’s quality system? How do you get certified?

ISO9001 and CMMI define frameworks for quality management and maturity. Organizations adopt these standards to structure their quality systems. Certification requires audits by external accreditation bodies.

### Can you name and define the 5 levels of CMMI?

1. Initial: ad-hoc, luck-based. Quality depends on individuals.
2. Managed: formal procedures (reactive). Quality depends on project managers.
3. Defined: institutionalized QA process. Organization is proactive.
4. Quantitatively Managed: process plus metrics. Quantitative data is necessary for improvement.
5. Optimizing: continuous improvement from feedback. Observations are used to enhance the QA process.

### Where would “use-cases” as defined in chapter 3 fit in the table of core process areas (p. 32)? Motivate your answer shortly.

They fit under Requirements Management (REQM) in Project Management (Level 2), as they specify and manage functional requirements and form part of requirements documentation.

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

Interne qualiteit leidt tot externe qualiteit + proces qualiteit leidt tot product qualiteit + externe qualiteit is pas meetbaar na afleveren van een product

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
