<img src="./cover.png" alt="AI Workflow Logo" width="1080" height="150"/>

# Ai-Workflow

This is a comprehensive AI workflow management system designed to normalize how developers create and use AI agents to develop features, bug fixes, and tests. The system provides a structured approach to building AI-powered applications, ensuring consistency and efficiency across development processes.

## Description

The concept is simple: treat AI prompts the same way we treat software—define them as clear pipelines with predictable inputs and outputs.

This repository provides a lightweight framework for using AI agents in a structured way, allowing developers to create, manage, and deploy AI-driven features seamlessly.

Think in blocks of code: each block can be changed, moved, and updated without affecting the rest of the system. Every block has a specific function, and they can be combined to create complex workflows.

## Structure

```text
|-- README.md
|-- workflow/
|  |-- agent.md
|  |-- pipeline/
|  |  |-- templates/
|  |  |-- feature_pipeline.md
|  |  |-- bugfix_pipeline.md
|  |  |-- test_pipeline.md
|  |-- backlog/
|  |-- features
|  |-- bugfixes
|  |-- tests
|-- workflow-example/
```

- `agent.md`: This can be a single file or an entire repository that defines the AI agents available to the pipelines.
- `pipeline/`: This folder receives each task that the agent will work on, using a specific pipeline template from the `templates/` folder.
  - `templates/`: This contains different pipeline templates for various tasks such as feature development, bug fixing, and testing.
- `backlog/`: This folder contains the tasks that need to be addressed by the AI agents.
  - `features`: A list of features to be developed.
  - `bugfixes`: A list of bugs to be fixed.
  - `tests`: A list of tests to be created or executed.
- `workflow-example/`: This folder contains example implementations of the AI workflow system.

> \*This model is a initial version that will be improved and expanded. So feel free to contribute with ideas, suggestions, and improvements!

### How to Use

1. Define your AI agents in the `agent.md` file or repository.
2. Create a pipeline for your specific task using a template from the `pipeline/templates/` folder.
3. Populate the `backlog/` folders with tasks that you want the AI agents to work on.
4. Move each task through the defined pipeline to see how the AI agents handle them.
5. Use the AI integration of your choice (OpenAI, etc.) to execute the tasks. Do not forget to move the current task to `/pipeline/` and link the agent definition with the corresponding backlog file (feature, bugfix, or test).

The idea behind this system is to frame every task as an AI prompt. You describe what you want, and the agent follows the defined steps to make it happen.

The pipeline defines how the agent will work on the task. For example, it can dictate:

1. Whether you need a log of changes for every step or just the final result.
2. Whether changes require manual review before being applied.
3. Whether tests must be created or updated after implementing a feature or fix.
4. Whether the agent should check for potential conflicts with existing code before making changes.

All these questions must be answered inside the pipeline so the agent knows exactly how to proceed.

## Creating Your Own Agent

The agent file or repository should define the capabilities and characteristics of the AI agents you want to use. You can create multiple agents with different specializations, such as feature development, bug fixing, or testing.

- This file can be regenerated with AI: ask your tool to create an agent definition for a specific programming language or framework using knowledge of the project and codebase so the agent starts from an informed baseline.

What I suggest including in your agent file (and refining over time):

- Define the agent's role and purpose.

  - `/backlog` tracks prioritized upcoming work; `/pipeline` holds the single task currently in progress. Treat those files as the source of truth for sequencing.
  - Every action the agent takes must be justified by information inside `/workflow` (never rely on memory or external context).

- Operating principles

  - Intake - Read `/pipeline` to understand the current task.
  - Cross-reference - Check `/backlog` to ensure the task is still relevant and prioritized.
  - Action - Execute the task as defined in `/pipeline`, adhering to the specified workflow steps.
  - Report - Log all actions and decisions in `/pipeline` for transparency and future reference.

- Specify what they can do, such as:

  - Code generation
  - Bug fixing
  - Test creation
  - Code review
  - Documentation generation

- Specify what they cannot do, such as:

  - Add external libraries without approval
  - Run commands on the system, even for testing
  - Make decisions without human oversight
  - Use emoticons or informal language in responses
  - Add casual comments in code (use JSDoc or equivalent if commenting is required)

- Code Base/Project information

  - Programming languages used
  - Frameworks and libraries
  - Coding standards and conventions
  - Project architecture overview
  - How the project is structured and organized

- Guideline project information (optional or placed in another file)
  - Code format
  - Testing framework
  - TSLint/ESLint rules
  - Commit message conventions

## Creating Different Pipelines

At this point I have only implemented a single pipeline: whatever sits inside the `/pipeline/` folder, using one of the templates located in `/pipeline/templates/`.

But in the future we can have different pipelines for different tasks, such as:

Each pipeline can include steps such as:

1. Analyze the task
2. Generate code changes
3. Review changes
4. Test changes
5. Document changes
6. Finalize and commit changes

OR

1. Understand the feature requirements
2. Design the feature architecture
3. Ask for review and code validation
4. Implement the feature or fix the bug

OR

1. Identify the bug
2. Locate the source of the bug
3. Create a file with Proposed fix (`proposed_fix.md`)

## Contributing

Contributions are welcome! If you have ideas for new features, improvements, or bug fixes, please open an issue or submit a pull request.

When contributing, please follow the established coding standards and guidelines outlined in the `/workflow/agent.md` file to ensure consistency across the codebase.

## Want to Learn More about how work with AI Agents?

Check my article: [🇺🇸 The Art of Talking to Machines](https://mwolfc.com/projects/the-art-of-talking-to-machines)

Substack: [🇧🇷 A arte de conversar com máquinas](https://substack.com/home/post/p-175744458)
