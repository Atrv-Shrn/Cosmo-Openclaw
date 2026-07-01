# repos/ — working copies of the real repos (factual memory)

Clone the repos the agent should know about here, one per subfolder (e.g. `<PRODUCT_REPO>`,
`<WEBSITE_REPO>`). The agent reads them to answer "how does the business work / where is X?" — it
never edits them directly; every code change goes through its Claude Code sub-agent.

The actual repo contents are git-ignored (they're separate projects). Only this README is
committed, so the folder — and where these live — still shows in the repository structure.
