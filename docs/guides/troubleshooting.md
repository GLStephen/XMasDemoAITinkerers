# Troubleshooting

## Authentication Issues

### "401 Unauthorized" from Atlassian API

**Symptoms:**
- MCP calls fail with 401 error
- "Invalid credentials" message

**Solutions:**
1. Verify API token hasn't expired
2. Check email matches Atlassian account
3. Regenerate API token at https://id.atlassian.com/manage-profile/security/api-tokens
4. Ensure `.claude/mcp.json` has correct values

### "403 Forbidden"

**Symptoms:**
- Can authenticate but operations fail

**Solutions:**
1. Verify you have permissions in the Jira project
2. Check Confluence space permissions
3. Some operations require admin access

## Confluence Sync Issues

### "A page with this title already exists"

**Cause:** File's sync footer was removed but page exists in Confluence.

**Solutions:**
1. Add footer back: `[//]: # (confluence-sync: pageId=XXXXX, lastSyncedAt=...)`
2. Or delete the Confluence page and re-sync

### Sync Creates Duplicate Pages

**Cause:** Footer comment lost during file editing.

**Solution:** Check that files retain their footer comments after editing.

### Images Not Appearing

**Cause:** MCP doesn't support image upload.

**Workaround:**
- Upload images directly to Confluence
- Reference via Confluence URLs in markdown

## Jira Issues

### "Project not found"

**Solutions:**
1. Verify project key in skill config
2. Check you have access to the project
3. Project keys are case-sensitive

### Custom Fields Not Working

**Symptoms:**
- Tickets created without expected fields

**Solutions:**
1. Verify custom field IDs for your Jira instance
2. Field IDs differ between instances (customfield_XXXXX)
3. Use Jira API to discover field IDs:
   ```
   GET /rest/api/3/field
   ```

### Epic Link Not Set

**Cause:** Parent field syntax may vary by Jira version.

**Solution:** Check if your instance uses `parent.key` or `customfield_10014` for epic links.

## Rate Limiting

### "429 Too Many Requests"

**Symptoms:**
- Operations fail mid-sync
- Rate limit errors

**Solutions:**
1. Wait a few minutes and retry
2. Sync smaller batches
3. Atlassian limit is ~120 requests/minute

## General

### MCP Server Not Starting

**Solutions:**
1. Check `npx` is available
2. Verify `.claude/mcp.json` syntax is valid JSON
3. Try running the MCP command manually to see errors

### Changes Not Reflected

**Solutions:**
1. Claude Code may need restart after config changes
2. Clear any cached state
3. Verify files are saved before operations
