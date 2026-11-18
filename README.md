# document-standards

A Claude Code skill defining how a project writes its documentation: design documents, the architecture decision records that are part of the design documentation, and requirements documents. Every type follows one premise: a document states the current conclusion, never the process that produced it. Change history, version numbers, authors, dates and review records stay in git; TODO items, schedules, milestones, owners and priorities stay out of the documents.

## Contents

| Path | What it is |
|---|---|
| `SKILL.md` | The rules shared by every document type, the configuration keys, the checker instructions, and the entry point to each type's standard |
| `references/design-documents.md` | Design tree: README index, architecture overview, module documents, fixed section order, implementation status vocabulary |
| `references/requirements-documents.md` | Requirements tree: overview, feature documents, journey documents |
| `references/decision-records.md` | ADR tree: record sections, the options weighed, and their verdicts |
| `templates/` | A starting file per document type, plus the glossary and references files shared by all of them |
| `scripts/check_documents.py` | Structural checker for the configured documentation trees |
| `scripts/test_check_documents.py` | Planted-violation suite covering the checker's rules |

## Install

Claude Code discovers skills in two places. For every project:

```bash
git clone git@github.com:wangzw/document-standards.git ~/.claude/skills/document-standards
```

Or, to share the standard with everyone who checks out a project:

```bash
git clone git@github.com:wangzw/document-standards.git <repo>/.claude/skills/document-standards
```

## Configure

Declare the documentation paths once, in the project's `CLAUDE.md`:

```markdown
## Documentation

- design: docs/design
- requirements: docs/prd
- adr: docs/adr
- glossary: docs/glossary.md
- references: docs/references.md
- language: en
```

Omitting a path key falls back to the default shown above. `language` is the exception: the checker exits with a configuration error when it is absent. Its values are `en` and `zh-CN`; when the skill writes without one, it infers the language from the documents already in the target directory and asks when that is inconclusive.

## Use

Claude Code lists the skill at session start. Its description directs Claude to load it before creating or editing a document under the configured paths, and when reviewing documentation. Before writing, it loads the document type's standard; a file in `templates/` is the starting point. After creating or editing a document it runs the checker and keeps the result at exit 0 before calling the work finished.

Run the checker from the project root:

```bash
python3 .claude/skills/document-standards/scripts/check_documents.py   # repository-level install
python3 ~/.claude/skills/document-standards/scripts/check_documents.py # user-level install
```

Use `--root PATH` to check a project from elsewhere; the root must hold `CLAUDE.md`. Findings print as `path:line: what is wrong`, or `path: what is wrong` when the problem belongs to the whole file. Exit code 0 means the structure passes, 1 means findings, 2 means a usage or configuration error.

The checker verifies structure: section presence and order, file naming, index coverage, status values, diagram bodies, glossary columns, reference citations, and the process metadata a document must not carry. Judgement rules—subjective language, whether a requirement is testable, whether a decision record was warranted—remain on the review checklist in `SKILL.md`.

## Test

```bash
python3 .claude/skills/document-standards/scripts/test_check_documents.py   # repository-level install
python3 ~/.claude/skills/document-standards/scripts/test_check_documents.py # user-level install
```

The suite needs no configuration and installs nothing beyond the Python standard library.

## License

Apache License 2.0. See [LICENSE](LICENSE).
