<p align="center">
  <a href="https://github.com/apps/pull">
    <img alt="Pull App" src="https://prod.download/pull-social-svg" />
  </a>
</p>

<p align="center">
 <a href="https://probot.github.io">
   <img alt="Probot Featured" src="https://badgen.net/badge/Probot/Featured/red?icon=dependabot&cache=86400" />
 </a>
 <a href="https://deno.com">
    <img alt="Deno 2.0" src="https://img.shields.io/badge/Deno%202.0-000000?logo=Deno&logoColor=ffffff" />
 </a>
 <a href="https://www.typescriptlang.org">
    <img alt="TypeScript" src="https://badgen.net/badge/_/TypeScript/blue?&label=&icon=typescript&cache=86400" />
 </a>
 <a href="https://github.com/wei/pull">
   <img alt="Version" src="https://badgen.net/https/pull.git.ci/badges/version?label=Version&color=orange&cache=300" />
 </a>
 <a href="https://github.com/wei/pull">
   <img alt="GitHub Stars" src="https://badgen.net/github/stars/wei/pull?label=Stars&icon=github&color=pink&cache=600" />
 </a>
 <a href="https://wei.mit-license.org">
   <img alt="License" src="https://badgen.net/badge/License/MIT/grey?cache=86400" />
 </a>
</p>

> 🤖 a GitHub App that keeps your forks up-to-date with upstream via automated
> pull requests.

<p>
 <a href="https://github.com/apps/pull">
   <img alt="Installations" src="https://badgen.net/https/pull.git.ci/badges/installations?labelColor=yellow&cache=600" />
 </a>
 <a href="https://github.com/apps/pull">
   <img alt="Repositories" src="https://badgen.net/https/pull.git.ci/badges/repos?labelColor=orange&cache=600" />
 </a>
 <a href="https://github.com/issues?q=author%3Aapp%2Fpull">
   <img alt="Triggered #" src="https://badgen.net/https/pull.git.ci/badges/triggers?labelColor=pink&cache=600" />
 </a>
</p>

## Features

- 🔄 **Automated Synchronization**: Ensures forks are updated by automatically
  creating pull requests to integrate new changes from upstream
- ⚙️ **Flexible Configuration**: Customize sync behavior through
  `.github/pull.yml` configuration to accommodate different merge strategies,
  including merge, squash, rebase, and hard reset
- 🕒 **Scheduled Updates**: Regularly checks for upstream changes periodically
  to ensure forks are always up-to-date
- 👥 **Team Integration**: Facilitates collaboration by automatically adding
  assignees and reviewers to pull requests, honoring branch protection rules and
  working seamlessly with pull request checks and reviews
- 🚀 **Enterprise Ready**: Supports GitHub Enterprise Server, ensuring a smooth
  integration process for enterprise-level projects

### Prerequisites

- Upstream must be in the same fork network.
- ⚠️ _Make a backup if you've made changes._

## Getting Started

**[⭐ Star this project][pull-repo]** (Highly recommended, starred users may
receive priority over other users)

### Basic Setup

- Just install
  **[<img src="https://prod.download/pull-18h-svg" valign="bottom"/> Pull app][pull-app]**.

Pull app will automatically watch and pull in upstream's default (master) branch
to yours using **hard reset** periodically. You can also manually
[trigger](#trigger-manually) it anytime.

### Advanced Configuration (with config file)

1. Create a new branch.
2. Setup the new branch as default branch under repository Settings > Branches.
3. Add `.github/pull.yml` to your default branch.

   #### Most Common
   (behaves the same as Basic Setup)
   ```yaml
   version: "1"
   rules:
     - base: master
       upstream: wei:master # change `wei` to the owner of upstream repo
       mergeMethod: hardreset
   ```

   #### Advanced usage
   ```yaml
   version: "1"
   rules: # Array of rules
     - base: master # Required. Target branch
       upstream: wei:master # Required. Must be in the same fork network.
       mergeMethod: hardreset # Optional, one of [none, merge, squash, rebase, hardreset], Default: none.
       mergeUnstable: false # Optional, merge pull request even when the mergeable_state is not clean. Default: false
     - base: dev
       upstream: master # Required. Can be a branch in the same forked repo.
       assignees: # Optional
         - wei
       reviewers: # Optional
         - wei
       conflictReviewers: # Optional, on merge conflict assign a reviewer
         - wei
   label: ":arrow_heading_down: pull" # Optional
   conflictLabel: "merge-conflict" # Optional, on merge conflict assign a custom label, Default: merge-conflict
   ```

4. Go to `https://pull.git.ci/check/${owner}/${repo}` to validate your
   `.github/pull.yml`.
5. Install
   **[![<img src="https://prod.download/pull-18h-svg" valign="bottom"/> Pull](https://prod.download/pull-18h-svg) Pull app][pull-app]**.

### For Upstream Repository Owners

For the most common use case (a single `master` branch), you can just direct
users to install Pull with no configurations. If you need a more advanced setup
(such as a `docs` branch in addition to `master`), consider adding
`.github/pull.yml` to your repository pointing to yourself (see example). This
will allow forks to install Pull and stay updated automatically.

Example (assuming `owner` is your user or organization name):

```yaml
version: "1"
rules:
  - base: master
    upstream: owner:master
    mergeMethod: hardreset
  - base: docs
    upstream: owner:docs
    mergeMethod: hardreset
```

## Contributing

See [CONTRIBUTING.md](./.github/CONTRIBUTING.md)

## License

[MIT](LICENSE) © [Wei He][pull-sponsor]

## Support

_Can you help keep this open source service alive?
**[💖 Please sponsor : )][pull-sponsor]**_

---

Made with ❤️ by [@wei](https://github.com/wei)

[probot-url]: https://probot.github.io/
[license-url]: https://wei.mit-license.org
[pull-app]: https://github.com/apps/pull
[pull-website]: https://wei.github.io/pull
[pull-repo]: https://github.com/wei/pull
[pull-sponsor]: https://prod.download/pull-readme-sponsor
