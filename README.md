# Awesome GitHub Actions runners 🏃🏾‍♀️🤖

![Awesome badge](assets/awesome.png) ![Static Badge](https://img.shields.io/badge/Made_with-Markdown-purple) ![GitHub Repo stars](https://img.shields.io/github/stars/neysofu/awesome-github-actions-runners) [![X (formerly Twitter) Follow](https://img.shields.io/twitter/follow/neysofu)](https://twitter.com/neysofu)

GitHub Actions are pretty damn cool, but lord knows the official runners are slow, unreliable, and [expensive](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions#about-billing-for-github-actions). Self-hosted runners are typically championed as the better alternative, but they're also a pain to set up and maintain and they come with important security [concerns](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners#self-hosted-runner-security).

**It doesn't have to be one or the other. Most people don't know this, but there's quite a few third-party GH Actions runner services out there, most of which require no changes at all to your CI workflows.** These are easy to migrate to, much cheaper than official runners, and often faster.

## Table of contents

- [Awesome GitHub Actions runners 🏃🏾‍♀️🤖](#awesome-github-actions-runners-️)
	- [Table of contents](#table-of-contents)
	- [List of providers](#list-of-providers)
		- [BuildJet ⭐](#buildjet-)
		- [Namespace ⭐](#namespace-)
		- [Actuated ⭐](#actuated-)
		- [Cirun](#cirun)
		- [GitRunners](#gitrunners)
	- [Honorable mentions](#honorable-mentions)
	- [Contributing to this list](#contributing-to-this-list)

## List of providers

### BuildJet ⭐

[BuildJet](https://buildjet.com/for-github-actions/docs) offers managed performance runners for GitHub Actions.

Pricing [here](https://buildjet.com/for-github-actions/docs/about/pricing).

Notable features:
- **1-line change to get faster and cheaper builds in most projects.**
- 64GiB disk storage[^1a] and 20GiB free cache per repository[^1b] via [`buildjet/cache`](https://github.com/BuildJet/cache) (as opposed to 16GiB disk storage and 10GiB free cache per repository in GitHub official runners).
- ARM support.[^1c] 
- Built-in support for [`Swatinem/rust-cache`](https://github.com/Swatinem/rust-cache) via `backend: buildjet`.
- **(Upcoming)** SOC2 compliance.[^1d] 🔜

[^1a]: https://buildjet.com/for-github-actions/docs/runners/hardware#runner-disk
[^1b]: https://buildjet.com/for-github-actions/docs/guides/migrating-to-buildjet-cache
[^1c]: https://buildjet.com/for-github-actions/docs/guides/migrating-to-arm
[^1d]: https://buildjet.com/for-github-actions/docs/about/security#is-build-jet-soc-2-compliant

### Namespace ⭐

[Namespace](https://cloud.namespace.so/docs/features/faster-github-actions) provides development environments, remote builders, ephemeral environments, managed CI runners, and more.

Pricing [here](https://cloud.namespace.so/pricing).

Notable features:
- **1-line change to get faster and cheaper builds in most projects.**
- Up to 250GiB disk storage and 100GiB cache, considerably more than both BuildJet and GitHub official runners.
- Caching is done via mounted volumes, which is API-incompatible with [`actions/cache`](https://github.com/actions/cache) but much faster and more reliable. A compatibility layer is [available](https://cloud.namespace.so/docs/actions/nscloud-cache-action#github-cache-action-compatibility-mode) but marked as deprecated.[^2a]
- Dedicated remote Docker builders with large capacity, zero-configuration incremental caching, ARM support, and more.[^2b]
- Many, many more CI solutions other than GitHub Actions runners. Check out their website for more information.

[^2a]: https://cloud.namespace.so/docs/actions/nscloud-cache-action
[^2b]: https://cloud.namespace.so/docs/features/faster-builds

### Actuated ⭐

[Actuated](https://actuated.io/) brings fast and secure GitHub Actions to your own infrastructure. It's a more ops-heavy solution compared to fully managed runners, but this comes with significant benefits and attractive pricing.

Pricing [here](https://actuated.dev/pricing).

Notable features:
- Native ARM support.[^3a]
- Runs directly within your own datacenter, which is useful if you work with large container images or datasets.
- Live debug stuck jobs over SSH.[^3b]
- Flat-rate billing based on the maximum allowed number of concurrent jobs, so the cost stays the same no matter how many minutes you use.
- Cool development blog showcasing many kinds of demoes, examples, and guides.[^3c]

[^3a]: https://actuated.dev/blog/native-arm64-for-github-actions
[^3b]: https://docs.actuated.dev/tasks/debug-ssh/
[^3c]: https://actuated.dev/blog

### Cirun

[Cirun](https://cirun.io/) is a tool which lets you **create on-demand self-hosted GitHub Actions runners on your cloud**. After connecting your cloud provider of choice, it's simple to set up and cheap to run.

Pricing [here](https://cirun.io/#pricing).

Notable features:
- **1-line change to get faster and cheaper builds in most projects.**[^4a]
- **Free for public repositories!**
- Cheap, flat-rate pricing based on the number of private repositories you run Cirun on.
- Native ARM support.
- GPU support.[^4b]
- Support for all major cloud providers.[^4c]
- Built by just one developer ([Amit Kumar](https://github.com/aktech)) in their spare time, so long-term maintenance is a concern.

[^4a]: https://docs.cirun.io/reference/one-line
[^4b]: https://docs.cirun.io/reference/yaml#gpu-gpu
[^4c]: https://docs.cirun.io/reference/yaml#cloud-cloud

### GitRunners

[GitRunners](https://gitrunners.com/) speeds up GitHub actions with cost-effective performance runners. It's cheaper than GitHub official runners, but doesn't hold up as well against other third-party runners.

Pricing [here](https://gitrunners.com/#pricing).

Notable features:
- 1-line change to get faster and cheaper builds in most projects.
- **(Upcoming)** Persistent storage and mounted volumes. 🔜
- **(Upcoming)** Flamegraph visualizations to analyze workflow runtimes. 🔜

## Honorable mentions

If you're interested in going down the self-hosted runner route, make sure to check out the tooling listed in [`jonico/awesome-runners`](https://github.com/jonico/awesome-runners)!

## Contributing to this list

If you'd like to add a service to this list or suggest any changes, please feel free to open a PR.

![PRs welcome!](https://camo.githubusercontent.com/0ff11ed110cfa69f703ef0dcca3cee6141c0a8ef465e8237221ae245de3deb3d/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5052732d77656c636f6d652d627269676874677265656e2e7376673f7374796c653d666c61742d737175617265)
