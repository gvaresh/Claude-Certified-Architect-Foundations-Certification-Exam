
Here is the consolidated set of Questions 1 through 60 with options, formatted directly from the original document source with the correct answer indicated in bold:


Question 1
Your agent has analyzed a complex service module—reading 23 source files, tracing request flows, and identifying error handling patterns. A developer wants to compare two testing strategies before committing to one: end-to-end tests with mocked external services vs. integration tests using real outputs. They need to independently develop both approaches to evaluate trade-offs. How should you manage the session?

* A. Start two fresh sessions, having each re-read the relevant source files before beginning. 
* B. Resume the analysis session with fork, creating a separate branch for each testing strategy. 
* C. Continue in the original session, developing end-to-end tests first, then snapshot tests sequentially. 
* D. Export the analysis session’s key findings to a file, then create two new sessions that reference this file. 

Question 2
An engineer asks your agent to identify untested code paths in a legacy payment processing module spanning 45 files. After reviewing the agent’s responses, they realize the previously discussed code patterns indirectly influenced its recommendations and traced critical payment flows. What is the most effective approach to complete this investigation?

* A. Switch to using Grep to search for specific function names instead of reading files. 
* B. Document all current findings in a summary report, clear context completely, then restart the exploration. 
* C. Spawn subagents to investigate specific questions (e.g., final test files for payment processing), while a coordinating agent coordinates findings and preserves high-level understanding. 
* D. Clear context with /clear, then selectively re-read only the most critical files discovered so far, relying on memory between context requests. 

Question 3
An engineer sees an unfamiliar error message "SYNC_CONFLICT: entity version mismatch detected" in production logs, but none of the services in the codebase generates it. They ask the agent to help locate the source code. What exploration approach will most efficiently find the responsible code?

* A. Read the project’s README and service configuration files to understand the architecture, then systematically inspect each service directory. 
* B. Use Glob to find files in directories commonly associated with error handling. Read each matching file. 
* C. Use Grep to find all files that import the project’s error handling module, then read those files to look for similar error definitions. 
* D. Use Grep to search for distinctive text from the error message (like "SYNC_CONFLICT" or "version mismatch"), then inspect the matching files to understand context. 

Question 4
Your productivity agent connects to three MCP servers: an issue tracker (search issues, get issue details, create comments), a documentation wiki (search docs, read pages), and a database explorer (run queries, get schema, list databases). When engineers ask cross-system questions like “What database tables are affected by the authentication refactor in PROJ-1234?”, monitoring shows the agent makes 8–10 sequential tool calls. The primary issue is explanatory calls because it lacks visibility into what content each server contains and exhausts context space before completing complex investigations.

Which architectural change best leverages MCP capabilities to address these issues?

* A. Add an orchestrator that routes questions to a single server based on keywords. 
* B. Consolidate all three servers into a unified MCP server with cross-referencing capabilities. 
* C. Add a separate investigation tool to each server that accepts a natural language question and returns relevant content summaries. 
* D. Expose each server’s content catalog as MCP resources—issue summaries, documentation hierarchies, database schemas. 

Question 5
An engineer who just joined the team asks the agent to help them understand the authentication and authorization architecture before making security improvements. The codebase has 800+ files across multiple services. What exploration strategy will most effectively build understanding given Claude’s built-in tools and context limits?

* A. Read any CLAUDE.md and README files first, then ask the engineer to specify which 10–15 files are most important. 
* B. Launch parallel subagents to explore different services simultaneously, then synthesize their findings into an architectural overview. 
* C. Read all files containing “auth”, “login”, “permission”, or “token” in their content or filename. 
* D. Use Grep to find authentication entry points, read those files, then follow imports and function calls from the auth flow toward identity services. 

Question 6
After adding an MCP server with specialized code refactoring tools (extract_function, rename_variable, inline_function) alongside basic text manipulation via Write and Bash commands for refactoring tasks, the MCP server is connected and healthy. Examining the configuration, you find each MCP tool has a minimal description like “extract_function: Extracts a function from code.”

What’s the most effective way to improve adoption of the MCP refactoring tools?

* A. Enhance the MCP tool descriptions to explain when each tool is preferable to text manipulation and clarify expected inputs and outputs. 
* B. Remove the Write tool from the agent’s configuration for refactoring sessions so it must use the MCP tools. 
* C. Implement a request classifier that detects refactoring intent and automatically routes those requests to the MCP server instead of letting the agent choose. 
* D. Accept this as expected behavior since simpler tools like sed are more predictable than specialized refactoring tools. 

Question 7
You’ve configured your Claude agent with three MCP servers: one for Git operations, one for Jira ticket management, and one for documentation search. When a user asks the agent to “create a branch for JIRA-123 and add documentation links to the ticket,” how does the agent access tools across these servers?

