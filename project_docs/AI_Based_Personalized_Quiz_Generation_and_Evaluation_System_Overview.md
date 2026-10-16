# AI-Based Personalized Quiz Generation and Evaluation System

## Project Overview

**Document type:** Project Overview and Scope\
**Version:** 1.1\
**Status:** Draft for team review\
**Primary users:** Professors and Students\
**Project approach:** Modular monolith with a shared quiz-generation and
evaluation engine

------------------------------------------------------------------------

## 1. Project Overview

The **AI-Based Personalized Quiz Generation and Evaluation System** is a
web application that helps professors prepare and assign quizzes and
helps students improve through automated evaluation, performance
analytics, and personalized practice.

The system has two primary roles:

-   **Professor:** Creates classes, generates or manually writes
    questions, reviews and edits quizzes, assigns assessments,
    configures assessment settings, and analyzes class performance.
-   **Student:** Joins classes, attempts assigned quizzes, receives
    scores and feedback, reviews personal performance, and generates
    personalized practice quizzes based on weak topics.

The core idea is to connect **quiz generation → evaluation → performance
analysis → personalized practice** in one learning cycle.

The application is not intended to become a full Learning Management
System (LMS). Class and enrollment functionality exists only to support
quiz assignment and performance analysis.

## 2. Problem Statement

Preparing quizzes manually can take time, while a total score alone does
not tell students what they should study next. Professors also need a
way to understand which concepts students find difficult.

The proposed system addresses these problems by:

1.  Generating quiz questions using AI from a topic and, optionally,
    uploaded study material.
2.  Letting professors review and edit generated questions before
    publishing assessments.
3.  Evaluating objective responses automatically and providing
    explanations.
4.  Showing students their marks, history, progress, and topic-level
    strengths and weaknesses.
5.  Giving professors individual and class-level performance analytics.
6.  Using previous performance to recommend topics and generate targeted
    practice quizzes.

## 3. Project Objectives

-   Reduce the manual effort involved in quiz preparation.
-   Support both AI-generated and manually written questions.
-   Provide controlled quiz assignment from professors to students.
-   Evaluate objective questions consistently.
-   Identify strengths and weaknesses at topic level.
-   Personalize practice using previous attempts and accuracy.
-   Help professors identify difficult concepts across a class.
-   Keep the implementation achievable for a three-member final-year
    team.

## 4. Scope

### 4.1 Core Scope

  -----------------------------------------------------------------------
  Area                                Included functionality
  ----------------------------------- -----------------------------------
  User management                     Registration, login, Professor and
                                      Student roles

  Class management                    Professor creates a class; students
                                      join using a code

  Quiz generation                     Generate questions from a topic and
                                      configuration

  Question management                 Review, edit, add, and remove
                                      questions

  Quiz assignment                     Assign a quiz to a class or
                                      selected students

  Assessment settings                 Time limit, marks, attempt limit,
                                      and deadline

  Quiz attempts                       Students answer and submit assigned
                                      quizzes

  Evaluation                          Automatically score supported
                                      objective question types

  Feedback                            Show results and explanations
                                      according to quiz settings

  Analytics                           Individual and class-level topic
                                      performance

  Personalization                     Recommend weak topics and generate
                                      practice quizzes

  Revision                            Review incorrect answers and
                                      generate additional practice

  History                             Store quiz attempts, scores, and
                                      progress
  -----------------------------------------------------------------------

### 4.2 Optional Enhancements

Implement these only after the core end-to-end workflow works:

-   PDF or text upload for source-grounded quiz generation.
-   Fill-in-the-blank questions.
-   Timed examination mode with configurable attempt limits.
-   Revision mode focused on previously incorrect answers.
-   AI-assisted short-answer evaluation using a rubric.
-   Study recommendations based on performance trends.
-   Export quiz or result reports.

### 4.3 Out of Scope for the Initial Version

-   Attendance management and timetables.
-   Live classes or video conferencing.
-   Social networking or messaging.
-   Webcam-based proctoring.
-   A full LMS with assignments, course content, and attendance.
-   Training a custom large language model from scratch.
-   Complex machine-learning recommendation models.

## 5. User Roles and Workflows

### 5.1 Professor

A professor should be able to:

1.  Register and log in.
2.  Create and manage classes and share a class join code.
3.  Create a quiz by entering a topic and selecting question count,
    difficulty, and question types.
