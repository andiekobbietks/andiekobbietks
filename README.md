<!--
  Andie Kobbie | GitHub profile
  Motion is kept in self-contained SVG assets because GitHub sanitises scripts
  and does not execute JavaScript in profile READMEs.
-->

<div align="center">

<img src="./assets/typing.svg" alt="Andie Kobbie: IT practitioner and product-minded engineer building agentic AI tooling, DevSecOps workflows, cloud infrastructure and open-source systems." width="100%" />

<p>
  <a href="https://uk.linkedin.com/in/andiekobbietks">LinkedIn</a> ·
  <a href="https://github.com/andiekobbietks?tab=repositories">Repositories</a> ·
  <a href="https://twitter.com/andiekobbie">X</a>
</p>

</div>

---

## About

I'm **Andie Kobbie**, an IT practitioner and product-minded engineer working across **agentic AI, DevSecOps, cloud infrastructure and open-source software**.

My focus is the engineering layer that makes modern systems useful and dependable: connecting agent workflows to tools, building practical cloud platforms, improving operational visibility, and making software easier to inspect, govern and run.

I bring together hands-on IT operations, infrastructure support, software development and technical education. I enjoy taking an idea from an early experiment through implementation, documentation, testing and release.

## Product engineering approach

I approach product engineering as an end-to-end discipline, not simply writing code or assembling a prototype. I work from the problem and intended user outcome through:

- **Problem framing:** clarify the user need, constraints, assumptions and what success should look like.
- **Systems thinking:** shape the architecture, interfaces, data flows and operational model around the wider product.
- **Build and integration:** use appropriate tools and automation to turn ideas into working software and connected services.
- **Validation:** test behaviour, usability, reliability and security; distinguish demonstrated capabilities from planned work.
- **Delivery and iteration:** document decisions, review changes, make releases traceable and improve the product from evidence.

My interest is in the connective tissue between product, software, infrastructure and operations: building things that are not only demonstrable, but understandable, maintainable and useful.


## Featured service identity: AKTOps

**AKTOps** is my IT operations, cloud infrastructure and DevSecOps service identity under Andrea Kwabena Technologies. It brings together practical platform operations, automation, infrastructure support and dependable digital services.

Built around a distinctive near-black and phosphorescent neon-green identity (`#080808` / `#39FF14`), the project brings together the service proposition and the engineering work behind it.