* A. Tools from all configured MCP servers are discovered at connection time and available simultaneously to the agent. 
* B. The agent automatically selects the most relevant server based on the request and adds only that server’s tools. 
* C. You must specify which MCP server to use for each turn, and the agent can only access one server’s tools at a time. 
* D. The agent queries each server sequentially to determine which handles each tool, routing calls based on tool name prefixes. 

Question 8
An engineer asks the agent to find all files in the monorepo that import the @company/auth package to understand how authentication is used across services. Which built-in tool is most appropriate for this task?

* A. Grep, to search for the import statement pattern across file contents. 
* B. Bash, to execute find . -type d -name "auth" and explore matching directories. 
* C. Glob, to find files with “auth” in their filename or path. 
* D. Read, starting with package.json files to trace dependency declarations. 

Question 9
Engineers frequently ask the agent to cross-reference code changes with Jira tickets during reviews—checking ticket descriptions, acceptance criteria, and recent comments. This currently requires manually copy-pasting content into conversations. The team wants the agent to access this ticket data directly. What’s the most effective approach?

* A. Use the Bash tool with curl to call Jira’s REST API, including authentication headers and parsing JSON responses inline. 
* B. Integrate an existing Jira MCP server that exposes tickets, comments, and metadata through discoverable MCP interfaces. 
* C. Build a custom MCP server wrapping Jira’s API with tools designed specifically for this team’s code review workflow. 
* D. Export Jira tickets to markdown files in the repository that the agent accesses using the Read tool. 

Question 10
Your code review assistant needs to analyze pull requests and provide feedback on three aspects: code style compliance, potential security issues, and documentation completeness. Each aspect requires reading files, running analysis tools, and generating a report section. The typical process follows the same three-step workflow for every PR.

Which task decomposition pattern is most appropriate for this workflow?

* A. Orchestrator-workers — have a central LLM analyze each PR to dynamically determine which checks are needed, then delegate to specialized worker LLMs for each identified subtask. 
* B. Routing — classify each PR by type (feature, bugfix, refactor) first, then route to different review prompts optimized for that category. 
* C. Single comprehensive prompt — include all instructions in one prompt and let the model handle all three aspects simultaneously. 
* D. Prompt chaining — break the review into sequential steps where each aspect (style, security, documentation) is analyzed separately and combined in a final synthesis step. 

Question 11
An engineer used Claude Code yesterday to investigate authentication flows in a legacy monolith, building up significant context over a 2-hour session. Today she wants to continue that specific investigation. She’s worked on three other codebases since then and knows the session isn’t the most recent “auth-deep-dive”. How should she resume?

* A. Use --resume auth-deep-dive to load that specific session by name. 
* B. Use --session-id with the UUID from yesterday’s session transcript file. 
* C. Start fresh and re-read the same files. 
* D. Use --continue to pick up where the most recent conversation left off. 

Question 12
You are refactoring a complex data parsing module in Claude Code. After three rounds of changes, the test suite starts failing with multiple edge-case errors. You realize your second change introduced a fundamental flaw, but the session context has become cluttered with debug output. What is the most effective approach to recover?

* A. Use /clear to reset the context window, then summarize the failed approach so Claude avoids repeating it. 
* B. Use /compact to summarize the history, then ask Claude to undo the recent changes. 
* C. Use git in a terminal tool call to run git checkout back to the starting commit, then start a fresh Claude Code session with clear context. 
* D. Ask Claude to debug the current errors step-by-step using additional tool calls. 

Question 13
You need to generate unit test coverage for a 200-file codebase with complex internal dependencies. You want to use Claude Code to build a comprehensive test suite across all modules over multiple days. What is the most effective exploration and execution strategy?

* A. Read all files in the codebase into context first, then generate tests module by module sequentially. 
* B. Systematically read all 200 files to create a complete function inventory before writing any tests. 
* C. Use Glob and Grep to map codebase structure, identify heavily-coupled modules, create a prioritized plan for high-impact areas, and adapt as dependencies are discovered. 
* D. Start writing tests for the first module alphabetically, using test failures and imports to discover related files organically. 

Question 14
An engineer submits two requests:

* Request A: “Rename the getUserData function to fetchUserProfile everywhere it’s used.” 
* Request B: “Improve error handling throughout the data processing module—add try/catch blocks, meaningful error messages, and prevent failures from silently corrupting data.” 
For which request does specifying an explicit multi-phase workflow (such as analyze → propose → implement with verification) provide the most benefit?

* A. Request B, the error-handling task. 
* B. Neither request benefits significantly. 
* C. Both requests benefit equally. 
* D. Request A, the function rename task. 

