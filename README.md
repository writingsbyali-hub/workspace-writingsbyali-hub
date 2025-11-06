# Workspace Template

**Version:** 1.0
**Last Updated:** November 5, 2025

This is the official template repository for creating new personal Workspace instances. When a user signs up, they automatically get a fork of this repository to store their research content.

## What is Workspace?

Workspace is a Git-first research documentation platform that enables researchers to:
- Document projects, experiments, and findings
- Share work responsibly with safety gating
- Own their data completely (stored in their own GitHub repo)
- Collaborate through standard Git workflows

## Architecture

- **Git = Source of Truth**: All content stored in this repository
- **Supabase = Auth + Cache**: Authentication and metadata only
- **Keystatic = CMS**: Visual editor for content
- **Astro = Frontend**: Static site generation

## Repository Structure

```
workspace-by-username/
├── content/                    # All user content (Git-tracked)
│   ├── projects/              # Research projects
│   │   └── [project-slug]/
│   │       ├── README.md      # Project overview + frontmatter
│   │       ├── .access.yml    # Optional: safety gating
│   │       └── streams/       # Work packages
│   │           └── [stream-slug]/
│   │               ├── README.md
│   │               ├── updates/    # Daily logs
│   │               ├── docs/       # Protocols
│   │               └── data/       # Datasets
│   └── notes/                 # Personal notes
│
├── public/                    # Static assets
│   └── images/
│
├── keystatic.config.ts        # Keystatic CMS configuration
├── astro.config.mjs           # Astro configuration
└── README.md                  # This file
```

## Branches

- **`main`**: Published content (publicly visible)
- **`draft`**: Work-in-progress (Keystatic writes here)

When you're ready to publish, merge `draft → main` via the Workspace UI.

## Getting Started

### For Users

1. **Sign up** at [workspace-by-ali.vercel.app](https://workspace-by-ali.vercel.app)
2. **Connect GitHub** (automatic fork of this template)
3. **Start documenting** using Keystatic at `/keystatic`
4. **Publish** when ready!

### For Developers

1. **Fork this repo** or let the signup flow do it automatically
2. **Clone locally**:
   ```bash
   git clone https://github.com/your-username/workspace-by-your-username.git
   cd workspace-by-your-username
   ```
3. **Install dependencies**:
   ```bash
   npm install
   ```
4. **Run dev server**:
   ```bash
   npm run dev
   ```
5. **Edit content**:
   - Use Keystatic at `http://localhost:4321/keystatic`
   - Or edit markdown files directly
6. **Deploy to Vercel** (or your preferred host)

## Content Guidelines

### Projects

Each project should have:
- Clear title and description
- Appropriate visibility setting (public/gated/private)
- At least one stream
- Regular updates documenting progress

### Safety Gating

If your project involves hazardous materials or procedures:
1. Create `.access.yml` in project directory
2. Set `gated: true`
3. Specify `required_acknowledgment` code
4. Create safety documentation

Example:
```yaml
# content/projects/plasma-research/.access.yml
gated: true
required_acknowledgment: "plasma_safety_v1.3"
risk_level: "high"
```

### Updates

Document your work regularly with updates:
- **Experiments**: Document procedures and results
- **Observations**: Record findings
- **Milestones**: Celebrate achievements
- **Notes**: Ideas and reflections

## Frontmatter Schemas

### Project (`content/projects/[slug]/README.md`)

```yaml
---
title: "Project Title"
visibility: "public"  # or "gated", "private"
gated: false
stream: "stream-name"
tags: ["tag1", "tag2"]
status: "active"  # or "draft", "archived"
startDate: 2025-11-05
lastUpdated: 2025-11-05
description: "Short description"
---
```

### Stream (`content/projects/[project]/streams/[slug]/README.md`)

```yaml
---
title: "Stream Title"
parentProject: "project-slug"
gated: false
startDate: 2025-11-05
lastUpdated: 2025-11-05
description: "Stream description"
---
```

### Update (`content/projects/[project]/streams/[stream]/updates/YYYY-MM-DD-slug.md`)

```yaml
---
title: "Update Title"
date: 2025-11-05
type: "experiment"  # or "observation", "milestone", "note"
tags: ["tag1", "tag2"]
---
```

## File Size Guidelines

- **Markdown files**: Keep under 500 KB
- **Images**: Optimize to <1 MB each
- **Data files**: <10 MB per file (use external storage for larger datasets)
- **Total repo**: Aim for <1 GB

For large datasets, consider:
- Supabase Storage
- AWS S3 / Backblaze B2
- Separate data repository with Git LFS

## Customization

### Branding

You can customize your workspace:
- Update site title in `astro.config.mjs`
- Add custom logo to `public/`
- Modify colors and styles (while preserving accessibility)

### Collections

To add new content types:
1. Update `keystatic.config.ts`
2. Create corresponding Astro content collection
3. Add pages to render new content

## Contributing

Improvements to this template are welcome!

1. Fork this repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## Documentation

Full documentation available at:
- [Phase 1 Implementation Guide](https://github.com/workspace-by-ali/workspace-by-ali/blob/main/docs/implementation/01_Phase1_Git_First_MVP.md)
- [Keystatic Integration](https://github.com/workspace-by-ali/workspace-by-ali/blob/main/docs/architecture/05_Keystatic_Integration.md)
- [Data Structures Reference](https://github.com/workspace-by-ali/workspace-by-ali/blob/main/docs/reference/Data_Structures.md)

## Support

- [Documentation](../../docs/README.md)
- [GitHub Issues](https://github.com/workspace-by-ali/workspace-by-ali/issues)
- [Community Discussions](https://github.com/workspace-by-ali/workspace-by-ali/discussions)

## License

MIT License - See LICENSE file for details

## Version History

### 1.0 (2025-11-05)
- Initial template release
- Example project with stream and updates
- Comprehensive documentation
- Safety gating support

---

**Template Maintained By:** Workspace Team
**Questions?** Open an issue or discussion on GitHub
