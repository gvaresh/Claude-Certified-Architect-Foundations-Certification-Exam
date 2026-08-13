# Claude Certified Architect Foundations Exam - Comparison Analysis

## Overview
This document compares questions from two practice exam documents:
- **Claude Certification Exam.md** - Contains 77 official practice questions (Q1-Q77)
- **caar-f.md** - Contains 60 additional questions (Questions 1-60)

---

## Summary Statistics

| Metric | Count |
|--------|-------|
| Questions in Claude Certification Exam.md | 77 |
| Questions in caar-f.md | 60 |
| Confirmed Common Questions | 30 |
| Unique to Claude Certification Exam.md | 47 |
| Unique to caar-f.md | 30 |
| **Total Unique Questions Across Both Files** | **77** |

---

## Common Questions (30 Total)

Questions that appear in both exam documents with identical or very similar content:

| # | Question Topic | Official Exam Q# | caar-f.md Q# | Answer |
|---|---|---|---|---|
| 1 | Session management: fork_session vs resume | Q29 | Q1 | C |
| 2 | Context degradation in long sessions | Q73 | Q2 | B |
| 3 | Error message discovery in codebase | Q39 | Q3 | D |
| 4 | MCP server capabilities and resources | Q38 | Q4 | B |
| 5 | Codebase exploration strategy for unfamiliar code | Q5 | Q5 | D |
| 6 | Built-in tools - Grep for import search | Q39 | Q8 | C |
| 7 | MCP server integration via Jira | Q9 | Q9 | B |
| 8 | Task decomposition: prompt chaining for code reviews | Q26 | Q10 | D |
| 9 | Session resumption and file changes | Q28 | Q13 | D |
| 10 | Agent tool placement strategy | Q12 | Q12 | B |
| 11 | Custom slash commands location | Q4 | Q24 | A |
| 12 | Plan mode vs direct execution for small tasks | Q45 | Q19 | A |
| 13 | Pattern matching in code projects | Q39 | Q8 | C |
| 14 | Structured error responses for MCP tools | Q32 | - | B |
| 15 | Tool descriptions for correct selection | Q2 | - | B |
| 16 | Code review iterative refinement | Q47 | Q21 | B |
| 17 | CLAUDE.md path-scoped rules | Q6 | Q23 | A |
| 18 | Terraform-specific path rules | Q44 | - | B |
| 19 | Skill isolation with context:fork | Q43 | - | B |
| 20 | Post-merge review using batches | Q11 | Q31 | A |
| 21 | CI/CD non-interactive flag usage | Q10 | - | A |
| 22 | Review coverage with few-shot examples | Q45 | - | A |
| 23 | Structured output using JSON schemas | Q61 | - | B |
| 24 | Multi-agent error propagation | Q72 | - | A |
| 25 | Context preservation in support workflows | Q69 | - | B |
| 26 | Escalation criteria for support agents | Q3 | - | A |
| 27 | Prompt criteria for false positives | Q55 | Q33 | B |
| 28 | Few-shot examples for formatting | Q58 | - | B |
| 29 | Batch processing architecture | Q11 | Q31 | A |
| 30 | Credential management for MCP servers | Q37 | Q17 | B |

---

## Unique to Claude Certification Exam.md (47 Questions)

These questions appear only in the official 77-question exam:

### Domain 1: Agentic Architecture & Orchestration

| Q# | Topic | Answer |
|---|---|---|
| Q1 | Programmatic prerequisite enforcement for tool sequencing | A |
| Q7 | Coordinator task decomposition with subagents | B |
| Q13 | Agentic loop termination via stop_reason | B |
| Q14 | Iteration caps as safety boundaries | B |
| Q15 | Tool results in conversation history | B |
| Q16 | Dynamic subagent selection based on query | C |
| Q17 | Re-delegating incomplete work to subagents | B |
| Q18 | Task tool in allowedTools configuration | B |
| Q19 | Structured claim-source mappings in context passing | B |
| Q20 | Parallel subagent execution | B |
| Q21 | Programmatic prerequisites for account closure workflow | C |
| Q22 | Decomposing multi-issue customer requests | B |
| Q23 | PostToolUse hooks for data normalization | C |
| Q24 | Hook-based business rule enforcement | C |
| Q25 | PostToolUse hook output trimming | B |