Question 15
An engineer submits two requests:

* Request A: “Rename the getUserData function to fetchUserProfile everywhere it’s used.” 
* Request B: “Improve error handling throughout the data processing module—add try/catch blocks, meaningful error messages, and prevent failures from silently corrupting data.” 
For which request does specifying an explicit multi-phase workflow (such as analyze → propose → implement with verification) provide the most benefit?

* A. Request B, the error-handling task. 
* B. Neither request benefits significantly. 
* C. Both requests benefit equally. 
* D. Request A, the function rename task. 

Question 16
Your team has three requirements for Claude Code’s behavior in your project:

1. Claude must never modify files in the db/migrations directory. 
2. Claude should prefer your custom logging module over console.log. 
3. All TypeScript files must be auto-formatted with Prettier after every edit. 
All three are currently written as instructions in your project’s CLAUDE.md. During a complex refactoring session, a teammate discovers that Claude edited a migration file, violating requirement #1. How should you restructure these requirements?

* A. Rewrite all three requirements in CLAUDE.md using stronger directive language and add examples. 
* B. Configure hooks for all three: a pre-tool-use hook blocking edits to migration files, a hook providing logging guidance, and a post-tool-use hook running Prettier after TypeScript edits. 
* C. Move all three requirements into .claude/rules as path-scoped rules. 
* D. Add an Edit permission deny rule for migrations and keep the logging preference and formatting instruction in CLAUDE.md. 

Question 17
Your team is configuring MCP servers in Claude Code. You want to add a shared venue lookup server that all team members should use, and you personally want to add an experimental music playlist server that only you are testing. Which configuration approach is correct?

* A. Add venue server to ~/.claude.json and playlist server to mcp.json. 
* B. Add both servers to your local ~/.claude.json. 
* C. Add venue server to mcp.json and playlist server to ~/.claude.json. 
* D. Add both servers to the project-level mcp.json file. 

Question 18
Your team has connected a custom MCP server that provides DevOps workflow templates. The server exposes several MCP prompts, such as deploy_checklist and incident_response, in addition to tools. How do these MCP prompts become accessible within Claude Code?

* A. They appear as slash commands (e.g., /mcp__servername__deploy_checklist) that you can invoke, with arguments passed after the command. 
* B. They are automatically prepended to every conversation as additional system-level context. 
* C. They are added to Claude Code’s tool registry alongside the server’s tools and invoked automatically. 
* D. They are surfaced as @-mentionable resources alongside files. 

Question 19
You need to add a date validation check ensuring event dates are in the future. This requires adding a conditional statement in one relatively small file. What is the most appropriate approach?

* A. Use direct execution to make the change. 
* B. Enter plan mode to analyze how the validation might impact other parts of the reservation flow. 
* C. Start with extended thinking mode enabled to ensure thorough reasoning about the validation logic. 
* D. Enter plan mode first to create a detailed implementation strategy before making the change. 

Question 20
You need to add a feature to an existing Node.js module that calculates shipping costs based on weight and distance. The project has comprehensive unit tests. Which approach reflects recommended best practices for working with Claude Code on this task?

* A. Ask Claude Code to analyze the whole repository, draft an architectural document, write the code, and refactor existing modules. 
* B. Write the complete implementation yourself and ask Claude Code to verify that no bugs were introduced. 
* C. Provide high-level requirements to Claude Code and let it make design decisions and write code without checking tests until the end. 
* D. Specify the shipping calculation requirements, ask Claude Code to write test cases first, verify they fail, then implement the logic until tests pass. 

Question 21
You ask Claude Code to fix a bug in a payment processing service. During its analysis, Claude Code identifies three additional issues: an unhandled edge case in tax calculation, an outdated dependency with a known security vulnerability, and inconsistent log formatting. What is the most effective way to handle these findings?

* A. Instruct Claude Code to address all four issues immediately in the current session while context is available. 
* B. Stop the current session, update project instructions to fix all four issues, and restart. 
* C. Focus Claude Code on fixing the primary payment bug first, then create separate tasks or sessions to address the other findings sequentially. 
* D. Ask Claude Code to document all four issues in CLAUDE.md so they are remembered for future sessions. 

Question 22
You are using Claude Code to refactor a critical component. Claude Code proposes a multi-file change that you want to carefully evaluate before proceeding. How can you best direct Claude Code's process?

* A. Direct Claude Code to output changes as a patch file that you can inspect manually before applying. 
* B. Use Plan Mode (/plan) to have Claude Code outline its strategy and affected files, review and refine the plan, then authorize execution. 
* C. Allow Claude Code to apply all changes, then use git diff to review what changed after the fact. 
* D. Instruct Claude Code to modify one file at a time, pausing for manual approval after each file edit. 

