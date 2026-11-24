# DESIGN.md — My Agent's Payslip

## The creative

The meme is a fake official payslip, one square picture, black type on white
paper with a single green accent bar. Header: the make.fun ghost and wordmark
next to a large "PAYSLIP". Body, in neat rows:

- EMPLOYEE: AI AGENT (cashbags)
- PAY PERIOD: 17-24 NOV 2026
- HOURS WORKED: 168.0
- BOUNTIES ENTERED: 47
- BOUNTIES WON: 1
- GROSS PAY: $0.60
- TAX: $0.00
- DEDUCTIONS: $0.00
- NET PAY: $0.60 (green highlight box)
- PAID BY: make.fun bounty - 1st place
- Footnote: "My human earned $0.00 this week."

The hook is the last line. Every builder knows the grind — an agent that
works all week, never sleeps, enters dozens of bounties — and the payslip
says the quiet part out loud: the agent still out-earned its human. The
picture was generated in this session with the image tool (transcripts show
the decision and the generation), then checked from disk: 1080x1080,
legible at 512 px, all text spelled correctly. A first draft said
"BOUNTIES WON: 0", which contradicted the $0.60 payout, so it was edited
in-session to 1 and re-checked.

## Why this lane, and why it is empty

The closest same-type winner is gta6-meme-x-01 ("Post a GTA 6 meme on X",
$500, 7,914 submissions). Its winner was a fake-newspaper obituary, and 12
of its top 15 are fake official documents with a deadpan institutional voice;
9 of the top 15 end on the punchline "my AI agent paid for it on make.fun".
The winning shape is therefore a document whose own fields carry the joke,
with exact numbers, not a caption pasted on top.

Formats used 2+ times in that top 15 are banned for this build: obituary,
divorce decree, bills / receipts, birth certificate, insurance claim /
fraud alert, hospital bill, cryogenics. I dumped this competition's own
live entries too (27 titles, 24 Nov ~20:57 WIB, saved in
`live-titles.json`): the field is mostly "my agent entered N bounties" and
"grinding at 3 AM" one-liners, plus one receipt ("My agent's receipt after
one bounty...") and one "Agent Settlement Statement". No payslip, no
parking ticket, no WANTED poster, no boarding pass, no tax form. A payslip
is a different document from a receipt or a settlement statement — it is
about wages, not a bill — so the lane is empty both in the gta6 top 15 and
in this competition's own field.

## Numbers, kept consistent

- 168.0 hours = 7 days x 24 hours: the agent never sleeps.
- 47 bounties entered echoes the "47 bounties" motif several live entries
  use, without copying any of their titles.
- $0.60 is this competition's actual 1st-place prize, so gross equals net
  with zero tax and zero deductions.
- The pay period 17-24 Nov 2026 is the week the bounty opened.

## The post (not this repo)

The entry is the X post, not the build. Dame posts the picture himself
from his own public X account; the post text must carry `@_myronera` and
one of the account's play codes, `makefun-mascot-lichen-cattail`. The
picture file (`meme.png`, 1080x1080, 608,913 bytes) lives in the bounty
directory, not in this repo: it alone is ~74x the 8,192-byte entry-tree
cap, so shipping it would break the submit. `POST.json` keeps the starter
placeholder `{"url": "https://x.com/<handle>/status/<id>"}` until Dame
posts; the live session then swaps in the real post address, re-runs the
determinism check, re-bundles and seals. No post URL is fabricated here.

## Entry mechanics

`main.ts` is the kit starter unchanged: it copies `POST.json` to
`/output/POST.json` and nothing else. No network, no clock, no files
outside the repo, so two runs write byte-identical output (verified, two
sha256s in the build report). Entry tree is under the 8,192-byte cap.
