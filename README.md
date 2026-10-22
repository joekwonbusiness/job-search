# job-search

**An open-source, local-first job search and application engine.**

Finding a job shouldn't be a full-time job.

You find a posting, read through the requirements, compare them against your experience, adjust your resume, fill out another application, and repeat. Half the time, you're entering information that's already on your resume.

I got tired of doing that.

Job Search is my attempt to automate the repetitive parts of finding work without turning the process into a spam machine.

The idea is simple: **find jobs I'm actually qualified for, prepare accurate applications, and send them with as little unnecessary work as possible.**

No subscription. No cloud AI requirement. No pretending I have experience I don't have.

Just a tool that helps people find work.

## What I'm building

Job Search brings job discovery, resume matching, application preparation, and tracking into one place.

The goal is to:

- **Find relevant jobs.** Pull openings from supported job APIs and applicant tracking systems.
- **Filter out bad matches.** Compare requirements against actual skills, experience, location, and preferences.
- **Run AI locally.** Use Ollama to evaluate job descriptions and help prepare applications without sending resumes to a hosted LLM.
- **Keep applications honest.** Generate answers using verified resume information, not invented qualifications.
- **Automate repetitive applications.** Submit applications through supported, authorized integrations, with approval controls and rate limits.
- **Track everything.** Know where you've applied, what happened, and which applications need attention.

I want to spend more time preparing for interviews and less time copying my employment history into text boxes.

## How it should work

```text
             JOB SOURCES
                  |
                  v
          Discover openings
                  |
                  v
        Normalize and dedupe
                  |
                  v
          Check eligibility
                  |
                  v
       Match against resume
                  |
                  v
          Local AI (Ollama)
                  |
                  v
       Prepare application
                  |
                  v
        Approval / policy
                  |
                  v
       Authorized submission
                  |
                  v
       Track and follow up
```

The important part is that applications should be relevant.

Sending 5,000 random applications isn't useful if none of them match your experience. I'd rather build something that can identify the right opportunities and handle the repetitive work reliably.

## Local-first by design

I don't want to upload my entire employment history to another AI service just to find a job.

Job Search is being designed around a few principles:

**Your information stays yours.** Resume processing and AI inference run locally. Application data only leaves the system when an authorized job provider needs it.

**No mandatory AI API keys.** Ollama handles local model inference.

**Network access is controlled.** External job data comes through explicitly allowlisted APIs. Unnecessary inbound connections and outbound destinations are denied.

**No fabricated experience.** AI-generated content must be grounded in verified resume facts.

**No duplicate applications.** Every submission needs an identifiable state, an audit record, and a way to verify its outcome.

**No CAPTCHA bypass or platform abuse.** Automation should respect provider permissions, restrictions, and rate limits.

This is as much a software engineering and security project as it is a job-search tool.

## Built on existing open-source work

There are already people building useful pieces of this problem. Rather than reinvent everything, I'm studying and adapting ideas from several projects.

### Core projects

- [Career Ops](https://github.com/career-ops-hq/career-ops) — Career workflows, integrations, and application tracking.
- [JobSweep](https://github.com/ybendiks/jobsweep) — Job discovery, filtering, scoring, and persistence.
- [Job Hunt Engine](https://github.com/agentwolf27/job-hunt-engine) — Eligibility checks, resume validation, and application workflow controls.

### Additional research and references

- [JobSpy](https://github.com/speedyapply/JobSpy) — Multi-platform job discovery.
- [browser-use](https://github.com/browser-use/browser-use) — Browser automation and security patterns.
- [AIHawk](https://github.com/11844/Auto_Jobs_Applier_AIHawk) — Automated application workflows.
- [LinkedIn Easy Apply Bot](https://github.com/nicolomantini/LinkedIn-Easy-Apply-Bot) — Application form automation.

These are upstream projects being evaluated, not necessarily dependencies or code already incorporated into this repository. Any reused code will retain the attribution and licensing required by its original authors.

## Planned architecture

The implementation is still being worked out, but the current direction is:

| Component | Planned technology |
|---|---|
| Backend | Python / FastAPI |
| Frontend | React / TypeScript / Vite |
| Database | PostgreSQL |
| Local AI | Ollama |
| Job discovery | Allowlisted ATS and job-provider APIs |
| Integration interface | REST APIs / optional MCP |
| Deployment | Docker Compose / Portainer |
| CI/CD | GitHub Actions / GHCR |
| Security | Least privilege, secrets isolation, dependency scanning, audit logging |

I'd like to keep this as a modular application rather than turn a relatively straightforward problem into a collection of unnecessary microservices.

Simple is easier to maintain. Easier to maintain is easier to trust.

## Project status

**Early development — architecture and upstream evaluation.**

This is not yet a working, end-to-end automated application system.

The immediate priorities are:

- [ ] Audit and pin upstream repositories.
- [ ] Establish a common job and application data model.
- [ ] Build allowlisted job discovery adapters.
- [ ] Implement resume parsing and verified experience records.
- [ ] Add deterministic eligibility filtering.
- [ ] Integrate local Ollama inference.
- [ ] Build an application preparation and review interface.
- [ ] Implement authorized submission adapters.
- [ ] Add idempotency, submission verification, and audit logs.
- [ ] Package a reproducible self-hosted deployment.
- [ ] Run security and integration tests.

I'll update this README as the implementation progresses.

## Contributing

If you've ever applied to dozens of jobs and wondered why every company needs you to type your resume into another form, you probably understand why I'm building this.

Contributions are welcome, particularly around job-source APIs, applicant tracking system integrations, resume matching, security, testing, and documentation.

I'd especially appreciate contributions that make the software simpler, more reliable, or easier for someone else to self-host.

Open an issue before starting a large change so we can agree on the approach.

## License

Apache License 2.0 is the intended license for original project code, subject to completing the upstream license review and adding the corresponding `LICENSE` and attribution files.

## Why open source?

Because finding work is already difficult enough.

People shouldn't need another expensive subscription just to organize their applications, and they shouldn't need to hand over their personal information to a hosted AI service to get useful assistance.

If this saves someone a few hours, helps them find a better opportunity, or gives another developer something useful to build on, that's a good outcome.

And if you find the project useful, consider giving it a star. It helps other people find it.

---

*Built by someone who would rather solve engineering problems than fill out the same application form for the hundredth time.*
