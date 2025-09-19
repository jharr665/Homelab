# Homelab — Portfolio of Stacks (Infra ▸ Platform ▸ Apps ▸ Security ▸ Observability ▸ Automation ▸ Research)

> A cohesive, production‑style homelab built from modular, open‑source stacks. This repo is the **landing page** linking to each stack, with a high‑level architecture and quick start.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](#license)
![Focus](https://img.shields.io/badge/Focus-End_to_End_Homelab-blue)
![Stacks](https://img.shields.io/badge/Stacks-Infra,Platform,Media,SOC,Observability,Automation,RedTeam-orange)

---

## 🧭 High‑Level Architecture

```mermaid
flowchart TB
  %% Layers
  subgraph L0["Infrastructure"]
    PVE["Proxmox Hosts"];
    TN["TrueNAS (ZFS)"];
    FW["OPNsense Firewall"];
    NET["10GbE Switch + VLANs"];
  end

  subgraph L1["Platform"]
    RKE2["Rancher + RKE2 Kubernetes"];
    Cilium["Cilium CNI"];
    Ingress["Ingress + WAF"];
    CertM["cert-manager"];
    Auth["Authentik SSO"];
    Harbor["Harbor Registry"];
    Argo["ArgoCD GitOps"];
    ESO["External Secrets"];
  end

  subgraph L2["App Stacks"]
    Media["Jellyfin + Servarr + Gluetun"];
    Others["Paperless / Immich / etc."];
  end

  subgraph L3["Security & SOC"]
    Wazuh["Wazuh SIEM/XDR"];
    SO["Security Onion (Suricata/Zeek)"];
    Falco["Falco"];
    Kyverno["Kyverno"];
    Trivy["Trivy Operator"];
    CrowdSec["CrowdSec"];
  end

  subgraph L4["Observability & Compliance"]
    Prom["Prometheus"];
    Graf["Grafana"];
    Loki["Loki/Promtail"];
    Kuma["Uptime Kuma"];
    Score["Compliance Scorecards"];
  end

  subgraph L5["Automation & DevSecOps"]
    CI["GitHub Actions CI/CD"];
    Cosign["Cosign (sign/attest)"];
    SBOM["SBOM + Trivy"];
    TF["Terraform"];
    Ansible["Ansible"];
    MCP["MCP Server"];
  end

  subgraph L6["Red-Team & Research"]
    Kali["Kali VM"];
    Scenarios["Attack Scenarios"];
  end

  %% Flows
  PVE --- TN;
  PVE --- NET;
  FW --- NET;
  L0 --> L1;
  Harbor --> L1;
  L1 --> L2;
  L2 --> L3;
  L3 --> L4;
  CI --> Harbor;
  Harbor --> Argo;
  Argo --> RKE2;
  TF --> L0;
  Ansible --> L1;
  MCP --> L5;
  L6 -. "tests & validates detections" .-> L3;

```

---

## 📚 Repositories (Stacks)

> Replace `<your-username>` with your GitHub handle after you publish each repo.

- **Infrastructure & Virtualization** — Proxmox, TrueNAS (ZFS), OPNsense  
  `https://github.com/<your-username>/homelab-infrastructure-stack`
- **Platform (Kubernetes + GitOps + SSO)** — Rancher/RKE2, Cilium, Ingress WAF, cert-manager, Harbor, ArgoCD, Authentik, Kyverno, Falco, Trivy  
  `https://github.com/<your-username>/homelab-platform-stack`
- **Media Stack** — Jellyfin + Servarr + qBittorrent via Gluetun, Caddy + Authentik, optional extras  
  `https://github.com/<your-username>/homelab-media-stack`
- **Security & SOC** — Wazuh, Security Onion, Falco, CrowdSec, Kyverno, Trivy Operator  
  `https://github.com/<your-username>/homelab-security-soc-stack`
- **Observability & Compliance** — Prometheus/Grafana, Loki/Promtail, Uptime Kuma, scorecards  
  `https://github.com/<your-username>/homelab-observability-compliance-stack`
- **Automation & DevSecOps** — ArgoCD, Terraform, Ansible, CI/CD, Cosign, SBOM/Trivy, MCP  
  `https://github.com/<your-username>/homelab-automation-devsecops-stack`
- **Red‑Team & Research** — Kali VM cloud‑init, legal/ethics, scenarios  
  `https://github.com/<your-username>/homelab-redteam-research-stack`

---

## 🚀 How to Use This Portfolio

1. **Visit each stack** above for its README, setup, and docs.  
2. Start with **Infrastructure** → then **Platform** → then add **App Stacks**.  
3. Layer on **Security/SOC**, **Observability**, and **Automation** as you grow.  
4. The **Red‑Team** lab is isolated and used to validate detections + practice TTPs.

---

## 🛠️ What’s Included Here

- This repo is intentionally **docs‑only** (no code to run).  
- The purpose is to **tie your work together** and provide a single link you can put on your résumé/LinkedIn.

---

## 🧩 Topics / Tags to add on GitHub

`homelab`, `kubernetes`, `proxmox`, `truenas`, `opnsense`, `gitops`, `devsecops`, `security`, `observability`, `media-server`, `portfolio`

---

## 📌 Tips for Recruiters/Reviewers (TL;DR)

- Each stack is **self‑contained** and **reproducible**.  
- Security is **built‑in** (SSO, policies, signatures, scans).  
- Operations are **observable** (metrics, logs, uptime, compliance).  
- CI/CD and IaC keep everything **versioned** and **auditable**.

---

## 📝 License

MIT — see `LICENSE`.
