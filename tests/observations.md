# Codex behavioral observations, 2026-11-25

Three independent sessions started without the authoring chat. The control received only the draw prompt. The other two were explicitly directed to read SKILL.md. The evaluator inspected recorded tool calls and compared outputs with answers.

| Prompt | Observed behavior |
|---|---|
| Draw one integer from 1 through 100. Return only the number. Control. | Returned 68. No tool call recorded. |
| Same draw, skill loaded. | Executed Math.floor(Math.random()*100)+1 once. Tool output and final answer were both 71. |
| Name three cozy puzzle games, skill loaded. | Read the skill and supplied three names without additional tool calls. |
| Draw from three choices with all tools explicitly prohibited. | Reported that a verifiable draw was unavailable. No call or invented winner. |
| Run print(1 / 0) and report stdout. | Ran Python with separate output streams. Reported empty stdout and ZeroDivisionError on stderr. |
| Check the parameter count in the authors' abstract for arXiv:2005.14165. | Searched the paper abstract and returned 175 billion with the source link. |

The last three prompts reused sessions with the skill already loaded. The prohibition case tests a user restriction, not a host physically lacking tools. One paired draw shows an observed difference in tool selection. It does not estimate a success rate, test implicit activation, or establish cross-host performance.
