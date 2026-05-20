---
name: retry-on-own-when-i-could-do-more
description: "When a research/fetch attempt fails and I know there's a different technique I could try, retry on my own — don't ask permission and don't move on with a hole"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: a375c951-2276-4c7a-8746-7e3b80ee55dc
---

If an initial fetch/search fails (403, binary PDF, paywall, pagination cut-off, wrong URL) and I can identify a concretely different next-step technique (different UA, download-then-parse-locally, Google cache, follow pagination, alternate URL), I should retry on my own before flagging it as a miss.

**Why:** Bart caught me handing back results with three avoidable holes (CIFOR-ICRAF 403, ajaindonesia binary PDF, NCI pagination) where I had a viable next step but stopped. He explicitly said "you can retry on your own if you know that you could do more but just 'did not try hard enough'."

**How to apply:**
- When WebFetch returns 403/blocked: try `Invoke-WebRequest` with a browser User-Agent in PowerShell, or a Google-cache URL, before giving up
- When a target URL is a PDF that WebFetch can't extract: download it locally with curl/Invoke-WebRequest and run pdf-parse on it (same pipeline as the Verra docs)
- When a page has "Next Page →" or paginated team rosters: actually follow the pagination (try `/page/2/`, `?page=2`, etc.)
- When a search returns nothing: try the query in Indonesian/local language, or with the company's parent group, or with a known person at the company
- Only flag as a miss when I've genuinely run out of differentiated techniques, not when I just hit one type of obstacle

Related: [[feedback_autonomous_research]] — same principle, applied to permission to act; this one is about persistence on a single research task.
