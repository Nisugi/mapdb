# In-Game Map Submissions

Players contribute map fixes directly from the game. The `cartographer.lic`
Lich script turns in-memory map edits into pull requests against this repo -
no git client or JSON editing required.

## Player quickstart

1. `;cartographer` - download and load the latest mapdb release
2. Edit rooms as usual (any script or tool that modifies the in-memory Map)
3. `;cartographer --diff` - see exactly what you changed vs. the release
4. One-time setup: create a **classic** GitHub token with only the
   `public_repo` scope (fine-grained tokens cannot open PRs against repos
   you don't own) and store it: `;cartographer --auth ghp_...`
5. `;cartographer --submit --rooms 285,1448 --message "fixed the arch" --upstream`

Without `--upstream` the PR opens on your own fork - useful for testing.
Selection (`--rooms`/`--all`) is always explicit because runtime scripts
(e.g. teleport utilities) legitimately modify the in-memory map, and those
local-only edits should not be submitted.

## What happens to a submission

Submissions arrive **raw**: `{room: {...}}` JSON with StringProcs inline as
`;e` strings and no checksum. The pipeline canonicalizes them:

1. **Submission Normalize check** (PR): validates each changed room,
   verifies it will canonicalize cleanly (schema, dangling StringProc
   references, path/id mismatches), posts a preview of the post-merge
   rewrite, and renders any new/changed StringProc code in the PR
   conversation for review. PRs that change proc code get the
   `stringprocs` label. Submissions that are semantically identical to
   `main` (re-submissions of already-merged edits against an older release
   baseline) are flagged as "nothing new to merge."
2. **Review and merge**: data-only PRs can auto-merge once checks pass
   (opt-in, see below). PRs labeled `stringprocs` need a human - StringProcs
   are executable Ruby that runs inside every player's session.
3. **Normalize Main** (post-merge): rewrites the merged submission into the
   git-canonical `{checksum, room}` form with externalized,
   standardrb-formatted `.rb` proc files. This runs post-merge because
   workflows cannot push rewrites to fork PR branches.
4. **Release**: release-please cuts the next version; players pick it up on
   their next `;cartographer` run, which also clears their local diff.

## Maintainer setup

- **StringProc review gate**: `.github/CODEOWNERS` routes `gs/**/*.rb` to
  the StringProc team; enable branch protection with "Require review from
  Code Owners" on `main` to enforce it. In-game submissions carry new procs
  *inline* inside room.json (externalized only post-merge), so the
  `stringprocs` label from the normalize check - not CODEOWNERS - is the
  gate for those; exclude labeled PRs from any auto-merge policy.
- **Auto-merge for data-only submissions**: set the repository variable
  `ENABLE_DATA_AUTO_MERGE=true`. Requires branch protection with required
  status checks. No-op re-submissions and proc-bearing PRs are excluded.
- **Cartographer CLI source**: the workflows run the CLI from
  `elanthia-online/cartographer@main` by default; override with the
  `CARTOGRAPHER_REPO` / `CARTOGRAPHER_REF` repository variables (e.g. forks
  rehearsing unmerged CLI branches).
