# Prompts

## Lesson 1: Implementing the Plan

### Demo: Prepare the Plan for Execution

**Prompt 1: Review the Plan for Gaps**

```text
Give me a brief explanation of the feature being implemented in the plan. And point out any inconsistencies, missing information in the plan, or anything missing the project that needs to be added before the execution of the plan starts.
```

**Prompt 2: List the Open Questions**

```text
In this conversation, give me each one of the open questions to answer and document this answer in the plan to prepare for execution
```

**Prompt 3: Recommend Resolutions for Each Open Point**

```text
Provide a recommendation for each of the open points/gaps. show me your recommendation first to confirm it before moving forward. as for Unit Tests, exclude those from the scope for now.
```

**Prompt 4: Build the Execution Plan**

```text
Build a detailed execution plan in a separate file for this feature identifying the following:
 - A breakdown of standalone tasks for this feature.
 - The modified files for each, and a brief explanation for each task to use as a description to use for the task ticket.
 - What tasks can be implemented in parallel and what depends on others, and create a small diagram.
```

**Prompt 5: Document the Decisions in One Place**

```text
document the decisions from earlier and open questions in the execution file to have everything documented on one place.
```

**Prompt 6: Confirm the Open Points**

```text
for the current open points. I confirm and its accepted
```

**Prompt 7: Start the Implementation Workflow**

```text
Go ahead and start the implementation, create a workflow based on the dependencies of the tasks, run parallel tasks when applicable, and create subagents where applicable
```

## Lesson 2: Conductor as a Review Team

### Demo: Reviewing With Conductor

**Session 1 — Prompt 1: Audit Against Goals and Non-Goals**

```text
This branch contains the implementation of the plan in "reviewed-feature-plan.md". I want you to audit what is implemented in the last commit against Goals and Non-goals from the plan. Don't fix anything, but generate a new file with all the positive and negative findings and suggested action items to take.
```

**Session 2 — Prompt 1: Audit Against the Proposed Swift Surface**

```text
This branch contains the implementation of the plan in "reviewed-feature-plan.md". I want you to audit what is implemented in the last commit against Against Proposed Swift Surface, Proposed added and modified files from the plan. Don't fix anything, but generate a new file with all the positive and negative findings and suggested action items to take.
```

**Session 3 — Prompt 1: Audit Against Edge Cases and Acceptance Criteria**

```text
This branch contains the implementation of the plan in "reviewed-feature-plan.md". I want you to audit what is implemented in the last commit against Edge Cases & Acceptance criteria from the plan. Don't fix anything, but generate a new file with all the positive and negative findings and suggested action items to take.
```

## Lesson 3: Xcode Specialists

### Demo: Auditing With Xcode's Specialist Agents

**Prompt 1: Run the Dynamic Type Specialist**

```text
/xcode-integration:accessibility-dynamic-type-specialist Audit the implementation of this application, write all the violations you find in a document
```

**Prompt 2: Run the VoiceOver Specialist**

```text
/xcode-integration:accessibility-voiceover-specialist review the implementation of the application and write the audit violations in a dedicated file
```