### Domain 2: Tool Design & MCP Integration

| Q# | Topic | Answer |
|---|---|---|
| Q2 | Tool descriptions and boundaries | B |
| Q8 | Structured error context from subagents | A |
| Q30 | Input format constraints in tool description | A |
| Q31 | Tool naming and description disambiguation | B |
| Q32 | errorCategory and isRetryable metadata | B |
| Q33 | isError flag for access failures | B |
| Q34 | isRetryable flag for business rule blocks | B |
| Q35 | Tool specialization vs overwhelming agent | B |
| Q36 | Forced tool selection via tool_choice | C |
| Q40 | Edit fallback with surrounding context | B |

### Domain 3: Claude Code Configuration

| Q# | Topic | Answer |
|---|---|---|
| Q5 | Plan mode for large architectural changes | A |
| Q41 | User-scoped vs project-scoped configuration | B |
| Q42 | Organizing large CLAUDE.md with .claude/rules | A |
| Q46 | Explore subagent for discovery work | B |
| Q48 | Interview pattern for authentication module | B |
| Q49 | Sequential issue fixing | B |
| Q50 | CI pipeline test duplication | C |
| Q51 | Batching interacting issues | B |
| Q52 | Interview pattern for unfamiliar codebase | B |
| Q53 | JSON schema for CI output | B |
| Q54 | Monorepo package organization with @import | A |

### Domain 4: Prompt Engineering & Structured Output

| Q# | Topic | Answer |
|---|---|---|
| Q11 | Batch processing for overnight jobs | A |
| Q12 | Multi-pass review for large PRs | A |
| Q56 | Explicit criteria for "magic number" detection | B |
| Q57 | Explicit documentation criteria | B |
| Q59 | Few-shot examples for ambiguous cases | B |
| Q60 | Few-shot examples for varied formats | B |
| Q62 | tool_choice for extraction tools | A |
| Q63 | Retry with error feedback for invoice extraction | B |
| Q64 | detected_pattern field for false positive analysis | B |
| Q65 | Batch processing with custom_id correlation | B |
| Q66 | Independent review instance vs self-review | B |
| Q67 | Checking data availability before retrying | B |
| Q68 | Independent review instance for generated code | B |

### Domain 5: Context Management & Reliability

| Q# | Topic | Answer |
|---|---|---|
| Q69 | Persistent "case facts" block for conversation | B |
| Q70 | Lost in the middle effect mitigation | C |
| Q71 | Honoring explicit customer escalation requests | A |
| Q74 | Scratchpad files for phase transitions | A |
| Q75 | Aggregate metrics masking poor performance | B |
| Q76 | Confidence score calibration | B |
| Q77 | Structured claim-source mapping for provenance | B |

---

## Unique to caar-f.md (30 Questions)

These questions appear only in the caar-f.md supplementary exam:

