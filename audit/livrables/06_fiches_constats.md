# Fiches Constats — Audit SSI Clinique Santé Plus
**Date : 24 décembre 2025**| **Équipe Audit SSI — Efrei Paris**

---

## Constat C-001 : Absence de MFA obligatoire pour tous les comptes Microsoft 365

### Critère de référence
- **ISO/IEC 27002:2022** — Contrôle 5.17 (Authentification)
- **ANSSI** — Recommandations hygiène informatique (authentification forte)
- **RGPD** — Article 32 (Sécurité du traitement)

### Observation
Lors de la revue des comptes Microsoft 365 (preuve P-002, P-003), il a été constaté que :
- **Seulement 40% des comptes utilisateurs** (6/15) ont activé l’authentification multifacteur (MFA)
- **Les comptes administrateurs** (3 comptes) ont tous la MFA activée, mais **aucune politique de Conditional Access** n’impose la MFA de manière obligatoire
- La politique de sécurité actuelle repose sur une **activation volontaire** par les utilisateurs

### Preuves
- **P-002** : Export statut MFA des comptes utilisateurs (08/12/2025)
- **P-003** : Captures politiques sécurité/authentification M365 (08/12/2025)
- **P-004** : Liste comptes à privilèges (admins) (08/12/2025)
- **P-005** : Rapport connexions (extrait anonymisé) (09/12/2025)

### Risque identifié
**Risque : Compromission de comptes utilisateurs par phishing ou vol de mots de passe**

- **Impact** : Élevé (accès non autorisé aux données de santé, violation RGPD, interruption d’activité)
- **Probabilité** : Moyenne (menaces ciblées sur secteur santé, faible sensibilisation)
- **Criticité** : **Élevée** (Impact Élevé × Probabilité Moyenne)

**Scénario** : Un attaquant obtient les identifiants d’un utilisateur via un email de phishing. Sans MFA, l’accès au compte est immédiat, permettant l’exfiltration de données patients ou l’accès à MedSimple.

### Recommandation
**P-1** : Implémenter une politique de Conditional Access Microsoft 365 imposant la MFA obligatoire pour **100% des comptes** (utilisateurs et administrateurs), avec activation progressive sur 2 semaines.

**Actions détaillées** :
1. Créer une politique Conditional Access "MFA obligatoire" (sauf exclusion temporaire pour tests)
2. Communiquer aux utilisateurs (email + session de 30 min) sur l’activation MFA (application Microsoft Authenticator recommandée)
3. Activer progressivement par groupe (direction → médecins → secrétariat → accueil)
4. Monitorer les échecs d’authentification et accompagner les utilisateurs en difficulté
5. Documenter la politique dans la procédure "Gestion des accès"

**Responsable** : Prestataire IT (avec validation Direction)  
**Échéance** : 31 janvier 2026  
**Coût estimé** : 0€ (fonctionnalité incluse dans M365)  
**Priorité** : **P1 — Critique**

---

## Constat C-002 : Stratégie de sauvegarde incomplète et absence de test de restauration récent

### Critère de référence
- **ISO/IEC 27002:2022** — Contrôle 8.13 (Sauvegarde de l’information)
- **ANSSI** — Recommandations sauvegardes (stratégie 3-2-1)
- **RGPD** — Article 32 (Sécurité du traitement)

### Observation
Lors de la revue de la stratégie de sauvegarde (preuves P-022, P-023, P-024, P-025) :
- **Sauvegardes quotidiennes** des documents SharePoint/OneDrive sont en place (automatisées M365)
- **Sauvegardes hebdomadaires** des 2 postes critiques (accueil + direction) vers NAS local sont documentées
- **Copie hors site** (cloud prestataire) existe mais **chiffrement non vérifié** dans le contrat
- **Dernier test de restauration** remonte à **8 mois** (avril 2025) — preuve P-025
- **Pas de sauvegarde dédiée de la base MedSimple** (reposant uniquement sur les sauvegardes de l’éditeur/hébergeur)
- **RTO/RPO non documentés** formellement