4.  Optionally provide a PDF or text source if source upload is
    implemented.
5.  Generate questions using AI or create questions manually.
6.  Review, edit, add, or remove questions.
7.  Configure marks, time limit, allowed attempts, and deadline.
8.  Publish and assign the quiz to a class or selected students.
9.  View submissions, marks, and completion status.
10. Analyze individual student performance and common weak topics across
    the class.

**Example:** A professor generates a quiz on recursion, reviews the
questions, assigns it to a Data Structures class, and later sees that
many students struggled with recursive base cases.

### 5.2 Student

A student should be able to:

1.  Register and log in.
2.  Join a class using a valid code.
3.  View assigned quizzes, availability, and deadlines.
4.  Attempt and submit a quiz.
5.  View marks and feedback when released by the professor.
6.  View quiz history, progress, and topic-level accuracy.
7.  Identify strong and weak topics.
8.  Generate independent practice quizzes based on selected or
    recommended topics.
9.  Review previous incorrect answers and attempt new questions on the
    same concepts.
10. Track improvement over time.

**Example:** A student scores poorly on recursion. The system identifies
recursion as a weak topic, recommends foundational practice, and
generates a new practice quiz. Practice scores remain separate from
official assessment marks.

## 6. High-Level Architecture

``` mermaid
flowchart TB
    Professor["Professor"]
    Student["Student"]

    subgraph Frontend["Frontend Application"]
        ProfessorUI["Professor Dashboard"]
        StudentUI["Student Dashboard"]
        QuizUI["Quiz Attempt Interface"]
        AnalyticsUI["Performance Views"]
    end

    subgraph Backend["Backend Application - Modular Monolith"]
        Auth["Authentication and Authorization"]
        Classes["Class and Enrollment Management"]
        QuizManagement["Quiz Management"]
        Generation["AI Quiz Generation"]
        Validation["Question Validation"]
        Evaluation["Evaluation Service"]
        Analytics["Performance Analytics"]
        Personalization["Personalization Engine"]
    end

    DB[("Relational Database")]
    AI["External AI Model API"]
    Files["Optional File Storage"]

    Professor --> ProfessorUI
    Student --> StudentUI
    ProfessorUI --> Auth
    StudentUI --> Auth
    ProfessorUI --> Classes
    ProfessorUI --> QuizManagement
    StudentUI --> QuizManagement
    StudentUI --> QuizUI
    StudentUI --> AnalyticsUI

    QuizManagement --> Generation
    Generation --> AI
    Generation --> Validation
    Validation --> QuizManagement
    Generation -. "Optional source file" .-> Files

    Classes --> DB
    Auth --> DB
    QuizManagement --> DB
    Evaluation --> DB
    DB --> Analytics
    Analytics --> Personalization
    Personalization --> Generation
    QuizUI --> Evaluation
    Analytics --> AnalyticsUI
    QuizManagement --> Analytics
```

### 6.1 Architecture Components

**Frontend application**

Provides professor and student dashboards, quiz creation screens,
question review, quiz attempts, results, and analytics.

**Authentication and authorization**

Verifies user identity and enforces role and resource permissions.
Authorization must be enforced in the backend, not only by hiding
frontend controls.

**Class and enrollment management**

Connects professors to their classes and students to enrolled classes.
It supports join codes and class membership without implementing
unrelated LMS functionality.

**Quiz management**

Owns quiz lifecycle and assignment rules: draft, review, published,
closed, and archived states as appropriate. It distinguishes
professor-assigned assessments from student-generated practice quizzes.

**AI quiz generation**

Builds requests for the AI provider and converts the response into the
application's question format. It should not be responsible for official
score calculation.

**Question validation**

Checks the structure and completeness of generated questions, option
counts, answer references, duplicates, and other detectable issues.
These checks cannot guarantee factual correctness.

**Evaluation service**

Evaluates student responses against stored answer keys and scoring
rules. Objective scoring should be deterministic.

**Performance analytics**

Aggregates attempt results into individual and class-level statistics.

**Personalization engine**

Uses stored performance and explicit rules to recommend topics and
difficulty for practice quizzes.

**Database**

Stores users, classes, enrollments, quizzes, questions, attempts,
responses, and topic performance.

**External AI provider**

Generates questions and explanations. API credentials must remain on the
server. The system should handle provider failures and rate limits.

