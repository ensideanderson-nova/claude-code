# Oncall Issue Triage Workflow

## Overview
This workflow identifies and labels critical blocking issues that require oncall attention using GroqCloud AI analysis.

## Requirements
- **Groq API Key**: This workflow requires a valid `GROQ_API_KEY` secret
- The workflow uses Groq's Llama models to analyze issues and determine which ones need oncall attention
- Free tier available at https://console.groq.com

## Current Status
✅ **Automatic triggers are ENABLED** - Groq provides free API access with generous rate limits.

## Configuration

### Active Triggers
- **Push to test branch**: `copilot/update-oncall-triage-workflow-yet-again` (temporary for testing only)
- **Scheduled runs**: Every 6 hours via cron
- **Manual trigger**: `workflow_dispatch` - Can be triggered manually from GitHub Actions UI

### Implementation
- Uses **Bun** runtime for fast TypeScript execution
- Script: `scripts/oncall-triage-groq.ts`
- AI Model: **Llama 3.3 70B Versatile** via GroqCloud API
- Timeout: 15 minutes

## How to Setup

1. Get a free Groq API key from https://console.groq.com
2. Add the API key as a secret in your repository:
   - Go to Settings > Secrets and variables > Actions
   - Click "New repository secret"
   - Name: `GROQ_API_KEY`
   - Value: Your Groq API key

## Troubleshooting

### "GROQ_API_KEY not found" Error
This error occurs when the Groq API key secret is not configured. To resolve:
1. Get a free API key from https://console.groq.com
2. Add it as a repository secret named `GROQ_API_KEY`

### Workflow Not Running
- Check that the workflow trigger conditions are met
- Verify the `GROQ_API_KEY` secret is set and valid
- Check GitHub Actions logs for detailed error messages

### Rate Limiting
Groq provides generous free tier limits. If you hit rate limits:
- The workflow will retry failed requests
- Consider reducing the schedule frequency (e.g., every 12 hours instead of 6)

## Manual Execution
To manually trigger the workflow:
1. Go to the Actions tab in GitHub
2. Select "Oncall Issue Triage" workflow
3. Click "Run workflow"
4. Select the branch and click "Run workflow"

## How It Works

1. **Fetches Issues**: Gets all open issues updated in the last 3 days
2. **Quick Filters**: Checks if issues are bugs and have ≥50 engagements (comments + reactions)
3. **AI Analysis**: Uses Groq's Llama model to determine if issues are truly blocking
4. **Labels Issues**: Adds "oncall" label to critical blocking issues
5. **Reports Summary**: Outputs detailed summary of all analyzed issues
