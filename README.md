# James Toolkit - Angular Development Plugin for Claude Code

A comprehensive Angular development toolkit for Claude Code that includes both **automatic Skills** and **manual Slash Commands** to scaffold and automate Angular projects.

## What This Plugin Does

This plugin extends Claude Code with two types of tools:

### 1. Skills (Automatic)
Claude automatically uses these when you ask for Angular help:
- **Scaffold complete Angular applications** with routing, guards, and best practices
- **Generate components, services, and modules** with proper structure
- **Create authentication guards and HTTP interceptors**
- **Initialize git repositories** with Angular-specific .gitignore
- **Set up organized folder architecture** (core, shared, features)

### 2. Slash Commands (Manual)
Explicitly invoke these commands for precise control:
- `/create-angular-app [name]` - Create a full Angular app with best practices
- `/ng-component [path/name]` - Generate a new component
- `/ng-service [path/name]` - Generate a new service
- `/ng-module [name]` - Generate a new feature module

## How It Works

### Skills (Automatic)
Just ask Claude naturally and it will automatically use the toolkit:

```
"Create an Angular app called my-dashboard"
"Generate a user service"
"Add an authentication guard"
"Create a products feature module"
```

### Slash Commands (Manual)
Type the command directly for explicit control:

```
/create-angular-app my-dashboard
/ng-component features/user/components/profile
/ng-service core/services/auth
/ng-module admin --routing
```

## Installation

### Recommended: Plugin Installation

The easiest way to install is using Claude Code's plugin system:

```bash
/plugin install james-toolkit@github:YOUR-USERNAME/james-toolkit
```

That's it! The plugin is now installed globally. All Skills and Commands are immediately available.

**Manage your installation:**
- `/plugin` - Open plugin manager to enable/disable
- `/plugin uninstall james-toolkit` - Remove the plugin
- Type `/help` to see all available commands

### Alternative: Manual Installation

#### For Individual Use (Global)
```bash
git clone https://github.com/YOUR-USERNAME/james-toolkit.git
cp -r james-toolkit/skills/james-toolkit ~/.claude/skills/
cp james-toolkit/commands/* ~/.claude/commands/
rm -rf james-toolkit
```

#### For Team Projects (Per-Project)
```bash
git clone https://github.com/YOUR-USERNAME/james-toolkit.git temp
mkdir -p .claude
cp -r temp/skills .claude/
cp -r temp/commands .claude/
rm -rf temp
git add .claude
git commit -m "Add james-toolkit for Angular development"
```

## Customizing the Toolkit

### Adding Custom Skills
Edit `skills/james-toolkit/SKILL.md`:

1. Add new capabilities in the **Capabilities** section
2. Provide bash commands or instructions for Claude to follow
3. Update the **description** in the frontmatter so Claude knows when to use it

### Adding Custom Commands
Create a new markdown file in `commands/`:

1. Create a file like `ng-pipe.md`
2. Add frontmatter with description and argument hints
3. Write the command instructions for Claude

Example:
```markdown
---
description: Generate an Angular pipe
argument-hint: [pipe-name]
---

Generate a new Angular pipe named $1:

```bash
ng generate pipe $1
```

Provide guidance on using the pipe in templates.
```

### Publishing Your Modified Version
1. Fork this repository
2. Make your changes to skills/ or commands/
3. Update version in `.claude-plugin/plugin.json`
4. Push to your fork
5. Users can install with: `/plugin install your-fork@github:YOUR-USERNAME/james-toolkit`

## Contributing

Have ideas for new Angular workflows or commands?

1. Fork this repository
2. Add your workflow to `skills/james-toolkit/SKILL.md` or create a new command in `commands/`
3. Test it with Claude Code
4. Update version in `.claude-plugin/plugin.json` following [semantic versioning](https://semver.org/)
5. Submit a pull request with description of changes

## Requirements

- **Node.js** (v18 or higher recommended)
- **npm** or **yarn**
- **Angular CLI** - Install globally: `npm install -g @angular/cli`
- **Git** (for repository initialization features)

## License

MIT License - feel free to modify and share!

## Questions?

Open an issue on GitHub or contribute improvements via pull request.