**Optional file storage**

Used only if PDF or document uploads are included. Text extraction and
source references should be handled before or during generation.

## 7. Major Components in Detail

### 7.1 Authentication and Authorization

Responsibilities:

-   Register and authenticate users.
-   Assign and enforce Professor or Student roles.
-   Verify class ownership and enrollment.
-   Prevent students from accessing other students' private results.
-   Prevent students from publishing or editing professor-owned
    assessments.
-   Protect answer keys before the permitted result-release time.

### 7.2 Class and Topic Management

Responsibilities:

-   Create and update classes.
-   Generate unique join codes.
-   Enroll students through valid codes.
-   Associate classes with quizzes.
-   Allow professors to organize topics and subjects as needed.

Keep this module small. It exists to support quiz assignment and
analytics, not to recreate a college portal.

### 7.3 AI Quiz Generation

**Inputs**

-   Topic or subject.
-   Difficulty.
-   Number of questions.
-   Question type.
-   Optional source text or uploaded document.

**Expected MCQ data**

-   Question statement.
-   Answer options, where applicable.
-   Correct answer or reference answer.
-   Explanation.
-   Topic tag.
-   Difficulty label.
-   Optional source reference.

**Processing steps**

1.  Validate generation parameters.
2.  Build a structured prompt.
3.  Call the AI provider.
4.  Parse the response.
5.  Validate the response schema and question fields.
6.  Detect duplicates and incomplete answer data where possible.
7.  Reject or regenerate invalid output within a limited retry count.
8.  Save accepted questions as a draft.
9.  Allow the professor to review before publishing.

Student-generated practice quizzes should also pass validation. They may
use a streamlined approval flow, but they should not bypass quality
checks.

### 7.4 Manual Question Creation and Quiz Editor

Professors should be able to:

-   Write a question manually.
-   Add or edit options.
-   Set the correct answer.
-   Edit the explanation, topic, and difficulty.
-   Remove a generated question.
-   Review the final quiz before publishing.

AI generation should assist the professor, not remove their control over
official assessments.

### 7.5 Quiz Assignment and Assessment Settings

A professor can assign a quiz to a class or selected students and
configure:

-   Start and end time or deadline.
-   Time limit.
-   Maximum attempts.
-   Marks per question and any negative marking rule, if supported.
-   When scores and explanations become visible.
-   Whether question and option order should be shuffled.

For the first version, keep the configuration limited to settings that
the team can enforce and test. A setting that exists only in the UI but
is not enforced by the backend is not a completed feature.

### 7.6 Quiz Attempt

Responsibilities:

-   Display questions and options.
-   Record responses.
-   Validate that the student is authorized to attempt the quiz.
-   Enforce availability, deadline, and attempt limits.
-   Submit answers safely and prevent duplicate submissions.
-   Preserve attempt status and timestamps.

### 7.7 Evaluation

For MCQs and true/false questions:

-   Compare the submitted answer with the stored answer key.
-   Calculate marks using the configured scoring rules.
-   Calculate the total and percentage.
-   Save question-level outcomes.
-   Release answers and explanations according to the assessment
    settings.

Short-answer evaluation is optional. If implemented, it should use an
explicit rubric and be presented as AI-assisted grading, not as
infallible judgment.

### 7.8 Performance Analytics

**Student view**

-   Marks and percentage for each attempt.
-   Quiz history and progress.
-   Topic-wise accuracy.
-   Performance by difficulty.
-   Strong and weak topics.
-   Incorrect questions and explanations, when released.

**Professor view**

-   Submission and completion rates.
-   Individual student scores.
-   Class average and score distribution.
-   Topic-wise class accuracy.
-   Topics with frequent incorrect responses.

A professor may see aggregate class weaknesses, while a student sees
their own personal weaknesses. Access must be restricted appropriately.

### 7.9 Personalized Adaptive Quizzes

The first version should use a transparent rule-based approach rather
than a trained recommendation model.

**Inputs**

-   Topic-wise accuracy.
-   Number of attempts.
-   Recent and overall performance.
-   Previously incorrect concepts.
-   Difficulty of attempted questions.

**Outputs**

-   Recommended topics.
-   Suggested difficulty.
-   Topic distribution for the next practice quiz.
-   Optional revision recommendations.

