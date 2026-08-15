Questions 1–60 

Question 1 

Your agent has analyzed a complex service module—reading 23 source files, tracing request flows, and identifying error handling patterns. A developer wants to compare two testing strategies before committing to one: end-to-end tests with mocked external services vs. integration tests using real outputs. They need to independently develop both approaches to evaluate trade-offs. How should you manage the session? 

A. Start two fresh sessions, having each re-read the relevant source files before beginning. 

B. Resume the analysis session with fork, creating a separate branch for each testing strategy. ✅

C. Continue in the original session, developing end-to-end tests first, then snapshot tests sequentially. 

D. Export the analysis session’s key findings to a file, then create two new sessions that reference this file. 

Question 2 

 An engineer asks your agent to identify untested code paths in a legacy payment processing module spanning 45  files. After reviewing the agent’s responses, they realize the previously discussed code patterns indirectly influenced its recommendations and traced critical payment flows. What is the most effective approach to complete this investigation? 

A. Switch to using Grep to search for specific function names instead of reading files. 

B. Document all current findings in a summary report, clear context completely, then restart the exploration. 

C. Spawn subagents to investigate specific questions (e.g., final test files for payment processing), while a                                                                                             coordinating agent coordinates findings and preserves high-level understanding. ✅

D. Clear context with /clear, then selectively re-read only the most critical files discovered so far, relying on memory between context requests. 

Question 3 

An engineer sees an unfamiliar error message "SYNC_CONFLICT: entity version mismatch detected" in production logs, but none of the services in the codebase generates it. They ask the agent to help locate the source code. What exploration approach will most efficiently find the responsible code? 

A. Read the project’s README and service configuration files to understand the architecture, then systematically inspect each service directory. 

B. Use Glob to find files in directories commonly associated with error handling. Read each matching file. 

C. Use Grep to find all files that import the project’s error handling module, then read those files to look for similar error definitions. 

D. Use Grep to search for distinctive text from the error message (like "SYNC_CONFLICT" or "version mismatch"), then inspect the matching files to understand context. ✅

Question 4 

Your productivity agent connects to three MCP servers: an issue tracker (search issues, get issue details, create comments), a documentation wiki (search docs, read pages), and a database explorer (run queries, get schema, list databases). When engineers ask cross-system questions like “What database tables are affected by the authentication refactor in PROJ-1234?”, monitoring shows the agent makes 8–10 sequential tool calls. The primary issue is explanatory calls because it lacks visibility into what content each server contains and exhausts context space before completing complex investigations. 

Which architectural change best leverages MCP capabilities to address these issues? 

A. Add an orchestrator that routes questions to a single server based on keywords. 

B. Consolidate all three servers into a unified MCP server with cross-referencing capabilities. 

C. Add a separate investigation tool to each server that accepts a natural language question and returns relevant content summaries. 

D. Expose each server’s content catalog as MCP resources—issue summaries, documentation hierarchies, database schemas. ✅

Question 5 

An engineer who just joined the team asks the agent to help them understand the authentication and authorization architecture before making security improvements. The codebase has 800+ files across multiple services. What exploration strategy will most effectively build understanding given Claude’s built-in tools and context limits? 

A. Read any CLAUDE.md and README files first, then ask the engineer to specify which 10–15 files are most important. 

B. Launch parallel subagents to explore different services simultaneously, then synthesize their findings into an architectural overview. 

C. Read all files containing “auth”, “login”, “permission”, or “token” in their content or filename. 

D. Use Grep to find authentication entry points, read those files, then follow imports and function calls from the auth flow toward identity services. ✅

⸻ 

Question 6 

After adding an MCP server with specialized code refactoring tools (extract_function, rename_variable, inline_function) alongside basic text manipulation via Write and Bash commands for refactoring tasks, the MCP server is connected and healthy. Examining the configuration, you find each MCP tool has a minimal description like “extract_function: Extracts a function from code.” 

What’s the most effective way to improve adoption of the MCP refactoring tools? 

A. Enhance the MCP tool descriptions to explain when each tool is preferable to text manipulation and clarify expected inputs and outputs. ✅

B. Remove the Write tool from the agent’s configuration for refactoring sessions so it must use the MCP tools. 

C. Implement a request classifier that detects refactoring intent and automatically routes those requests to the MCP server instead of letting the agent choose. 

D. Accept this as expected behavior since simpler tools like sed are more predictable than specialized refactoring tools. 

⸻ 

Question 7 

You’ve configured your Claude agent with three MCP servers: one for Git operations, one for Jira ticket management, and one for documentation search. When a user asks the agent to “create a branch for JIRA-123 and add documentation links to the ticket,” how does the agent access tools across these servers? 

A. Tools from all configured MCP servers are discovered at connection time and available simultaneously to the agent. ✅

B. The agent automatically selects the most relevant server based on the request and adds only that server’s tools. 

C. You must specify which MCP server to use for each turn, and the agent can only access one server’s tools at a time. 

