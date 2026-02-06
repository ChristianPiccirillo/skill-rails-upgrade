# ⚙️ skill-rails-upgrade - Effortless Rails Upgrade Assessments

[![Download Here](https://img.shields.io/badge/Download%20Now-From%20Releases-blue)](https://github.com/ChristianPiccirillo/skill-rails-upgrade/releases)

## 📖 About the Skill

This tool, designed for both Claude Code and OpenCode, helps you upgrade Rails applications smoothly. It performs a thorough analysis and provides clear guidance on what to do next.

## 🤔 What It Does

When you run this skill within your Rails project, it:

1. Confirms you are in a Rails application.
2. Identifies your current Rails version.
3. Retrieves the latest Rails release from GitHub.
4. Determines the type of upgrade needed (patch, minor, major).
5. Accesses the official Rails upgrade guide.
6. Gathers configuration differences from railsdiff.org.
7. Creates a detailed upgrade summary, including a complexity rating.

## ⚙️ Prerequisites

Before you begin, ensure you have the following:

- [GitHub CLI](https://cli.github.com/) (referred to as `gh`) installed on your computer and authenticated.

## 🚀 Getting Started

To get started with the Rails upgrade skill, follow these steps carefully.

### 📥 Download & Install

**Step 1:** Visit this page to download: [GitHub Releases](https://github.com/ChristianPiccirillo/skill-rails-upgrade/releases)

**Step 2:** Choose the latest version and download the files to your computer. Make sure to extract them if they’re in a compressed format.

### 🛠️ Installation for Claude Code

Follow these instructions for Claude Code:

1. First, create the skills directory. If it doesn't exist yet, run:
   ```bash
   mkdir -p ~/.claude/skills
   ```

2. Next, clone or copy the skill to the skills directory. You can do this by running:
   ```bash
   git clone https://github.com/robzolkos/skill-rails-upgrade.git ~/.claude/skills/rails-upgrade
   ```

   If you prefer to copy it manually, you can do so with:
   ```bash
   cp -r /path/to/skill-rails-upgrade ~/.claude/skills/
   ```

### ⚙️ Execution

1. Open a terminal window.
2. Navigate to your Rails project directory.
3. To run the skill, execute:
   ```bash
   claude load rails-upgrade
   ```

### 📊 Understanding Your Result

After running the skill, it will provide a summary of the upgrade process. Pay attention to:

- Upgrade type: This will help you understand the level of changes required.
- Official upgrade guide: Follow this guide for detailed instructions on the next steps you need to take.
- Configuration diffs: Use this information to adjust your application settings accordingly.
- Complexity rating: This gives you an overview of how challenging the upgrade may be.

## 🔧 Features

- Simple and intuitive interface.
- Comprehensive upgrade assessments.
- Easy access to the latest Rails updates.
- Clear documentation for non-technical users.

## 📚 Additional Resources

For more information about Rails upgrades, check out the following resources:

- [Ruby on Rails Guides](https://guides.rubyonrails.org/)
- [RailsDiff for Configuration Diffs](https://railsdiff.org/)
- [GitHub CLI Documentation](https://cli.github.com/manual/)

## ❓ Frequently Asked Questions

**Q: Can I use this skill on any Rails version?**  
A: This skill is designed to work with most Rails versions. However, make sure to check compatibility before running it.

**Q: What if I face issues?**  
A: Visit the issue tracker on the GitHub repository to report any problems or seek assistance.

**Q: Is this skill free?**  
A: Yes, the skill is open-source and free to use.

### 📬 Contact

For further support, feel free to reach out via the GitHub repository comments. We appreciate your feedback and aim to improve your upgrade experience.

## 🔁 Check for Updates

Stay up to date by checking for updates regularly. New features and improvements are added continuously.

Remind yourself to visit this page to download updates: [GitHub Releases](https://github.com/ChristianPiccirillo/skill-rails-upgrade/releases)