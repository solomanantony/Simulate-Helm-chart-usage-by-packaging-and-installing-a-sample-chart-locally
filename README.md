# Helm Chart Simulation Project

## Overview

This project demonstrates the usage of Helm for packaging, rendering, and managing Kubernetes application deployments without requiring a live Kubernetes cluster. The exercise focuses on creating a sample Helm chart, validating it, rendering Kubernetes manifests, packaging the chart, and simulating installation, upgrade, and rollback operations using Helm commands.

## Objectives

- Create a sample Helm chart using Helm CLI.
- Understand Helm chart structure and components.
- Validate Helm charts using linting.
- Render Kubernetes manifests locally using Helm templates.
- Package Helm charts for distribution.
- Simulate installation and upgrade operations using dry-run.
- Demonstrate rollback command syntax and limitations without a Kubernetes cluster.

---

## Prerequisites

- Windows Operating System
- Helm 3.x Installed
- PowerShell or Command Prompt
- Visual Studio Code (Optional)

---

## Project Structure

```text
HELMDEMO
│
├── mywebapp
│   ├── charts
│   ├── templates
│   │   ├── tests
│   │   │   └── test-connection.yaml
│   │   ├── _helpers.tpl
│   │   ├── deployment.yaml
│   │   ├── hpa.yaml
│   │   ├── httproute.yaml
│   │   ├── ingress.yaml
│   │   ├── NOTES.txt
│   │   ├── service.yaml
│   │   └── serviceaccount.yaml
│   ├── .helmignore
│   ├── Chart.yaml
│   └── values.yaml
│
├── screenshots
│   ├── Chart-creation.png
│   ├── Chart.yaml.png
│   ├── Folder-structure.png
│   ├── Helm-version-output.png
│   ├── Package-the-Chart.png
│   ├── RenderAgain.png
│   ├── Rollback-Demonstration.png
│   ├── Simulate-Installation.png
│   ├── Simulate-Upgrade.png
│   └── Validate-Chart.png
│
├── mywebapp-0.1.0.tgz
├── rendered.yaml
└── README.md
```

---

## Step 1: Verify Helm Installation

```powershell
helm version
```

### Output

```text
version.BuildInfo{Version:"v3.x.x", ...}
```

Screenshot:
- Helm-version-output.png

---

## Step 2: Create a Helm Chart

```powershell
helm create mywebapp
```

### Output

```text
Creating mywebapp
```

Screenshot:
- Chart-creation.png

---

## Step 3: Validate Chart Structure

```powershell
tree /F
```

Screenshot:
- Folder-structure.png

---

## Step 4: Review Chart Metadata

Open:

```powershell
notepad mywebapp\Chart.yaml
```

Screenshot:
- Chart.yaml.png

---

## Step 5: Validate the Helm Chart

```powershell
helm lint mywebapp
```

### Output

```text
1 chart(s) linted, 0 chart(s) failed
```

Screenshot:
- Validate-Chart.png

---

## Step 6: Render Kubernetes Manifests

```powershell
helm template demo-release mywebapp
```

Save output:

```powershell
helm template demo-release mywebapp > rendered.yaml
```

Generated file:

```text
rendered.yaml
```

Screenshot:
- Rendered manifest output

---

## Step 7: Package the Chart

```powershell
helm package mywebapp
```

### Output

```text
Successfully packaged chart and saved it to:
mywebapp-0.1.0.tgz
```

Generated File:

```text
mywebapp-0.1.0.tgz
```

Screenshot:
- Package-the-Chart.png

---

## Step 8: Simulate Installation

```powershell
helm install demo-release mywebapp --dry-run --debug
```

Purpose:
- Simulates chart installation.
- Displays generated manifests.
- No resources are created.

Screenshot:
- Simulate-Installation.png

---

## Step 9: Modify Values

Edit:

```yaml
replicaCount: 3
```

File:

```text
mywebapp/values.yaml
```

Render again:

```powershell
helm template demo-release mywebapp
```

Verify:

```yaml
replicas: 3
```

Screenshot:
- RenderAgain.png

---

## Step 10: Simulate Upgrade

```powershell
helm upgrade demo-release mywebapp --dry-run --debug
```

Purpose:
- Simulates an application upgrade.
- Shows updated manifests before deployment.

Screenshot:
- Simulate-Upgrade.png

---

## Step 11: Rollback Demonstration

Command:

```powershell
helm rollback demo-release 1 --dry-run
```

### Result

```text
Error: kubernetes cluster unreachable
```

### Explanation

Helm rollback requires release history stored within a Kubernetes cluster. Since this project was executed without a Kubernetes cluster, rollback could not be performed. The command syntax was demonstrated for educational purposes.

Screenshot:
- Rollback-Demonstration.png

---

## Deliverables

### Source Helm Chart

```text
mywebapp/
```

### Packaged Helm Chart

```text
mywebapp-0.1.0.tgz
```

### Generated Manifest

```text
rendered.yaml
```

### Documentation

```text
README.md
```

### Screenshots

Stored under:

```text
screenshots/
```

---

## Conclusion

This project successfully demonstrates Helm chart creation, validation, manifest rendering, packaging, installation simulation, and upgrade simulation without requiring a Kubernetes cluster. Helm's template and dry-run capabilities provide an effective way to understand Helm workflows and chart behavior in a local development environment.