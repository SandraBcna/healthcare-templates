# Healthcare Templates

Five Microsoft 365 Copilot **Cowork** plugins for healthcare and life sciences. Each plugin gives
Copilot a real piece of clinical, revenue cycle or regulatory work, with the rules, contracts and
deterministic engines that make the output reliable and reviewable.

## The plugins

| Plugin | What it does |
|--------|--------------|
| [Prior Authorization Packet](plugins/prior-auth-assist) | Find the governing payer policy, check the chart against each criterion, draft the medical necessity narrative and list what is missing |
| [Clinical Docs Companion](plugins/clinical-documentation-companion) | Draft the referral letter, after-visit summary and handoff from a signed note; build the coding rationale and check quality measures |
| [Denials & Appeals Response](plugins/denials-appeals-response) | Classify a denial, attach policy and chart evidence, rank the queue by deadline and value, draft the appeal |
| [Discharge Transition Packet](plugins/discharge-care-transition) | Reconcile medications, draft the discharge summary and plain language instructions, build the follow-up checklist |
| [Reg Submission Authoring](plugins/reg-submission-authoring) | Plan and draft clinical study report or 510(k) sections from source documents, then check every number against the sources |

Each plugin has five skills, 25 in total.

## Install

1. Download the plugin's `.zip` from the [latest release](https://github.com/SandraBcna/healthcare-templates/releases/latest).
2. Upload it to Microsoft 365 Copilot Cowork as is. The zip is the app package, with
   `manifest.json` at its root.
3. Fill in the settings marked `[TO CONFIGURE]` in each skill's `config/` folder for your
   organisation. Until you do, the skills report the item as not routed rather than guessing.

## How a plugin is built

| Piece | What it does |
|-------|--------------|
| `manifest.json` | The Cowork app package manifest that declares the skills, in run order |
| `<skill>/SKILL.md` | One skill, with when to use it and when not to |
| `<skill>/base/scripts/` | Deterministic Python engines: anything that produces a number, a status or a deadline |
| `<skill>/base/contracts/` | The versioned JSON contract each skill hands to the next, with data, confidence, provenance and citations |
| `<skill>/base/references/` | The numbered rules the engines mirror and the prompts cite |
| `<skill>/config/` | Settings each organisation replaces: payer policies, appeal windows, quality measures, escalation contacts |

**Engines compute, the model extracts and drafts.** The model never invents a deadline, a
criterion status or a medication discrepancy. It quotes the engine and cites the rule and the
source line.

**Draft-first.** Every plugin prepares work for a clinician, coder or medical writer to review and
sign off. None writes back to an EHR or any system of record, and none renders a clinical or
coverage decision.

## Important

- **No patient data.** Payers, contacts and examples are fictional (for example, Contoso Health
  Plan).
- **Starter grounding.** The rules in `base/references/` and the values in `config/` are
  illustrative, written for these plugins. They are not payer policies, clinical guidelines,
  coding guidance or regulatory requirements, and they are not medical, legal or billing advice.
  Replace them with your organisation's own documents before real use.
- **Provided as-is**, with no service-level agreement. Report problems in
  [Issues](https://github.com/SandraBcna/healthcare-templates/issues); never attach patient data.

## Licence

MIT, see [LICENSE](LICENSE). This matches the Microsoft-built skills in [CAT Agent Skills](https://github.com/microsoft/cat-agent-skills).