D. The agent queries each server sequentially to determine which handles each tool, routing calls based on tool name prefixes. 

⸻ 

Question 8 

An engineer asks the agent to find all files in the monorepo that import the @company/auth package to understand how authentication is used across services. Which built-in tool is most appropriate for this task? 

A. Grep, to search for the import statement pattern across file contents. ✅

B. Bash, to execute find . -type d -name "auth" and explore matching directories. 

C. Glob, to find files with “auth” in their filename or path. 

D. Read, starting with package.json files to trace dependency declarations. 

⸻ 

Question 9 

Engineers frequently ask the agent to cross-reference code changes with Jira tickets during reviews—checking ticket descriptions, acceptance criteria, and recent comments. This currently requires manually copy-pasting content into conversations. The team wants the agent to access this ticket data directly. What’s the most effective approach? 

A. Use the Bash tool with curl to call Jira’s REST API, including authentication headers and parsing JSON responses inline. 

B. Integrate an existing Jira MCP server that exposes tickets, comments, and metadata through discoverable MCP interfaces. ✅

C. Build a custom MCP server wrapping Jira’s API with tools designed specifically for this team’s code review workflow. 

D. Export Jira tickets to markdown files in the repository that the agent accesses using the Read tool. 

⸻ 

Question 10 

Your code review assistant needs to analyze pull requests and provide feedback on three aspects: code style compliance, potential security issues, and documentation completeness. Each aspect requires reading files, running analysis tools, and generating a report section. The typical process follows the same three-step workflow for every PR. 

Which task decomposition pattern is most appropriate for this workflow? 

A. Orchestrator-workers — have a central LLM analyze each PR to dynamically determine which checks are needed, then delegate to specialized worker LLMs for each identified subtask. 

B. Routing — classify each PR by type (feature, bugfix, refactor) first, then route to different review prompts optimized for that category. 

C. Single comprehensive prompt — include all instructions in one prompt and let the model handle all three aspects simultaneously. 

D. Prompt chaining — break the review into sequential steps where each aspect (style, security, documentation) is analyzed separately and combined in a final synthesis step. ✅


Question 11 

An engineer used Claude Code yesterday to investigate authentication flows in a legacy monolith, building up significant context over a 2-hour session. Today she wants to continue that specific investigation. She’s worked on three other codebases since then and knows the session isn’t the most recent “auth-deep-dive”. How should she resume? 

A. Use --resume auth-deep-dive to load that specific session by name. ✅

B. Use --session-id with the UUID from yesterday’s session transcript file. 

C. Start fresh and re-read the same files. 

D. Use --continue to pick up where the most recent conversation left off. 

Question 12 

Your agent needs to insert a new helper function into the middle of a 150-line utility module between two existing functions. The old_string parameter cannot find unique text to match—the file has repetitive docstrings, variable names, and structural patterns. What’s the best way to complete this insertion? 

A. Use Edit’s replace_all parameter to target a common pattern and embed the new function in that replacement text. 

B. Use Read to load the file, add the function at the appropriate location, then Write the updated file. ✅

C. Use Bash to append the function definition to the end of the file using redirect syntax. 

D. Use Edit with an extremely long old_string capturing 30+ lines of context to guarantee uniqueness. 

⸻ 

Question 13 

Your codebase exploration tool stores session IDs to allow engineers to continue investigations across work sessions. An engineer spent two hours analyzing a legacy authentication module, building context about its architecture and dependencies. They want to continue that session today, but version control shows 3 of the 12 files the agent previously read were modified overnight by teammates. What approach best balances efficiency and accuracy? 

A. Resume the session and immediately have the agent re-read all 12 previously analyzed files. 

B. Resume the session without informing the agent about the changed files. 

C. Start a fresh session to ensure the agent works with the current codebase state without stale assumptions. 

D. Resume the session and inform the agent which specific files changed for targeted re-analysis. ✅

⸻ 

Question 14 

An engineer asks your agent to add comprehensive tests to a legacy codebase with 200 files and minimal existing test coverage. The engineer hasn’t specified which modules to prioritize. How should the agent decompose this open-ended task? 

A. Create a fixed testing schedule upfront based on directory structure, allocating equal effort to each top-level directory regardless of actual complexity or business importance. 

B. Systematically read all 200 files to create a complete function inventory before writing any tests. 

C. Use Glob and Grep to map codebase structure, identify heavily-coupled modules, create a prioritized plan for high-impact areas, and adapt as dependencies are discovered. ✅

D. Start writing tests for the first module alphabetically, using test failures and imports to discover related files organically. 

⸻ 

Question 15 

An engineer submits two requests: 

* Request A: “Rename the getUserData function to fetchUserProfile everywhere it’s used.” 

* Request B: “Improve error handling throughout the data processing module—add try/catch blocks, meaningful error messages, and prevent failures from silently corrupting data.” 

For which request does specifying an explicit multi-phase workflow (such as analyze → propose → implement with verification) provide the most benefit? 

