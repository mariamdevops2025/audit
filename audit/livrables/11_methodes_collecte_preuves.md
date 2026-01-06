# Méthodes de collecte des preuves — Audit SSI Clinique Santé Plus
**Date : 5 janvier 2026** 

Ce document détaille **comment chaque preuve a été collectée** lors de l'audit, en respectant l'approche **non intrusive** et les accès simulés accordés.

---

## 1. Méthodes générales de collecte

### 1.1 Revue documentaire
**Méthode** : Demande de documents à la Direction / Référent SI  
**Accès** : Documents fournis par email ou partage sécurisé  
**Anonymisation** : Identifiants, noms, données patients masqués

**Preuves collectées** :
- P-001 (Organigramme)
- P-006 (Procédure onboarding/offboarding)
- P-022 (Plan sauvegarde)
- P-027 (Procédure incidents)
- P-029 (Contrats + DPA)
- P-030 (Attestation HDS)

### 1.2 Exports depuis consoles (lecture seule)
**Méthode** : Accès "Security Reader" / "Reports Reader" aux consoles  
**Accès** : Comptes temporaires avec droits lecture seule  
**Anonymisation** : Exports anonymisés (identifiants, IP, données sensibles)

**Preuves collectées** :
- P-002 (Export MFA M365)
- P-004 (Liste admins M365)
- P-005 (Rapport connexions M365)
- P-008 (Matrice rôles MedSimple)
- P-010 (Logs accès MedSimple)
- P-014 (Couverture EDR)
- P-015 (Alertes EDR)
- P-023 (Logs sauvegardes)

### 1.3 Captures d'écran (lecture seule)
**Méthode** : Captures d'écran depuis consoles / interfaces  
**Accès** : Accès lecture seule aux interfaces  
**Anonymisation** : Floutage identifiants, IP, données sensibles

**Preuves collectées** :
- P-003 (Politiques MFA M365)
- P-009 (Paramètres sécurité MedSimple)
- P-018 (Configuration Wi‑Fi)
- P-019 (Règles isolation invité)

### 1.4 Observations sur site (non intrusives)
**Méthode** : Accès accompagné à des postes échantillons  
**Accès** : Présence sur site, observation visuelle + commandes lecture seule  
**Anonymisation** : Captures anonymisées, pas d'élévation de privilèges

**Preuves collectées** :
- P-012 (Windows Update poste accueil)
- P-016 (BitLocker poste direction)
- P-017 (Verrouillage session poste direction)

### 1.5 Entretiens
**Méthode** : Entretiens semi-directifs avec Direction, IT, utilisateurs  
**Accès** : Réunions en présentiel ou visioconférence  
**Anonymisation** : Comptes-rendus anonymisés

**Preuves collectées** :
- Informations contextuelles (non documentées individuellement, mais utilisées dans constats)

### 1.6 Exercices / Tests encadrés
**Méthode** : Exercices table-top ou tests de restauration encadrés  
**Accès** : Présence équipe audit + prestataire IT  
**Anonymisation** : PV anonymisés, données fictives

**Preuves collectées** :
- P-025 (PV test restauration)
- P-026 (Fichier restauré anonymisé)
- P-028 (PV exercice table-top ransomware)

---

## 2. Détail par preuve — Méthode de collecte

### P-001 : Organigramme + Rôles SI
**Méthode** : Revue documentaire  
**Source** : Direction / Référent SI  
**Date** : 2 décembre 2025  
**Procédure** :
1. Demande formelle lors de la réunion de lancement
2. Document fourni par email (PDF)
3. Anonymisation : Noms masqués, structure conservée

---

### P-002 : Export statut MFA
**Méthode** : Export depuis console M365  
**Source** : Microsoft 365 Admin Center  
**Date** : 8 décembre 2025  
**Accès** : Compte temporaire "Security Reader"  
**Procédure** :
1. Connexion M365 Admin Center (rôle Security Reader)
2. Navigation : Utilisateurs → Authentification multifacteur
3. Export CSV de la liste des utilisateurs avec statut MFA
4. Anonymisation : Emails remplacés par "user001@santeplus.fr", noms masqués

---

