#### Purpose of the Document
- The document provides a fictional requirements specification for the SmartUniversity platform.
- The platform aims to replace existing learning systems, similar to SisA and Blackboard.
- The document will be used for assignments within a Software Engineering course.
- Some parts of the document are intentionally vague to support exercises.

#### Introduction
- **Current Systems**: Existing platforms, such as Blackboard and SisA, have become outdated.
- **Goal**: Replace these platforms with a comprehensive learning solution called SmartUniversity.
- **Partnership**: Developed by AnSyMo research group and Flemish start-up SmartUniversity.
- **Scope**: Covers enrolment, lectures, assignments, grading, administrative tasks, etc.
- **Technologies**: Must use state-of-the-art technologies like AI, mobile compatibility (smartphones/smartwatches).
- **Security Considerations**: Attention to financial transactions, privacy, two-factor authentication, and GDPR compliance.
- **Longevity**: System must be adaptable and scalable for future needs.
- **Compatibility**: Should integrate with existing university infrastructure (e.g., single sign-on, Microsoft Outlook).

#### Description of the System
- **Student Enrolment**:
  - Students can enroll in a program and courses at the start of the academic year.
  - Enrollment applications are processed by administrative staff.
  - Late enrollment requires administrative approval.
  - **Course Selection**: Students can view prerequisites and study credits while selecting courses.
  - **Notifications**: Students receive an email once courses are approved and reminders for unpaid tuition.
  
- **Personalized Program Recommendations**:
  - Before selecting a program, students answer questions to receive recommended programs.
  - AI-driven course recommendations are also provided when selecting courses.
  - **AI Integration**: Uses ChatGPT for generating personalized suggestions.
  - **Data Collection**: A central database will collect data on students (e.g., grades, interests).
  - **Data Security**: Blockchain technology ensures data security and privacy.

- **Lecture Management**:
  - Professors can upload and livestream lectures.
  - **Uptime and Quality Requirements**: 99.99% uptime, minimum 720p quality for recordings/live broadcasts.
  - **Scalability**: Video streaming infrastructure must be flexible to manage variable loads.
  - **Interactive Features**: Students can interact using microphones, and mobile polling options should be available.
  - **Calendar Integration**: Lectures can be synchronized with digital calendars for students and faculty.

- **Assignments and Grading**:
  - **Assignment Management**: Assistants create obligatory and optional assignments.
  - **Submission and Deadlines**: Students can view and submit assignments before the deadline.
  - **Reminders**: Students receive reminders for unsolved assignments.
  - **Missed Deadlines**: Missing a deadline results in a grade of zero.
  - **Plagiarism Detection**: Tool to detect plagiarism, including use of ChatGPT for assignments.
  - **Grading Overview**: A page for students to view scores for assignments and total grades.
  - **Score Upload**: Assistants and professors can upload assignment and exam grades.
  - **Data Storage**: Scores and related data must be stored securely for up to 10 years after graduation.

- **Program Adjustments and Reporting**:
  - **Program Review**: University can adjust courses and add new programs.
  - **Statistical Reports**: Platform must generate reports such as pass rates, graduation rates, workload of professors, etc.
  - **Developer Accessibility**: IT department developers should be able to easily add new report types. 

#### Summary of Key Requirements
- **Technology**: AI for personalization, blockchain for data security, mobile compatibility, and state-of-the-art software engineering practices.
- **Security and Compliance**: Emphasis on security, privacy, GDPR, and secure data handling.
- **Student Interaction**: Enrollment management, personalized recommendations, interactive learning, assignment handling, and grading feedback.
- **Scalability and Availability**: 99.99% uptime for video streaming, flexible infrastructure for varying demands.
- **Data Management**: Secure storage, integration with existing systems, and compliance with data retention policies.
- **Adaptability**: Platform must evolve with changing academic and administrative needs, with ease of adding features for IT developers.