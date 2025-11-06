---
title: "Example Project"
visibility: "public"
gated: false
stream: "general"
tags:
  - example
  - tutorial
status: "active"
startDate: 2025-11-05
lastUpdated: 2025-11-05
description: "An example project to demonstrate the Workspace structure"
---

# Example Project

Welcome to your first Workspace project! This is an example to help you understand the structure and organization.

## What is a Project?

A project is a collection of related research, experiments, or work. Each project can have:
- Multiple **streams** (work packages or sub-projects)
- Documentation
- Updates and logs
- Data files

## Getting Started

1. **Edit this file** using Keystatic CMS at `/keystatic`
2. **Create a new stream** under the `streams/` directory
3. **Add updates** to document your progress
4. **Publish your work** when ready by merging draft → main

## Project Structure

```
example-project/
├── README.md                 (this file)
├── .access.yml              (optional: for gated content)
└── streams/
    └── example-stream/
        ├── README.md        (stream overview)
        ├── updates/         (daily logs and entries)
        ├── docs/            (protocols, guides)
        └── data/            (datasets, files)
```

## Next Steps

- Replace this example with your own project
- Check out the [documentation](../../docs/README.md)
- Learn about [safety gating](../../docs/architecture/07_Safety_Protocol_System.md) if working with hazardous materials

---

**Created:** November 5, 2025
**Template Version:** 1.0
