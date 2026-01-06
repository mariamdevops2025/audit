# Dossier Preuves — Audit SSI Clinique Santé Plus

Ce dossier contient les **preuves collectées** lors de l'audit (captures, exports, documents).

**Important** : Toutes les données sensibles ont été **anonymisées** (identifiants, données patients, adresses IP).

## Preuves disponibles

### Documents organisationnels
- `P-001_organigramme_roles.md` — Organigramme + rôles SI

### Authentification & Accès
- `P-002_export_mfa.csv` — Export statut MFA (40% utilisateurs activés)
- `P-003_policies_mfa.md` — Politiques sécurité M365
- `P-004_admin_accounts.csv` — Liste comptes administrateurs

### Postes & Sécurité
- `P-012_windows_update_accueil.md` — État mises à jour (retard 15 jours)
- `P-014_couverture_edr.csv` — Couverture EDR (100% postes)
- `P-016_bitlocker_direction.md` — État BitLocker (chiffré)
- `P-017_verrouillage_session.md` — Paramètres verrouillage (10-30 min)

### Réseau
- `P-018_wifi_config.md` — Configuration Wi‑Fi (WPS activé sur invité)

### Sauvegardes
- `P-022_plan_sauvegarde.md` — Plan de sauvegarde (quotidienne + hebdo + offsite)
- `P-023_logs_sauvegardes.csv` — Logs sauvegardes (30 jours)
- `P-025_pv_test_restauration.md` — PV test restauration (dernier test : 8 mois)

### Incidents
- `P-027_procedure_incident.md` — Procédure gestion incidents (incomplète)
- `P-028_pv_exercice_ransomware.md` — PV exercice table-top (lacunes identifiées)

### Conformité RGPD/HDS
- `P-029_contrats_dpa.md` — Contrats + DPA (clauses incomplètes)
- `P-030_attestation_hds.md` — Attestation HDS (conforme)

**Total** : 15 preuves principales documentées (sur 30 référencées dans le registre)

## Formats

- **`.md`** : Documents texte (exportables en PDF)
- **`.csv`** : Exports de données (ouvrables dans Excel)
- **Captures** : Décrites en markdown (simulation de captures d'écran)

## Convention de nommage

Format : `P-XXX_description.type`
- `P-XXX` : ID de la preuve (référencé dans le registre)
- `description` : Description courte
- `type` : Extension (.md, .csv, .png, .pdf)
