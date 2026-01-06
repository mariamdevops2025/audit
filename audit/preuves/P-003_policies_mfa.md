# P-003 : Politiques sécurité/authentification M365
**Date : 8 décembre 2025** | **Source : M365 Admin Center** | **Type : Capture**

---

## Configuration actuelle — Microsoft 365

### Conditional Access Policies

**Aucune politique de Conditional Access configurée pour imposer la MFA de manière obligatoire.**

### Multi-Factor Authentication (MFA)

**Statut global** :
- MFA activée pour **3 comptes administrateurs** (100% admins)
- MFA activée pour **6 comptes utilisateurs** sur 15 (40% utilisateurs)
- **Aucune politique** n'impose la MFA de manière automatique

### Authentification

**Méthodes supportées** :
- ✅ Application Microsoft Authenticator
- ✅ SMS
- ⚠️ Pas de politique de sécurité des mots de passe centralisée (reposant sur paramètres par défaut)

### Observations

- Les comptes administrateurs ont tous la MFA activée (bonne pratique)
- Les utilisateurs doivent activer la MFA **manuellement** (activation volontaire)
- Aucune politique Conditional Access ne bloque les connexions sans MFA

---

*Capture anonymisée — Audit SSI Efrei Paris*
