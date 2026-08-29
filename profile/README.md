# Uraion Labs

Uraion Labs researches and builds adaptive AI systems. We work on agent runtimes, orchestration, persistent memory, and reliable execution — including local and private deployments.

[Website](https://uraionlabs.com) · [Research](https://uraionlabs.com/#research) · [Products](https://uraionlabs.com/products) · [Contact](https://uraionlabs.com/#contact)

## What we are building

Research produces methods. We turn those methods into systems, put the systems into products, and learn from how the products run.

Current product work is **Uraion Fabric**: an agent runtime that uses frontier models for planning and difficult reasoning, and smaller specialized models for focused work. Memory stores useful procedures and past failures. Results are checked with tests, tool output, and structured review before they are accepted.

Fabric is in development and has not been released. Public details are on the [product page](https://uraionlabs.com/products). Source will be published in this organization when it is ready for an external audience.

## Focus

- **Agents and orchestration** — planning, splitting work, running tasks in parallel, recovering from failure, and escalating when needed
- **Agent runtimes** — processes that own execution, tool use, and the boundary between a model and a machine
- **Memory** — storing and retrieving procedures, context, and failures across runs
- **Local and private AI** — running sensitive work and smaller models on infrastructure you control
- **Open models and research** — using open models, local deployment, and alternative architectures when they are the better engineering choice
- **Evaluation** — testing real workflows rather than isolated prompts

We prefer the smallest capable model for a task and escalate only when necessary.

## Projects and research

### Uraion Fabric

An adaptive agent runtime. Frontier models supervise; specialized workers execute; memory and verification sit on the critical path. Local and private execution is a first-class concern.

- Status: in development, not released
- Public write-up: [uraionlabs.com/products](https://uraionlabs.com/products)

This GitHub organization is new. Public repositories will appear here as we release systems, libraries, and research artifacts.

### Research

We study how agents plan, delegate, remember, and check their work, and how to run that stack efficiently. Current tracks:

| Track | Question |
| --- | --- |
| Agent orchestration | How agents plan, split work, run in parallel, recover, and escalate |
| Memory systems | How systems store and retrieve procedures, context, and past failures |
| Model specialization | How smaller models handle focused tasks within clear limits |
| Efficient and local inference | How to use the smallest capable model, including on private infrastructure |
| Evaluation and verification | How to test real workflows with tools, structured checks, and review |
| Adaptive systems | How systems learn from validated experience without retraining for every lesson |

## Contributing

We welcome issues and pull requests on public repositories. Some work is still private or unreleased; if a repository is not open, the website is the public source of information.

1. Read the repository README and any repo-specific contributing guide.
2. Search existing issues before opening a new one.
3. Use the issue templates for bugs and feature requests.
4. Open a focused pull request that states what changed, why, and how it was tested.

Organization defaults (a repository may override these):

- [Contributing](https://github.com/UraionLabs/.github/blob/main/CONTRIBUTING.md)
- [Code of conduct](https://github.com/UraionLabs/.github/blob/main/CODE_OF_CONDUCT.md)
- [Security](https://github.com/UraionLabs/.github/blob/main/SECURITY.md)
- [Support](https://github.com/UraionLabs/.github/blob/main/SUPPORT.md)

## Contact

Use the [contact form](https://uraionlabs.com/#contact) for product, research, infrastructure, partnership, and career inquiries.