A. Request B, the error-handling task. ✅

B. Neither request benefits significantly. 

C. Both requests benefit equally. 

D. Request A, the function rename task. 

⸻ 

Question 16 

Your team has three requirements for Claude Code’s behavior in your project: 

1. Claude must never modify files in the db/migrations directory. 

2. Claude should prefer your custom logging module over console.log. 

3. All TypeScript files must be auto-formatted with Prettier after every edit. 

All three are currently written as instructions in your project’s CLAUDE.md. During a complex refactoring session, a teammate discovers that Claude edited a migration file, violating requirement #1. How should you restructure these requirements? 

A. Rewrite all three requirements in CLAUDE.md using stronger directive language and add examples. 

B. Configure hooks for all three: a pre-tool-use hook blocking edits to migration files, a hook providing logging guidance, and a post-tool-use hook running Prettier after TypeScript edits. ✅

C. Move all three requirements into .claude/rules as path-scoped rules. 

D. Add an Edit permission deny rule for migrations and keep the logging preference and formatting instruction in CLAUDE.md. 

⸻ 

Question 17 

Your team is configuring MCP servers in Claude Code. You want to add a shared venue lookup server that all team members should use, and you personally want to add an experimental music playlist server that only you are testing. Which configuration approach is correct? 

A. Add venue server to ~/.claude.json and playlist server to mcp.json. 

B. Add both servers to your local ~/.claude.json. 

C. Add venue server to mcp.json and playlist server to ~/.claude.json. ✅

D. Add both servers to the project-level mcp.json file. 

⸻ 

Question 18 

Your team has connected a custom MCP server that provides DevOps workflow templates. The server exposes several MCP prompts, such as deploy_checklist and incident_response, in addition to tools. How do these MCP prompts become accessible within Claude Code? 

A. They appear as slash commands (e.g., /mcp_servername_deploy_checklist) that you can invoke, with arguments passed after the command. ✅

B. They are automatically prepended to every conversation as additional system-level context. 

C. They are added to Claude Code’s tool registry alongside the server’s tools and invoked automatically. 

D. They are surfaced as @-mentionable resources alongside files. 

⸻ 

Question 19 

You need to add a date validation check ensuring event dates are in the future. This requires adding a conditional statement in one relatively small file. What is the most appropriate approach? 

A. Use direct execution to make the change. ✅

B. Enter plan mode to analyze how the validation might impact other parts of the reservation flow. 

C. Start with extended thinking mode enabled to ensure thorough reasoning about the validation logic. 

D. Enter plan mode first to create a detailed implementation strategy before making the change. 

⸻ 

Question 20 

You’re implementing a new payment processing module that must follow your project’s established patterns for database transactions, error handling, and audit logging. You’ve identified three existing modules that exemplify these patterns. These patterns are well-documented in your team wiki and don’t need additional project-level documentation. What is the most effective approach? 

A. Describe the patterns from the three modules in natural language in your prompt, explaining the transaction handling approach, error handling, and logging conventions Claude should follow. 

B. Use @ references to include the three modules directly in your prompt, giving Claude concrete code examples to follow. ✅

C. Ask Claude to explore your codebase to find and understand the transaction, error handling, and logging patterns before generating a new module. 

D. Add documentation of each pattern to your CLAUDE.md file establishing them as project conventions. 

Question 21 

You’ve asked Claude Code to build a PDF report generation feature. The initial implementation generates the basic report correctly but has several formatting issues: table columns are too narrow causing content truncation, dates display without proper formatting, and page breaks occur in awkward locations. What’s the most effective approach for iterating toward a working solution? 

A. Start fresh with a detailed prompt specifying all formatting requirements upfront. 

B. Show Claude an example of a correctly formatted report and ask it to match the output while fixing the specific issues. ✅

C. Provide all three issues in a single detailed message with exact specifications for each. 

D. Address the column width issue first with specific measurements, verify it works, then fix date formatting, then adjust page breaks—testing after each change. 

⸻ 

Question 22 

A critical bug is affecting production users. Error logs show exceptions in the OrderProcessing module within a code path that handles payment failures. You haven’t worked with this module before. What’s the most effective approach? 

A. Use direct execution to examine the stack trace, read the relevant code, and implement a fix once you identify the root cause. 

B. Use plan mode to analyze the error in context of the module’s design, enumerate potential root causes, and identify investigation steps before acting. ✅

C. Enter plan mode to explore the module’s architecture and dependencies before attempting any fixes. 

D. Start with direct execution to gather initial information, then switch to plan mode to design a comprehensive fix after identifying the problem area. 

⸻ 

Question 23 

You’ve documented API error handling conventions in a CLAUDE.md file at your project root. After several sessions, you notice Claude Code sometimes follows these conventions and sometimes generates generic error messages. The inconsistency appears random across different coding sessions. What’s the most efficient fix? 

A. Create path-specific rules in .claude/rules with YAML frontmatter scoping error handling instructions to API-related files. 

