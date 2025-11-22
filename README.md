# Zion Documentation

Official documentation for **Zion** - the AI-powered school management system designed specifically for ACE (Accelerated Christian Education) schools.

**Live Documentation:** [docs.zionapp.co](https://docs.zionapp.co)

## About Zion

Zion transforms time-consuming manual processes into intelligent automation, liberating administrators and supervisors to focus on what matters most: student success.

**Key Features:**
- **Goal Check Intelligence** - Transform 2-3 hours of manual compilation into <1 minute
- **PACE Curriculum Integration** - Complete ACE PACE catalog (144 PACEs, 1001-1144)
- **Real-Time Dashboards** - Instant school-wide and centre-level intelligence
- **Automated Reporting** - Generate professional daily and weekly reports in seconds
- **Multi-Centre Management** - Purpose-built for ACE schools with multiple learning centres

## Documentation Structure

This repository contains comprehensive documentation covering:

### Getting Started
- **Welcome Page** - Zion overview and value proposition
- **Quickstart Guide** - 15-minute school setup walkthrough
- **Features Overview** - Complete feature catalog

### User Guides
- **Administrator Onboarding** - Complete handbook for school administrators
- **Supervisor Goal Check Workflow** - Daily morning-to-evening workflow
- **Monitor Guides** - Data entry workflows and best practices

### Feature Documentation
- **Goal Check Intelligence** - Complete system overview and usage
- **Student Management** - Roster and PACE assignment guides
- **Reporting** - Daily and weekly report generation
- **Data Export** - CSV export and integration

### Resources
- **Changelog** - Version history and upcoming features
- **FAQ** - Frequently asked questions
- **Support** - Contact information and troubleshooting

## Documentation Statistics

- **Total Pages:** 9 comprehensive MDX files
- **Word Count:** ~25,000+ words of original content
- **Coverage:** Epic 1 (Foundation) and Epic 2 (Goal Check Intelligence) fully documented
- **AI Tools Integration:** Claude Code, Cursor, and Windsurf guides

## Local Development

### Prerequisites

- Node.js 18+ installed
- npm or yarn package manager

### Install Mintlify CLI

```bash
npm i -g mint
```

### Run Local Preview

Navigate to the repository root (where `docs.json` is located) and run:

```bash
mint dev
```

View your local preview at `http://localhost:3000`.

### Update CLI

If your dev environment isn't running properly:

```bash
mint update
```

## Publishing Changes

This repository is connected to Mintlify via GitHub app integration. Changes are automatically deployed to production when pushed to the `main` branch.

### Deployment Workflow

1. Make documentation changes locally
2. Preview with `mint dev`
3. Commit changes with descriptive message
4. Push to `main` branch
5. Mintlify automatically rebuilds and deploys (typically <2 minutes)

### Branch Strategy

- **main** - Production documentation (auto-deploys to docs.zionapp.co)
- **feature/** - Feature branches for new documentation
- **fix/** - Fix branches for corrections

## Documentation Standards

### Content Guidelines

- **Voice:** Second-person ("you") throughout
- **Style:** Concise, actionable instructions
- **Examples:** Real-world scenarios and use cases
- **Prerequisites:** Listed at start of procedural content
- **Time Estimates:** Provided for all major tasks

### MDX File Requirements

All MDX files must include frontmatter:

```mdx
---
title: "Page Title"
description: "Concise summary for SEO/navigation"
icon: "icon-name" # Optional, for navigation
---
```

### Component Usage

Use Mintlify components consistently:
- `<Card>` - Highlight important information or links
- `<CardGroup>` - Group related cards
- `<Steps>` - Multi-step procedures
- `<Tip>` - Helpful tips and best practices
- `<Warning>` - Important warnings or gotchas
- `<Note>` - Additional context or information

### Code Blocks

Always include language tags:

````mdx
```typescript
// TypeScript code example
```
````

### Links

- **Internal Links:** Use relative paths (`/guides/administrator/onboarding`)
- **External Links:** Use full URLs (`https://zionapp.co`)
- **Alt Text:** Required for all images

## Contributing

### Making Changes

1. Create a feature branch: `git checkout -b feature/new-guide`
2. Make your documentation changes
3. Test locally with `mint dev`
4. Commit with descriptive message following conventional commits
5. Push and create pull request

### Commit Message Format

Follow conventional commits:

```
docs: Add student management guide
docs: Update Goal Check workflow with new features
fix: Correct typo in administrator onboarding
chore: Update navigation structure
```

### Review Process

All documentation changes should be:
- Tested locally with `mint dev`
- Proofread for clarity and accuracy
- Checked for broken links
- Verified frontmatter is complete
- Confirmed component usage is correct

## Project Structure

```
zion-documentation/
├── docs.json                          # Navigation and configuration
├── index.mdx                          # Welcome page
├── quickstart.mdx                     # Quickstart guide
├── features.mdx                       # Features overview
├── changelog.mdx                      # Version history
├── support.mdx                        # Support information
├── faq.mdx                            # FAQ
├── guides/
│   ├── administrator/
│   │   └── onboarding.mdx            # Administrator handbook
│   └── supervisor/
│       └── goal-check.mdx            # Supervisor workflow
├── features/
│   └── goal-check/
│       └── overview.mdx              # Goal Check overview
├── ai-tools/
│   ├── claude-code.mdx               # Claude Code guide
│   ├── cursor.mdx                    # Cursor guide
│   └── windsurf.mdx                  # Windsurf guide
└── logo/
    ├── light.svg                      # Light mode logo
    └── dark.svg                       # Dark mode logo
```

## Troubleshooting

### Dev Environment Issues

**Page loads as 404:**
- Ensure you're in the folder with `docs.json`
- Check the page path matches navigation in `docs.json`
- Verify frontmatter is valid YAML

**CLI not running:**
- Run `mint update` to get latest version
- Check Node.js version (18+ required)
- Clear npm cache: `npm cache clean --force`

**Changes not appearing:**
- Hard refresh browser (Cmd+Shift+R or Ctrl+Shift+R)
- Check file is saved
- Restart dev server

### Deployment Issues

**Changes not deploying:**
- Verify push to `main` branch succeeded
- Check GitHub app integration at [Mintlify Dashboard](https://dashboard.mintlify.com)
- Wait 2-3 minutes for build to complete

**Build failing:**
- Check Mintlify build logs in dashboard
- Verify all MDX files have valid frontmatter
- Ensure no syntax errors in docs.json

## Resources

- **Zion App:** [zionapp.co](https://zionapp.co)
- **Live Documentation:** [docs.zionapp.co](https://docs.zionapp.co)
- **Mintlify Documentation:** [mintlify.com/docs](https://mintlify.com/docs)
- **Support:** support@zionapp.co

## License

© 2025 Zion. All rights reserved.

## Maintained By

This documentation is maintained by the Zion team and community contributors.

For questions or suggestions, contact: docs@zionapp.co
