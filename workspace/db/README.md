# db/ — disposable copy of the production database (factual memory)

Drop a schema + data dump here (`.sql` files). It's disposable: the agent reads it to answer
business questions, but it's never the source of truth and never holds a live connection to prod.

The dumps are git-ignored. Only this README is committed, so the folder still shows in the
repository structure.
