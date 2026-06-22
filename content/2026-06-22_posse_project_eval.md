---
tags: education, teaching, open-source, development
authors: dcbrown
---

# POSSE Project Evaluator

A few days ago, I [reflected on my experience](2026-06-10_posse.html) at the Professors' Open Source Software Experience (POSSE) workshop, a three-day event focused on integrating HFOSS into classroom settings. One of the most practical takeaways was focusing on **project health checks** to evaluate whether an open-source repository is a good fit for students. The workshop introduced a [9-criterion rubric](https://teachingopensource.org/Project_Evaluation_Rubric_(Activity)) (scored 0-2, 18 points max) that instructors can use as a quick first pass.

The workshop provided a guided example, interactive activity to review an existing project, and unconference time for participants to devote to planning for OSS integration into their courses. I found the rubric very helpful for systematically assessing whether candidate projects are active, well-maintained, etc., but I quickly found that applying it manually to repositories was time-consuming and tedious. In particular, for each project I had to:

- Visit each repo's GitHub page;
- Check the license file, veryfing whether it existing and was an [OSI-approved license](https://opensource.org/licenses);
- Scan the commit graph for recent activity;
- Count the number of contributors;
- Look for CONTRIBUTING.md and CODE_OF_CONDUCT.md files;
- Check stars, forks, releases, etc.;
- Enter these results with evidence into the rubric table for documenting;
- ...and repeat for every candidate project

To help with this, I built a tool to automate it.

---
## Automating the Rubric

My original goal was to implement this manually, but I quickly realized that I did not have the time available to commit to writing the code myself. Thus, leveraging the help of generative AI (opencode 1.17.8 with opencode/big-pickle), [`posse_project_eval.py`](https://github.com/chbrown13/posse_project_eval) was implemented. The POSSE Project Evaluator is a Python CLI that scores any public GitHub repository against the full POSSE rubric using the [PyGitHub](https://github.com/PyGithub/PyGithub) library to inspect a repo across all nine criteria:

| Criterion | What it checks |
|-----------|----------------|
| Licensing | OSI-approved open source license? |
| Technology | Top languages match your preferred stack? |
| Level of Activity | Commits across the last four quarters? |
| Number of Contributors | Size of the contributor base |
| Project Size | Estimated lines of code |
| Issue Tracker | Open issues and recent activity? |
| New Contributor | CONTRIBUTING file and community profile? |
| Community Norms | Code of Conduct present? |
| User Base | Stars, forks, and releases? |

The benefits of this approach are:

* It can score multiple candidate projects in seconds, reducing effort to pre-screen projects;
* Criteria are configurable based on instructor/course preferences (e.g., technology, project size, etc...);
* The results are repeatable for measuring and comparing OSS project health;
* In cases where students will need to select their own projects, they can also run this tool to compare OSS projects;
* Results along with rationales are presented in a readable table (see sample below), which can also be saved to an output file.

```
================================================================================
FOSS Project Name: OED
Description: Open Energy Dashboard
Repository: https://github.com/OpenEnergyDashboard/OED
================================================================================
Licensing — Level 2/2
  Data:   mpl-2.0
  Source: https://github.com/OpenEnergyDashboard/OED/blob/main/LICENSE
  Reason: OSI-approved open source license
--------------------------------------------------------------------------------
...
Total Score: 16/18
```

## Agentic Evaluations 🤖

Given the rise in generative AI and agents for automating tasks, the repository also includes AI-optimized files. This includes a [skill definition](https://github.com/chbrown13/posse_project_eval/blob/main/.ai/skills/posse-eval.md) with the full rubric and an [agent workflow](https://github.com/chbrown13/posse_project_eval/blob/main/.ai/agents/project-evaluator.agent.md) for conversational evaluation. 

The agent should ideally be able to run for any agentic coding assistant (i.e., Claude Code, opencode, etc.), invoked using `@project-evaluator` with a given repository/list of repositories to evaluate. While these results may not be as repeatable, they are derived conversationally and could incorporate additional contexts. The agent by default bases responses on the results of the Python script, but can also use it's own web fetching capabilities if preferred.

## Try It Out!

More details on installing, configuring, and running the POSSE Project Evaluator are available in the project [README](https://github.com/chbrown13/posse_project_eval/blob/main/README.md). The tool is MIT-licensed and available at [github.com/chbrown13/posse_project_eval](https://github.com/chbrown13/posse_project_eval). If you're an instructor considering integrating HFOSS into your course or a developer interested in assessing projects to contribute to in your own time, feel free to try it out! Pull requests, issues, and suggestions are also welcome!