Use accuracy, attempt count, and recent performance together. Avoid changing difficulty based on a single answer. If there is insufficient history, offer a baseline quiz or let the student choose a starting difficulty.

Illustrative starting rules:

  Topic accuracy   Initial recommendation
  ---------------- ----------------------------------------
  Below 40%        Foundational practice and explanations
  40--69%          Easy-to-medium targeted practice
  70--84%          Medium practice and revision
  85% or above     Harder questions and occasional review

These are configurable heuristics, not universal learning thresholds.
Use a minimum number of attempts and consider recent performance. A new
student with little data should be allowed to choose a difficulty or
take a baseline quiz.

### 7.10 Revision Mode

Revision mode should:

-   Identify previously incorrect questions or concepts.
-   Let students review explanations.
-   Generate new questions targeting the same concepts.
-   Track later performance separately from the original assessment.

Generating new questions about a missed concept is preferable to
repeatedly showing the exact same question, because repeating an answer
can measure memory of the option rather than understanding.

## 8. Professor Workflow

``` mermaid
flowchart TD
    A["Professor logs in"] --> B["Create or select class"]
    B --> C["Configure quiz"]
    C --> D{"Question source"}
    D --> E["Generate questions using AI"]
    D --> F["Write questions manually"]
    E --> G["Validate questions"]
    F --> H["Review questions"]
    G --> H
    H --> I{"Ready to publish?"}
    I -- "No" --> J["Edit or regenerate"]
    J --> G
    I -- "Yes" --> K["Configure assessment settings"]
    K --> L["Publish and assign"]
    L --> M["Students attempt quiz"]
    M --> N["Evaluate submissions"]
    N --> O["Update analytics"]
    O --> P["Professor reviews class performance"]
```

### Workflow explanation

1.  The professor selects a class.
2.  The professor configures a quiz.
3.  Questions are generated by AI or written manually.
4.  Generated questions are validated.
5.  The professor reviews and edits the questions.
6.  The professor sets deadlines, marks, time limits, and attempt
    limits.
7.  The quiz is published and assigned.
8.  Students submit their attempts.
9.  The system evaluates objective answers.
10. The professor reviews individual and class-level analytics.

## 9. Student Assessment and Practice Workflow

``` mermaid
flowchart TD
    A["Student logs in"] --> B["View assigned quizzes"]
    B --> C["Attempt assigned quiz"]
    C --> D["Submit responses"]
    D --> E["Evaluate objective answers"]
    E --> F["Release marks and feedback when permitted"]
    F --> G["Update topic performance"]
    G --> H["Show strong and weak topics"]
    H --> I["Generate personalized practice quiz"]
    I --> J["Attempt practice quiz"]
    J --> K["Evaluate practice results"]
    K --> L["Update learning profile"]
    L --> M{"Further practice recommended?"}
    M -- "Yes" --> H
    M -- "No" --> N["Continue learning"]
```

### Workflow explanation

The student's assigned assessment produces the performance data used by
the personalization engine. The student then practices weak topics
through separate practice quizzes. The results of practice attempts
update the learning profile without silently changing official
assessment marks.

## 10. Conceptual Data Model

This is an initial domain model, not the final database schema.

``` mermaid
erDiagram
    USER ||--o{ CLASS : teaches
    USER ||--o{ ENROLLMENT : joins
    CLASS ||--o{ ENROLLMENT : contains
    CLASS ||--o{ QUIZ : receives
    USER ||--o{ QUIZ : creates
    QUIZ ||--|{ QUESTION : contains
    USER ||--o{ QUIZ_ATTEMPT : makes
    QUIZ ||--o{ QUIZ_ATTEMPT : receives
    QUIZ_ATTEMPT ||--o{ RESPONSE : contains
    QUESTION ||--o{ RESPONSE : answered_in
    USER ||--o{ TOPIC_PERFORMANCE : has

    USER {
        long id PK
        string name
        string email
        string password_hash
        string role
    }

    CLASS {
        long id PK
        long professor_id FK
        string name
        string join_code
    }

    ENROLLMENT {
        long id PK
        long class_id FK
        long student_id FK
        datetime joined_at
    }

    QUIZ {
        long id PK
        long creator_id FK
        long class_id FK
        string title
        string origin
        string status
        datetime deadline
    }

    QUESTION {
        long id PK
        long quiz_id FK
        string question_text
        string question_type
        string topic
        string difficulty
        json answer_data
    }

    QUIZ_ATTEMPT {
        long id PK
        long quiz_id FK
        long student_id FK
        decimal score
        string status
        datetime submitted_at
    }

    RESPONSE {
        long id PK
        long attempt_id FK
        long question_id FK
        json submitted_answer
        boolean is_correct
        decimal awarded_marks
    }

    TOPIC_PERFORMANCE {
        long id PK
        long student_id FK
        string topic
        decimal accuracy
        int attempt_count
        datetime updated_at
    }
```