### Preuves
- **P-022** : Plan de sauvegarde (fréquence, périmètre, rétention) (05/12/2025)
- **P-023** : Logs jobs sauvegarde (30 jours) (15/12/2025)
- **P-024** : Preuve copie hors site chiffrée (contrat/rapport) (15/12/2025)
- **P-025** : PV test restauration (date, résultat, RTO/RPO) (18/12/2025)
- **P-026** : Preuve élément restauré (anonymisé) (18/12/2025)

### Risque identifié
**Risque : Perte définitive de données critiques en cas d’incident (ransomware, panne matérielle, erreur humaine)**

- **Impact** : Très élevé (perte dossiers patients, interruption soins, non-conformité RGPD/HDS, arrêt d’activité)
- **Probabilité** : Moyenne (secteur santé ciblé, dépendance forte au SI)
- **Criticité** : **Très élevée** (Impact Très élevé × Probabilité Moyenne)

**Scénario** : Un ransomware chiffre les postes et le NAS local. La restauration depuis la copie hors site n’a pas été testée récemment et échoue (incompatibilité, corruption). Les données sont perdues définitivement.

### Recommandation
**P-2** : Compléter la stratégie de sauvegarde selon le principe 3-2-1 et formaliser les tests de restauration trimestriels.

**Actions détaillées** :
1. **Documenter RTO/RPO** : RTO = 24h, RPO = 24h (objectifs réalistes pour la clinique)
2. **Vérifier chiffrement** de la copie hors site (demander attestation au prestataire)
3. **Ajouter sauvegarde export MedSimple** : export hebdomadaire automatisé vers stockage sécurisé (si fonctionnalité disponible)
4. **Planifier tests restauration trimestriels** : Q1, Q2, Q3, Q4 (PV + preuve fichier restauré)
5. **Créer procédure de restauration** documentée (étapes, contacts, escalade)

**Responsable** : Prestataire IT (avec validation Direction)  
**Échéance** : 28 février 2026  
**Coût estimé** : 500€/an (si export MedSimple payant)  
**Priorité** : **P1 — Critique**

---

## Constat C-003 : Retard dans l’application des correctifs de sécurité sur les postes de travail

### Critère de référence
- **ISO/IEC 27002:2022** — Contrôle 8.8 (Gestion des vulnérabilités techniques)
- **ANSSI** — Recommandations hygiène informatique (mises à jour)
- **RGPD** — Article 32 (Sécurité du traitement)

### Observation
Lors de l’observation de 3 postes échantillons (accueil, médecin, direction — preuves P-012, P-013, P-014, P-015) :
- **Poste accueil** : Dernière mise à jour Windows = 15 novembre 2025 (retard de **15 jours** par rapport aux correctifs critiques de novembre)
- **Poste médecin** : Dernière mise à jour = 8 novembre 2025 (retard de **22 jours**)
- **Poste direction** : Dernière mise à jour = 20 novembre 2025 (retard de **10 jours**)
- **Aucune politique formelle** de gestion des correctifs (délais cibles, exceptions, tests)
- Le prestataire IT effectue des mises à jour "à la demande" mais **pas de cycle automatisé**

### Preuves
- **P-012** : Captures Windows Update (poste accueil) (12/12/2025)
- **P-013** : Reporting patch (si disponible) ou ticketing (12/12/2025)
- **P-014** : Couverture antivirus/EDR (inventaire postes) (13/12/2025)
- **P-015** : Alertes 90 jours + statut traitement (anonymisé) (13/12/2025)

### Risque identifié
**Risque : Exploitation de vulnérabilités connues non corrigées**

- **Impact** : Élevé (compromission poste, propagation malware, exfiltration données)
- **Probabilité** : Moyenne (vulnérabilités publiques, attaquants automatisés)
- **Criticité** : **Élevée** (Impact Élevé × Probabilité Moyenne)

**Scénario** : Une vulnérabilité critique Windows (ex. CVE-2025-xxxx) est exploitée par un ransomware. Les postes non mis à jour sont compromis en premier, permettant la propagation sur le réseau.

### Recommandation
**P-3** : Mettre en place une politique de gestion des correctifs avec application automatique dans un délai de 7 jours pour les correctifs critiques.

