---
description: Create a uniquely-named brief for a project, never overwriting.
argument-hint: [client-slug] [artifact-type]
---

Compute a non-overwriting brief path and create it.

Steps:
1. Parse arguments from "$ARGUMENTS":
   - First word = client-slug (lowercase, hyphenate spaces).
     If empty, use "prospect-$(date +%Y-%m-%d)".
   - Second word = artifact-type (e.g. "discovery", "strategy").
     If empty, use "discovery".

2. Run this bash to compute a collision-proof path:

   YEAR=$(date +%Y)
   SLUG="<client-slug>"
   TYPE="<artifact-type>"
   DIR="projects/${SLUG}/${YEAR}"
   mkdir -p "$DIR"
   BASE="brief-${TYPE}"
   PATHNAME="${DIR}/${BASE}.md"
   N=2
   while [ -f "$PATHNAME" ]; do
     PATHNAME="${DIR}/${BASE}-v${N}.md"
     N=$((N+1))
   done
   echo "$PATHNAME"

3. Invoke the orchestrator agent to run Refine on the request and produce
   the brief CONTENT using the _templates/brief.md structure.

4. Write the brief to the exact $PATHNAME computed in step 2.
   Never write to a bare "brief.md". Never overwrite an existing file.

5. Report the path written and the routing decision.