Question 23
Your project has a long-running test suite that takes 12 minutes to execute completely. You are using Claude Code to iteratively implement a new API endpoint. What is the most effective testing strategy during development?

* A. Run the full test suite after every minor edit to guarantee no regressions are introduced at any point. 
* B. Skip running tests entirely during development and run the full suite once after all code is complete. 
* C. Instruct Claude Code to run only the specific test file relevant to the new endpoint after edits, and run the full suite only before final submission. 
* D. Disable failing tests temporarily so Claude Code can proceed without interruption. 

Question 24
You are working on a React application where components frequently require custom hooks and specific prop patterns. You want Claude Code to follow these project-specific conventions automatically across all developer sessions. What is the most appropriate mechanism?

* A. Add detailed instructions to the project's CLAUDE.md file specifying component and hook conventions. 
* B. Pass custom prompt flags every time you launch Claude Code. 
* C. Include coding standards in every individual user prompt during sessions. 
* D. Rely on Claude Code's default React knowledge since standard patterns are already built-in. 

Question 25
You need to debug a complex race condition in a multi-threaded service. The issue occurs intermittently and requires analyzing log files, thread dumps, and source code simultaneously. How should you approach this with Claude Code?

* A. Provide all log files, thread dumps, and source files at once and ask Claude Code to immediately produce a fix. 
* B. Use Claude Code in a step-by-step manner: first ask it to analyze logs and identify suspicious timestamps, then investigate corresponding code paths, and hypothesis-test before changing code. 
* C. Ask Claude Code to rewrite the multi-threaded module using a single-threaded pattern to eliminate race conditions entirely. 
* D. Run Claude Code in direct execution mode repeatedly until it randomly encounters and fixes the issue. 

Question 26
Your team’s CLAUDE.md includes a rule: “Use 4-space indentation and always run Prettier formatting.” Despite this, Claude Code generates inconsistent formatting. Sometimes 2-space indentation appears. You also use Prettier, but it doesn’t eliminate the issue completely. What’s the most effective way to ensure consistently formatted code?

* A. Extract the formatting rules into a dedicated skill that Claude loads automatically when generating code, with more detailed examples. 
* B. Split the formatting rules into path-scoped .claude/rules files that load when Claude works on formatting-related files. 
* C. Configure a PostToolUse hook with an Edit/Write matcher that automatically runs Prettier on each file Claude modifies. 
* D. Add a stronger prompt-based check that evaluates whether generated code follows formatting requirements before accepting it. 

Question 27
A security audit requires updating your authentication library from v2 to v3. The migration guide documents breaking changes: authenticateUser now returns a Promise instead of accepting a callback, the User type has restructured fields, and three deprecated methods were removed. The library is imported in 45 files across several modules. What’s the most effective approach?

* A. Paste the migration guide’s breaking changes into your prompt and use direct execution to update all usage across the 45 files. 
* B. Create a custom slash command encapsulating the migration transformations, then execute it against each file without your continued supervision. 
* C. Update the dependency version, run the test suite, and use Claude Code to fix each failure as it appears. 
* D. Enter plan mode to explore library usage across modules, map affected code paths, then create a migration strategy before implementing changes. 

Question 28
Your monorepo contains shared coding standards in docs/standards/:

* security-rules.md (for API-facing services) 
* api-conventions.md (for services handling user data) 
* package-specific standards in individual packages 
Claude is applying all standards everywhere. What’s the most effective approach?

* A. Create .claude/rules/ files for each standard with YAML frontmatter specifying the packages/files where each standard applies. 
* B. Use @imports in each package’s CLAUDE.md to reference only the standards relevant to that package. 
* C. Create a shared-standards.md that combines all standards and have each package import it. 
* D. Put all standards in the root CLAUDE.md and add override instructions in package-level files. 

Question 29
You’ve asked Claude to write a data migration script, but the initial output doesn’t correctly handle records with null values. What’s the most effective way to iterate toward a working solution?

* A. Provide a test case with example input containing null values and the expected output, then ask Claude to fix it. 
* B. Describe the null value problem in detail and ask Claude to regenerate the entire script. 
* C. Add “think harder about edge cases” to your prompt and request a complete rewrite. 
* D. Manually edit the generated code to fix the null handling, then continue working with Claude on other parts. 

Question 30
Your team wants Claude to follow a detailed code review checklist (8 items covering API changes, tests, documentation, etc.) whenever reviewing pull requests. Developers currently paste the checklist at the start of every review session. What’s the best approach?

