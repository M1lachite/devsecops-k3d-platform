# devsecops-k3d-platform
A DevSecOps lab focused on securing software supply chain — from CI/CD pipelines to K3d runtime - against vulnerabilities and breaches.

🚧 Project in development 🚧

Structure:

```
devsecops-lab-platform/
├── app/                 # Demo application source code
├── ops/                 # Operational tooling and management pane
│   ├── jenkins/         # Jenkins Configuration as Code (JCasC) with Dockerfile
│   └── wazuh/           # Wazuh Configuration with Dockerfile
├── infra/               # Infrastructure as Code (IaC)
│   └── k3d/             # K3d cluster configuration
├── scripts/             # Automation scripts
└── docs/                # Documentation
```