B. Run /memory to check which memory files are loaded and verify your CLAUDE.md is included. 

C. Search for conflicting instructions in .claude/CLAUDE.md or .claude/rules that might override your project conventions. ✅

D. Add more detailed code examples to your CLAUDE.md showing the exact error message pattern for different response types. 

⸻ 

Question 24 

Your team frequently migrates React components to Vue. You’ve written a step-by-step workflow for Claude Code to follow during these migrations. You want every developer on the team to invoke it by typing /migrate-component. The workflow should stay in sync as the team refines it. Where should you place the skill file? 

A. In .claude/skills/migrate-component/SKILL.md at the project root, committed to version control. ✅

B. In the project’s .claude/settings.json using a skillOverride entry. 

C. In ~/.claude/skills/migrate-component/SKILL.md on each developer’s machine. 

D. As a detailed instruction block in the project’s root CLAUDE.md file. 

⸻ 

Question 25 

You’re implementing a complex graph traversal algorithm with specific performance requirements and edge cases (disconnected nodes, weighted edges). You want to structure your workflow for efficient iterative refinement with Claude. What approach will most effectively enable progressive improvement across multiple iterations? 

A. Provide Claude with a detailed natural language specification of the algorithm, including all requirements and edge cases, then iteratively provide descriptive feedback on behavior that needs to change. 

B. Have Claude extensively research the algorithm and create a detailed implementation plan, then implement based on that plan. 

C. Write a test suite covering expected behaviors, edge cases, and performance requirements, run the tests, then iterate by sharing test failures with each refinement request.✅ 

D. Provide Claude with a reference implementation from documentation, then ask it to rewrite the code to match your codebase’s patterns. 

⸻ 

Question 26 

Your team’s CLAUDE.md includes a rule: “Use 4-space indentation and always run Prettier formatting.” Despite this, Claude Code generates inconsistent formatting. Sometimes 2-space indentation appears. You also use Prettier, but it doesn’t eliminate the issue completely. What’s the most effective way to ensure consistently formatted code? 

A. Extract the formatting rules into a dedicated skill that Claude loads automatically when generating code, with more detailed examples. 

B. Split the formatting rules into path-scoped .claude/rules files that load when Claude works on formatting-related files. 

C. Configure a PostToolUse hook with an Edit/Write matcher that automatically runs Prettier on each file Claude modifies.✅ 

D. Add a stronger prompt-based check that evaluates whether generated code follows formatting requirements before accepting it. 

⸻ 

Question 27 

A security audit requires updating your authentication library from v2 to v3. The migration guide documents breaking changes: authenticateUser now returns a Promise instead of accepting a callback, the User type has restructured fields, and three deprecated methods were removed. The library is imported in 45 files across several modules. What’s the most effective approach? 

A. Paste the migration guide’s breaking changes into your prompt and use direct execution to update all usage across the 45 files. 

B. Create a custom slash command encapsulating the migration transformations, then execute it against each file without your continued supervision. 

C. Update the dependency version, run the test suite, and use Claude Code to fix each failure as it appears.✅ 

D. Enter plan mode to explore library usage across modules, map affected code paths, then create a migration strategy before implementing changes. 

⸻ 

Question 28 

Your monorepo contains shared coding standards in docs/standards/: 

* security-rules.md (for API-facing services) 

* api-conventions.md (for services handling user data) 

* package-specific standards in individual packages 

Claude is applying all standards everywhere. What’s the most effective approach? 

A. Create .claude/rules/ files for each standard with YAML frontmatter specifying the packages/files where each standard applies. ✅

B. Use @imports in each package’s CLAUDE.md to reference only the standards relevant to that package. 

C. Create a shared-standards.md that combines all standards and have each package import it. 

D. Put all standards in the root CLAUDE.md and add override instructions in package-level files. 

⸻ 

Question 29 

You’ve asked Claude to write a data migration script, but the initial output doesn’t correctly handle records with null values. What’s the most effective way to iterate toward a working solution? 

A. Provide a test case with example input containing null values and the expected output, then ask Claude to fix it.✅ 

B. Describe the null value problem in detail and ask Claude to regenerate the entire script. 

C. Add “think harder about edge cases” to your prompt and request a complete rewrite. 

D. Manually edit the generated code to fix the null handling, then continue working with Claude on other parts. 

⸻ 

Question 30 

Your team wants Claude to follow a detailed code review checklist (8 items covering API changes, tests, documentation, etc.) whenever reviewing pull requests. Developers currently paste the checklist at the start of every review session. What’s the best approach? 

A. Configure plan mode as the default for code review sessions. 

B. Create a dedicated review subagent with the checklist embedded in its configuration. ✅

C. Add the checklist to the project’s CLAUDE.md file under a “Code Review” section. 

D. Create a /review slash command containing the checklist, invoked when starting review sessions. 

Question 31 

