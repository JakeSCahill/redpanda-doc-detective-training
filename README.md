# Doc Detective Workshop

Welcome to the **Doc Detective Workshop**! This repository is a sandbox for our team to get hands-on experience writing automated tests for our Redpanda docs using [Doc Detective](https://example.com/doc-detective-docs). The goal here is to practice writing tests and learn how to simulate user interactions in our docs. At the end of this workshop, we'll have our guide for creating topics in Cloud set up with automated testing.

## Introduction

In this workshop, you'll write tests using Doc Detective. These tests simulate real user interactions, such as logging in, navigating, and filling forms, so that we can ensure our docs remain user-friendly and error-free.

**Goals:**

- Learn the basics of writing automated tests.
- Understand how to set up and run tests.
- Experiment with different test steps and actions.

---

## How tests work

Tests use a JSON format, and each test is a series of steps. Each step defines an action, such as:

- `setVariables`: Loads environment variables for future test steps.
- `goTo`: Navigates to a specific URL.
- `find`: Locates elements on the page and optionally clicks them.
- `typeKeys`: Simulates typing (including special keys like `$ENTER$`).
- `wait`: Pauses test execution, such as waiting for a page to finish loading.

Each action has properties associated with it. For example, the `find` action has a required `selector` property that tells Doc Detective which element on the page it needs to find for the step to pass. The `selector` property takes CSS selectors. For example, this selector tells Doc Detective to find an element with the `title` attribute called `Search`.

```json
{
  "action": "find",
  "selector": "[title=Search]"
}
```

If you want to ensure the label on an element hasn't changed, you can ask Doc Detective to check the label text. For example, to ask Doc Detective to pass only if the text inside the element says 'Search':

```json
{
  "action": "find",
  "selector": "[title=Search]",
  "matchText": "Search"
}
```

## Run tests

To run a test or a series of tests, you use the `npx doc-detective runTests` command. This command expects a directory or a file that contains one or more tests.

```
npx doc-detective runTests --input intro.json -c challenge/.doc-detective.json
```

- `--input intro.json`: Runs the test in the `input.json` file.
- `-c challenge/.doc-detective.json`: Tells Doc Detective to use the configuration file in the `challenge/` directory.

## Agenda

Below is the agenda for our workshop. This schedule is a rough guide and may be adjusted based on feedback and progress:

1. Introduction (10 min)

1. Demo: Login test (10 min)

1. Hands-on challenge (30 min)

1. Break (10 min)

1. Review and discussion (30 min)

## Get started with the challenge

1. Clone the repository:

   ```bash
   git clone https://github.com/JakeSCahill/redpanda-doc-detective-training.git
   cd redpanda-doc-detective-training
   ```

1. Install dependencies:

    ```bash
    npm install
    ```

1. Add the password to the `.env` file (you'll be told what this password is during the workshop):

    ```ini
    PASSWORD=<password>
    ```

1. Run the example:

    ```bash
    cd challenge
    npx doc-detective runTests --input cloud-login.json
    ```

A `screenshots/login.png` image was autogenerated and saved to your local filesystem.
Notice how the image shows a modal. But, you want to be able to test creating a topic is Cloud and take a screenshot of the final result.

## Repository structure

This repository is organized to help you progressively build your testing skills. Here’s an overview of the structure:

```bash
doc-detective-test-practice/
├── README.md                    # Workshop overview and instructions
├── challenge/                   # Hands-on exercise
│   ├── cloud-login.json         # Test configuration for the challenge
    ├── .doc-detective.json      # Configuration for Doc Detective
    ├── create-topic.adoc        # Doc file where you'll complete the challenge
├── package-lock.json            # Auto-generated lock file (Node.js dependencies)
├── package.json                 # Project metadata and dependency definitions
└── solution/                    # Complete solution for the challenge
└── .env                         # Environment file for password
```

## Additional resources

- [Doc Detective docs](https://doc-detective.com/)
- [Doc Detective GitHub repo](https://github.com/doc-detective/doc-detective)
- [Doc Detective GitHub Action repo](https://github.com/doc-detective/github-action)
- [Internal wiki on doc testing](https://redpandadata.atlassian.net/wiki/spaces/DOC/pages/1031503969/Docs+as+Tests+How+we+test+our+docs)

## Contribute

This workshop is all about learning and experimentation. If you create new tests or come up with ideas to improve the testing process:

1. Fork the repository.
1. Create a branch for your test or improvement.
1. Submit a pull request to share your changes with the team.
1. Provide feedback using the **Issues** tab. You can suggest improvements or ask questions.