### P-003 : Politiques sécurité/authentification M365
**Méthode** : Capture d'écran depuis console  
**Source** : Microsoft 365 Admin Center  
**Date** : 8 décembre 2025  
**Accès** : Compte temporaire "Security Reader"  
**Procédure** :
1. Connexion M365 Admin Center
2. Navigation : Sécurité → Conditional Access
3. Capture d'écran des politiques (ou constat d'absence)
4. Navigation : Authentification → MFA
5. Capture d'écran des paramètres MFA
6. Anonymisation : Floutage identifiants, conservation structure

---

### P-004 : Liste comptes administrateurs
**Méthode** : Export depuis console M365  
**Source** : Microsoft 365 Admin Center  
**Date** : 8 décembre 2025  
**Accès** : Compte temporaire "Security Reader"  
**Procédure** :
1. Connexion M365 Admin Center
2. Navigation : Utilisateurs → Filtre "Rôles administrateur"
3. Export CSV des comptes admin
4. Anonymisation : Emails remplacés, noms masqués

---

### P-005 : Rapport connexions
**Méthode** : Export depuis console M365  
**Source** : Microsoft 365 Admin Center (Sign-in logs)  
**Date** : 9 décembre 2025  
**Accès** : Compte temporaire "Reports Reader"  
**Procédure** :
1. Connexion M365 Admin Center
2. Navigation : Rapports → Connexions
3. Export CSV (période : 30 derniers jours)
4. Anonymisation : Emails, IP, localisations masqués

---

### P-012 : Captures Windows Update (poste accueil)
**Méthode** : Observation sur site  
**Source** : Poste accueil (accompagné)  
**Date** : 12 décembre 2025  
**Accès** : Accès accompagné, pas d'élévation de privilèges  
**Procédure** :
1. Présence sur site avec Référent SI
2. Accès au poste accueil (session utilisateur standard)
3. Navigation : Paramètres → Windows Update
4. Capture d'écran de l'état des mises à jour
5. Commande `winver` (lecture seule) pour version OS
6. Anonymisation : Nom poste masqué, dates conservées

---

### P-014 : Couverture EDR
**Méthode** : Export depuis console EDR  
**Source** : Console EDR prestataire (lecture seule)  
**Date** : 13 décembre 2025  
**Accès** : Compte temporaire lecture seule (fourni par prestataire)  
**Procédure** :
1. Connexion console EDR (via prestataire)
2. Navigation : Inventaire → Postes
3. Export CSV de la liste des postes avec statut agent
4. Anonymisation : Noms postes remplacés, IP masquées

---