- **[Visit the existing website deployment](https://akcloud.netlify.app)** (legacy AKCloud URL; domain and site branding will be updated separately)
- **[Explore the website repository](https://github.com/andiekobbietks/akcloud-site)** (repository name retained for now; rebrand planned)

## What I'm building

I use projects to investigate practical engineering questions: where existing systems fall short, what could work differently, and how an idea can be turned into something testable. The descriptions below explain the problem behind each project and the question it is designed to answer.

| Project | Problem or curiosity | What the project explores | Stack and engineering rationale |
| --- | --- | --- | --- |
| **[AI Trust Observatory](https://github.com/andiekobbietks/ai-trust-observatory)** | Dragos's canary-based investigation raised a difficult question: when prompts pass through AI providers, routers and downstream services, can organisations see where their data goes and test the assurances they are given? | An independent, open-source AI inference supply-chain assurance and observability research framework. It explores synthetic canaries, inference-route visibility and evidence correlation. Inspired by Dragos's published research; independently developed and not affiliated with or endorsed by Dragos. | **JSON Schema, JSONL, static HTML, Markdown and GitHub Actions.** A lightweight research scaffold keeps evidence portable and inspectable without introducing a backend before the collectors and event pipeline are implemented. OpenObserve and provider integrations are planned, not yet complete. |
| **[AgentSON](https://github.com/andiekobbietks/AgentSON)** | Agent sessions and their histories can become fragmented across tools and runtimes. How can session data be preserved, inspected and exchanged without losing context or provenance? | An open interchange format and tooling for structured agent-session data, interoperability and governance. | **Python, JSON/JSONL, JSON Schema, CLI tooling and tests, with JavaScript/TypeScript components for supporting web tooling.** Python provides cross-platform parsing and transformation; an open, schema-backed data format keeps session records portable and independent of any one agent runtime. |
| **[Edge LLM Benchmark](https://github.com/andiekobbietks/edge-llm-benchmark-vivobook)** | Does useful local AI inference always require a powerful GPU or expensive hardware? What can an everyday, memory-constrained laptop realistically run? | Reproducible local inference experiments on constrained hardware, comparing execution paths and documenting performance, compatibility and limitations, including CPU and integrated-GPU testing. | **Python, Ollama, OpenVINO, Hugging Face model artefacts and Windows/PowerShell tooling.** These provide comparable local inference paths and reproducible measurements across CPU and integrated graphics, exposing real hardware constraints rather than relying on theoretical GPU performance. |
| **[Abena AI API](https://github.com/andiekobbietks/abena-ai-api)** | How can developers build with African-language speech technology if useful capabilities are difficult to access or integrate into their own applications? | An HTTP API that makes African-language speech technology easier to experiment with and integrate into applications. | **HTTP/REST, JSON, multipart audio uploads and Base64-encoded WAV responses.** A language-agnostic API contract lets web, mobile and server applications integrate speech synthesis and transcription without a proprietary client. The repository documents the API surface; it does not establish the underlying provider's backend framework. |
| **[Taskmaster Productivity Suite](https://github.com/andiekobbietks/taskmaster-pro-ultimate-todo-productivity-suite)** | Can a practical productivity application be built on lightweight serverless infrastructure without depending on a conventional always-on application server? | A serverless application exploring Cloudflare Workers, Hono and SQLite Durable Objects for application logic and persistent state. | **TypeScript (ES modules), Hono, Cloudflare Workers and Durable Objects with embedded SQLite.** Hono keeps routing lightweight; Workers avoid an always-on server; Durable Objects provide coordinated, persistent state close to the application logic. |
| **[Product Engineering Lab](https://github.com/andiekobbietks/product-engineering-lab)** | How do you move beyond a compelling technical demo and develop an idea into something that can be evaluated, improved and delivered as a product? | Experiments connecting generative 3D, AI-assisted engineering and evidence-led product development, with an emphasis on turning exploration into testable outcomes. | **Python, Blender's Python API, Sand3D and GitHub Actions, with GLB, URDF, USDA, OBJ and STL exports.** Python makes geometry generation and validation scriptable; Sand3D is the canonical modelling and assembly path; standard formats support downstream inspection and interoperability. Legacy CadFlow work is retained for comparison, not the active build path. |

## Open-source & engineering interests

- **Agentic systems:** agent CLIs, MCP, session interoperability, evaluation and governance.
- **DevSecOps:** secure-by-design workflows, code review, automation, observability and release discipline.
- **Cloud & infrastructure:** AWS, Azure, Oracle Cloud Infrastructure, Cloudflare and containerised workloads.
- **Applied AI:** local inference, LLM evaluation, retrieval workflows and practical AI integration.
- **Product engineering:** turning prototypes into documented, testable and maintainable software.

## Engineering standards

The preferred application stack, security baseline, repository classifications and incremental adoption policy are documented in the [Engineering Standards](./ENGINEERING_STANDARDS.md). These standards are additive: existing projects retain their architecture unless a measured, reviewed change justifies otherwise.

## Contribution activity

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/andiekobbietks/andiekobbietks/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/andiekobbietks/andiekobbietks/output/github-contribution-grid-snake.svg" />
  <img alt="Animated contribution trail in AKTOps neon green and dark tones" src="https://raw.githubusercontent.com/andiekobbietks/andiekobbietks/output/github-contribution-grid-snake.svg" width="100%" />
</picture>

## Technology toolkit

<div align="center">

![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white)
![Microsoft Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Oracle Cloud](https://img.shields.io/badge/Oracle_Cloud-F80000?style=for-the-badge&logo=oracle&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![LLM tooling](https://img.shields.io/badge/LLM_tooling-412991?style=for-the-badge&logo=openai&logoColor=white)

</div>

## Education & learning

- **BSc (Hons) Information Communication Technology** - University of South Wales.

  My degree included a progressive, three-year sequence of computer networking modules:

  | UK undergraduate level | Module | What the level represents |
  | --- | --- | --- |
  | **Level 4** | Computer Systems and Network Technologies | First-year undergraduate study. Built the foundations in computer systems and networking concepts. |
  | **Level 5** | Applied Computer Networking | Second-year undergraduate study. Developed the ability to apply networking knowledge to practical networking scenarios. |
  | **Level 6** | Advanced Applied Computer Networking | Final-year honours-level study. Progressed to more advanced application and analysis of computer networking. |

  For readers outside the UK, Levels 4, 5 and 6 refer to the stages of study within my UK bachelor's degree: broadly, first, second and final year. They are not separate certifications or three separate degrees.

- **Cisco Networking Academy (NetAcad)** - accessed through university-provided NetAcad login credentials and course enrolments throughout my studies, with enrolment continuing year on year. I completed the NetAcad CCNA v7 learning materials available at the time, including the associated Packet Tracer labs. The completed lab work and supporting evidence are available upon request. This was completion of learning materials and practical labs, **not a Cisco CCNA certification or a claim that I passed the CCNA certification exam**.

  I am currently continuing my CCNA studies independently, building on that foundation through ongoing hands-on Packet Tracer practice and further networking labs.

- **AWS re/Start** - cloud computing and practical AWS foundations.
- Continuing to develop across cloud architecture, automation, secure software delivery and AI engineering.

## Beyond the terminal

I'm also a **semi-professional drummer and percussionist**, with performing experience across rock, jazz, bossa nova and gospel. Alongside music, I'm a STEM Ambassador and community mentor. Through education and community work, I enjoy helping people build confidence with technology and access opportunities in digital careers.

## Find me

- [LinkedIn](https://uk.linkedin.com/in/andiekobbietks)
- [GitHub repositories](https://github.com/andiekobbietks?tab=repositories)
- [X](https://twitter.com/andiekobbie)

<sub>Build thoughtfully. Make it observable. Document the work. Keep learning.</sub>