### Entity explanations

-   **USER:** Stores shared account information and the role.
-   **CLASS:** Represents a class created by a professor.
-   **ENROLLMENT:** Links students to classes.
-   **QUIZ:** Stores quiz metadata, creator, origin, publication status,
    and assignment context.
-   **QUESTION:** Stores question text, type, topic, difficulty,
    options, and protected answer data.
-   **QUIZ_ATTEMPT:** Represents one attempt by one student.
-   **RESPONSE:** Stores the answer submitted for a question and the
    evaluation outcome.
-   **TOPIC_PERFORMANCE:** Stores or caches topic-level performance for
    dashboards and personalization.

### Data model considerations

-   Enforce unique class enrollments.
-   Keep practice quiz results distinguishable from official assessment
    results.
-   Protect answer keys from student-facing API responses.
-   Define how published questions can be edited.
-   Preserve question versions or snapshots so later edits do not alter
    historical evaluation.
-   Store enough response detail to reproduce how a score was
    calculated.
-   Decide whether topic performance is computed on demand or maintained
    as an aggregate.

## 11. AI Generation and Validation Pipeline

``` mermaid
flowchart TD
    A["Generation request"] --> B["Validate parameters"]
    B --> C["Build prompt"]
    C --> D["Call AI provider"]
    D --> E["Parse structured output"]
    E --> F{"Schema valid?"}
    F -- "No" --> G["Retry within limit or reject"]
    G --> D
    F -- "Yes" --> H["Validate fields and answer references"]
    H --> I["Check duplicates and completeness"]
    I --> J["Check source grounding when applicable"]
    J --> K["Professor review or practice approval"]
    K --> L["Store accepted quiz"]
```

### Quality and reliability rules

-   Valid JSON does not guarantee a correct answer.
-   Validate all required fields and question options.
-   Keep retries bounded.
-   Retain source references when generation is based on study material, and avoid unsupported facts outside that material.
-   Allow professors to edit official questions.
-   Provide a way to report questionable practice questions.
-   Never expose the correct answer before the configured release time.

## 12. Suggested Technology Stack

  -----------------------------------------------------------------------
  Layer                   Suggested technology    Responsibility
  ----------------------- ----------------------- -----------------------
  Frontend                React                   Professor and student
                                                  interfaces

  Backend                 Spring Boot             APIs and business logic

  Database                PostgreSQL              Persistent relational
                                                  data

  ORM                     Spring Data JPA /       Database access
                          Hibernate               

  Security                Spring Security         Authentication and
                                                  authorization

  AI integration          External LLM API        Question and
                                                  explanation generation

  API documentation       OpenAPI / Swagger       API testing and
                                                  documentation

  Optional file storage   Local storage during    Uploaded study material
                          development or suitable 
                          object storage          
  -----------------------------------------------------------------------

A **modular monolith** is recommended for the initial implementation.
Deploy one backend application with well-separated internal modules.
Microservices would add deployment and communication complexity without
being necessary for this project.

## 13. Non-Functional Requirements

### Security

-   Store password hashes rather than plaintext passwords.
-   Enforce roles and resource permissions on the backend.
-   Protect answer keys and private student results.
-   Keep AI credentials on the server.
-   Validate class membership, quiz assignment, and attempt permissions.

### Reliability

-   Handle AI timeouts, provider errors, and rate limits.
-   Reject invalid generated questions.
-   Bound retry attempts.
-   Prevent duplicate submission processing.
-   Preserve submitted responses and historical results.

### Performance

-   Avoid unnecessary AI calls.
-   Store accepted generated quizzes.
-   Paginate long histories and result lists.
-   Use efficient queries for class analytics.

### Maintainability

-   Separate application modules.
-   Define request and response DTOs.
-   Use consistent error responses.
-   Test scoring, authorization, and personalization independently.

