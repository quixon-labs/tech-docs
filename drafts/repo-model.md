# Source code repository model

### Highlights

- **Hybrid mix of monorepo and multi-repo.** 
- Each project lives in it's own repo.
- Checkout all relevant source code into a mono-repo root, say "quixon" directory. 
- Local builds follow monorepo paradigm.
- Internal repo paths are always relative.
- [TODO] Versioning is explained here.

### Detailed:

- Cognitively, a high-level mono repo.
- **Dependency projects** are resolved from the **mono-repo root** (usually the parent dir). 
- But **each project, own repo**, under the mono-repo root.(Currently, the gitlab/github organization root)
- This provides the ease of the mono-repository, while having things split into small, focused multi-repositories. 
- Permissions can be controlled individually, unlike pure monorepos.
- Secure dependencies can be mocked easily with mock repositories, while the CI systems access real repos. 
- Can move in either direction as we scale - A mono-repo system like Google, Facebook with extensive test coverage and build infra or a multi-repo system like Amazon, with extensive arbitration infra.
- This price of this simplicity is an external CI runner that builds all repos as a mono repo with intelligent caches on each commit. 
