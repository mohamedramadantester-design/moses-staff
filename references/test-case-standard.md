# Test Case Standard

Use this reference when designing the workbook and validating its contents.

## Authoritative columns

Keep the following columns in `Test Cases`, in this order unless the user supplies a required template:

| Column | Rule |
| --- | --- |
| Test Case ID | Stable, unique identifier such as `AUTH-TC-001`. Never renumber unchanged cases during a revision. |
| Requirement ID | Source requirement, story, acceptance criterion, or `Not provided`. |
| Module | Short feature or screen name. |
| Title | Concise behavior and outcome. Prefer 5–14 words when practical. |
| Scenario Type | `Happy Path`, `Negative`, `Boundary`, or `Alternative`. |
| Test Type | Examples: `Functional`, `API`, `UI`, `Integration`, `Security`, `Accessibility`, `Performance`. Use only applicable values. |
| Preconditions | Minimum required state, role, configuration, or `None`. |
| Test Data | Specific values or data class required by the case. Do not hide test data inside prose when it matters. |
| Steps | Numbered, atomic actions separated by line breaks. |
| Expected Result | Observable result, including state or persistence when relevant. |
| Priority | `Critical`, `High`, `Medium`, or `Low` based on business and delivery order. |
| Severity | `Blocker`, `Critical`, `Major`, `Minor`, or `Trivial` based on impact if the behavior fails. |
| Automation Candidate | `Yes`, `No`, or `Review`. |
| Status | Initially `Not Run`; after execution use `Pass`, `Fail`, `Blocked`, or `Not Run`. |
| Actual Result | Blank before execution; concise observed behavior afterward. |
| Evidence / Defect | Blank before execution; afterward use an evidence path, defect ID, or blocking reason. |
| Environment | Blank until confirmed or executed. |
| Executed At | Blank before execution; afterward use an unambiguous date-time including timezone when available. |
| Source Reference | PDF page/section, screenshot name/region, file and heading, or another precise locator. |
| Notes / Assumptions | Only material assumptions, dependencies, or limits. Leave blank when unnecessary. |

If the user or target test-management tool requires fields such as Component, Labels, Assignee, Test Repository Path, Fix Version, or Linked Story, add them without removing the authoritative content.

## Priority and severity

Priority answers: **How soon should this test be designed, run, or automated?**

- `Critical`: release gate or essential smoke path.
- `High`: core workflow or high business risk.
- `Medium`: important standard behavior with a viable workaround or lower exposure.
- `Low`: low-frequency, cosmetic, or non-blocking coverage.

Severity answers: **What is the impact if the product fails this case?**

- `Blocker`: system or critical workflow cannot proceed and no workaround exists.
- `Critical`: data loss, security exposure, financial corruption, or failure of a primary business function.
- `Major`: significant incorrect behavior with limited workaround.
- `Minor`: localized issue with a practical workaround.
- `Trivial`: cosmetic or negligible functional impact.

Assign values from the described impact. Do not make every happy path high severity or copy priority into severity automatically.

## Case construction

### Titles

Name the behavior and meaningful condition:

- Good: `Reject checkout when the card authorization expires`
- Good: `Save the profile with all required fields`
- Weak: `Verify checkout functionality`
- Weak: `Test profile page`

### Steps and expected results

Keep steps reproducible and free of expected outcomes. Put the primary expected result in its own field. Include intermediate results only when they are necessary checkpoints.

Prefer:

1. Open the sign-in page.
2. Enter a registered email and an incorrect password.
3. Select **Sign in**.

Expected result: `The user remains signed out. The page shows the invalid-credentials message and does not identify which credential is incorrect.`

Avoid instructions such as “Enter invalid data” when the invalid class is not obvious. Name the value or constraint in `Test Data`.

### Coverage rules

- Use equivalence classes instead of repeating every value.
- Cover exact boundaries and the nearest values on each side when the rule is numeric, length-based, or date-based.
- Separate cases when setup, risk, or failure diagnosis differs materially.
- Combine steps only when they form one user goal and one failure would not obscure diagnosis.
- Do not infer hidden validations from UI appearance alone.
- When the source is contradictory, create a coverage-gap entry instead of choosing an expected result silently.

## Coverage sheet

Use these columns:

`Source Item`, `Behavior / Rule`, `Test Case IDs`, `Coverage Status`, `Gap / Assumption`, `Source Reference`

Allowed coverage values are `Covered`, `Partial`, and `Blocked`. Every confirmed rule should map to at least one test case or have a specific gap.

## Suggestions sheet

Use these columns:

`Suggestion ID`, `Area`, `Observation`, `Proposed Improvement`, `Reason`, `Impact`, `Source Reference`, `Review Status`

Set `Review Status` to `Review`. Suggestions are not requirements, defects, or approved test cases. Phrase them as concrete product, acceptance-criteria, observability, accessibility, security, or testability improvements. Omit generic advice.

## Jira Import sheet

Jira import formats vary by product configuration and test-management app. If the user provides an export sample or import template, reproduce its exact headers and controlled values.

Without a target template, create a generic staging sheet with:

`External ID`, `Issue Type`, `Summary`, `Description`, `Priority`, `Labels`, `Component`, `Requirement ID`, `Preconditions`, `Test Data`, `Steps`, `Expected Result`

Use `Test` as the provisional issue type only when the target project supports it; otherwise leave the value ready for mapping. Keep one row per case and preserve `Test Case ID` as `External ID`. Explain outside the workbook that Jira may require CSV conversion and custom-field mapping. Never present this generic sheet as guaranteed one-click import.

## Workbook validation checklist

- IDs are unique and stable.
- Titles, steps, and expected results are present and readable.
- Each expected result is observable.
- Controlled fields contain only allowed values.
- Every case has a source reference or a clearly labeled assumption.
- `Coverage` has no unexplained confirmed rule without a case.
- Suggestions are separate from executable cases.
- Initial execution fields do not imply tests were run.
- The workbook contains no AI-related language, internal reasoning, or filler text.
- Filters, frozen headers, wrapping, and column widths work at normal zoom.
