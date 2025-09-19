# GAWG - ICOMOS Website Pantheon to GitHub Sync Repository

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Repository Purpose
GAWG (Estonian: "ICOMOS lehe imemine Pantheonist otse Githubi") is a repository for syncing the ICOMOS website content from Pantheon hosting platform directly to GitHub. This repository serves as a bridge for website content management and deployment workflows.

## Working Effectively

### Initial Repository Setup
This repository is intentionally minimal and serves as a sync/mirroring tool rather than a traditional development project:

- Clone the repository: `git clone https://github.com/liikane/GAWG.git`
- Navigate to repository: `cd GAWG`
- Check current status: `git status`
- Verify repository structure: `ls -la`

### Repository Structure
The repository contains:
- `.gitattributes` - Git configuration for text file handling (LF normalization)
- `.github/` - Directory for GitHub-specific configurations and workflows
- History of removed Pantheon mirroring workflows (see commit history)

### Build and Test Operations
**CRITICAL**: This repository does not contain traditional build processes as it serves as a content sync repository.

- **No build process required** - This is a git-based content synchronization repository
- **No test suite exists** - Content validation would be done on the target Pantheon site
- **No package managers** - No `package.json`, `composer.json`, or similar dependency files
- **No compilation needed** - Content is synced as-is between Pantheon and GitHub

### Git Operations
Standard git operations work as expected:
- `git fetch --all` - Fetch all branches and remotes
- `git branch -a` - List all branches (local and remote)
- `git log --oneline --all` - View commit history across branches
- `git status` - Check working directory status

**Timing**: Git operations typically complete within 5-10 seconds.

### Content Sync Workflow
The repository previously contained GitHub Actions workflows for:
- `pantheon-lisa.yml` - Pantheon to GitHub sync for Lisa site
- `sync-pantheon.yml` - General Pantheon to GitHub synchronization

These workflows were removed but may need to be recreated for active syncing.

## Validation

### Repository Validation
After making changes to this repository:
1. **Always verify git status**: `git status` to ensure clean working directory
2. **Check file permissions**: `ls -la` to verify proper file permissions
3. **Validate GitHub Actions**: If adding workflows, check `.github/workflows/` syntax
4. **Test sync functionality**: If recreating sync workflows, validate with dry-run first

### Content Validation
Since this repository syncs content from Pantheon:
1. **Verify source connectivity**: Ensure Pantheon site is accessible
2. **Check authentication**: Validate SSH keys and access tokens if workflows require them
3. **Test sync direction**: Confirm whether sync is Pantheon→GitHub, GitHub→Pantheon, or bidirectional

## Common Tasks

The following are outputs from frequently run commands. Reference them instead of viewing, searching, or running bash commands to save time.

### Repository Root Structure
```bash
ls -la
total 20
drwxr-xr-x 4 runner runner 4096 Sep 19 19:31 .
drwxr-xr-x 3 runner runner 4096 Sep 19 19:28 ..
drwxrwxr-x 7 runner runner 4096 Sep 19:32 .git
-rw-rw-r-- 1 runner runner   66 Sep 19 19:28 .gitattributes
drwxrwxr-x 2 runner runner 4096 Sep 19 19:32 .github
```

### Git Status Output
```bash
git status
On branch copilot/fix-2
Your branch is up to date with 'origin/copilot/fix-2'.
nothing to commit, working tree clean
```

### Git Branch Information
```bash
git branch -a
* copilot/fix-2
  remotes/origin/copilot/fix-2
```

### Repository History
```bash
git log --oneline --all
2f5b81e Initial plan  
f0f92e9 Remove Pantheon mirroring workflows
```

### Working with Sync Workflows
If recreating the removed Pantheon sync workflows:
1. Create workflow files in `.github/workflows/`
2. Configure Pantheon SSH authentication
3. Set up proper git sync logic with `git fetch` and `git push`
4. **NEVER CANCEL**: Sync operations may take 10-30 minutes depending on content size
5. Use timeout values of 45+ minutes for sync workflows

### Repository Maintenance
- **Check repository size**: `du -sh .git` (sync repositories can grow large)
- **Clean git history if needed**: Consider periodic cleanup of large sync histories
- **Monitor workflow runs**: Check GitHub Actions for sync status and errors

### File Operations
- **Always use LF line endings**: Repository configured for `* text=auto` in `.gitattributes`
- **Preserve file permissions**: Especially important for web content files
- **Handle binary files properly**: Images, documents should be tracked with LFS if large

## Troubleshooting

### Common Issues
1. **Large repository size**: Pantheon sites can be large; monitor `.git` directory size
2. **Sync conflicts**: Handle merge conflicts carefully when syncing bidirectionally  
3. **Authentication failures**: Verify SSH keys and tokens for Pantheon access
4. **Workflow timeouts**: Use generous timeout values (45+ minutes) for content sync

### Emergency Recovery
- **Reset to last known good state**: `git reset --hard HEAD~1` (if safe to do so)
- **Force sync from Pantheon**: May need to force push if content diverges significantly
- **Contact Pantheon support**: For authentication or access issues

## Important Notes
- **This is a sync repository, not a development repository**
- **Content changes should typically be made on Pantheon, not directly in GitHub**
- **Always coordinate with ICOMOS content managers before making sync configuration changes**
- **Monitor sync frequency to avoid overwhelming Pantheon or GitHub API limits**

## Repository Metadata
- **Primary branch**: `master`
- **Language**: Repository content language varies (Estonian ICOMOS content)
- **Created**: 2025-09-19
- **Purpose**: Content synchronization between Pantheon and GitHub platforms
- **Active workflows**: None currently (previously removed)