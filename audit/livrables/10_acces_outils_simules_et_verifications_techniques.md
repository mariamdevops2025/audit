**Accès & outils simulés + vérifications techniques (non intrusives)**  
Audit SSI — **Clinique Santé Plus** — Période : **01/12/2025 → 05/01/2026**  

Ce document décrit un **SI fictif cohérent** (accès/outils “lecture seule”) et une liste de **vérifications techniques raisonnables** (sans intrusion), alignées ISO/IEC 27001/27002, ANSSI, RGPD.

---

## 1. SI fictif (cible auditée) — hypothèses réalistes
### 1.1 Organisation & périmètre
- Petite clinique (≈ 15 employés) : accueil, secrétariat, médecins, facturation, direction.
- 1 site principal, 1 baie réseau.
- Volume : ≈ 50 patients/jour.

### 1.2 Actifs & architecture (simplifiée)
- **Postes** : 8 PC Windows 11 Pro (accueil x2, secrétariat x2, médecins x3, direction x1).
- **Imprimantes/MFP** : 2 multifonctions réseau.
- **Réseau** :
  - 1 pare-feu/routeur (type “appliance” ou box pro) avec Wi‑Fi,
  - 1 switch manageable,
  - 2 SSID : `SANTEPLUS-INTERNE` et `SANTEPLUS-INVITES`.
- **Données & applicatif patient** :
  - Application SaaS “**MedSimple**” (gestion dossiers patients, RDV, facturation),
  - Hébergement annoncé “HDS” (simulé au niveau documentaire).
- **Messagerie** : Microsoft 365 (Exchange Online) + OneDrive/SharePoint (dépôt documents).
- **Sauvegardes** :
  - Sauvegarde quotidienne des documents (SharePoint/OneDrive via politique M365 + export),
  - Sauvegarde hebdomadaire “image” des 2 postes critiques (accueil + direction) vers NAS,
  - Copie hors site chiffrée hebdo (cloud prestataire).
- **Prestataire IT** : maintenance + supervision AV/patch.

### 1.3 Comptes & rôles (cohérents)
- Comptes nominatifs Microsoft 365 (ex. `prenom.nom@santeplus.fr`).
- Comptes “MedSimple” par rôle : `Accueil`, `Médecin`, `Admin applicatif`.
- Comptes d’administration : 2 admins IT (prestataire) + 1 admin clinique (direction).

---

## 2. Accès simulés (lecture seule) donnés aux auditeurs
### 2.1 Accès “console” (capture/export uniquement)
1) **Microsoft 365 Admin Center** — rôle “Security Reader / Reports Reader”  
   - Exports : liste utilisateurs, MFA, politiques, rapports connexions.
2) **Portail MedSimple (admin lecture)**  
   - Exports : rôles, permissions, journaux d’accès (si disponibles), paramètres sécurité.
3) **Console antivirus/EDR prestataire (lecture)**  
   - Exports : couverture postes, dernière mise à jour signatures, alertes 90 jours.
4) **Console sauvegardes (lecture)** (NAS/outil prestataire)  
   - Exports : jobs, succès/échecs, rétention, logs, dernier test restauration.
5) **Interface pare-feu/routeur (lecture)**  
   - Export configuration, règles, réseaux/VLAN, Wi‑Fi (WPA2/3, WPS), logs.

### 2.2 Accès “terrain” (sur site, non intrusif)
- Accès accompagné à 3 postes échantillons (accueil, médecin, direction) :
  - vérification visuelle des paramètres (Windows Update, BitLocker, antivirus, verrouillage session),
  - sans installation d’outil, sans scan agressif, sans élévation non autorisée.

### 2.3 Jeu de preuves simulées (pack documentaire)
Le “pack preuves” peut être fourni sous forme de captures/export (PDF/PNG/CSV) **anonymisés** :
- Organigramme, procédures, contrats prestataires + DPA, attestation HDS (si applicable).
- Captures de paramètres (MFA, Wi‑Fi, sauvegardes, patch, AV).
- Extraits logs/rapports (connexions, alertes, succès sauvegardes).

---

## 3. Outils autorisés (non intrusifs)
### 3.1 Outils “bureautiques” (recommandés)
- Export natif des consoles (CSV/PDF).
- Captures d’écran **anonymisées** (floutage identifiants, patients, IP si nécessaire).

### 3.2 Commandes locales (si poste Windows fourni en observation)
Uniquement des commandes de **lecture** :
- `winver`, `systeminfo` (version OS)
- `Get-BitLockerVolume` (PowerShell) (état chiffrement)
- `Get-MpComputerStatus` (Defender) (si Defender)
- Vérifications via UI : Windows Update, pare-feu, verrouillage écran

### 3.3 Interdits (rappel)
- Nmap agressif, exploitation, brute force, phishing réel, DoS, exploitation de failles.

---

## 4. Vérifications techniques (liste précise, non intrusive)
Chaque vérification produit au moins **1 preuve** (ID `P-xxx`) et peut alimenter un constat (`C-xxx`).