### P-016 : État BitLocker (poste direction)
**Méthode** : Observation sur site + commande PowerShell  
**Source** : Poste direction (accompagné)  
**Date** : 12 décembre 2025  
**Accès** : Accès accompagné, commande lecture seule  
**Procédure** :
1. Présence sur site avec Référent SI
2. Accès au poste direction (session utilisateur standard)
3. Ouverture PowerShell (non administrateur)
4. Commande : `Get-BitLockerVolume` (lecture seule, pas d'élévation)
5. Capture d'écran du résultat
6. Anonymisation : Nom poste masqué, structure conservée

---

### P-017 : Paramètres verrouillage session
**Méthode** : Observation sur site  
**Source** : Poste direction (accompagné)  
**Date** : 12 décembre 2025  
**Accès** : Accès accompagné, pas d'élévation  
**Procédure** :
1. Présence sur site avec Référent SI
2. Accès au poste direction
3. Navigation : Paramètres → Confidentialité → Verrouillage de l'écran
4. Capture d'écran des paramètres
5. Vérification sur autres postes (accueil, médecin) par observation visuelle
6. Anonymisation : Noms postes masqués

---

### P-018 : Configuration Wi‑Fi
**Méthode** : Capture depuis interface routeur  
**Source** : Pare-feu/Routeur (lecture seule)  
**Date** : 14 décembre 2025  
**Accès** : Interface routeur (compte lecture seule fourni par prestataire)  
**Procédure** :
1. Connexion interface routeur (via prestataire IT)
2. Navigation : Wi‑Fi → Configuration
3. Capture d'écran des paramètres (SSID, chiffrement, WPS)
4. Anonymisation : Mots de passe masqués, SSID conservés (fictifs)

---

### P-022 : Plan de sauvegarde
**Méthode** : Revue documentaire  
**Source** : Prestataire IT  
**Date** : 5 décembre 2025  
**Procédure** :
1. Demande formelle au prestataire IT
2. Document fourni par email (PDF)
3. Anonymisation : Noms prestataire masqués, structure conservée

---

### P-023 : Logs sauvegardes
**Méthode** : Export depuis console sauvegardes  
**Source** : Console sauvegardes (NAS/outil prestataire)  
**Date** : 15 décembre 2025  
**Accès** : Compte lecture seule (fourni par prestataire)  
**Procédure** :
1. Connexion console sauvegardes
2. Navigation : Jobs → Historique (30 jours)
3. Export CSV des logs
4. Anonymisation : Chemins fichiers masqués, volumes conservés

---

### P-025 : PV test restauration
**Méthode** : Exercice encadré  
**Source** : Prestataire IT (test réalisé en présence équipe audit)  
**Date** : 18 décembre 2025  
**Procédure** :
1. Demande de test de restauration au prestataire
2. Test réalisé en présence équipe audit (observation)
3. Restauration d'un fichier fictif depuis sauvegarde NAS
4. PV rédigé par prestataire (validé équipe audit)
5. Anonymisation : Fichier test anonymisé, dates conservées

---

### P-027 : Procédure gestion incidents
**Méthode** : Revue documentaire  
**Source** : Clinique Santé Plus  
**Date** : 16 décembre 2025  
**Procédure** :
1. Demande formelle à la Direction
2. Document fourni par email (PDF)
3. Anonymisation : Noms, contacts masqués, structure conservée

---

### P-028 : PV exercice table-top ransomware
**Méthode** : Exercice table-top animé par équipe audit  
**Source** : Équipe audit (animation)  
**Date** : 19 décembre 2025  
**Procédure** :
1. Organisation exercice table-top (30 min)
2. Participants : Direction, Référent SI, Prestataire IT, Équipe audit
3. Scénario : Ransomware chiffre postes et NAS
4. Animation : Équipe audit (questions, observation réactions)
5. PV rédigé par équipe audit (validé participants)
6. Anonymisation : Noms participants masqués, actions conservées

---

### P-029 : Contrats + DPA
**Méthode** : Revue documentaire  
**Source** : Clinique Santé Plus  
**Date** : 6 décembre 2025  
**Procédure** :
1. Demande formelle à la Direction
2. Documents fournis par email (PDF)
3. Anonymisation : Noms prestataires, montants, clauses sensibles masqués

---

### P-030 : Attestation HDS
**Méthode** : Revue documentaire  
**Source** : Prestataire/Hébergeur MedSimple  
**Date** : 6 décembre 2025  
**Procédure** :
1. Demande formelle à la Direction (transmission par hébergeur)
2. Document fourni par email (PDF)
3. Anonymisation : Numéro attestation masqué, dates conservées

---

## 3. Précautions et garanties

### 3.1 Approche non intrusive
- ✅ **Aucune action intrusive** : Pas de scans agressifs, pas d'exploitation
- ✅ **Lecture seule** : Tous les accès en lecture seule (pas de modification)
- ✅ **Accompagnement** : Observations sur site avec Référent SI
- ✅ **Autorisation** : Toutes les actions autorisées par la Direction

### 3.2 Anonymisation
- ✅ **Identifiants** : Emails, noms, IP masqués
- ✅ **Données patients** : Aucune donnée réelle (audit fictif)
- ✅ **Captures** : Floutage identifiants sensibles
- ✅ **Exports** : Données anonymisées avant export

### 3.3 Traçabilité
- ✅ **Registre de preuves** : Toutes les preuves référencées (P-001 à P-030)
- ✅ **Journal de bord** : Toutes les activités tracées (dates, participants)
- ✅ **Lien preuve ↔ constat** : Chaque constat référence ses preuves

---

## 4. Résumé des méthodes par type

| Type de preuve | Nombre | Méthode principale |
|---|---|---|
| **Revue documentaire** | 6 | Documents fournis par Direction/Prestataire |
| **Exports consoles** | 8 | Exports CSV depuis consoles (lecture seule) |
| **Captures d'écran** | 4 | Captures interfaces (anonymisées) |
| **Observations sur site** | 3 | Accès accompagné, commandes lecture seule |
| **Exercices/Tests** | 3 | Exercices encadrés (table-top, restauration) |
| **Total** | **24** | (sur 30 preuves référencées) |

---

*Document préparé par l'Équipe Audit SSI — Efrei Paris*  
*Date : 5 janvier 2026*
