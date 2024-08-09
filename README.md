# Awesome GitHub Actions runners ⚡🤖

![Awesome badge](assets/awesome.png) ![Static Badge](https://img.shields.io/badge/Made_with-Markdown-purple) ![GitHub Repo stars](https://img.shields.io/github/stars/neysofu/awesome-github-actions-runners) [![X (formerly Twitter) Follow](https://img.shields.io/twitter/follow/neysofu)](https://twitter.com/neysofu)

GitHub Actions are pretty damn cool, but lord knows the official runners are slow, unreliable, and [expensive](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions#about-billing-for-github-actions). Self-hosted runners are typically championed as the better alternative, but they're also a pain to set up and maintain and they come with important security [concerns](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners#self-hosted-runner-security).

**It doesn't have to be one or the other. Most people don't know this, but there's quite a few third-party GH Actions runner services out there, most of which require no changes at all to your CI workflows.** These are easy to migrate to, much cheaper than official runners, and often faster.

## Table of contents

- [Awesome GitHub Actions runners ⚡🤖](#awesome-github-actions-runners-)
	- [Table of contents](#table-of-contents)
	- [List of providers](#list-of-providers)
		- [Namespace ⭐](#namespace-)
		- [BuildJet ⭐](#buildjet-)
		- [Actuated ⭐](#actuated-)
		- [WarpBuild](#warpbuild)
		- [Blacksmith](#blacksmith)
		- [Ubicloud](#ubicloud)
		- [RunsOn](#runson)
		- [Cirun](#cirun)
	- [Honorable mentions](#honorable-mentions)
	- [Contributing to this list](#contributing-to-this-list)

## List of providers

### Namespace ⭐

[Namespace](https://namespace.so/docs/features/faster-github-actions) provides development environments, remote builders, ephemeral environments, managed CI runners, and more. It also supports BuildKite[^2e].

Pricing [here](https://namespace.so/pricing).

Notable features:
- **1-line change to get faster and cheaper builds in most projects.**
- Up to 250GiB disk storage and terabytes of cache, considerably more than both BuildJet and GitHub official runners.
- High-performance caching via mounted volumes backed by local storage. This is a separate API from [`actions/cache`](https://github.com/actions/cache), but much faster and more reliable.
- Built-in observability for CPU, memory, and storage usage. Streams and retains Docker container logs in addition to runner logs. Remote terminal (SSH) access.
- Dedicated high-performance remote Docker builders with zero-configuration incremental caching, ARM support, and more.[^2b]
- Supports ephemeral previews running on runners as well as separate instances, based on Docker[^2c] or Kubernetes[^2d].
- macOS runners on Apple Silicon (M2).
- Custom base images support.
- **(Coming soon)** Windows support (Q1 2024). 🚧
- **(Coming soon)** SOC2 compliance (Q1 2024). 🚧

[^2a]: https://namespace.so/docs/actions/nscloud-cache-action
[^2b]: https://namespace.so/docs/features/faster-builds
[^2c]: https://namespace.so/docs/features/previews
[^2d]: https://namespace.so/docs/features/kubernetes-previews
[^2e]: https://namespace.so/docs/features/on-demand-buildkite-agents

### BuildJet ⭐

[BuildJet](https://buildjet.com/for-github-actions/docs) offers managed performance runners for GitHub Actions.

Pricing [here](https://buildjet.com/for-github-actions/docs/about/pricing).

Notable features:
- **1-line change to get faster and cheaper builds in most projects.**
- 64GiB disk storage[^1a] and 20GiB free cache per repository[^1b] via [`buildjet/cache`](https://github.com/BuildJet/cache) (as opposed to 16GiB disk storage and 10GiB free cache per repository in GitHub official runners).
- ARM support.[^1c] 
- Built-in support for [`Swatinem/rust-cache`](https://github.com/Swatinem/rust-cache) via `backend: buildjet`.
- In some cases cache download and upload speeds have been reported to be quite bad, slowing down builds[^buildjet-bad-cache]. ⚠️
- **(Coming soon)** SOC2 compliance.[^1d] 🚧

[^1a]: https://buildjet.com/for-github-actions/docs/runners/hardware#runner-disk
[^1b]: https://buildjet.com/for-github-actions/docs/guides/migrating-to-buildjet-cache
[^1c]: https://buildjet.com/for-github-actions/docs/guides/migrating-to-arm
[^1d]: https://buildjet.com/for-github-actions/docs/about/security#is-build-jet-soc-2-compliant
[^buildjet-bad-cache]: https://news.ycombinator.com/item?id=38571518

### Actuated ⭐

[Actuated](https://actuated.dev/) brings fast and secure GitHub Actions to your own infrastructure. It's a more ops-heavy solution compared to fully managed runners, but this comes with significant benefits and attractive pricing.

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

### WarpBuild

[WarpBuild](https://www.warpbuild.com/) offers high performance runners for GitHub Actions, made by the creators of [Argonaut](https://www.argonaut.dev/).

Pricing [here](https://www.warpbuild.com/pricing).

Notable features:
- 1-line change to get faster and cheaper builds in most projects[^warp-1click].
- Support for x86-64 and ARM runners with free unlimited concurrency.
- 150GB disk storage with unlimited fast caches and `setup-*` actions[^warp-cache].
- Bring Your Own Cloud to run workflows in your AWS account and region[^warp-byoc].
- Customizable runner, disk, and processor configurations[^warp-customrunners].
- **Live debug failed jobs over SSH.**[^warp-debug]
- Discounts for open-source projects and young startups, and referral programs to get extra minutes.[^warp-pricing]
- Support for macOS runners on M2 Pros.[^warp-runners]
- Container layer caching, SOC2 Type 2, and 10x faster incremental builds (~Aug 2024). 🚧

[^warp-1click]: https://docs.warpbuild.com/quickstart
[^warp-debug]: https://docs.warpbuild.com/tools/action-debugger
[^warp-pricing]: https://www.warpbuild.com/pricing
[^warp-runners]: https://docs.warpbuild.com/runners#macos-m2-pro-on-arm64
[^warp-byoc]: https://docs.warpbuild.com/byoc
[^warp-cache]: https://docs.warpbuild.com/cache
[^warp-customrunners]: https://docs.warpbuild.com/cloud-runners/custom-runners


### Blacksmith

[Blacksmith](https://blacksmith.sh/) provides high-performance runners for GitHub Actions that run up to twice as fast as GitHub's official runners at half the cost. Founded by ex-engineers at Cockroach Labs and Faire.

Pricing [here](https://docs.blacksmith.sh/runners/pricing).

Notable features:
- 1-line change to get faster and cheaper builds in most projects, as well as a "**Migration Wizard**" which can automatically migrate multiple workflow files at once.[^blacksmith-1line][^blacksmith-wizard]
- 64GiB disk storage[^blacksmith-storage] and 25GiB high-speed cache per repository via [`useblacksmith/cache@v5`](https://github.com/useblacksmith/cache).
- Docker local registry mirror which caches Docker images and prevents customers from getting rate limited by Docker Hub.[^blacksmith-mirror]
- SOC2 Type 1 Compliant [^blacksmith-soc2]
- **3000 free minutes per month**.[^blacksmith-free-minutes]
- **(Coming soon)** ARM runners. 🚧
- **(Coming soon)** Workflow insights to help customers break down spending and performance across workflows. 🚧

[^blacksmith-1line]: https://docs.blacksmith.sh/getting-started/quickstart
[^blacksmith-storage]: https://docs.blacksmith.sh/runners/config
[^blacksmith-cache]: https://docs.blacksmith.sh/feature-spotlight/collocated-cache
[^blacksmith-mirror]: https://docs.blacksmith.sh/feature-spotlight/docker-pull-through-mirror
[^blacksmith-wizard]: https://blacksmith.sh/blog/launch-migration-wizard
[^blacksmith-soc2]: https://blacksmith.sh/blog/blacksmith-is-soc2-type-1-compliant
[^blacksmith-free-minutes]: https://docs.blacksmith.sh/runners/pricing#free-minutes

### Ubicloud

[Ubicloud](https://www.ubicloud.com/docs/github-actions-integration/quickstart) brings IaaS solutions to bare metal servers, but it also offers a managed platform. GitHub Actions runners are part of this offering. It doesn't seem to have any feature that other providers lack, but it has one of the most attractive pricing plans in the market.

Pricing [here](https://www.ubicloud.com/docs/github-actions-integration/price-performance).

Notable features:
- **1-line change to get faster and cheaper builds in most projects.**[^ubicloud-cheap]
- **By far one of the cheapest providers** at about ~10x cheaper than official GH Actions runners.[^ubicloud-cheap]
- **1250 free minutes per month.**[^5a]
- Native ARM support.[^5b]
- Open source under the GNU AGPL v3.0 license.[^5c]

[^ubicloud-cheap]: https://www.ubicloud.com/docs/github-actions-integration/price-performance
[^5a]: https://www.ubicloud.com/use-cases/github-actions
[^5b]: https://www.ubicloud.com/blog/ubicloud-hosted-arm-runners-100x-better-price-performance
[^5c]: https://github.com/ubicloud/ubicloud/blob/main/routes/web/webhook/github.rb

### RunsOn

[RunsOn](https://runs-on.com/) is a self-hosted, open-source GitHub Actions runner tool that runs on your own AWS account. It's **free for non-commercial usage**, and comes at a €300 flat yearly fee for commercial projects.

Pricing [here](https://runs-on.com/).

Notable features:
- **1-line change to get faster and cheaper builds in most projects.**
- Easy install with a CloudFormation template (video guide available).
- Cheap, flat-rate pricing with an easy-to-use [pricing calculator](https://runs-on.com/calculator/) that you can use to calculate your spending.
- ARM, GPU, and custom base image support.
- Up to 256 vCPUs per runner, by far the most of any provider, and customizable disk sizes and instance types.
- Although actively maintained and developed as of Feb. '24, it's built by just one developer ([Cyril Rohr](https://runs-on.com/about/)), so long-term maintenance is a concern. ⚠️

### Cirun

[Cirun](https://cirun.io/) is a tool which lets you **create on-demand self-hosted GitHub Actions runners on your cloud**. After connecting your cloud provider of choice, it's simple to set up and cheap to run.

Pricing [here](https://cirun.io/#pricing).

Notable features:
- **1-line change to get faster and cheaper builds in most projects.**[^4a]
- **Free for public repositories!**
- Cheap, flat-rate pricing based on the number of private repositories you run Cirun on.
- ARM support.
- GPU support.[^4b]
- Support for all major cloud providers.[^4c]
- Built by just one developer ([Amit Kumar](https://github.com/aktech)) in their spare time, so long-term maintenance is a concern. ⚠️

[^4a]: https://docs.cirun.io/reference/one-line
[^4b]: https://docs.cirun.io/reference/yaml#gpu-gpu
[^4c]: https://docs.cirun.io/reference/yaml#cloud-cloud

## Honorable mentions

If you're interested in going down the self-hosted runner route, make sure to check out the tooling listed in [`jonico/awesome-runners`](https://github.com/jonico/awesome-runners)!

## Contributing to this list

If you'd like to add a service to this list or suggest any changes, please open a PR! The list is intentionally opinionated based on pricing and features, but I strive to be reasonable and impartial.

![PRs welcome!](https://camo.githubusercontent.com/0ff11ed110cfa69f703ef0dcca3cee6141c0a8ef465e8237221ae245de3deb3d/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5052732d77656c636f6d652d627269676874677265656e2e7376673f7374796c653d666c61742d737175617265)
