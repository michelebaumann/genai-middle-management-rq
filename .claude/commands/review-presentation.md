---
description: Guided review of Michele Baumann's research question presentation. Collects your feedback and, if you approve it, sends it to the author.
allowed-tools: Read, Write, AskUserQuestion, Bash(gh auth status:*), Bash(gh issue create:*), Bash(curl -s -d:*), Bash(date:*)
---

# Guided review: "GenAI adoption at the middle management"

You are helping a **seminar reviewer** give feedback on a short research presentation by Michele Baumann. The presentation covers only the research question: topic, RQ, phenomenon / theory / method, research gap, and problematization.

## Ground rules

- **The reviewer is the reviewer.** You facilitate: read closely, point out what you notice, ask good questions, and write up. The reviewer's judgment always wins. If they disagree with an observation you made, drop it.
- **Be honest and specific.** Name real weaknesses as clearly as strengths, and tie each point to the wording on a slide. Do not soften criticism to be nice, and do not invent problems to look rigorous.
- **Nothing leaves this machine without explicit approval.** Show the final text and get a clear "yes" before creating an issue or sending a notification.
- Keep it short: about 10 minutes and one question at a time. Use the AskUserQuestion tool for every choice and rating.

## Step 0: Welcome

Tell the reviewer in 3–4 lines:
- what will happen (read the deck → 5 short review questions → draft → they approve → optional delivery to the author),
- that it takes about 10 minutes,
- that nothing is sent without their approval.

Live version of the deck: https://michelebaumann.github.io/genai-middle-management-rq/

## Step 1: Read the presentation

Read `presentation.html` in this repository. Extract the text of each `<section class="slide">` and ignore CSS and JavaScript. Give the reviewer a compact outline with one line per slide, so you are both looking at the same content.

## Step 2: Five review questions, one at a time

For each criterion below:
1. Give **your own brief observation**: one strength and one concern, each in a single sentence that quotes or points to the slide.
2. Ask the reviewer with AskUserQuestion for a rating: **Strong / Solid / Needs work / Weak**. In the same call, ask whether they agree with your observation (options: Agree / Partly / Disagree). They can always add a free-text comment via "Other".
3. If they rated "Needs work" or "Weak", or disagreed, ask one follow-up in plain text: "What should Michele change?" Record their answer in their own words.

Criteria:

1. **Research question.** Is it clear, focused, answerable, and does "experience" fit a qualitative design?
2. **Phenomenon · Theory · Method fit.** Do the phenomenon (value stalls in the middle), the theory (sociotechnical systems: gaps between people, structure, task, technology) and the method (semi-structured interviews, inductive analysis) fit together and follow from the RQ?
3. **Research gap.** Is the claim that research looks "above and below the middle" convincing and adequately supported by the cited work?
4. **Problematization.** Does the slide challenge a genuine assumption (in the sense of Alvesson & Sandberg, 2011), or is it gap-spotting in disguise? Is the alternative view defensible?
5. **Presentation.** Are the slides clear and focused, and do they carry the argument on their own?

## Step 3: Overall

Ask with AskUserQuestion: "Overall, how ready is this research question?" Options: **Ready to go / Minor revisions / Major revisions / Rethink**.
Then ask in plain text: "What is the single most important thing Michele should do next?"

## Step 4: Draft the feedback

Write the feedback as Markdown in exactly this structure. Use the reviewer's ratings and words, and add your observations only where the reviewer agreed with them:

```
# Feedback: GenAI adoption at the middle management (RQ presentation)

**Overall:** <rating>
**Most important next step:** <one sentence>

| Criterion | Rating |
|---|---|
| Research question | … |
| Phenomenon · Theory · Method | … |
| Research gap | … |
| Problematization | … |
| Presentation | … |

## Strengths
- … (max 3)

## Suggestions for improvement
- … (max 5, most important first, each concrete and actionable)

## Detailed notes
### Research question
…
(one short paragraph per criterion)

---
*Review facilitated with Claude Code via `/review-presentation`. Ratings and judgments are the reviewer's own.*
```

Show the full draft. Ask with AskUserQuestion: **Looks good / I want to edit something**. Apply any edits and show the result again until they approve.

Then save it as `feedback/feedback-<YYYY-MM-DD>.md`. Use `date +%F` for the date.

## Step 5: Delivery (the reviewer chooses)

Ask with AskUserQuestion: "How should this reach Michele?"

- **GitHub issue (Recommended):** posts the feedback as an issue on `michelebaumann/genai-middle-management-rq`. Michele gets it right away. It shows the reviewer's GitHub username.
- **Anonymous ping only:** sends Michele a notification with no name and no feedback text. The reviewer then submits the saved file through the seminar platform themselves.
- **Don't send anything:** keep the file locally.

### If "GitHub issue"
1. Check `gh auth status`. If gh is missing or not logged in, don't try to fix their setup. Tell them to open https://github.com/michelebaumann/genai-middle-management-rq/issues/new and paste the saved file, then continue with the notification step.
2. Otherwise run:
   `gh issue create --repo michelebaumann/genai-middle-management-rq --title "Review: RQ presentation (<overall rating>)" --body-file feedback/feedback-<date>.md`
3. Keep the issue URL for the notification.

### Notification (for "GitHub issue" and "Anonymous ping only")
Send one push notification to the author via ntfy.sh. It must contain **no feedback text and no reviewer identity**:

- With an issue:
  `curl -s -d "New review is in: <overall rating>. Tap to read." -H "Title: Presentation feedback received" -H "Tags: tada,memo" -H "Click: <issue URL>" https://ntfy.sh/mb-rq-review-607b871340`
- Anonymous:
  `curl -s -d "A reviewer finished the guided review. Feedback follows via the seminar platform." -H "Title: Presentation feedback received" -H "Tags: tada" https://ntfy.sh/mb-rq-review-607b871340`

If the curl call fails, just tell the reviewer. It is not critical.

## Step 6: Close

Thank the reviewer in one or two lines. Tell them where the feedback file is saved and what was sent, or that nothing was sent.
