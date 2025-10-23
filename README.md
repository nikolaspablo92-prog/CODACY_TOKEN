# secret-action

This is a template repository that contains a workflow used in the "[Storing your secrets safely](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely)" exercise on GitHub Docs! ✨ 🔐 ✨

## Codacy Integration

This repository includes automated Codacy code analysis in the CI workflow. To enable it:

1. **Add the CODACY_TOKEN secret to your repository:**
   - Go to `Settings` → `Secrets and variables` → `Actions` → `New repository secret`
   - Name: `CODACY_TOKEN`
   - Value: Your Codacy API token (get it from your Codacy project settings)

2. **The workflow will automatically run Codacy analysis on:**
   - Push events to `main` or `develop` branches
   - Pull requests targeting `main` branch
   - Linux runners only (for Docker compatibility)

3. **View results:**
   - Check the `Actions` tab in your repository
   - Look for the `Run Codacy Analysis CLI` step in the build job
   - Review any issues found in your Codacy dashboard
