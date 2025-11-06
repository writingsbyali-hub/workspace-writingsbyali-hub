---
title: "Welcome to Your Workspace"
date: 2025-11-05
tags:
  - welcome
  - getting-started
related_projects:
  - example-project
---

# Welcome to Your Workspace

Congratulations on setting up your personal Workspace! This is your space to document research, experiments, projects, and ideas.

## What is Workspace?

Workspace is a Git-first research documentation platform that helps you:
- **Organize** projects and experiments systematically
- **Document** your work with updates and notes
- **Share** responsibly with safety gating
- **Collaborate** through Git workflows
- **Own** your data completely

## Getting Started

### 1. Explore the Example Project

Check out `content/projects/example-project/` to see how content is structured.

### 2. Edit Content

You have two ways to edit content:

**Option A: Keystatic CMS (Recommended)**
- Navigate to `/keystatic` on your site
- Visual editor for all content
- Auto-commits to your `draft` branch

**Option B: Direct Git Editing**
- Edit markdown files directly in your favorite editor
- Commit and push to `draft` branch
- Full control over Git history

### 3. Publish Your Work

When ready to make content public:
1. Review changes in `draft` branch
2. Click "Publish" button (merges `draft → main`)
3. Changes go live on your site!

## Content Structure

```
content/
├── projects/          Your research projects
│   └── [project]/
│       ├── README.md       Project overview
│       └── streams/        Work packages
│           └── [stream]/
│               ├── README.md      Stream overview
│               ├── updates/       Daily logs
│               ├── docs/          Protocols
│               └── data/          Datasets
└── notes/             Personal notes and ideas
    └── [note].md
```

## Next Steps

1. **Delete or modify** the example project
2. **Create your first project** in Keystatic
3. **Document your first update**
4. **Explore safety gating** if needed for hazardous work
5. **Invite collaborators** (coming in Phase 2!)

## Resources

- [Full Documentation](../../docs/README.md)
- [Git-First Architecture](../../docs/implementation/01_Phase1_Git_First_MVP.md)
- [Keystatic Guide](../../docs/architecture/05_Keystatic_Integration.md)
- [Safety Protocols](../../docs/architecture/07_Safety_Protocol_System.md)

## Questions?

- Check the [documentation](../../docs/README.md)
- Open an issue on GitHub
- Join community discussions

---

Happy researching! 🚀

**Template Version:** 1.0
**Last Updated:** November 5, 2025
