# Claude Code — Security Audit Skill

Skill [Claude Code](https://docs.anthropic.com/en/docs/claude-code) pour réaliser un **audit de sécurité complet** d'une web app.

## Ce que ça couvre

- **OWASP Top 10 (2021)** — chaque finding est mappé à sa catégorie OWASP + CWE
- **16 sections d'audit** : headers HTTP, authentification, CSRF, open redirect, injection (SQL/XSS/command), contrôle d'accès / IDOR, secrets & cryptographie, paywall / billing, composants vulnérables, CORS, fichiers & configuration, intégrité, WebSocket, SSRF, logging & monitoring, intégrité des données
- **Scan automatique des dépendances** : `npm audit`, `pip-audit`, versions des frameworks
- **Rapport structuré** avec sévérité (CRITIQUE → HAUTE → MOYENNE → BASSE), fichier:ligne, et fix recommandé avec code
- **Score global sur 10**

## Installation

Copie le fichier dans ton répertoire de skills Claude Code :

```bash
# Skill global (disponible partout)
mkdir -p ~/.claude/commands
cp .claude/commands/security-audit.md ~/.claude/commands/security-audit.md

# OU skill projet (disponible uniquement dans un repo spécifique)
mkdir -p .claude/commands
cp .claude/commands/security-audit.md <ton-projet>/.claude/commands/security-audit.md
```

## Utilisation

Dans Claude Code, lance :

```
/security-audit /chemin/vers/ton/projet
```

Claude va analyser l'ensemble du projet et générer un rapport complet.

## Exemple de rapport généré

```
# Rapport d'audit sécurité — Mon Projet
Date : 2026-02-26
Auditeur : Claude Code (security-audit skill)

## Résumé exécutif
L'application présente une posture de sécurité correcte avec quelques
points d'attention sur les headers HTTP et la validation des inputs.

## Résultats

### CRITIQUE — Corriger immédiatement
| # | Vulnérabilité | OWASP | CWE | Fichier:ligne | Impact | Fix recommandé |
|---|---|---|---|---|---|---|
| 1 | Secret API hardcodé | A02 | CWE-798 | src/config.py:42 | Compromission totale | Utiliser variable d'env |

### HAUTE — Corriger avant mise en production
...

## Score global
7/10
```

## Licence

MIT
