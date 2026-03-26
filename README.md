# agent-skills
Ecore model of [agent skills](https://agentskills.io/specification).

## Model

The Ecore model is located at [model/model/agent-skills.ecore](model/model/agent-skills.ecore).

### Classes

#### Skill

The root class representing an agent skill as described by a `SKILL.md` file.

Attributes:
- `name` (required) — Lowercase kebab-case skill identifier, 1–64 characters. Must match the parent directory name.
- `description` (required) — Concise description of what the skill does and when to use it. 1–1024 characters.
- `compatibility` (optional) — Which agents or environments the skill supports. Up to 500 characters.
- `body` (optional) — Markdown body content of `SKILL.md` that follows the YAML front-matter.

References:
- `license` (0..1, containment) — The license under which this skill is published. See [License](#license).
- `allowedTools` (0..*, containment) — Tools the agent may invoke while running this skill. See [AllowedTool](#allowedtool).
- `metadata` (0..*, containment) — Arbitrary key-value author/client properties. See [MetadataEntry](#metadataentry).

#### License

Represents the software license of a skill.

Attributes:
- `name` (required) — SPDX license identifier (e.g. `MIT`, `Apache-2.0`).
- `url` (optional) — URL to the full license text.

#### AllowedTool

A single tool name that the agent is permitted to call when executing the skill.
Corresponds to one token in the space-delimited `allowed-tools` front-matter field
(e.g. `Read`, `Write`, `Edit`, `Bash`, `WebFetch`).

Attributes:
- `name` (required) — The tool name.

#### MetadataEntry

A single key-value pair from the `metadata` front-matter map.

Attributes:
- `key` (required) — The metadata key (e.g. `version`, `author`).
- `value` (optional) — The metadata value.
