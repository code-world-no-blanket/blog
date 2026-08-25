---
tags: ai, teaching, software-engineering
authors: dcbrown
---

# An Agent Template for Teaching Software Engineering

Generative AI coding assistants are rapidly changing how software is developed in practice, and students are increasingly using these tools into their coursework with or without instructor guidance. In a [recent reflection](./2026-06-10_posse.html) on the POSSE workshop, I discussed plans to integrate free and open-source AI-assisted development tools into our undergraduate software engineering course this fall ([CS3704: Intermediate Software Design and Engineering](https://github.com/CS3704-VT/Course)) this fall. The plan included adopting open-source AI tooling along with automating scaffolding so the focus stays on learning with the usage of AI tools [Wang2025]. 

This post introduces the **[agent template](https://github.com/CS3704-VT/agent-template)** I will use for the class this semester. The template is based on [opencode](https://opencode.ai), a free and open-source AI coding environment similar to Claude Code where students interact with a team of specialized AI agents. Students will leverage this harness using models provided through the Virginia Tech Advanced Research Computing, most of which are open-source/open-weight and are freely available to VT students. 

The devised agents (see below) were designed to have defined roles, clear boundaries, and built-in moments for reflection and learning. The goal is to provide an opportunity for students to experience something close to how developers work with agents on real projects while also supporting their learning. The remainder of this post provides an overview of how the template attempts to achieve these goals.

## The Agents


* **Plan** (default in Opencode) is a read-only agent designed to help with planning and brainstorming, but it cannot edit files. 
* **Build** (default in Opencode) is the coding agent that has full edit and bash access to implement what Plan designs, including features, tests, and refactors.
* **@dcbrown** is the course assistant subagent, designed to answer schedule and policy questions by fetching details from the course repository and syllabus. `dcbrown` can also run concept checks and quizzes to help students gain knowledge on course topics.
* **@assignment** is another course assistant subagent with three main commands: `analyze` parses assignment requirements from the course repository into a structured file; `validate` checks the student's repository against those requirements; and `submit` packages everything for submission with an AI-usage disclosure. 

## The Skills

Skills are loadable modules that any agent can invoke to provide specialized instructions and resources for specific tasks.

### Quiz

The `quiz` skill designs brief learning assessments based on the cours learning outcomes. Quizzes can be invoked by the user or automatically invoked by an agent for a "pop quiz".

### Concept Explain

The `concept-explain` skill provides definitions of software engineering concepts when prompted by students derived from the lecture materials. Each concept has a concise definition shown to the student, followed by two or three knowledge-check questions.

### Learning Opportunities

Derived from the skills from [Cat Hicks](https://www.drcathicks.com/), the [`learning-opportunities`](https://github.com/DrCatHicks/learning-opportunities) skill provides exercises to facilitate deliberate skill development after significant AI coding work (e.g., a commit to the repository). The exercises are based on cognitive science research, and can be invoked by the user or automatically using a git hook when the user makes a commit. This also relies on the [`orient`](https://github.com/mcmullarkey/orient) skill which generates a repository orientation document by systematically exploring the codebase to provide a structural overview of an unfamiliar project.

### Learning Goal

The [`learning-goal`](https://github.com/DrCatHicks/learning-goal) skill, also based on work by Cat Hicks, is a structured goal-setting exercise based on Mental Contrasting with Implementation Intentions [Oettingen2010]. Students can set a concrete goal, refine it, identify obstacles, and build if-then plans to overcome them. The exercise supports three scopes (semester-wide, per-assignment, and team project goals) and produces a concise goal card that agents can reference throughout the semester.

### Submit

`Submit` handles the assignment submission, including collecting the mandatory AI-usage disclosures through five structured questions and running a packaging script to produce a submission archive (when applicable).

## Looking Ahead

The baseline agents will be used in CS3704 this semester, with new agents and skills being added over the course of the semester (e.g., [`requirements-analyst`](https://github.com/constellize/constellize-plugins-official/blob/main/plugins/constellize-design/agents/requirements-analysts.md), [`system-architect`](https://github.com/constellize/constellize-plugins-official/blob/main/plugins/constellize-design/agents/system-architects.md), and [UI/UX skills](https://github.com/nathanconklin/skills/tree/main/hci-design)) as well as students adding their own agents and skills. Long-term, the goal is to support both individual assignments and a full team-based software engineering workflow with specialized agents supporting each phase of the development life cycle. If you have ideas for improving [this approach](https://github.com/CS3704-VT/agent-template), feedback and suggestions are welcome!

---
**Footnotes and References**
>>>

[Wang2025] Tianjia Wang, Matthew Trimble, Chris Brown. _"DevCoach: Supporting Students Learning the Software Development Life Cycle with a Generative AI powered Multi-Agent System"_. Foundations of Software Engineering, Software Engineering Education Track (FSE-SEET 2025).

[Oettingen2010] Oettingen, G., & Gollwitzer, P. M. (2010). Strategies of setting and implementing goals: Mental contrasting and implementation intentions.