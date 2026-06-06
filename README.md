# Screenshots

## 1. Helm Version Verification

![Helm Version](screenshots/Helm-version-output.png)

---

## 2. Helm Chart Creation

![Chart Creation](screenshots/Chart-creation.png)

---

## 3. Helm Chart Structure

![Folder Structure](screenshots/Folder-structure.png)

---

## 4. Chart.yaml Configuration

![Chart YAML](screenshots/Chart.yaml.png)

---

## 5. Helm Chart Validation

![Validate Chart](screenshots/Validate-Chart.png)

---

## 6. Package the Helm Chart

![Package Chart](screenshots/Package-the-Chart.png)

---

## 7. Simulated Installation

![Simulate Installation](screenshots/Simulate-Installation.png)

---

## 8. Modify Values and Render Again

![Render Again](screenshots/RenderAgain.png)

---

## 9. Simulated Upgrade

![Simulate Upgrade](screenshots/Simulate-Upgrade.png)

---

## 10. Rollback Demonstration

![Rollback Demonstration](screenshots/Rollback-Demonstration.png)

---

## 11. Rendered Kubernetes Manifest

The generated manifest file:

```text
rendered.yaml
```

contains the Kubernetes resources rendered from the Helm chart using:

```powershell
helm template demo-release mywebapp > rendered.yaml
```

---