### V-01 — MFA et durcissement des comptes Microsoft 365
- **Objectif** : réduire compromission identifiants (phishing).
- **Méthode** : export liste utilisateurs + statut MFA ; vérifier admins avec MFA obligatoire.
- **Critères** : ISO27002 5.17 ; RGPD 32 ; ANSSI hygiène.
- **Preuves** : `P-002` (export MFA), `P-003` (captures policies).
- **Attendu** : MFA activée pour 100% comptes, a minima pour comptes admin.

### V-02 — Comptes à privilèges : nombre, usage, traçabilité
- **Méthode** : liste admins ; vérifier comptes séparés (admin ≠ user), logs connexions.
- **Preuves** : `P-004` (liste admins), `P-005` (rapport connexions).
- **Attendu** : admins limités, comptes dédiés, traçabilité disponible.

### V-03 — Gestion des entrées/sorties (onboarding/offboarding)
- **Méthode** : échantillon 3 mouvements RH fictifs ; vérifier création/suppression comptes.
- **Preuves** : `P-006` (procédure), `P-007` (preuves suppression/disable).
- **Attendu** : désactivation ≤ 24h départ ; revue droits à l’arrivée.

### V-04 — Rôles & permissions MedSimple (moindre privilège)
- **Méthode** : export rôles ; vérifier séparation Accueil/Médecin/Admin ; accès dossiers.
- **Preuves** : `P-008` (matrice rôles), `P-009` (paramètres sécurité).
- **Attendu** : pas d’accès “admin” pour métiers ; accès limité par rôle.

### V-05 — Journalisation accès applicatif (si disponible)
- **Méthode** : vérifier logs d’accès, durée rétention, accès aux logs.
- **Preuves** : `P-010` (extrait logs), `P-011` (politique rétention).
- **Attendu** : logs consultables, ≥ 6 mois si possible (sinon justification).

### V-06 — Postes : état des mises à jour
- **Méthode** : sur 3 postes échantillons, vérifier Windows Update + date dernier patch.
- **Preuves** : `P-012` (captures Update), `P-013` (report prestataire si existant).
- **Attendu** : correctifs sécurité ≤ 30 jours (ou procédure d’exception).

### V-07 — Postes : antivirus/EDR, couverture et alertes
- **Méthode** : console EDR lecture ; vérifier 100% postes couverts ; alertes 90 jours.
- **Preuves** : `P-014` (rapport couverture), `P-015` (journal alertes).
- **Attendu** : couverture complète, alertes traitées, signatures à jour.

### V-08 — Chiffrement disque et verrouillage session
- **Méthode** : vérifier BitLocker (ou équivalent) et verrouillage auto.
- **Preuves** : `P-016` (BitLocker), `P-017` (GPO/param écran).
- **Attendu** : chiffrement sur postes direction/accueil ; verrouillage ≤ 5 minutes.

### V-09 — Wi‑Fi : chiffrement, WPS, rotation clés, invité isolé
- **Méthode** : interface routeur ; vérifier WPA2/3 ; WPS désactivé ; VLAN/règles.
- **Preuves** : `P-018` (config Wi‑Fi), `P-019` (règles isolation invité).
- **Attendu** : invité isolé (pas d’accès SI interne) ; WPA2/3 ; WPS off.

### V-10 — Pare-feu : exposition Internet, règles sortantes/entrantes
- **Méthode** : revue règles + NAT ; vérifier services exposés.
- **Preuves** : `P-020` (export règles), `P-021` (liste services exposés).
- **Attendu** : exposition minimale ; administration distante protégée.

### V-11 — Sauvegardes : stratégie 3-2-1, rétention, chiffrement, hors site
- **Méthode** : console backup ; vérifier fréquence, rétention, offsite, chiffrement.
- **Preuves** : `P-022` (plan backup), `P-023` (logs jobs), `P-024` (preuve offsite).
- **Attendu** : backups réguliers, au moins 1 copie hors site, chiffrement.

### V-12 — Test de restauration (preuve)
- **Méthode** : demander PV test ; sinon réaliser table-top + restauration fictive encadrée.
- **Preuves** : `P-025` (PV test), `P-026` (fichier restauré anonymisé).
- **Attendu** : test ≤ 6 mois, RTO/RPO documentés.

### V-13 — Incidents : procédure + exercice ransomware (table-top)
- **Méthode** : revue procédure, arbre d’appel ; exercice 30 min.
- **Preuves** : `P-027` (procédure), `P-028` (PV exercice).
- **Attendu** : rôles clairs, notification RGPD connue (72h), kit de crise.

### V-14 — Fournisseurs : clauses RGPD (art. 28), sécurité, HDS (si applicable)
- **Méthode** : revue contrats/DPA ; vérifier notification incident, sous-traitants ultérieurs.
- **Preuves** : `P-029` (contrats + DPA), `P-030` (attestation HDS).
- **Attendu** : DPA complet, responsabilités claires.

---

## 5. Sorties attendues (techniques)
- Une **preuve** par vérification (minimum), référencée dans le registre `05_registre_preuves.csv`.
- Des constats **factuels** (si écarts), consolidés dans `06_fiches_constats.md`.
- Une cartographie des risques et un plan d’actions priorisé dans `07_rapport_audit.md`.

