# GitHub Actions Automation Suite
This repository centralizes reusable GitHub Action workflows designed to automate your development lifecycle and enforce standard branching policies.

**Key Features:**
- **Automated Flow:** Automatically creates or updates a Pull Request from `develop` to `master` upon every merge into the `develop` branch.
- **Release Management:** On merging to `master`, the system handles **version bumping**, generates **Git tags**, and publishes a **GitHub Release** with automated release notes.

Streamline your CI/CD and keep your branches in sync effortlessly.

```mermaid
flowchart LR
    feat["feature/**"]
    dev["develop"]
    pr(["Release PR\nchore: release X.X.X"])
    main["main"]
    rel[/"GitHub Release vX.X.X"/]

    feat -->|"merged"| dev
    dev -- "auto-created on push" --> pr
    pr -->|"manually merged"| main
    main -- "auto: bump patch version\ntag vX.X.X\npublish release" --> rel
    main -->|"auto: force-sync"| dev
```