Your pipeline includes a release notes generation step that classifies and summarizes approximately 200 commits at the end of each release. Each commit is currently sent as a separate Messages API call using a Sonnet-tier Claude model. The release notes aren’t needed until the following morning (results have ~12 hours of acceptable latency). Your team needs to reduce per-token API cost for this step without changing prompts, model tier, or output quality. Which approach satisfies all of these constraints? 

A. Issue the 200 Messages API requests in parallel using concurrent connections. 

B. Switch the summarization calls from the Sonnet-tier model to a Haiku-tier model. 

C. Submit the 200 requests to the Message Batches API with unique custom IDs and retrieve results later. ✅

D. Concatenate all 200 commit messages into a single Messages API request. 

⸻ 

Question 32 

Your automated review CI jobs take 18 seconds to initialize before Claude begins analyzing code. Profiling shows the delay comes from loading hooks, MCP servers, plugins, skills, and multiple nested CLAUDE.md files throughout your monorepo. You want to cut startup latency while still enforcing your team’s coding standards, which are documented in your root-level CLAUDE.md file. What is the most effective approach? 

A. Keep the default initialization and add --exclude-dynamic-system-prompt-sections. 

B. Run with --bare mode and pass --append-system-prompt-file CLAUDE.md. ✅

C. Replace the default prompt entirely using --system-prompt-file. 

D. Run with --bare mode and specify all review criteria directly in the prompt. 

⸻ 

Question 33 

After deploying the automated review, you notice high precision but low recall—real bugs are slipping through undetected. Investigation reveals the review prompt instructs Claude to “only report high-confidence issues you are certain about” and err on the side of not commenting. However, a race condition that caused a production outage was visible in a reviewed PR but wasn’t reported. You need to substantially improve bug detection while keeping false positive rates manageable for your team. What is the most effective approach? 

A. Add detailed few-shot examples demonstrating bug categories Claude should flag. 

B. Remove conservative filtering instructions and report all potential issues. 

C. Expand the context window with related files and dependency information. 

D. Split the review into a findings stage and a separate thresholding stage.✅ 

⸻ 

Question 34 

The automated review consistently flags patterns your team uses intentionally—force-unwrapping optionals in test files, architectural conventions, and importing internally-maintained modules instead of third-party abstractions. Approximately 30% of all findings are project-specific false positives. Which approach prevents the model from generating these findings on every review? 

A. Build post-processing keyword filters. 

B. Add inline suppress comments and preprocess diffs. 

C. Document accepted patterns and conventions in the project’s CLAUDE.md.✅ 

D. Analyze only changed lines without surrounding context. 

⸻ 

Question 35 

You built an LLM-powered code review tool that analyzes pull requests and outputs structured findings. Each finding has: 

* line_number 

* issue_category 

* description 

Developers can dismiss findings. About 35% of findings get dismissed. You want to analyze these dismissals to understand what your system is getting wrong and improve the prompts accordingly. What change to your output structure would best support this analysis? 

A. Add a detected_pattern field recording the code construct that triggered each finding.✅ 

B. Add a model_confidence field (0.0–1.0). 

C. Expand the description field with more detailed explanations. 

D. Remove the issue_category field. 

⸻ 

Question 36 

After deploying automated code review, developers report that approximately 35% of flagged findings are false positives from project-specific style suggestions contradicting team conventions. Security warnings for patterns safe in your deployment context also create noise. You want to reduce false positives while maintaining the ability to catch genuinely novel issues and enable the model to generalize its judgment to patterns it hasn’t seen before. What approach best enables the model to generalize its judgment to novel code patterns it hasn’t seen before? 

A. Create a comprehensive written specification of all patterns that should not be flagged. 

B. Add instructions to “be conservative”. 

C. Implement post-processing keyword matching. 

D. Include few-shot examples showing acceptable and problematic patterns.✅ 

⸻ 

Question 37 

Your test generation produces unit tests for new code, but reviews show 55% are low-value trivial assertions that verify implementation details rather than behavior. Other tests duplicate existing coverage or ignore your team’s fixture conventions. How do you reduce the rate of low-value tests being generated in the first place? 

A. Implement a two-phase generation with a second Claude call scoring tests. 

B. Restrict test generation to selected directories. 

C. Document testing standards in CLAUDE.md, including examples of meaningful tests.✅ 

D. Add post-generation coverage analysis. 

⸻ 

Question 38 

Your pipeline runs: 

PROMPT="You are a code reviewer." 

PROMPT="$PROMPT Analyze the provided diff" 

PROMPT="$PROMPT for bugs, security issues," 

PROMPT="$PROMPT and style violations." 

claude -p \ 

  --dangerously-skip-permissions \ 

  --system-prompt "$PROMPT" \ 

  < diff.txt 

The reviews complete and return feedback, but Claude only comments on the piped diff itself—it never reads surrounding files in the repository to understand broader context. You want Claude to read related files while still applying your custom review instructions. 

A. Keep --system-prompt and add --allowedTools "Read,Grep". ✅

B. Stop piping the diff via stdin and embed it in the prompt. 