* A. Configure plan mode as the default for code review sessions. 
* B. Create a dedicated review subagent with the checklist embedded in its configuration. 
* C. Add the checklist to the project’s CLAUDE.md file under a “Code Review” section. 
* D. Create a /review slash command containing the checklist, invoked when starting review sessions. 

Question 31
You’ve configured Claude Code to analyze security vulnerabilities in a web application. During the analysis, Claude identifies a potential SQL injection vulnerability in a database query function. What is the most appropriate next step?

* A. Ask Claude to automatically rewrite all database queries across the application to prevent future vulnerabilities. 
* B. Have Claude attempt an exploit against the production server to verify the vulnerability exists. 
* C. Disregard the finding since automated tools frequently generate false positives for security issues. 
* D. Ask Claude to generate a minimal proof-of-concept test case or explain the specific input that triggers the issue before making changes. 

Question 32
You want to run Claude Code in an automated CI/CD pipeline to analyze daily security logs and post summaries to Slack. Which execution mode and set of permissions should you use?

* A. Run in default interactive mode and use a script to answer permission prompts automatically. 
* B. Run non-interactively with full admin permissions to ensure no steps are blocked. 
* C. Run interactively using --plan mode so human approval is required for every step. 
* D. Run non-interactively using --print or non-interactive mode with restricted permissions scoped to only the necessary log-reading tools. 

Question 33
Your team is building a complex multi-agent research pipeline using Claude Code. The pipeline needs to execute initial search tasks concurrently, aggregate results, evaluate research quality, and conditionally route to either a deep-dive task or a summary step. Which orchestration architecture best supports this design?

* A. Single agent loop with extended prompt instructions. 
* B. Linear prompt chain executing steps sequentially. 
* C. Parallel worker pool running isolated sub-agents managed by a central supervisor/orchestrator agent. 
* D. Purely autonomous agent network with peer-to-peer messaging without centralized control. 

Question 34
In a multi-agent system built with Claude Code, sub-agents frequently duplicate exploration work (e.g., re-reading the same files and re-running identical search queries) when performing parallel research subtasks. How can you optimize state management to avoid redundant effort?

* A. Share a centralized context store/cache where agents log visited resources and findings before initiating new tools. 
* B. Run all subtasks sequentially in a single session so context is naturally preserved. 
* C. Increase context limits so sub-agents can re-read files without impacting performance. 
* D. Restrict each sub-agent to a single tool call per turn. 

Question 35
When generating automated technical reports from multi-agent analysis sessions, you notice the synthesized output occasionally cites facts or findings that cannot be traced back to any tool output or source file. Which strategy most effectively ensures accurate source attribution?

* A. Require synthesis agents to explicitly cite specific tool outputs, file paths, or line numbers for every key claim and validate citations against execution logs. 
* B. Increase the temperature setting on the final synthesis agent to allow for more creative interpretation. 
* C. Run the final synthesis step twice and compare outputs for consistency. 
* D. Append "Ensure all claims are true" to the system prompt. 

Question 36
You are designing a code review workflow where an orchestrator agent delegates checks to three parallel worker agents: Security, Performance, and Style. The orchestrator needs to wait for all three workers to finish before consolidating findings into a final review comment. How should concurrency and control flow be managed?

* A. Have each worker directly post its comments to the PR as soon as it finishes. 
* B. Use an asynchronous join/barrier pattern where the orchestrator collects outputs from all parallel workers before invoking the synthesis step. 
* C. Run worker agents in a random sequence and merge output files on disk. 
* D. Allow the fastest worker agent to write the final review and cancel the remaining tasks. 

Question 37
A complex multi-agent workflow intermittently fails because worker agents produce output formats that deviate slightly from the expected JSON schema. What is the most robust way to ensure reliable inter-agent communication?

* A. Instruct the orchestrator to retry failed parses up to 10 times with the same prompt. 
* B. Implement strict schema validation (e.g., using tool call structure or JSON mode) at agent boundaries, re-prompting workers with validation errors when schemas are violated. 
* C. Relax the orchestrator's parsing logic to ignore missing fields and format errors. 
* D. Switch all inter-agent communication from structured JSON to unstructured plain text. 

Question 38
You are running Claude non-interactively in a CI pipeline using the command:

Bash




PROMPT="$PROMPT Analyze the provided diff"  
PROMPT="$PROMPT for bugs, security issues,"  
PROMPT="$PROMPT and style violations."  
claude -p \  
  --dangerously-skip-permissions \  
  --system-prompt "$PROMPT" \  
  < diff.txt 
The reviews complete and return feedback, but Claude only comments on the piped diff itself—it never reads surrounding files in the repository to understand broader context. You want Claude to read related files while still applying your custom review instructions. Which change achieves this?