## 14. Suggested Development Phases

### Phase 1: Foundation

-   Finalize scope, domain entities, and API contracts.
-   Implement authentication and roles.
-   Implement class creation and enrollment.
-   Set up the database and project structure.

### Phase 2: Quiz Generation and Management

-   Integrate an AI provider.
-   Generate structured questions.
-   Implement validation and question editing.
-   Add manual question creation.
-   Implement quiz publication and assignment.

### Phase 3: Quiz Attempts and Evaluation

-   Build the student quiz interface.
-   Record answers and submissions.
-   Calculate objective scores.
-   Store attempt history.
-   Implement feedback-release settings.

### Phase 4: Analytics and Personalization

-   Calculate topic-wise accuracy.
-   Build student and professor dashboards.
-   Identify weak topics.
-   Generate personalized practice quizzes.
-   Track performance across attempts.

### Phase 5: Optional Enhancements and Testing

-   Add PDF or text upload if time permits.
-   Add revision mode and timed quizzes if needed.
-   Test authorization, scoring, and AI output quality.
-   Test personalization with synthetic learner histories.
-   Run end-to-end professor and student workflows.
-   Deploy and prepare the demonstration.

## 15. Success Criteria

Evaluate the project by measurable quality rather than the number of
screens.

  -----------------------------------------------------------------------
  Area                                Evaluation
  ----------------------------------- -----------------------------------
  Generation quality                  Human-review a sample for clarity,
                                      relevance, duplication, and
                                      correctness

  Evaluation accuracy                 Compare system scores against
                                      manually calculated
                                      objective-question scores

  Personalization                     Verify that weak-topic performance
                                      changes the next practice quiz

  Analytics correctness               Compare dashboard metrics with
                                      stored attempts

  Authorization                       Test access to other classes,
                                      students' results, and answer keys

  Reliability                         Test malformed AI responses,
                                      provider failures, and duplicate
                                      submissions

  Usability                           Observe representative users
                                      completing the main workflows
  -----------------------------------------------------------------------

### End-to-end demonstration scenario

1.  A professor creates a class and shares its code.
2.  Students join the class.
3.  The professor generates, reviews, and assigns a quiz.
4.  Students attempt and submit the quiz.
5.  The system evaluates responses and releases results according to the
    settings.
6.  The professor reviews class-level weak topics.
7.  A student reviews their own weak topics and generates a practice
    quiz.
8.  The student completes practice and sees updated progress.

## 16. Decisions Requiring Team Confirmation

The following decisions affect scope or data design and should be
finalized before detailed design.

  -----------------------------------------------------------------------
  Decision                Recommended initial     Status
                          default                 
  ----------------------- ----------------------- -----------------------
  Question types          MCQ and true/false;     Proposed
                          fill-in-the-blank later 

  Study material upload   Topic-based generation  Proposed
                          first; PDF/text upload  
                          as an enhancement       

  Short-answer grading    Exclude from MVP        Proposed

  Quiz assignment         Class-wide assignment;  Needs confirmation
                          selected-student        
                          assignment only if      
                          needed                  

  Practice quiz marks     Separate from official  Recommended
                          assessment marks        

  Professor review        Required before         Recommended
                          publishing official     
                          quizzes                 

  Personalization         Rule-based using topic  Proposed
                          accuracy, attempt       
                          count, and recent       
                          performance             

  Class analytics         Individual and          Proposed
                          topic-level aggregates  

  Assessment settings     Deadline, time limit,   Needs confirmation
                          maximum attempts, and   
                          result-release policy   
  -----------------------------------------------------------------------

## 17. Final Project Definition

The project is a two-role academic quiz application centered on
AI-powered question generation, reliable evaluation, and personalized
practice.

Professors create, review, configure, and assign quizzes and analyze
class performance. Students attempt assessments, view their marks and
feedback, identify their strong and weak topics, and generate targeted
practice quizzes. The shared backend uses performance history to guide
subsequent practice.

The main technical contribution is the integration of AI-generated
questions with evaluation, topic-level analytics, and a feedback loop
that adapts future practice to each student's needs.

**Recommended MVP:** Professor and Student roles, class join codes,
AI-generated MCQs and true/false questions, manual question editing,
quiz assignment, objective evaluation, performance analytics, and
rule-based personalized practice.

The implementation should remain a modular monolith and should not
expand into a full LMS.