C. Remove --system-prompt and place instructions in CLAUDE.md. 

D. Replace --system-prompt with --append-system-prompt. 

⸻ 

Question 39 

Your CI pipeline performs security-focused code reviews on approximately 50 PRs daily. Reviews are non-blocking—developers merge after tests pass and address findings in follow-up commits. You are evaluating the Message Batches API for cost reduction. What factor most determines whether batch processing is appropriate for this use case? 

A. Whether review feedback arriving up to 24 hours after PR creation remains actionable.✅ 

B. Whether your result processing can handle reviews arriving in a different order than submitted. 

C. Whether you can structure each review as a single request without multi-turn refinement. 

D. Whether reducing per-review latency from 30–60 seconds to near-instant matters. 

Question 40 

Question: 

A developer uses Claude Code to refactor a function during their development session. Before committing, they ask the same Claude session to review the code for issues. Later, a separate automated CI review catches several bugs that the same-session review missed. What best explains this discrepancy? 

Options: 

A. The extended session length caused the context window to fill with conversation history, leaving less room for thorough analysis. 

B. Claude retains context about its prior reasoning in the session, making it less likely to question its own decisions.✅ 

C. The CI environment has access to the full codebase context while the local session only sees the current file. 

D. The CI review uses a more specific prompt tailored for catching bugs, while the developer’s request was too general. 

⸻ 

Question 41 

Question: 

The automated review pipeline generates an average of 18 findings per PR. Developer feedback reveals three categories of unwanted findings: formatting issues already enforced by CI, findings on auto-generated template code under src/generated/, and comments about intentional project conventions that resemble common anti-patterns. How should you reduce this noise while preserving detection of real issues? 

Options: 

A. Create a REVIEW.md at the repository root with skip rules for CI-enforced checks and generated files, and require findings to cite specific evidence of incorrect behavior. 

B. Add a prompt parameter to the GitHub Action configuration instructing it to suppress findings matching common anti-pattern patterns and apply stricter evidence requirements. 

C. Configure separate GitHub Action workflow files for each code area and a general workflow for everything else. 

D. Add detailed explanations to the project’s CLAUDE.md describing conventions and patterns. 

⸻ 

Question 42 

Question: 

Your automated reviewer uses a single prompt covering security issues, API design, and business logic correctness. It achieves high recall for API design findings but poor recall for business logic edge cases. When you split the prompt, business logic recall improves significantly while API design recall drops. How should you update the architecture? 

Options: 

A. Provide the full repository as context instead of just changed files and surrounding code. 

B. Replace the few-shot examples with a detailed checklist for specific logic edge cases. 

C. Split the review into separate focused prompts (e.g., security, API design, business logic) and consolidate findings before posting. 

D. Upgrade to a more capable model. 

⸻ 

Question 43 

Question: 

During initial testing of the automated review pipeline, you notice that reviews on large PRs (50+ changed files) sometimes take more than 10 minutes and cost $8–12 per run due to extensive agentic loops. Your team wants execution to stop once it reaches a fixed iteration count and a fixed dollar amount. Which configuration change directly enforces both per-invocation caps? 

Options: 

A. Add --max-turns 10 --max-budget-usd 2.00 to the Claude invocation. 

B. Set --permission-mode dontAsk to auto-deny tool permission requests not in the allowed set. 

C. Set timeout-minutes: 5 on the GitHub Actions job step. 

D. Switch the --model flag to a smaller, cheaper model. 

⸻ 

Question 44 

Question: 

Your pipeline reviews approximately 200 database migration scripts daily using the Message Batches API. Each batch review includes a large shared system prompt containing migration review guidelines and schema documentation. Monitoring shows cache hit rates only in requests concentrated later in the batch window. Which change will best address the root cause of the latency? 

Options: 

A. Split the 200 requests into 10 sequential batches of 20, submitting each only after the previous completes to improve cache reuse. 

B. Move the cache_control breakpoints from the system prompt to the individual migration script content. 

C. Add pre-warming requests with max_tokens: 0 at the beginning of each batch. 

D. Use the extended 1-hour cache TTL instead of the default 5-minute TTL. 

⸻ 

Question 45 

Question: 

Your code review prompts include both implementation changes and the corresponding test file. The model correctly flags functions that have no tests at all but fails to identify missing conditional branches within tested functions. What’s the most effective way to improve detection of branch-level coverage gaps without overcomplicating the pipeline? 

Options: 

A. Include few-shot examples showing code with an uncovered branch paired with review comments identifying the specific missing test. 

B. Implement a multi-pass pipeline where separate LLM calls first extract all conditional branches, then a second pass checks coverage. 

C. Restructure the prompt to interleave implementation and tests, presenting each function followed immediately by its test cases. 

D. Add explicit instructions directing the model to enumerate each conditional branch and exception path, then verify corresponding test assertions. 

⸻ 

Question 46 

Question: 