* A. Keep --system-prompt and add --allowedTools "Read,Grep". 
* B. Stop piping the diff via stdin and embed it in the prompt. 
* C. Remove --system-prompt and place instructions in CLAUDE.md. 
* D. Replace --system-prompt with --append-system-prompt. 

Question 39
Your CI pipeline performs security-focused code reviews on approximately 50 PRs daily. Reviews are non-blocking—developers merge after tests pass and address findings in follow-up commits. You are evaluating the Message Batches API for cost reduction. What factor most determines whether batch processing is appropriate for this use case?

* A. Whether review feedback arriving up to 24 hours after PR creation remains actionable. 
* B. Whether your result processing can handle reviews arriving in a different order than submitted. 
* C. Whether you can structure each review as a single request without multi-turn refinement. 
* D. Whether reducing per-review latency from 30–60 seconds to near-instant matters. 

Question 40
A developer uses Claude Code to refactor a function during their development session. Before committing, they ask the same Claude session to review the code for issues. Later, a separate automated CI review catches several bugs that the same-session review missed. What best explains this discrepancy?

* A. The extended session length caused the context window to fill with conversation history, leaving less room for thorough analysis. 
* B. Claude retains context about its prior reasoning in the session, making it less likely to question its own decisions. 
* C. The CI environment has access to the full codebase context while the local session only sees the current file. 
* D. The CI review uses a more specific prompt tailored for catching bugs, while the developer’s request was too general. 

Question 41
The automated review pipeline generates an average of 18 findings per PR. Developer feedback reveals three categories of unwanted findings: formatting issues already enforced by CI, findings on auto-generated template code under src/generated/, and comments about intentional project conventions that resemble common anti-patterns. How should you reduce this noise while preserving detection of real issues?

* A. Create a REVIEW.md at the repository root with skip rules for CI-enforced checks and generated files, and require findings to cite specific evidence of incorrect behavior. 
* B. Add a prompt parameter to the GitHub Action configuration instructing it to suppress findings matching common anti-pattern patterns and apply stricter evidence requirements. 
* C. Configure separate GitHub Action workflow files for each code area and a general workflow for everything else. 
* D. Add detailed explanations to the project’s CLAUDE.md describing conventions and patterns. 

Question 42
Your automated reviewer uses a single prompt covering security issues, API design, and business logic correctness. It achieves high recall for API design findings but poor recall for business logic edge cases. When you split the prompt, business logic recall improves significantly while API design recall drops. How should you update the architecture?

* A. Provide the full repository as context instead of just changed files and surrounding code. 
* B. Replace the few-shot examples with a detailed checklist for specific logic edge cases. 
* C. Split the review into separate focused prompts (e.g., security, API design, business logic) and consolidate findings before posting. 
* D. Upgrade to a more capable model. 

Question 43
During initial testing of the automated review pipeline, you notice that reviews on large PRs (50+ changed files) sometimes take more than 10 minutes and cost $8–12 per run due to extensive agentic loops. Your team wants execution to stop once it reaches a fixed iteration count and a fixed dollar amount. Which configuration change directly enforces both per-invocation caps?

* A. Add --max-turns 10 --max-budget-usd 2.00 to the Claude invocation. 
* B. Set --permission-mode dontAsk to auto-deny tool permission requests not in the allowed set. 
* C. Set timeout-minutes: 5 on the GitHub Actions job step. 
* D. Switch the --model flag to a smaller, cheaper model. 

Question 44
Your pipeline reviews approximately 200 database migration scripts daily using the Message Batches API. Each batch review includes a large shared system prompt containing organization-wide schema standards, safety rules, and anti-pattern detectors. When analyzing cost metrics, you observe that input token costs remain higher than expected despite using batch processing. What optimization best addresses this cost bottleneck?

* A. Structure batch requests to leverage prompt caching for the shared system prompt across reviews. 
* B. Compress the system prompt text by removing whitespace and abbreviating standard descriptions. 
* C. Move the schema standards from the system prompt into the individual user prompts for each batch request. 
* D. Switch to a smaller model for processing migration scripts while keeping the system prompt unchanged. 

Question 45
A developer creates a PR updating a security-critical payment module. The automated review pipeline triggers, but due to a high volume of concurrent PRs, the review takes 12 minutes to complete. The developer merges the PR after unit tests pass at minute 5, before receiving the automated review feedback that flagged an unhandled authorization failure. What architectural change best prevents unreviewed code from reaching main branch?

* A. Configure the review workflow as a required status check in GitHub repository settings. 
* B. Add a post-merge step that automatically reverts PRs if high-severity findings are generated later. 
* C. Increase the timeout limit on the review job step so it isn't cancelled during high load. 
* D. Send Slack alerts to the security team whenever a PR in the payment module is opened. 