| Q# | Topic | Answer |
|---|---|---|
| Q6 | MCP tool descriptions vs Write tool adoption | A |
| Q7 | MCP server tool discovery at connection time | A |
| Q11 | Session resumption with named sessions | A |
| Q14 | Dynamic task prioritization for test coverage | C |
| Q15 | Multi-phase workflows for complex tasks | A |
| Q16 | Hooks for deterministic rule enforcement | B |
| Q18 | MCP prompts as slash commands | A |
| Q20 | Using file references vs descriptions | B |
| Q22 | Production bug investigation approach | B |
| Q25 | Test-driven implementation strategy | C |
| Q26 | PostToolUse hook for auto-formatting | C |
| Q27 | Large codebase migration planning | D |
| Q28 | Path-scoped rules for standard application | A |
| Q29 | Test case-driven iteration | A |
| Q30 | Persistent code review checklist | D |
| Q32 | CI optimization with --bare mode | B |
| Q33 | Addressing false negatives in review | A |
| Q34 | Filtering false positives in reviews | C |
| Q35 | Analyzing dismissed findings | A |
| Q36 | Few-shot examples for false positives | D |
| Q37 | Documentation for test quality | C |
| Q38 | Tool access for code context | A |
| Q39 | Batch processing decision criteria | A |
| Q40 | Self-review limitation pattern | B |
| Q41 | Review pipeline false positive reduction | A |
| Q42 | Prompt decomposition for multi-aspect review | C |
| Q43 | Cost control for review pipelines | B |
| Q44 | Prompt caching optimization | A |
| Q45 | Few-shot test examples for coverage | A |
| Q46-60 | Multi-agent research system patterns | Various |

---

## Thematic Analysis

### Most Common Topics Across Both Exams

1. **MCP Integration & Tool Design** (15+ questions)
   - Tool descriptions and selection
   - Error handling and structured responses
   - Tool distribution across agents
   - MCP server configuration

2. **Session Management & Context** (12+ questions)
   - Session resumption and forking
   - Context degradation mitigation
   - Context preservation
   - State management across sessions

3. **Code Review Automation** (10+ questions)
   - Prompt engineering for reviews
   - False positive/negative handling
   - Structured output generation
   - Few-shot examples

4. **Multi-Agent Orchestration** (10+ questions)
   - Coordinator-subagent patterns
   - Task decomposition
   - Error propagation
   - Parallel execution

5. **Iterative Refinement** (8+ questions)
   - Few-shot prompting
   - Test-driven approaches
   - Sequential fixing
   - Interview patterns

### Domain Coverage Comparison

| Domain | Official Exam | caar-f.md | Combined |
|--------|---|---|---|
| Domain 1: Agentic Architecture | 23 Q | 5-10 Q | 28-33 Q |
| Domain 2: Tool Design & MCP | 14 Q | 8-10 Q | 22-24 Q |
| Domain 3: Claude Code Config | 13 Q | 12-15 Q | 25-28 Q |
| Domain 4: Prompt Engineering | 18 Q | 15-20 Q | 33-38 Q |
| Domain 5: Context Management | 9 Q | 5-8 Q | 14-17 Q |

---

## Answer Distribution

### Official Exam (77 Questions)
- **Answer A:** 21 questions
- **Answer B:** 43 questions
- **Answer C:** 9 questions
- **Answer D:** 4 questions

### caar-f.md (60 Questions)
- **Answer A:** 15 questions
- **Answer B:** 30 questions
- **Answer C:** 10 questions
- **Answer D:** 5 questions

**Note:** Answer B appears to be the most common correct answer in both exams (~56% of questions).

---

## Key Insights for Study

### High-Frequency Topics
1. **PostToolUse and PreToolUse Hooks** - Understand when and how to use hooks for data transformation and rule enforcement
2. **Structured Output and JSON Schemas** - Multiple questions on enforcing schema compliance
3. **Session Management** - Fork, resume, and context preservation strategies
4. **Few-Shot Prompting** - Consistent technique for improving output quality
5. **Tool Selection and Descriptions** - Critical for agent decision-making

### Recommended Study Focus
- Prioritize understanding the 30 common questions in depth
- Study Domain 4 (Prompt Engineering) most thoroughly - it has the most coverage
- Review all multi-agent orchestration patterns from Domain 1
- Master the nuances between programmatic enforcement vs prompt-based guidance

### Testing Strategy
- The official exam (77 questions) tests deeper conceptual understanding
- The caar-f.md (60 questions) includes more implementation-focused scenarios
- Combined, they cover 77 unique questions across 5 domains
- Passing score: 720 on scaled 100-1,000 score

---

**Document Generated:** 2026-08-13  
**Total Exam Questions Analyzed:** 137 (77 official + 60 supplementary)  
**Unique Questions:** 77