Production reviews reveal inconsistent handling of uncertainty in final reports. Sometimes conflicting estimates are synthesized into a single confident statement; other times reports over-hedge. How can this be addressed systematically? 

Options: 

A. Instruct the synthesis agent to structure reports with explicit sections distinguishing well-established findings from uncertain findings, including source characterization and methodological context. 

B. Add a verification subagent that cross-references findings across sources and synthesizes only independent sources. 

C. Implement a confidence calibration layer that normalizes uncertainty expressions and averages findings by calibrated confidence. 

D. Configure subagents not to report findings beneath a confidence threshold. 

⸻ 

Question 47 

Question: 

In production, simple fact-checking queries (e.g., “What year was the Paris Climate Agreement signed?”) still trigger all research subagents sequentially, consuming 40+ seconds and many tokens. Query types evolve frequently as users discover new applications. What is the most effective optimization? 

Options: 

A. Implement pattern-based routing that categorizes queries into predefined subagent combinations. 

B. Have the coordinator analyze each query and dynamically decide which subagents to invoke based on its assessment. 

C. Create a fast-path for factual questions that bypasses subagents entirely. 

D. Train a query-complexity classifier on historical data to predict optimal subagent combinations. 

⸻ 

Question 48 

Question: 

The coordinator agent has AgentDefinitions configured for all four specialized subagents, each with appropriate restrictions and prompts. During testing, the coordinator correctly reasons about when to delegate (“I need a source-finding agent for this topic”), but no subagent execution ever occurs. Logs show no errors. What is the most likely cause? 

Options: 

A. The coordinator’s max_tokens setting is too low, causing task tool invocations to be truncated before execution. 

B. The AgentDefinitions are configured correctly, but the coordinator’s system prompt does not explicitly list the available subagents or explain that they can be invoked. 

C. Subagent context isolation prevents task descriptions from being forwarded through ClaudeAgentOptions. 

D. The coordinator’s allowedTools configuration doesn’t include Task, so it cannot invoke the defined subagents. 

Question 49 

Question: 

The web search agent has gathered several relevant sources for a research topic. The document analysis agent later analyzes those sources. How does information typically flow between these two specialized subagents? 

Options: 

A. Both agents access a shared memory store where the web search agent writes findings and the document analysis agent reads them. 

B. The web search agent directly invokes the document analysis agent, passing the discovered sources as parameters. 

C. The coordinator agent receives the web search agent’s output and includes relevant findings in the prompt when invoking the document analysis agent. 

D. The agents communicate through an event-driven message queue, with the document analysis agent subscribing to source-discovery events. 

⸻ 

Question 50 

Question: 

Your multi-agent research pipeline crashed after processing 12 of 78 documents. The web search agent had identified relevant sources, the document analyzer had partially completed extraction, and the synthesis agent had begun pattern identification. You need to resume processing without repeating work or losing fidelity of prior findings. What state-management approach best balances information fidelity with efficient recovery? 

Options: 

A. Have each agent maintain its own persistent state file and reload it independently at the start of each session. 

B. Have each agent persist a structured export to a known location. On resume, the coordinator loads the intermediate outputs and reconstructs prompts. 

C. Index all agent outputs in a shared vector store. When resuming, each agent queries the store using semantic search to recover context. 

D. Persist the coordinator’s conversation log containing all task delegations and responses. 

⸻ 

Question 51 

Question: 

In production, final reports frequently contain claims without proper source attribution. Investigation shows the web search and document analysis agents correctly attach citations to their outputs, but the synthesis agent loses track of which sources support which conclusions. What is the most effective architectural change? 

Options: 

A. Require all subagents to output structured claim–source mappings, preserving attribution across multiple sources. 

B. Have the coordinator inject source identifier prefixes into text before each handoff, then parse them back out during report generation. 

C. Maintain complete transcripts of all subagent interactions and add a citation-resolution agent before report generation. 

D. Add a verification step where the report generator uses semantic similarity matching to determine which documents support each conclusion. 

⸻ 

Question 52 

Question: 

When researching “renewable energy adoption,” the web search agent returns recent statistics (2024: 35% adoption), while the document analysis agent extracts data from internal reports (2021: 18% adoption). The synthesis agent incorrectly flags these as contradictory sources rather than recognizing that the data shows growth over time. What change would best enable correct interpretation? 

Options: 

A. Instruct the synthesis agent to always treat the most recent data as authoritative and place older findings in a separate historical appendix. 

B. Configure the web search agent to only return results from the past 6 months. 

C. Require subagents to include publication or data-collection dates in their structured outputs. 

D. Add a conflict-resolution agent that automatically discards older data when newer data exists for the same metric. 

⸻ 

Question 53 

Question: 

The synthesis agent receives summarized findings from the web search and document analysis agents. During testing, you discover the generated reports make factual claims without properly connecting statements to their original sources because metadata was lost during the summarization step. What is the most effective way to preserve source attribution in the final reports? 

Options: 

A. Skip summarization and pass full raw outputs from web search and document analysis directly to the report generator. 

