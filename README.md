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
    - [Depot](#depot)
    - [Cirrus Runners](#cirrus-runners)
  - [Honorable mentions](#honorable-mentions)
  - [Contributing to this list](#contributing-to-this-list)

## List of providers

### Namespace ⭐

[Namespace](https://namespace.so/docs/features/faster-github-actions) provides managed CI runners, remote Docker builders, native Bazel caching and more. It also backs BuildKite Hosted Agents[^2e].

Pricing [here](https://namespace.so/pricing).

Notable features:

- **1-line change to get faster and cheaper builds in most projects.**
- Up to 250GiB disk storage and terabytes of cache, considerably more than both BuildJet and GitHub official runners.
- High-performance caching via mounted volumes backed by local storage. This is a separate API from [`actions/cache`](https://github.com/actions/cache), but much faster and more reliable.
- Built-in observability for CPU, memory, and storage usage. Streams and retains Docker container logs in addition to runner logs. Remote terminal (SSH) access.
- Dedicated high-performance remote Docker builders with zero-configuration incremental caching, ARM support, and more.[^2b]
- Supports ephemeral previews running on runners as well as separate instances, based on Docker[^2c] or Kubernetes[^2d].
- macOS runners on Apple Silicon (M4 Pro and M2 Pro) with Remote terminal (SSH) and Remote Display (VNC) access.
- SOC 2 Type 2 compliant.[^2f]
- **(Coming soon)** Windows support (Q1 2025). 🚧

[^2b]: https://namespace.so/docs/features/faster-builds
[^2c]: https://namespace.so/docs/features/previews
[^2d]: https://namespace.so/docs/features/kubernetes-previews
[^2e]: https://namespace.so/docs/features/on-demand-buildkite-agents
[^2f]: https://trust.namespace.so

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

[WarpBuild](https://www.warpbuild.com/) offers high performance runners for GitHub Actions with support for Linux, Windows, and macOS. This is available as a managed service, but you can also run it on your own AWS, GCP, or Azure cloud infrastructure.

Pricing [here](https://www.warpbuild.com/pricing).

Notable features:

- 50-90% cheaper GitHub Actions runners with a 1-line chang.[^warp-pricing]
- Support for x86-64 and ARM runners with free unlimited concurrency.
- 150GB disk storage and unlimited fast caches and `setup-*` actions[^warp-cache].
- Bring Your Own Cloud to run workflows in your AWS, GCP, or Azure account and region[^warp-byoc].
- Customizable runner, disk, and processor configurations[^warp-customrunners].
- **Live debug failed jobs over SSH.**[^warp-debug]
- Support for Windows and macOS runners on M2 Pros.[^warp-runners]
- Container layer caching, and 10x faster incremental builds[^warp-snapshots].
- SOC2 Type 2 compliant[^warp-soc2].

[^warp-1click]: https://docs.warpbuild.com/quickstart
[^warp-debug]: https://docs.warpbuild.com/tools/action-debugger
[^warp-pricing]: https://www.warpbuild.com/pricing
[^warp-runners]: https://docs.warpbuild.com/runners#macos-m2-pro-on-arm64
[^warp-byoc]: https://docs.warpbuild.com/byoc
[^warp-cache]: https://docs.warpbuild.com/cache
[^warp-customrunners]: https://docs.warpbuild.com/cloud-runners/custom-runners
[^warp-snapshots]: https://docs.warpbuild.com/snapshot-runners
[^warp-soc2]: https://www.warpbuild.com/blog/soc2

### Blacksmith

[Blacksmith](https://blacksmith.sh/) provides high-performance runners for GitHub Actions that run up to twice as fast as GitHub's official runners at half the cost. Founded by ex-engineers at Cockroach Labs and Faire.

Pricing [here](https://docs.blacksmith.sh/runners/pricing).

Notable features:

- 1-line change to get faster and cheaper builds in most projects, as well as a "**Migration Wizard**" which can automatically migrate multiple workflow files at once.[^blacksmith-1line][^blacksmith-wizard]
- 64GiB disk storage[^blacksmith-storage] and 25GiB high-speed cache per repository via [`useblacksmith/cache@v5`](https://github.com/useblacksmith/cache).
- Docker local registry mirror which caches Docker images and prevents customers from getting rate limited by Docker Hub.[^blacksmith-mirror]
- SOC2 Type 2 Compliant [^blacksmith-soc2]
- **3000 free minutes per month**.[^blacksmith-free-minutes]
- ARM runners.[^blacksmith-arm]
- Workflow statistics to help customers break down spending and performance across workflows.
- Unlimited concurrency at no additional cost, allowing customers to shard without worrying about resource provisioning times.

[^blacksmith-1line]: https://docs.blacksmith.sh/getting-started/quickstart
[^blacksmith-storage]: https://docs.blacksmith.sh/runners/config
[^blacksmith-cache]: https://docs.blacksmith.sh/feature-spotlight/collocated-cache
[^blacksmith-mirror]: https://docs.blacksmith.sh/feature-spotlight/docker-pull-through-mirror
[^blacksmith-wizard]: https://blacksmith.sh/blog/launch-migration-wizard
[^blacksmith-soc2]: https://www.blacksmith.sh/blog/blacksmith-achieves-soc-2-type-2-compliance
[^blacksmith-free-minutes]: https://docs.blacksmith.sh/runners/pricing#free-minutes
[^blacksmith-arm]: https://docs.blacksmith.sh/runners/config#arm

### Ubicloud

[Ubicloud](https://www.ubicloud.com/docs/github-actions-integration/quickstart) brings IaaS solutions to bare metal servers, but it also offers a managed platform. GitHub Actions runners are part of this offering. It doesn't seem to have any feature that other providers lack, but it has one of the most attractive pricing plans in the market.

Pricing [here](https://www.ubicloud.com/docs/github-actions-integration/price-performance).

Notable features:

- **1-line change to get faster and cheaper builds in most projects.**[^ubicloud-cheap]
- **By far one of the cheapest providers** at about ~10x cheaper than official GH Actions runners.[^ubicloud-cheap]
- 1250 free minutes per month.[^ubicloud-free-minutes]
- Native ARM and GPU support.[^ubicloud-arm] [^ubicloud-gpu]
- Transparent Cache offers 30GB of free, faster GitHub Actions cache with no configuration needed. [^ubicloud-cache]
- Live debug jobs over SSH. [^ubicloud-debug]
- Open source under the GNU AGPL v3.0 license.[^ubicloud-open-source]
- SOC2 Type 2 Compliant [^ubicloud-soc2]

[^ubicloud-cheap]: https://www.ubicloud.com/docs/github-actions-integration/price-performance
[^ubicloud-free-minutes]: https://www.ubicloud.com/use-cases/github-actions
[^ubicloud-arm]: https://www.ubicloud.com/blog/ubicloud-hosted-arm-runners-100x-better-price-performance
[^ubicloud-gpu]: https://www.ubicloud.com/docs/github-actions-integration/use-gpu-runners
[^ubicloud-cache]: https://www.ubicloud.com/docs/github-actions-integration/ubicloud-cache#ubicloud-transparent-cache
[^ubicloud-debug]: https://www.ubicloud.com/docs/github-actions-integration/debug-workflow-with-ssh
[^ubicloud-open-source]: https://github.com/ubicloud/ubicloud/blob/main/routes/web/webhook/github.rb
[^ubicloud-soc2]: https://www.ubicloud.com/docs/security/soc2

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

### Depot

[Depot](https://depot.dev) accelerates Docker image builds and Github Actions workflows with optimized remote builders and centralized cache. Depot's remote builders now power all [fly.io](https://fly.io/) builds.[^5a]

Pricing [here](https://depot.dev/pricing).

Notable features:

- **Half the price** of hosted GitHub runners.
- **3x faster** than hosted GitHub runners.[^5b]
- Native build support for **macOS (M2)** and **ARM**.[^5c]
- **Unlimited cache storage**.
- Per-second billing. No 1 minute minimum.
- Bring your own GPU support.[^5d]

[^5a]: https://community.fly.io/t/depot-remote-builders-becoming-the-default/21756?u=kylet-depot
[^5b]: https://depot.dev/products/github-actions
[^5c]: https://depot.dev/docs/github-actions/runner-types
[^5d]: https://depot.dev/docs/managed/using-gpus

### Cirrus Runners

[Cirrus Runners](https://cirrus-runners.app/) offers managed large runners (macOS M4 Pro, Linux x86/Arm/GPU) at a fixed price per month. Unlimited minutes with a limited concurrency.

Pricing [here](https://cirrus-runners.app/pricing/).

Notable features:

- Cirrus Labs develops their own virtualization solutions and host their own hardware off traditional cloud providers.
- **Fixed price** of hosted GitHub runners. No hidden fees.
- **2x faster** than hosted GitHub runners.[^6a]
- Additional caching at no extra cost.
- SOC2 Type 1 compliant.

[^6a]: https://cirrus-runners.app/blog/2025/01/07/announcing-m4-pro-availability-for-cirrus-runners/

## Honorable mentions

If you're interested in going down the self-hosted runner route, make sure to check out the tooling listed in [`jonico/awesome-runners`](https://github.com/jonico/awesome-runners)!

## Contributing to this list

If you'd like to add a service to this list or suggest any changes, please open a PR! The list is intentionally opinionated based on pricing and features, but I strive to be reasonable and impartial.

![PRs welcome!](https://camo.githubusercontent.com/0ff11ed110cfa69f703ef0dcca3cee6141c0a8ef465e8237221ae245de3deb3d/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5052732d77656c636f6d652d627269676874677265656e2e7376673f7374796c653d666c61742d737175617265)
