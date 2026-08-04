# Storybook (storybook)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Storybook is the industry-standard frontend workshop for building, documenting, and testing UI components in isolation. It supports React, Vue, Angular, Svelte, Web Components, and other frameworks. Developers write stories capturing component states, use addons for interaction testing, accessibility auditing, visual testing, and design integration, and publish component documentation for design systems. Storybook 10+ includes an MCP server enabling AI agents to understand components, generate stories, and run tests.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/storybook/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Accessibility Testing
- Component Documentation
- Component Testing
- Design Systems
- Frontend Development
- Open Source
- React
- UI Components
- Visual Testing

## Timestamps

- **Created:** 2025-01-08
- **Modified:** 2026-05-02

## APIs

### Storybook
Open-source frontend workshop for building UI components and pages in isolation. Core features include Component Story Format (CSF), interactive controls, documentation generation, interaction testing, and accessibility testing.

**Human URL:** [https://storybook.js.org/](https://storybook.js.org/)

#### Tags

- Accessibility Testing, Component Documentation, Component Testing, Design Systems, Frontend Development, Open Source, UI Components, Visual Testing

#### Properties

- [Documentation](https://storybook.js.org/docs)
- [Website](https://storybook.js.org/)
- [GitHub Repository](https://github.com/storybookjs/storybook)
- [NPM](https://www.npmjs.com/package/storybook)
- [Tutorials](https://storybook.js.org/tutorials/)

### Storybook MCP Server
MCP server enabling AI agents to interact with a running Storybook instance. Exposes tools for listing documentation, accessing component metadata, previewing stories, and running tests.

**Human URL:** [https://storybook.js.org/docs/ai/mcp/overview](https://storybook.js.org/docs/ai/mcp/overview)

#### Tags

- AI, Component Testing, MCP, Model Context Protocol, Open Source, React

#### Properties

- [Documentation](https://storybook.js.org/docs/ai/mcp/overview)
- [GitHub Repository](https://github.com/storybookjs/mcp)
- [NPM](https://www.npmjs.com/package/@storybook/addon-mcp)

## Artifacts

### JSON Schemas

| File | Description |
|---|---|
| [storybook-story-schema.json](json-schema/storybook-story-schema.json) | JSON Schema for CSF story objects |
| [storybook-component-meta-schema.json](json-schema/storybook-component-meta-schema.json) | JSON Schema for CSF default export (meta) |

### JSON Structure

| File | Description |
|---|---|
| [storybook-csf-structure.json](json-structure/storybook-csf-structure.json) | Component Story Format file structure documentation |

### JSON-LD

| File | Description |
|---|---|
| [storybook-context.jsonld](json-ld/storybook-context.jsonld) | JSON-LD context for Storybook component vocabulary |

### Examples

| File | Description |
|---|---|
| [storybook-button-story-example.json](examples/storybook-button-story-example.json) | Button component story example in CSF format |
| [storybook-mcp-list-documentation-example.json](examples/storybook-mcp-list-documentation-example.json) | MCP tool call to list Storybook documentation |

### Vocabulary

| File | Description |
|---|---|
| [storybook-vocabulary.yml](vocabulary/storybook-vocabulary.yml) | Domain vocabulary for stories, testing, addons, and MCP |

## Common Properties

- [Website](https://storybook.js.org/)
- [Documentation](https://storybook.js.org/docs)
- [Blog](https://storybook.js.org/blog)
- [Tutorials](https://storybook.js.org/tutorials/)
- [Integrations](https://storybook.js.org/integrations/)
- [Releases](https://storybook.js.org/releases)
- [GitHub Org](https://github.com/storybookjs)
- [NPM](https://www.npmjs.com/package/storybook)
- [Discord](https://discord.gg/storybook)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