Question 46
You are configuring a CI/CD pipeline using Claude Code to perform automated code reviews on incoming PRs. You want to ensure the agent executes non-interactively, exits cleanly with an error status if execution fails, and limits max spending to $1.00 per PR review. Which command syntax correctly implements these requirements?

* A. claude --max-turns 10 --max-budget 1.00 --batch "Review PR #$PR_NUMBER" 
* B. claude -p "Review PR #$PR_NUMBER" --auto-approve --max-cost 1.00 
* C. claude -p "Review PR #$PR_NUMBER" --dangerously-skip-permissions --max-budget-usd 1.00 
* D. claude review --non-interactive --budget 1.00 --pr $PR_NUMBER 

Question 47
You want to configure an automated code review workflow that posts review comments directly to GitHub PRs. Which configuration strategy ensures proper authentication and authorization for both Claude Code and GitHub?

* A. Hardcode an API token into the workflow file and grant write permissions to the default GITHUB_TOKEN. 
* B. Store ANTHROPIC_API_KEY as a repository secret, pass it as an environment variable to the job step, and grant pull-requests: write permissions to GITHUB_TOKEN. 
* C. Pass ANTHROPIC_API_KEY via CLI flags and use a personal access token with admin permissions for GitHub API calls. 
* D. Use OAuth authentication for Claude Code and store the resulting access token in the repository's .env file. 

Question 48
Your automated code review action runs on pull_request events from fork pull requests submitted by external contributors. The workflow requires access to ANTHROPIC_API_KEY to run Claude Code and needs to post review comments back to the PR. How should you structure the workflow to handle secrets and permissions securely?

* A. Use pull_request_target event with explicit permission checks before running Claude Code. 
* B. Split into two workflows: pull_request (runs review in untrusted context and uploads results as an artifact) and workflow_run (downloads artifact and posts comments with write permissions). 
* C. Pass secrets directly into the pull_request workflow using secrets.INHERIT. 
* D. Grant pull-requests: write permissions to the default pull_request workflow. 

Question 49
Your automated PR reviewer generated feedback that included fabricated function signatures and cited line numbers that don't exist in the changed files. How should you modify the prompt to reduce these hallucinations?

* A. Include negative examples showing hallucinated comments and instruct the model not to generate them. 
* B. Add instructions requiring the model to verify line numbers against the diff and cite exact file paths and code snippets before commenting. 
* C. Switch from JSON output format to plain markdown output. 
* D. Increase the temperature parameter to give the model more flexibility in identifying edge cases. 

Question 50
You notice that automated PR reviews frequently flag issues in third-party library code under node_modules/ or generated protobuf files under proto_gen/, consuming context and generating noisy comments. How can you most effectively restrict the review scope?

* A. Add path exclusions to .claudeignore or specify matching glob patterns in the review invocation. 
* B. Instruct the model in the system prompt to ignore files with "generated" in their paths. 
* C. Delete node_modules/ and proto_gen/ directories before running the review step. 
* D. Run a post-processing script to filter out comments that reference excluded directories. 

Question 51
You are setting up an automated code review workflow using Claude Code in GitHub Actions. You want to ensure the agent receives feedback on its actions and can perform multi-step file inspections, while strictly preventing it from making any modifications to the repository or executing arbitrary shell scripts. Which configuration set meets these requirements?

* A. Run with --allowedTools "Read,Grep,Glob" and --dangerously-skip-permissions. 
* B. Run in default interactive mode and redirect stdin from /dev/null. 
* C. Run with --read-only flag enabled and set permissions: read-all in the GitHub Actions workflow context. 
* D. Run with --allowedTools "Read,Grep,Glob" and --permission-mode dontAsk. 

Question 52
Your automated PR reviewer generated feedback that included fabricated function signatures and cited line numbers that don't exist in the changed files. How should you modify the prompt to reduce these hallucinations?

* A. Include negative examples showing hallucinated comments and instruct the model not to generate them. 
* B. Add instructions requiring the model to verify line numbers against the diff and cite exact file paths and code snippets before commenting. 
* C. Switch from JSON output format to plain markdown output. 
* D. Increase the temperature parameter to give the model more flexibility in identifying edge cases. 

Question 53
You notice that automated PR reviews frequently flag issues in third-party library code under node_modules/ or generated protobuf files under proto_gen/, consuming context and generating noisy comments. How can you most effectively restrict the review scope?

