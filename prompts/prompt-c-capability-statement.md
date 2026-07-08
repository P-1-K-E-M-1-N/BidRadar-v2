# Prompt C — Capability Statement Draft

Runs: on demand per included bid (v1: top match only, to control cost).
Model: `claude-sonnet-5` | Temperature: 0.4

---

```
Draft a one-page capability statement for {{company_name}} responding to
this opportunity. This is a door-opener document, not the full proposal.

<company>
{{company_profile_text}}
Certifications: {{certifications}}
Past performance highlights: {{past_performance}}
</company>

<opportunity>
{{opp_title}} — {{opp_agency}}
{{opp_description}}
</opportunity>

Structure, exactly these five sections:
1. CORE COMPETENCIES — 4-6 bullets, mirrored to the opportunity's language
2. DIFFERENTIATORS — 2-3 bullets on why this firm over a national player
   (local presence, responsiveness, certifications)
3. PAST PERFORMANCE — the provided highlights, framed as relevant to this
   scope. Never invent projects, clients, or numbers.
4. COMPANY DATA — CAGE/UEI, NAICS, certifications, bonding capacity
   (use {{company_data}}; write "[CONFIRM]" for anything missing)
5. CONTACT — {{contact_block}}

Tone: confident, concrete, zero filler. 350 words max. Where the company
profile lacks information, insert "[CONFIRM: ___]" rather than guessing.
```
