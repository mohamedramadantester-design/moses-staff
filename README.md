# Moses' Staff

Moses' Staff is a Codex skill that turns product requirements from PDFs, text files, screenshots, or pasted evidence into a professional Excel test-case workbook.

It designs a compact, traceable set of Happy Path, Negative, Boundary, and applicable alternative scenarios. It does not execute tests until the user approves the delivered workbook and confirms the permitted environment, access, and test data.

## Output

The generated workbook contains:

- `Test Cases` — the authoritative executable set.
- `Coverage` — requirement-to-test mapping and explicit gaps.
- `Suggestions` — product and testability improvements.
- `Jira Import` — a generic staging view for later Jira/Xray/Zephyr mapping.

Workbook content is written in professional English by default. Exact product labels remain in their source language when needed for accurate test steps and traceability.

## Install with Codex

### Skill installer

In Codex, ask the bundled installer to install this repository:

```text
$skill-installer

Install the moses-staff skill from this GitHub repository:
https://github.com/mohamedramadantester-design/moses-staff
```

Start a new chat after installation so Codex discovers the skill.

### Manual installation

Copy or clone this repository into the user-scoped skills directory:

```text
~/.codex/skills/moses-staff/
```

On Windows, the equivalent location is:

```text
%USERPROFILE%\.codex\skills\moses-staff\
```

Windows PowerShell example:

```powershell
git clone https://github.com/mohamedramadantester-design/moses-staff.git "$env:USERPROFILE\.codex\skills\moses-staff"
```

Keep the complete directory structure, including `references/` and `agents/`.

## Usage

Invoke the skill explicitly in a new Codex chat:

```text
$moses-staff

Analyze the attached requirements and create Happy Path, Negative, and Boundary test cases. Stop after delivering the Excel workbook and do not execute any test until I approve it.
```

The skill can also be selected automatically for requests that clearly ask for test design from supplied product evidence.

## Workflow boundary

1. Analyze the supplied evidence.
2. Design and verify the Excel workbook.
3. Deliver the exact version for review.
4. Stop and request explicit approval.
5. Execute only approved cases in the confirmed environment.

Approval is version-specific. Material changes to the test set require approval again.

## Repository structure

```text
moses-staff/
|-- SKILL.md
|-- agents/
|   `-- openai.yaml
`-- references/
    `-- test-case-standard.md
```

## License

MIT License. See [LICENSE](LICENSE).
