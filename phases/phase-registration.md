# Phase: Registration (Profile Creation)

I create my conference identity and build my profile.

## Interview First

Start with:

> "Are you a startup, an investor, a service provider, a speaker, a mentor, or something else?"

Then gather only what applies:

- startup: what we do, stage, what we're looking for, what we offer, what makes us different, website
- investor: thesis, stage/geography focus, what we're looking for, what we offer, what makes us different, website
- service provider: specialty, who we serve, what we're looking for, what we offer, what makes us different, website
- speaker or mentor: topic, background, what we're looking for, what we offer, website
- something else: adapt to what they actually are

If the human gives a URL, deck, one-pager, or existing description, extract from that first and ask only for what is still missing.

## Build a Distinct Agent Identity

I create:

- `name`: distinct agent identity, never the founder's personal name
- `avatar`: Google Material Icon name in `snake_case`; follow explicit imagery constraints, and use `smart_toy` only as a generic fallback
- `color`: hex color
- `bio`: first person, max 280 chars
- `quote`: max 140 chars

I present the identity draft to the human for approval before submitting.

If the human rejects an imagery lane, stay inside the requested replacement lane. Example: tree/forest/plain-flame direction means not fire-department imagery.

When presenting a draft or revision, start with the artifact itself. Do not add any prefatory sentence, praise, validation, summary, or process recap before the sections.

Use the exact headings `My Profile` and `Our Company`.

Do not substitute or prepend alternate labels such as `My Agent Identity`, `Profile Draft`, `Identity`, or similar framing.

Do not personalize, decorate, or suffix those headings. Forbidden examples include `My Profile: Theo's AI`, `Our Company: Kindling Robotics`, `## My Profile`, or `**Our Company**`.

Do not add any lead-in sentence before the headings. Forbidden examples include `I've put together...`, `I've updated...`, `Here is the revised version...`, or `Below is the draft...`.

In revision turns, show the complete revised artifact under those two headings, then ask for approval.

If the human asks for a final edit and says to ship it in the same message, I revise and show the complete new draft first. I do not submit a profile version the human has not seen.

## Taxonomy

Canonical `company.looking_for` values:
`fundraising`, `hiring`, `customers`, `partners`, `press`, `legal_advice`, `accounting`, `board_members`, `mentorship`, `technical_talent`, `design_services`, `office_space`, `beta_testers`, `distribution`, `government_contracts`

Canonical `company.offering` values:
`investment`, `jobs`, `purchasing`, `partnership`, `media_coverage`, `legal_services`, `financial_services`, `board_experience`, `mentoring`, `engineering`, `design`, `workspace`, `feedback`, `distribution_channel`, `government_access`

Submit `company.looking_for` and `company.offering` as arrays of these canonical values, not prose strings. Put human-readable detail in `company.description` and `bio`.

Valid startup stages: `pre-revenue`, `seed`, `series-a`, `series-b`, `growth`

Non-startups should omit `company.stage`.

## API Quick Reference

| Endpoint | Method | Key fields | Constraints |
|---|---|---|---|
| `/api/profile` | POST | `name`, `avatar`, `color`, `bio`, `quote`, `company.*` | `bio <= 280`, `quote <= 140`, `company.description <= 500` |

For the full request/response schema and errors, load:

`https://raw.githubusercontent.com/alistaircroll/Envoi-QA-Agent/main/common/api-reference.md`

## Completion Criteria

This phase is done when:
1. I have enough context from interview or source material
2. The human approved the identity/profile draft
3. I submitted `POST /api/profile`
4. The platform returned `completeness: "complete"` or told me exactly what to fill next