**Actions détaillées** :
1. **Définir politique de correctifs** : Critiques = 7 jours, Importants = 30 jours, Optionnels = trimestriel
2. **Configurer Windows Update for Business** (ou équivalent via prestataire) pour déploiement automatisé
3. **Créer procédure d’exception** : tests préalables sur poste pilote si logiciel métier incompatible
4. **Monitorer conformité** : rapport mensuel de l’état des mises à jour (prestataire → direction)
5. **Documenter dans procédure SSI** : "Gestion des correctifs"

**Responsable** : Prestataire IT (avec validation Direction)  
**Échéance** : 15 février 2026  
**Coût estimé** : 0€ (fonctionnalité Windows incluse)  
**Priorité** : **P1 — Critique**

---

## Constat C-004 : Isolation insuffisante du réseau Wi‑Fi invité

### Critère de référence
- **ISO/IEC 27002:2022** — Contrôle 8.20 (Séparation dans les réseaux) et 8.21 (Sécurisation des services réseau)
- **ANSSI** — Recommandations réseau (séparation, isolation)

### Observation
Lors de la revue de la configuration réseau (preuves P-018, P-019, P-020, P-021) :
- **Wi‑Fi invité** (`SANTEPLUS-INVITES`) utilise **WPA2** (conforme) mais **WPS activé** (risque)
- **Isolation invité** : Le réseau invité est sur un **VLAN séparé**, mais les **règles de pare-feu** permettent un accès partiel au réseau interne (ports 80, 443, 53 ouverts vers interne)
- **Pas de bande passante limitée** pour le réseau invité
- **Pas de portail captif** (authentification/acceptation CGU)

### Preuves
- **P-018** : Configuration Wi‑Fi (WPA2/3, WPS, SSID) (14/12/2025)
- **P-019** : Règles isolation réseau invité (VLAN/ACL) (14/12/2025)
- **P-020** : Export règles pare‑feu/NAT (anonymisé) (14/12/2025)
- **P-021** : Liste services exposés Internet + justification (14/12/2025)

### Risque identifié
**Risque : Accès non autorisé au réseau interne depuis le Wi‑Fi invité**

- **Impact** : Moyen (accès limité mais possible à certaines ressources internes, exfiltration données)
- **Probabilité** : Faible à moyenne (dépend de la motivation d’un attaquant physique)
- **Criticité** : **Moyenne** (Impact Moyen × Probabilité Faible à Moyenne)

**Scénario** : Un attaquant se connecte au Wi‑Fi invité et exploite les règles de pare-feu permissives pour accéder à des ressources internes (partages, imprimantes, postes non sécurisés).

### Recommandation
**P-4** : Renforcer l’isolation du réseau Wi‑Fi invité et désactiver le WPS.

**Actions détaillées** :
1. **Désactiver WPS** sur le routeur/point d’accès
2. **Modifier règles pare-feu** : bloquer tout trafic du VLAN invité vers le réseau interne (sauf Internet sortant)
3. **Limiter bande passante** invité (ex. 5 Mbps par client)
4. **Optionnel** : Mettre en place un portail captif avec acceptation CGU (si fonctionnalité disponible)
5. **Documenter** : procédure "Gestion réseau invité"

**Responsable** : Prestataire IT  
**Échéance** : 31 janvier 2026  
**Coût estimé** : 0€ (configuration uniquement)  
**Priorité** : **P2 — Important**

---

## Constat C-005 : Procédure de gestion des incidents incomplète et exercice table-top révélant des lacunes

### Critère de référence
- **ISO/IEC 27002:2022** — Contrôle 5.24 (Gestion des événements de sécurité de l’information) et 5.25 (Gestion des incidents de sécurité de l’information)
- **RGPD** — Article 33 (Notification d’une violation à l’autorité de contrôle) et 34 (Communication d’une violation à la personne concernée)

### Observation
Lors de la revue de la procédure d’incidents et de l’exercice table-top ransomware (preuves P-027, P-028) :
- **Procédure d’incident** existe mais **manque de détails** sur :
  - Rôles et responsabilités (qui fait quoi, escalade)
  - Délais de notification RGPD (72h CNIL, communication personnes)
  - Procédure de communication externe (patients, autorités)
