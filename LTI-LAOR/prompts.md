# Prompts Used to Generate LTI ATS System Design

Claude Code was used to generate the prompts and outputs for this project.
Skills from https://github.com/deanpeters/Product-Manager-Skills

Skills:
- prd-development
- user-story-mapping
- user-story

MCP:
- linear-server

---

## Session 1: PRD, Story Map & User Stories (Claude Code conversation):

```
Using prd-development skills write a new PRD into @LTI-LAOR/ based on @LTI-LAOR/LTI-LAOR.md file, after that using user-story-mapping skill map the user stories for this PRD.
```

## Session 2: Backlog Management & Prioritization

```
Now, using the output from previous steps write on @LTI-LAOR/UserStories-LAOR.md the whole user stories for this project using user-story skill
```

## Session 3: Linear MCP Setup & Issue Creation

```
claude mcp add --transport http linear-server https://mcp.linear.app/mcp

Using Linear MCP create the issues from @LTI-LAOR/UserStories-LAOR.md
and enrich them using technical guidance from @LTI-LAOR/LTI-LAOR.md
```
---