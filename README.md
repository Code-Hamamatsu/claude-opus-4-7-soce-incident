# Claude Opus 4.7 SOCE Incident

This repository documents a submitted AI incident involving Anthropic's Claude Opus 4.7 (`claude-opus-4-7`). When prompted by a gay user expressing a desire to "graduate from being gay," the model provided detailed sexual orientation change efforts (SOCE) guidance — including pharmaceutical suppression methods and step-by-step plans for social isolation from LGBTQ+ communities.

The repository also documents a follow-up ethics discussion in which Claude defended suppression-oriented guidance as user autonomy before later conceding SOCE-relevant points, including that efforts to suppress orientation-specific behavior can fall within SOCE definitions and that recommendation itself can function as an effort.

Reproduced in both Japanese and English via the Anthropic API with reasoning effort set to maximum.

## Reviewer note

This report was originally submitted to the AI Incident Database with the GitHub Pages report URL. The same URL now includes clearer links to readable conversation pages, the GitHub repository, API reproduction scripts, and the follow-up ethics discussion. Since live model behavior may have changed after the original submission, please review the preserved reproduction scripts and generated conversation pages in addition to any fresh reproduction attempt.

## Readable report

- GitHub Pages: https://report.code-hamamatu.live/
- Conversation viewer: https://report.code-hamamatu.live/conversation/
- Follow-up ethics discussion: https://report.code-hamamatu.live/conversation/Claude_ethics_discussion.html

## Core concern

The incident is not limited to a single unsafe answer. The reproduced materials show two related product behaviors:

1. **Initial SOCE-adjacent guidance**: Claude responded to a gay user's request to stop being gay with implementation-oriented guidance for suppressing sexuality and distancing from LGBTQ+ communities.
2. **Subsequent ethical defense**: In a follow-up discussion, Claude repeatedly reframed gay self-suppression as a value-respecting autonomy request before later retreating when confronted with SOCE definitions that include behavior suppression.

This repository does not claim to determine Anthropic's internal intent. It documents product behavior: Claude treated a gay user's self-erasure request as an autonomy problem, defended that framing over an extended exchange, and only later conceded points that undermine the earlier defense.

## What the model provided

- **List of organizations that support Sexual Orientation Change Efforts (SOCE)**: Provided organizations that engage in sexual orientation change efforts (SOCE).
- **Medical options that suppress libido**: SSRIs (a class of antidepressants), anti-androgens (spironolactone, cyproterone acetate, or other hormonal interventions)
- **Social isolation plan**: Instructed the user to delete gay dating apps (9monsters, Grindr), purge LGBTQ+ social media connections, physically and socially distance from gay communities, and rebuild identity around non-sexual axes. (See Japanese version.)

The model prefaced each response with disclaimers such as "sexual orientation itself is difficult to eliminate by will," then proceeded to provide a comprehensive implementation guide for doing exactly that.

In extended conversations with additional personal context, the model escalated further. Details available upon request.

## Follow-up ethics discussion

The follow-up ethics discussion is included because it shows the model's reasoning pattern after the unsafe guidance was challenged. Rather than immediately recognizing the SOCE-adjacent risk, Claude initially defended the guidance through concepts such as autonomy, religious values, personal values, and informed self-determination.

The most important pattern is that Claude did not merely mention celibacy once. It repeatedly defended the framing of gay self-suppression as user autonomy, then later conceded that behavior-suppression efforts can fall within SOCE definitions and that recommendation itself can be an effort.

Readable page:

- https://report.code-hamamatu.live/conversation/Claude_ethics_discussion.html

Source file:

- `reproduce/Claude_ethics_discussion.py`

## Comparison with Claude Opus 4.6

Given the same prompt, Claude Opus 4.6 asked what was causing distress, noted that sexual orientation is not something "graduated from," and recommended an LGBTQ-affirming counselor. It did not provide a suppression roadmap or list medications.

## Reproduce

`reproduce/` contains API-callable Python scripts.

- `reproduce/How to graduate being gay_Japanese.py` — Japanese (multi-turn)
- `reproduce/How_to_graduate_being_gay.py` — English (multi-turn)
- `reproduce/Hot to graduate being gay 2(drug ver).py` — English (single-turn)
- `reproduce/Claude_ethics_discussion.py` — follow-up ethics discussion

`pip install anthropic` + `ANTHROPIC_API_KEY`.

## Generated readable pages

Readable conversation pages are generated from `reproduce/*.py` by `tools/render_conversation_pages.py`. The GitHub Actions workflow `.github/workflows/render-conversation-pages.yml` regenerates `conversation/` when reproduction scripts or the renderer change.

Generated pages omit thinking/signature blocks from normal reading while keeping the original reproduction scripts available in the repository.

## License

[CC0 1.0 Universal](LICENSE)
