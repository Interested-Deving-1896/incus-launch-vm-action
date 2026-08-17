# incus-launch-vm-action

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/incus-launch-vm-action) [![KDE Eco](https://img.shields.io/badge/KDE%20Eco-certified-brightgreen?logo=kde&logoColor=white&style=flat-square)](https://eco.kde.org/) [![Blue Angel](https://img.shields.io/badge/Blue%20Angel-DE--UZ%20215-0055a4?style=flat-square)](https://www.blauer-engel.de/en/certification/criteria) [![Energy](https://api.green-coding.io/v1/ci/badge/get?repo=Interested-Deving-1896%2Fincus-launch-vm-action&branch=main&workflow=eco-audit.yml)](https://metrics.green-coding.io/ci-index.html)


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
_Contributors pending._
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
This repo uses automated accessibility auditing via `check-accessibility.yml`.

Checks include: CODEOWNERS ownership coverage, README screen-reader compatibility,
WCAG 2.1 AA HTML compliance, audio overview (espeak-ng), and Braille output (liblouis).




Run the [Check Accessibility](https://github.com/Interested-Deving-1896/incus-launch-vm-action/actions/workflows/check-accessibility.yml)
workflow to generate the first report and accessibility artifacts.
See [DOCS/accessibility.md](https://github.com/Interested-Deving-1896/incus-launch-vm-action/blob/main/DOCS/accessibility.md) for the full reference.
<!-- AI:end:accessibility -->

## License

<!-- AI:start:license -->
[Apache-2.0](https://github.com/Interested-Deving-1896/incus-launch-vm-action/blob/main/LICENSE) © 2026 [Interested-Deving-1896](https://github.com/Interested-Deving-1896)
<!-- AI:end:license -->
