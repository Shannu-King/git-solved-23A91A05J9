# My Git Mastery Challenge Journey

## Student Information
- **Name**: Shanmukh Tharun
- **Student ID**: 23A91A05J9
- **Repository**: https://github.com/Shannu-King/git-solved-23A91A05J9.git
- **Date Started**: 29/10/2025
- **Date Completed**: 29/10/2025

## Task Summary
Cloned an instructor's repository with pre-built conflicts. I resolved all merge conflicts across two major merge operations (main+dev, main+conflict-simulator) and practiced advanced Git commands like stash, rebase, and cherry-pick. I documented the entire process and pushed the final, resolved repository to my own GitHub.

## Commands Used
| Command | Times Used | Purpose |
|---|---|---|
| `git clone` | 1 | Clone instructor's repository |
| `git checkout` | 10+ | Switch between branches |
| `git branch` | 5+ | View and manage branches |
| `git merge` | 2 | Merge `instructor/dev` and `instructor/conflict-simulator` into main |
| `git add` | 20+ | Stage resolved conflicts and new files |
| `git commit` | 10+ | Commit resolved changes |
| `git push` | 10+ | Push to my `origin` repository |
| `git fetch` | 1 | Fetch updates from `instructor` remote |
| `git pull` | 1 | Pull updates from `instructor` remote |
| `git stash` | 1 | Save temporary work while switching branches |
| `git cherry-pick`| 2 | Copy specific commit (one from feature, one from reflog) |
| `git rebase` | 1 | Rebase feature branch onto main |
| `git reset` | 3 | Undo commits (soft/mixed/hard) |
| `git revert` | 1 | Safe undo |
| `git tag` | 2 | Create `v1.0.0` and `v1.1.0` release tags |
| `git status` | 20+ | Check repository state |
| `git log` | 10+ | View history |
| `git diff` | 1 | Compare `main` to `instructor/main` |
| `git remote` | 3+ | Manage `origin` and `instructor` remotes |
| `git reflog` | 1 | Find "lost" commit |

## Conflicts Resolved

### Merge 1: main + dev (6 files)

#### Conflict 1: `config/app-config.yaml`
- **Issue**: Production used port 8080, development used 3000.
- **Resolution**: Created a unified config file with both production and development settings, using the production settings as default and adding development keys as optional.
- **Difficulty**: Medium

#### Conflict 2: `config/database-config.json`
- **Issue**: Different database hosts, SSL modes, and keys.
- **Resolution**: Restructured the JSON to have separate top-level keys: `production` and `development`, each containing its own connection and backup settings.
- **Difficulty**: Medium

#### Conflict 3: `scripts/deploy.sh`
- **Issue**: Completely different deployment strategies (production vs. docker-compose).
- **Resolution**: Added conditional logic using an `if/elif/else` block based on the `$DEPLOY_ENV` variable to handle `production` and `development` deploys in one script.
- **Difficulty**: Hard

#### Conflict 4: `scripts/monitor.js`
- **Issue**: Different monitoring intervals and log formats.
- **Resolution**: Created a `monitorConfig` object with nested `production` and `development` profiles. The script reads `process.env.NODE_ENV` to decide which config to use.
- **Difficulty**: Medium

#### Conflict 5: `docs/architecture.md`
- **Issue**: Different architectural descriptions.
- **Resolution**: Merged both descriptions into one comprehensive document, adding sections to clarify the differences between production and development.
- **Difficulty**: Easy

#### Conflict 6: `README.md`
- **Issue**: Different feature lists and version numbers.
- **Resolution**: Combined all features, put them under `Production` and `Development` sub-headings, and added my Student ID.
- **Difficulty**: Easy

---

### Merge 2: main + conflict-simulator (6 files)


#### Conflict 1: `config/app-config.yaml`
- **Issue**: My resolved `main` branch conflicted with the new `experimental` version.
- **Resolution**: Kept my stable `prod/dev` config and added the new `ai_features`, `cloud_providers`, etc., as **comments** to prevent them from breaking the build.
- **Difficulty**: Medium

#### Conflict 2: `config/database-config.json`
- **Issue**: My `prod/dev` JSON structure conflicted with the new `distributed` database structure.
- **Resolution**: Kept my `production` and `development` profiles and added the entire `conflict-simulator` version as a new top-level key: `"experimental"`.
- **Difficulty**: Medium

#### Conflict 3: `scripts/deploy.sh`
- **Issue**: My `if/elif` script conflicted with a new experimental AI deployment script.
- **Resolution**: Added a new `elif [ "$DEPLOY_ENV" = "experimental" ]` block and pasted the entire experimental script's logic inside it, creating a 3-mode script.
- **Difficulty**: Hard

#### Conflict 4: `scripts/monitor.js`
- **Issue**: My 2-mode config object conflicted with a new experimental AI monitoring script.
- **Resolution**: Added an `"experimental"` profile to the `monitorConfig` object and then added an `if (config.aiEnabled)` block in the `checkSystemHealth` function to run the correct logic.
- **Difficulty**: Hard

#### Conflict 5: `docs/architecture.md`
- **Issue**: My `prod/dev` documentation conflicted with the new experimental architecture doc.
- **Resolution**: Appended the entire experimental documentation (starting with `# System Architecture - Experimental Build`) to the end of my existing file.
- **Difficulty**: Easy

#### Conflict 6: `README.md`
- **Issue**: My resolved `README.md` conflicted with the new experimental `README.md`.
- **Resolution**: Merged them by adding a new "Experimental Features" section and an "Experimental Mode" quick-start block to my existing README.
- **Difficulty**: Easy

## Most Challenging Parts
1.  **`scripts/monitor.js` Merge 2:** The second merge of `monitor.js` was the hardest. The two versions did completely different things. I had to create a new config profile and then wrap the new logic in an `if` statement to make it work.
2.  **`git rebase`**: Understanding `rebase` vs. `merge` was tricky. Needing to use `--force` after a rebase was scary but I understand why it's necessary now.
3.  **`git reset`**: Realizing that `git reset --hard` *actually* deletes your work was a surprise, but `git reflog` is an amazing safety net.

## Key Learnings
- **Conflicts are Just Decisions:** Merge conflicts aren't errors; they're just Git asking me to make a decision.
- **Read the Markers:** The `<<<<< HEAD`, `=======`, and `>>>>>` markers are my guide. `HEAD` is always my current branch.
- **`git status` is My Best Friend:** I ran `git status` constantly to see what state I was in, especially during merges.
- **Advanced Commands are Situational:** `stash` is for interruptions, `cherry-pick` is for surgical fixes, and `rebase` is for cleaning up history *before* sharing.