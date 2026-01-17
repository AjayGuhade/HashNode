---
title: "Git Basics For Fresher DevOps"
datePublished: Fri Jan 16 2026 05:26:02 GMT+0000 (Coordinated Universal Time)
cuid: cmkgfqum1000902l8htg969zm
slug: git-basics-for-fresher-devops
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/0gkw_9fy0eQ/upload/55493abcc88a1c62d0037a8c7702eff4.jpeg
tags: github, git, devops, trainwithshubham, continuous-learning

---

# Git Basics Every DevOps Fresher Should Know 🚀

As a DevOps fresher, Git is one of the most important tools you must learn. In this short blog, I’ll share basic Git commands that helped me a lot.

## 🔹 What is Git?

Git is a distributed version control system used to track code changes.

## 🔹 Most Used Git Commands

* `git init` – Initialize a repository
    
* `git status` – Check file status
    
* `git add .` – Stage changes
    
* `git commit -m "message"` – Save changes
    
* `git push` – Push code to GitHub
    

## 🔹 Why Git is Important for DevOps?

* Helps manage infrastructure code
    
* Supports CI/CD pipelines
    
* Enables team collaboration
    

# 🎤 Advanced Mock Interview — Git & GitHub for DevOps (Senior Level)

---

## **Scenario 1 — Secret leaked AND forked**

**Interviewer:**  
A developer pushed a secret to GitHub. Before you noticed, someone forked the repo. What now?

**You:**  
Rotate the secret immediately, invalidate the compromised credentials, then remove the secret from history. After that, treat the secret as fully compromised and monitor for abuse.

**Explanation:**  
Forks copy history. You cannot guarantee deletion everywhere. Rotation is the only safe action.

**Example:**

```plaintext
git filter-repo --path .env --invert-paths
git push --force
aws iam delete-access-key
aws iam create-access-key
```

---

## **Scenario 2 — CI pipeline compromised**

**Interviewer:**  
Someone modified `.github/workflows/deploy.yml` to echo secrets into logs. What do you do?

**You:**  
Disable pipeline, rotate all exposed secrets, audit logs, revert malicious commit, lock down workflow permissions.

**Explanation:**  
CI has production access. Treat it as a security incident.

---

## **Scenario 3 — Git history rewritten in main**

**Interviewer:**  
Someone ran `git push --force` on `main`. Production is now inconsistent.

**You:**  
Stop deployments, restore `main` from last known good commit or tag, communicate with team, enforce branch protection.

---

## **Scenario 4 — Partial deployment failure**

**Interviewer:**  
Your pipeline deploys to 5 regions. One region failed mid-deploy.

**You:**  
Detect drift, rollback failed region or roll forward consistently.

**Explanation:**  
Inconsistent versions cause data corruption.

---

## **Scenario 5 — GitOps controller outage**

**Interviewer:**  
ArgoCD is down and cannot sync infra. A critical change is needed.

**You:**  
Apply emergency change manually, document it, reconcile back into Git once GitOps is restored.

---

## **Scenario 6 — Malicious PR with hidden intent**

**Interviewer:**  
A PR passes CI but secretly opens a backdoor in code.

**You:**  
Use code review, static analysis, runtime security, principle of least privilege.

---

## **Scenario 7 — Repo with 2k commits slow**

**Interviewer:**  
Large monorepo is slow to clone.

**You:**  
Use shallow clones, partial checkouts, split repo or use sparse checkout.

---

## **Scenario 8 — Accidental deletion of main**

**Interviewer:**  
Someone deleted the main branch.

**You:**  
Restore from remote or GitHub UI, recreate protection.

---

## **Scenario 9 — Audit after breach**

**Interviewer:**  
Security asks: “Which secrets were exposed in last 90 days?”

**You:**  
Scan git history, logs, PRs, rotate all suspicious credentials.

---

## **Scenario 10 — GitHub outage during incident**

**Interviewer:**  
GitHub and registry are down; production is failing.

**You:**  
Use last built artifact, emergency manual deploy, post-incident sync.

---

# 🧠 Deep Explanation Patterns

| Concept | Why Important |
| --- | --- |
| History rewrite | Can destroy audit trail |
| Secrets in Git | Permanent exposure risk |
| Branch protection | Prevents human error |
| GitOps | Prevents drift |
| CI security | CI has prod access |
| Auditability | Compliance requirement |

---

# 🔥 Key Interview Phrases

Use these:

* “I treat this as a security incident.”
    
* “First I contain the blast radius.”
    
* “We restore service before root cause.”
    
* “We prevent recurrence using automation.”
    

---

# 🟢 Final Tip

At senior level:  
You are judged not on **commands**, but on:

* Risk management
    
* Blast radius control
    
* Compliance & auditability
    
* Team safety
    

---