B. Have each agent output structured data separating content summaries from source metadata and provenance. 

C. Have the report generator query the web search agent for source URLs whenever citations are needed. 

D. Instruct the synthesis agent to embed source references inline within summary text regardless of format. 

⸻ 

Question 54 

Question: 

The synthesis agent completes its initial pass but flags that three key research questions remain unanswered because analysis agents didn’t find relevant information on those subtopics. The coordinator currently forwards the incomplete synthesis report. What change would most effectively improve research completeness? 

Options: 

A. Have the coordinator evaluate synthesis output for gaps, then re-delegate to web search and document analysis before running synthesis again. 

B. Increase the initial breadth of queries sent to web search and document analysis to reduce the probability of missed topics. 

C. Have the report-generation agent note which research questions couldn’t be answered so readers know about the limitations. 

D. Give the synthesis agent direct access to web search tools so it can autonomously gather missing information. 

⸻ 

Question 55 

Question: 

A user is expanding the research system beyond its single web-search agent by adding a specialized financial-analysis agent that returns structured JSON with revenue, margins, and growth rates, and a news-monitoring agent that returns event timelines. The synthesis agent currently converts everything into bullet points, causing financial comparisons to lose tabular clarity and news summaries to lose chronological structure. What change would best improve briefing quality? 

Options: 

A. Add a format-conversion layer between subagents and synthesis that transforms all outputs to a common markdown structure. 

B. Standardize all subagent outputs to JSON with fields for title, summary, score, and citation. 

C. Update the synthesis agent to render each content type appropriately rather than forcing all outputs into a single summary format. 

D. Standardize all subagent outputs to concise summaries with inline citations. 

⸻ 

Question 56 

Question: 

After the web search and document analysis subagents complete their tasks, the coordinator needs to spawn the synthesis subagent with the information it needs. What is the correct approach for providing the synthesis subagent with findings? 

Options: 

A. Spawn the subagent with only a brief task description, relying on automatic context inheritance from the coordinator. 

B. Provide the subagent with tool definitions that allow it to request outputs from other subagents via callbacks. 

C. Pass reference identifiers and configure the subagent with read access to a shared memory store where other subagents wrote results. 

D. Include the complete findings from both subagents directly in the synthesis subagent prompt. 

⸻ 

Question 57 

Question: 

Production monitoring shows the research phase takes longer than expected. Analysis reveals the coordinator invokes the web search subagent, waits for its response, then invokes the document analysis subagent. These tasks are independent. How should the system be modified to run them concurrently? 

Options: 

A. Create an async orchestration layer, outside the agent, that spawns parallel threads for independent subagents and waits for both results. 

B. Structure the coordinator to emit both Task tool calls for web search and document analysis in a single conversation turn. 

C. Switch both subagents to use a Haiku-tier model instead of Sonnet to reduce individual request latency. 

D. Add detailed instructions to the coordinator’s system prompt explaining that independent subagents should be started simultaneously. 

⸻ 

Question 58 

Question: 

You’ve configured the system so that all four subagents have access to the complete set of 18 tools. During testing, tool-selection behavior degrades—the synthesis agent attempts web searches, and the report generator tries to analyze documents. What is the most likely cause? 

Options: 

A. Choosing from 18 tools instead of 4–5 relevant ones increases decision complexity beyond useful specialization benefits. 

B. The tool definitions consume too much context-window space, leaving insufficient room for task execution. 

C. The coordinator cannot track which capabilities each subagent has, leading to misrouted tasks. 

D. The agents’ role descriptions in their system prompts conflict with having access to the complete toolset 

Question 59 

Question: 

When analyzing complex legal cases that cite multiple precedents, the document analysis subagent processes each precedent sequentially and takes over 3 minutes to analyze completely. What is the most effective way to reduce latency while preserving result quality and making the system easier to monitor and debug? 

Options: 

A. Create a recursive agent hierarchy where analysis agents subdivide work among child agents without coordinator involvement. 

B. Implement a message queue where precedent analysis tasks are processed asynchronously by a pool of worker agents. 

C. Enable the document analysis subagent to spawn its own specialized subagents dynamically for each precedent. 

D. Have the coordinator spawn parallel document analysis subagents, each focused on a subset of precedents. 

Question 60 

Question: 

After the web search agent finds 25 sources (120K tokens of raw content), the document analysis agent extracts key insights (18K tokens), and the synthesis agent produces a coherent narrative draft (3K tokens), the coordinator must pass context to the report-generation agent while preserving proper source citations. What context-passing strategy provides the best balance of completeness and efficiency? 

Options: 

A. Pass only the synthesis draft and have a separate post-processing pipeline match claims to sources and insert citations. 

B. Pass the synthesis draft along with a structured source index that maps key claims to their source URLs and relevant excerpts. 

C. Pass a condensed summary of all prior stages that preserves the main findings and attributes them to source URLs. 

D. Pass the full accumulated context from all prior agents. 
