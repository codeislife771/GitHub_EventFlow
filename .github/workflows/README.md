# GitHub Actions Workflow Examples

This project demonstrates how to use **GitHub Actions** with different events in a Git workflow.  
It is built as a learning exercise to understand **event-driven automation** in CI/CD pipelines.

---

## 📌 Project Goal
- Learn how GitHub Actions workflows are triggered by different events.
- Practice separating workflows into multiple files for better organization.
- Get familiar with common Git events: `push`, `pull_request`, `review`, and more.
- Build a clear mental model of how automation fits into a development process.

---

## 📂 Project Structure
All workflows are stored in the `.github/workflows/` folder:

- **main.yml** → Runs on push to `main` branch.  
- **feature.yml** → Runs on push to any `feature-*` branch.  
- **pr_opened.yml** → Runs when a Pull Request is opened.  
- **pr_closed.yml** → Runs when a Pull Request is closed or merged.  
- **pr_synchronize.yml** → Runs when new commits are pushed to an open Pull Request.  
- **pr_review.yml** → Runs when a Pull Request review is submitted.  

Each workflow contains a simple job that prints a message with `echo` to confirm the event.

---

## ▶️ Manual Runs (`workflow_dispatch`)
You can run any workflow **manually** from the Actions tab by adding:
```yaml
on:
  workflow_dispatch:
```
This is great for learning/testing without creating a push/PR event.

---

## 🚀 How to Use

1. **Clone or fork this repository.**
   ```bash
   git clone <your-repo-url>
   cd <your-repo>
   ```

2. **Trigger runs**

   - **Manual**: Go to **GitHub → Actions**, select a workflow, and click **Run workflow**.  
   - **By event**:
     - Push to `main` → triggers **main.yml**.  
     - Create `feature-xyz` branch and push → triggers **feature.yml**.  
     - Open a Pull Request → triggers **pr_opened.yml**.  
     - Push more commits to the PR → triggers **pr_synchronize.yml**.  
     - Submit a review on the PR → triggers **pr_review.yml**.  
     - Merge/close the PR → triggers **pr_closed.yml** (+ then **main.yml** on merge push).  

---

