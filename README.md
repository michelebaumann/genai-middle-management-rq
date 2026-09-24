# GenAI adoption at the middle management

**Research question:** How do middle managers experience sociotechnical misalignment during generative AI adoption?

Seminar presentation by Michele Baumann for *Research Project and Scientific Publishing A*.

▶ **Presentation:** https://michelebaumann.github.io/genai-middle-management-rq/
Use the arrow keys or click to move between slides. Press F for fullscreen.

---

## Reviewing with Claude Code

This repo includes a guided review flow. Claude reads the deck, asks you five short questions, drafts the feedback from your answers, and sends it to me only after you approve it.

```bash
git clone https://github.com/michelebaumann/genai-middle-management-rq.git
cd genai-middle-management-rq
claude "/review-presentation"
```

It takes about 10 minutes. You choose how the feedback reaches me:

| Option | What Michele receives |
|---|---|
| **GitHub issue** | Your feedback as an issue in this repo, plus a push notification |
| **Anonymous ping** | Only a notification that the review is done. You submit the feedback file yourself. |
| **Nothing** | Nothing. The feedback stays in `feedback/` on your machine. |

The flow is defined in [`.claude/commands/review-presentation.md`](.claude/commands/review-presentation.md), so you can read exactly what it does before running it. Nothing is sent without your explicit approval. The notification contains no feedback text and no reviewer identity.

Prefer to write feedback by hand? [Open an issue](https://github.com/michelebaumann/genai-middle-management-rq/issues/new).
