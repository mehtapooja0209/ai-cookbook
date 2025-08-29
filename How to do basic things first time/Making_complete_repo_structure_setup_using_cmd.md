# Creating Your AI Cookbook Repository Structure with GitHub Codespaces

This guide will help you set up your repository structure using GitHub Codespaces - no installations or command line experience required!

## What is GitHub Codespaces?

GitHub Codespaces gives you a complete development environment in your browser. Think of it as a temporary computer that lives in the cloud, connected directly to your GitHub repository.

## Step-by-Step Instructions

### Step 1: Create Your Repository

1. Go to [GitHub.com](https://github.com) and sign in to your account
2. Click the "+" icon in the top-right corner
3. Select "New repository"
4. Name your repository (e.g., "ai-cookbook")
5. Add a description (optional): "A collection of AI/LLM techniques and best practices"
6. Choose "Public" or "Private" visibility
7. Check "Add a README file"
8. Click "Create repository"

### Step 2: Open GitHub Codespaces

1. Navigate to your new repository
2. Look for the green "Code" button near the top of the page
3. Click the "Code" button
4. Select the "Codespaces" tab
5. Click "Create codespace on main"
6. Wait while GitHub sets up your codespace (this may take a minute)
   - You'll see a loading screen with a progress indicator
   - When complete, you'll see a development environment in your browser

### Step 3: Create Your Directory Structure

Once your codespace is ready, you'll see a code editor with a terminal at the bottom. The terminal is where we'll create our directory structure.

1. Click on the terminal area at the bottom of the screen
2. Copy the command below (this creates the default AI Cookbook structure):

```bash
mkdir -p prompts/{basics,advanced,templates,examples} llm-guides/{claude,gpt,open-source,comparisons} agents/{tutorials,architectures,use-cases,debugging} context-engineering/{memory-management,rag-systems,embeddings,vector-databases} integrations/{openrouter,api-setup,cost-optimization,rate-limiting} code-snippets/{python,javascript,prompts,configs} best-practices/{security,performance,error-handling,testing} experiments/{failed,successful,ongoing} resources/{tools,links,papers} && echo "# AI Cookbook" > README.md && for dir in prompts llm-guides agents context-engineering integrations code-snippets best-practices experiments resources; do echo "# ${dir^}" > $dir/README.md; for subdir in $dir/*/; do subdir_name=$(basename "$subdir"); echo "# ${subdir_name^}" > "$subdir/README.md"; done; done && git add . && git commit -m "Create repository structure" && git push
```

3. Paste it into the terminal (right-click and select paste, or use Ctrl+V / Cmd+V)
4. Press Enter to run the command
5. Wait for the command to complete (you'll see a message about files being added and pushed)

### Step 4: Customize Your Structure (Optional)

Want to create your own custom directory structure instead? Here's how:

1. In the terminal, create your main directories:

```bash
mkdir -p your-folder-name1 your-folder-name2 your-folder-name3
```

2. Create subdirectories:

```bash
mkdir -p your-folder-name1/subfolder1 your-folder-name1/subfolder2
mkdir -p your-folder-name2/subfolder1 your-folder-name2/subfolder2
```

3. Create README files:

```bash
echo "# Your Folder Name 1" > your-folder-name1/README.md
echo "# Subfolder 1" > your-folder-name1/subfolder1/README.md
```

4. Save your changes to GitHub:

```bash
git add .
git commit -m "Create custom directory structure"
git push
```

### Step 5: View Your Repository Structure

1. Close the codespace by clicking on the menu in the bottom-left corner (three horizontal lines)
2. Select "Codespaces" from the menu
3. Click "Close Current Codespace"
4. Go back to your repository on GitHub
5. Refresh the page
6. You should now see all your folders and files!

## Example: Creating a Custom AI Research Structure

Here's an example of creating a custom structure for AI research:

```bash
# Create main directories
mkdir -p research-papers tools-and-libraries experiments blog-posts courses

# Create subdirectories
mkdir -p research-papers/summaries research-papers/implementations
mkdir -p tools-and-libraries/python tools-and-libraries/javascript
mkdir -p experiments/successful experiments/failed
mkdir -p blog-posts/technical blog-posts/tutorials
mkdir -p courses/completed courses/in-progress

# Create README files
echo "# AI Research Repository" > README.md
echo "# Research Papers" > research-papers/README.md
echo "# Tools and Libraries" > tools-and-libraries/README.md
echo "# Experiments" > experiments/README.md
echo "# Blog Posts" > blog-posts/README.md
echo "# Courses" > courses/README.md

# Add subdirectory READMEs
echo "# Paper Summaries" > research-papers/summaries/README.md
echo "# Paper Implementations" > research-papers/implementations/README.md
echo "# Python Libraries" > tools-and-libraries/python/README.md
echo "# JavaScript Libraries" > tools-and-libraries/javascript/README.md
echo "# Successful Experiments" > experiments/successful/README.md
echo "# Failed Experiments" > experiments/failed/README.md
echo "# Technical Posts" > blog-posts/technical/README.md
echo "# Tutorials" > blog-posts/tutorials/README.md
echo "# Completed Courses" > courses/completed/README.md
echo "# Courses In Progress" > courses/in-progress/README.md

# Save changes to GitHub
git add .
git commit -m "Create custom AI research structure"
git push
```

## Troubleshooting

### "Permission denied" error
- Make sure you're in the correct repository
- Try running `git config --global --add safe.directory "*"` and then try again

### "Failed to push some refs" error
- Run `git pull --rebase` first
- Then try `git push` again

### Codespace is slow or unresponsive
- Try refreshing the page
- Close and reopen the codespace

## Next Steps

1. Start adding content to your repository
2. Explore your folders in the file explorer on the left side of the codespace
3. Create new files by right-clicking on folders and selecting "New File"
4. Edit your README.md files to add more information

Congratulations! You've successfully set up your repository structure using GitHub Codespaces!