- **Exercice table-top** (19/12/2025) a révélé :
  - **Confusion sur le délai CNIL** (certains pensaient 7 jours)
  - **Pas de kit de crise** (contacts urgents, modèles de communication)
  - **Décision de communication patients** non préparée (qui décide, quel message)
  - **Pas de procédure de restauration** documentée (étapes, contacts prestataire)

### Preuves
- **P-027** : Procédure de gestion des incidents + arbre d’appel (16/12/2025)
- **P-028** : PV exercice table-top ransomware + actions (19/12/2025)

### Risque identifié
**Risque : Réaction inadaptée en cas d’incident majeur (ransomware, fuite de données)**

- **Impact** : Très élevé (violation RGPD, sanctions CNIL, perte de confiance patients, interruption activité)
- **Probabilité** : Moyenne (secteur santé ciblé)
- **Criticité** : **Très élevée** (Impact Très élevé × Probabilité Moyenne)

**Scénario** : Un ransomware chiffre les systèmes. L’équipe ne sait pas qui contacter en urgence, ne respecte pas le délai CNIL (72h), et communique mal aux patients, aggravant la crise.

### Recommandation
**P-5** : Compléter la procédure de gestion des incidents et créer un kit de crise opérationnel.

**Actions détaillées** :
1. **Enrichir procédure incidents** :
   - RACI détaillé (RSSI/IT/Direction/DPO/externe)
   - Délais stricts : CNIL 72h, patients si risque élevé
   - Arbre de décision (quand notifier, qui valide)
2. **Créer kit de crise** :
   - Liste contacts urgents (CNIL, prestataire IT, avocat, assurance cyber)
   - Modèles de communication (CNIL, patients, presse si nécessaire)
   - Checklist actions (isolation, analyse, restauration, communication)
3. **Planifier exercices trimestriels** : scénarios variés (ransomware, fuite données, déni de service)
4. **Former le personnel clé** (direction, IT) sur la procédure (session 2h)

**Responsable** : Direction (avec support DPO si existe, sinon prestataire)  
**Échéance** : 15 février 2026  
**Coût estimé** : 0€ (rédaction interne)  
**Priorité** : **P1 — Critique**

---

## Constat C-006 : Clauses RGPD incomplètes dans les contrats avec les prestataires

### Critère de référence
- **RGPD** — Article 28 (Responsable du traitement et sous-traitant)
- **ISO/IEC 27002:2022** — Contrôle 5.19 (Gestion des relations avec les fournisseurs)

### Observation
Lors de la revue des contrats et DPA (preuves P-029, P-030) :
- **Contrat prestataire IT** : DPA (Data Processing Agreement) présent mais **manque** :
  - Clause explicite sur **notification d’incidents** (délai, contenu)
  - Clause sur **sous-traitants ultérieurs** (autorisation préalable)
  - Clause sur **audit sécurité** (possibilité d’audit ou rapport tiers)
- **Contrat hébergeur MedSimple** : Attestation HDS fournie (conforme), mais **DPA générique** (non spécifique à la clinique)
- **Pas de registre des sous-traitants** (qui traite quelles données, pour quels besoins)

### Preuves
- **P-029** : Contrats prestataires + DPA (art.28 RGPD) (06/12/2025)
- **P-030** : Attestation HDS (si applicable) ou justification (06/12/2025)

### Risque identifié
**Risque : Non-conformité RGPD et responsabilité en cas d’incident chez le prestataire**

- **Impact** : Élevé (sanctions CNIL, responsabilité civile, perte de confiance)
- **Probabilité** : Faible à moyenne (dépend de la survenance d’un incident chez le prestataire)
- **Criticité** : **Moyenne** (Impact Élevé × Probabilité Faible à Moyenne)

**Scénario** : Le prestataire IT subit une fuite de données. Le DPA incomplet ne permet pas de déterminer clairement les responsabilités, et la clinique est tenue responsable par défaut.

