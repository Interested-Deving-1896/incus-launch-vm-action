# incus-launch-vm-action

[![AI agent ready](https://img.shields.io/badge/AI_agent-ready-2ea44f?style=flat-square)](https://github.com/Interested-Deving-1896/fork-sync-all/blob/main/DOCS/ai-agent-badges.md)
[![Open in Codex](https://img.shields.io/badge/Open_in-Codex-000000?style=flat-square&logo=openai&logoColor=white)](https://chatgpt.com/codex)
[![Open in Claude Code](https://img.shields.io/badge/Open_in-Claude_Code-d97757?style=flat-square&logo=anthropic&logoColor=white)](https://claude.ai/code)
[![Open in GitHub Copilot](https://img.shields.io/badge/Open_in-GitHub_Copilot-181717?style=flat-square&logo=githubcopilot&logoColor=white)](https://github.com/copilot)
[![Open in Cursor](https://img.shields.io/badge/Open_in-Cursor-111111?style=flat-square)](https://cursor.com/agents)
[![Use with Gemini CLI](https://img.shields.io/badge/Use_with-Gemini_CLI-4285f4?style=flat-square&logo=googlegemini&logoColor=white)](https://github.com/google-gemini/gemini-cli)
[![KDE Eco](https://img.shields.io/badge/KDE%20Eco-certified-brightgreen?logo=kde&logoColor=white&style=flat-square)](https://eco.kde.org/) [![Blue Angel](https://img.shields.io/badge/Blue%20Angel-DE--UZ%20215-0055a4?style=flat-square)](https://www.blauer-engel.de/en/certification/criteria)




<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/incus-launch-vm-action.git
cd incus-launch-vm-action
```

## Usage


To use the Action, include it in your workflow file:

```yaml
jobs:
  setup_incus:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup Incus and Connect to Remote Server
        uses: nubificus/incus-launch-vm-action@v1
        with:
          vm_name: 'test-vm'
          vm_description: 'New VM to run tests'
          incus_remote: 'my-incus-remote'
          incus_image: 'images:ubuntu/22.04/cloud'
          cpu_cores: '2'
          memory: '2' # size in GiB
          disk_size: '10' # size in GiB
          incus_profile: 'default'
          incus_project: 'default'
          cleanup: 'true'
          snapshot: 'true'
```

Additionally to `cleanup` input that is passed at the start of the action, a ENV variable (`CLEANUP_OVERRIDE`) can be set during
the execution of the workflow to override the behavior defined in the input. This allows the user to retain the VM if a specific
condition is met during the next steps of the workflow.

```yaml
    - name: Run ctr tests
      id: test-ctr
      run: |
        export VM_NAME=${{ env.INCUS_CLUSTER }}:${{ env.VM_NAME }}
        export TEST_CMD="cd /root/develop/urunc && PATH=/usr/local/go/bin:$PATH make test_ctr"
        if ! incus exec "$VM_NAME" -- sh -c "$TEST_CMD"; then
          echo "Test failed"
          echo "CLEANUP_OVERRIDE=false" >> $GITHUB_ENV
          exit 1
        fi
```

## Configuration

<!-- Document configuration options here. This section is yours — the AI will not modify it. -->

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/incus-launch-vm-action`](https://github.com/Interested-Deving-1896/incus-launch-vm-action) and mirrored through:

```
Interested-Deving-1896/incus-launch-vm-action  ──►  OpenOS-Project-OSP/incus-launch-vm-action  ──►  OpenOS-Project-Ecosystem-OOC/incus-launch-vm-action
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
| Contributor | Commits |
|---|---|
| [@Interested-Deving-1896](https://github.com/Interested-Deving-1896) | 24 |
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream influences recorded._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## Accessibility

<!-- AI:start:accessibility -->
No  was found when this README was generated. Check the
[Actions tab](https://github.com/Interested-Deving-1896/incus-launch-vm-action/actions) for repository-specific checks, and document an
accessibility status only when a report or workflow provides evidence for it.




See the [W3C Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/)
for accessibility guidance.
<!-- AI:end:accessibility -->

## License

<!-- AI:start:license -->
[Apache-2.0](https://github.com/Interested-Deving-1896/incus-launch-vm-action/blob/main/LICENSE) © 2026 [Interested-Deving-1896](https://github.com/Interested-Deving-1896)
<!-- AI:end:license -->