* A. Add path exclusions to .claudeignore or specify matching glob patterns in the review invocation. 
* B. Instruct the model in the system prompt to ignore files with "generated" in their paths. 
* C. Delete node_modules/ and proto_gen/ directories before running the review step. 
* D. Run a post-processing script to filter out comments that reference excluded directories. 

Question 54
You are configuring a CI/CD pipeline using Claude Code to perform automated code reviews on incoming PRs. You want to ensure the agent executes non-interactively, exits cleanly with an error status if execution fails, and limits max spending to $1.00 per PR review. Which command syntax correctly implements these requirements?

* A. claude --max-turns 10 --max-budget 1.00 --batch "Review PR #$PR_NUMBER" 
* B. claude -p "Review PR #$PR_NUMBER" --auto-approve --max-cost 1.00 
* C. claude -p "Review PR #$PR_NUMBER" --dangerously-skip-permissions --max-budget-usd 1.00 
* D. claude review --non-interactive --budget 1.00 --pr $PR_NUMBER 

Question 55
You want to configure an automated code review workflow that posts review comments directly to GitHub PRs. Which configuration strategy ensures proper authentication and authorization for both Claude Code and GitHub?

* A. Hardcode an API token into the workflow file and grant write permissions to the default GITHUB_TOKEN. 
* B. Store ANTHROPIC_API_KEY as a repository secret, pass it as an environment variable to the job step, and grant pull-requests: write permissions to GITHUB_TOKEN. 
* C. Pass ANTHROPIC_API_KEY via CLI flags and use a personal access token with admin permissions for GitHub API calls. 
* D. Use OAuth authentication for Claude Code and store the resulting access token in the repository's .env file. 

Question 56
Your automated code review action runs on pull_request events from fork pull requests submitted by external contributors. The workflow requires access to ANTHROPIC_API_KEY to run Claude Code and needs to post review comments back to the PR. How should you structure the workflow to handle secrets and permissions securely?

* A. Use pull_request_target event with explicit permission checks before running Claude Code. 
* B. Split into two workflows: pull_request (runs review in untrusted context and uploads results as an artifact) and workflow_run (downloads artifact and posts comments with write permissions). 
* C. Pass secrets directly into the pull_request workflow using secrets.INHERIT. 
* D. Grant pull-requests: write permissions to the default pull_request workflow. 

Question 57
A complex multi-agent workflow intermittently fails because worker agents produce output formats that deviate slightly from the expected JSON schema. What is the most robust way to ensure reliable inter-agent communication?

* A. Instruct the orchestrator to retry failed parses up to 10 times with the same prompt. 
* B. Implement strict schema validation (e.g., using tool call structure or JSON mode) at agent boundaries, re-prompting workers with validation errors when schemas are violated. 
* C. Relax the orchestrator's parsing logic to ignore missing fields and format errors. 
* D. Switch all inter-agent communication from structured JSON to unstructured plain text. 

Question 58
You’ve configured the system so that all four subagents have access to the complete set of 18 tools. During testing, tool-selection behavior degrades—the synthesis agent attempts web searches, and the report generator tries to analyze documents. What is the most likely cause?

* A. Choosing from 18 tools instead of 4–5 relevant ones increases decision complexity beyond useful specialization benefits. 
* B. The tool definitions consume too much context-window space, leaving insufficient room for task execution. 
* C. The coordinator cannot track which capabilities each subagent has, leading to misrouted tasks. 
* D. The agents’ role descriptions in their system prompts conflict with having access to the complete toolset. 

Question 59
When analyzing complex legal cases that cite multiple precedents, the document analysis subagent processes each precedent sequentially and takes over 3 minutes to analyze completely. What is the most effective way to reduce latency while preserving result quality and making the system easier to monitor and debug?

* A. Create a recursive agent hierarchy where analysis agents subdivide work among child agents without coordinator involvement. 
* B. Implement a message queue where precedent analysis tasks are processed asynchronously by a pool of worker agents. 
* C. Enable the document analysis subagent to spawn its own specialized subagents dynamically for each precedent. 
* D. Have the coordinator spawn parallel document analysis subagents, each focused on a subset of precedents. 

Question 60
After the web search agent finds 25 sources (120K tokens of raw content), the document analysis agent extracts key insights (18K tokens), and the synthesis agent produces a coherent narrative draft (3K tokens), the coordinator must pass context to the report-generation agent while preserving proper source citations. What context-passing strategy provides the best balance of completeness and efficiency?

* A. Pass only the synthesis draft and have a separate post-processing pipeline match claims to sources and insert citations. 
* B. Pass the synthesis draft along with a structured source index that maps key claims to their source URLs and relevant excerpts. 
* C. Pass a condensed summary of all prior stages that preserves the main findings and attributes them to source URLs. 
* D. Pass the full accumulated context from all prior agents.