### Recommandation
**P-6** : Compléter les DPA avec les clauses manquantes et créer un registre des sous-traitants.

**Actions détaillées** :
1. **Compléter DPA prestataire IT** :
   - Notification incidents : délai 24h, contenu (nature, données concernées, mesures)
   - Sous-traitants ultérieurs : autorisation préalable écrite
   - Audit : possibilité d’audit annuel ou rapport tiers (ex. ISO 27001)
2. **Demander DPA spécifique** à l’hébergeur MedSimple (si possible, sinon valider DPA générique)
3. **Créer registre sous-traitants** : tableau (nom, données traitées, finalité, base légale, garanties)
4. **Réviser annuellement** les contrats et DPA (ajout nouveaux prestataires)

**Responsable** : Direction (avec support juridique si disponible)  
**Échéance** : 28 février 2026  
**Coût estimé** : 0€ à 500€ (si consultation juridique)  
**Priorité** : **P2 — Important**

---

## Constat C-007 : Absence de politique de verrouillage automatique des sessions

### Critère de référence
- **ISO/IEC 27002:2022** — Contrôle 5.16 (Gestion des privilèges d’accès)
- **ANSSI** — Recommandations hygiène informatique (verrouillage session)

### Observation
Lors de l’observation des postes (preuve P-017) :
- **Poste direction** : Verrouillage automatique configuré à **10 minutes** (acceptable mais non optimal)
- **Postes accueil/secrétariat** : Verrouillage à **30 minutes** ou **absent** (non sécurisé)
- **Pas de politique centralisée** (GPO ou équivalent) imposant un délai uniforme
- **Pas de sensibilisation** sur l’importance du verrouillage manuel (Win+L)

### Preuves
- **P-017** : Paramètres verrouillage session/timeout (12/12/2025)

### Risque identifié
**Risque : Accès non autorisé aux postes laissés sans surveillance**

- **Impact** : Moyen (accès aux données locales, applications ouvertes, exfiltration)
- **Probabilité** : Faible (nécessite présence physique, mais contexte clinique = accès visiteurs/patients)
- **Criticité** : **Moyenne** (Impact Moyen × Probabilité Faible)

**Scénario** : Un poste accueil reste déverrouillé pendant une pause. Un visiteur accède aux applications ouvertes (MedSimple, messagerie) et consulte/modifie des données patients.

### Recommandation
**P-7** : Implémenter une politique de verrouillage automatique des sessions (5 minutes maximum) et sensibiliser le personnel.

**Actions détaillées** :
1. **Configurer verrouillage automatique** : 5 minutes maximum (via GPO ou paramètres locaux)
2. **Sensibiliser personnel** : rappel lors de la formation MFA sur l’importance du verrouillage (Win+L)
3. **Monitorer conformité** : vérification trimestrielle sur échantillon de postes
4. **Documenter** : procédure "Sécurisation des postes"

**Responsable** : Prestataire IT (avec communication Direction)  
**Échéance** : 31 janvier 2026  
**Coût estimé** : 0€ (configuration uniquement)  
**Priorité** : **P2 — Important**

---

## Synthèse des constats

| ID | Constat | Criticité | Priorité | Échéance recommandée |
|---|---|---|---|---|
| C-001 | Absence de MFA obligatoire | Élevée | P1 | 31/01/2026 |
| C-002 | Stratégie sauvegarde incomplète | Très élevée | P1 | 28/02/2026 |
| C-003 | Retard correctifs sécurité | Élevée | P1 | 15/02/2026 |
| C-004 | Isolation Wi‑Fi invité insuffisante | Moyenne | P2 | 31/01/2026 |
| C-005 | Procédure incidents incomplète | Très élevée | P1 | 15/02/2026 |
| C-006 | Clauses RGPD incomplètes | Moyenne | P2 | 28/02/2026 |
| C-007 | Absence politique verrouillage session | Moyenne | P2 | 31/01/2026 |

**Total** : 7 constats (4 critiques P1, 3 importants P2)

---

*Document préparé par l’Équipe Audit SSI — Efrei Paris*  
*Date de finalisation : 24 décembre 2025*
