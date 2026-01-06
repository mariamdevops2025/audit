# Rapport d'Audit de Sécurité des Systèmes d'Information (SSI)
**Clinique Santé Plus**

**Date : 5 janvier 2026** | **Équipe Audit SSI — Efrei Paris**

---

## Table des matières

1. [Résumé exécutif](#résumé-exécutif)
2. [Contexte et périmètre](#contexte-et-périmètre)
3. [Méthodologie](#méthodologie)
4. [Analyse des risques](#analyse-des-risques)
5. [Constats détaillés](#constats-détaillés)
6. [Recommandations et plan d'actions](#recommandations-et-plan-dactions)
7. [Conclusion](#conclusion)
8. [Annexes](#annexes)

---

## 1. Résumé exécutif

### 1.1 Objectif de l'audit

La présente mission d'audit SSI a été réalisée pour la **Clinique Santé Plus** du **1er décembre 2025 au 5 janvier 2026**, dans le cadre du module "Audit et gestion des risques — Normes ISO" de l'Efrei Paris.

L'objectif était d'évaluer le niveau de sécurité du système d'information, de vérifier l'application des bonnes pratiques et exigences réglementaires (ISO/IEC 27001/27002, RGPD, HDS), et d'identifier les principaux risques affectant la confidentialité, l'intégrité et la disponibilité des données de santé.

### 1.2 Périmètre audité

- **Organisation** : Clinique Santé Plus (≈ 15 employés, 50 patients/jour)
- **Systèmes** : Postes Windows, réseau interne/Wi‑Fi, application MedSimple (SaaS), Microsoft 365
- **Processus** : Gestion des accès, sauvegardes, incidents, conformité RGPD/HDS
- **Exclusions** : Tests d'intrusion, audits physiques des locaux, systèmes externes non maîtrisés

### 1.3 Méthodologie

L'audit a été conduit selon une approche **non intrusive** (lecture seule, observations, entretiens, revue documentaire), alignée sur les référentiels **ISO/IEC 27001/27002**, **ANSSI**, et **RGPD**.

**Phases** :
- **Semaine 1** : Cadrage (lettre de mission, note de cadrage)
- **Semaines 2-3** : Travaux de terrain (20 contrôles, 30 preuves collectées)
- **Fin semaine 3** : Analyse des risques et formulation des constats
- **Semaine 4** : Rédaction du rapport et restitution orale

### 1.4 Synthèse des résultats

**7 constats** ont été identifiés, répartis comme suit :

| Criticité | Nombre | Constats |
|---|---|---|
| **Très élevée** | 2 | C-002 (Sauvegardes), C-005 (Incidents) |
| **Élevée** | 2 | C-001 (MFA), C-003 (Correctifs) |
| **Moyenne** | 3 | C-004 (Wi‑Fi invité), C-006 (RGPD), C-007 (Verrouillage) |

**Points positifs identifiés** :
-  MFA activée pour les comptes administrateurs
-  Stratégie de sauvegarde partiellement en place (quotidienne + hors site)
-  Procédure d'incidents existante (à compléter)
-  Attestation HDS pour l'hébergeur MedSimple
-  Antivirus/EDR déployé sur 100% des postes

**Risques majeurs** :
- **Absence de MFA obligatoire** pour tous les comptes (risque phishing)
- **Stratégie de sauvegarde incomplète** et tests de restauration non réguliers
- **Retard dans l'application des correctifs** de sécurité
- **Procédure d'incidents incomplète** (délais RGPD, kit de crise)

### 1.5 Plan d'actions priorisé

**4 actions critiques (P1)** à traiter avant le **28 février 2026** :
1. Implémenter MFA obligatoire (échéance : 31/01/2026)
2. Compléter stratégie sauvegarde + tests trimestriels (échéance : 28/02/2026)
3. Mettre en place politique correctifs (échéance : 15/02/2026)
4. Compléter procédure incidents + kit de crise (échéance : 15/02/2026)

**3 actions importantes (P2)** à traiter avant le **28 février 2026** :
5. Renforcer isolation Wi‑Fi invité (échéance : 31/01/2026)
6. Compléter clauses RGPD dans contrats (échéance : 28/02/2026)
7. Implémenter politique verrouillage session (échéance : 31/01/2026)

**Coût total estimé** : 0€ à 1000€ (principalement configuration et rédaction interne)

---

## 2. Contexte et périmètre

### 2.1 Présentation de l'organisation

La **Clinique Santé Plus** est une clinique médicale de petite taille (≈ 15 employés) assurant des soins médicaux généraux et des analyses biologiques. Elle gère quotidiennement des **données de santé sensibles** (dossiers patients, informations administratives) soumises au **RGPD** et à l'**Hébergement de Données de Santé (HDS)**.

**Contexte réglementaire** :
- **RGPD** : Obligations de sécurité (art. 32), notification violations (art. 33-34), registre traitements (art. 30)
- **HDS** : Hébergement des données de santé par un prestataire certifié HDS
- **Secteur santé** : Cible privilégiée des cyberattaques (ransomwares, fuites de données)

### 2.2 Périmètre de l'audit

**Inclus** :
- **Systèmes** : 8 postes Windows 11 Pro, réseau interne/Wi‑Fi, application SaaS MedSimple, Microsoft 365
- **Processus** : Gestion des accès (M365, MedSimple), sauvegardes, gestion des incidents, conformité RGPD/HDS
- **Organisation** : Direction, IT (prestataire), utilisateurs métiers

**Exclus** :
- Tests d'intrusion
- Audits physiques des locaux
- Systèmes externes non maîtrisés par la clinique
- Tests de charge/performance

### 2.3 Référentiels utilisés

- **ISO/IEC 27001:2022** : Cadre de management de la SSI (clauses 4-10)
- **ISO/IEC 27002:2022** : Bonnes pratiques de sécurité (contrôles sélectionnés)
- **RGPD** : Règlement Général sur la Protection des Données (articles 28, 30, 32, 33, 34)
- **ANSSI** : Recommandations hygiène informatique, guides sectoriels
- **HDS** : Référentiel Hébergement de Données de Santé (attestation prestataire)

---

## 3. Méthodologie

### 3.1 Approche d'audit

L'audit a été conduit selon une approche **non intrusive** et **factuelle**, alignée sur les principes ISO 19011 (lignes directrices pour l'audit).

**Principes** :
- **Indépendance** : Équipe externe (étudiants Efrei Paris)
- **Objectivité** : Constats basés sur des preuves (30 preuves collectées)
- **Confidentialité** : Toutes les données sensibles ont été anonymisées
- **Non-intrusion** : Aucune action intrusive (pas de scans agressifs, pas d'exploitation)

### 3.2 Techniques d'audit utilisées

1. **Revue documentaire** : Politiques, procédures, contrats, DPA, attestations
2. **Entretiens** : Direction, référent SI, prestataire IT, utilisateurs métiers
3. **Observations techniques** : Configuration postes, réseau, consoles (lecture seule)
4. **Exports/rapports** : M365, MedSimple, EDR, sauvegardes (anonymisés)
5. **Exercice table-top** : Scénario ransomware (30 min)

### 3.3 Échantillonnage

- **Postes** : 3 postes échantillons (accueil, médecin, direction) sur 8
- **Comptes** : 6 comptes M365 (3 récents, 3 anciens) sur 15
- **Profils applicatifs** : 3 profils MedSimple (accueil, médecin, admin) sur 5
- **Contrats** : 2-3 contrats prestataires (IT, hébergeur MedSimple)

### 3.4 Preuves collectées

**30 preuves** ont été collectées et référencées dans le registre de preuves (`05_registre_preuves.csv`), réparties comme suit :
- **Documents** : 12 (politiques, procédures, contrats, DPA)
- **Exports** : 10 (M365, MedSimple, EDR, sauvegardes)
- **Captures** : 6 (configurations, paramètres, logs)
- **Observations** : 2 (postes, test restauration)

Toutes les preuves ont été **anonymisées** (identifiants, données patients, adresses IP).

---

## 4. Analyse des risques

### 4.1 Méthode d'évaluation

Les risques ont été évalués selon une **matrice de criticité** combinant :
- **Impact** : Faible / Moyen / Élevé / Très élevé
- **Probabilité** : Faible / Moyenne / Élevée
- **Criticité** : Impact × Probabilité

### 4.2 Cartographie des risques

| ID | Risque | Impact | Probabilité | Criticité | Constat associé |
|---|---|---|---|---|---|
| **R-001** | Compromission comptes utilisateurs (phishing) | Élevé | Moyenne | **Élevée** | C-001 |
| **R-002** | Perte définitive données critiques (ransomware/panne) | Très élevé | Moyenne | **Très élevée** | C-002 |
| **R-003** | Exploitation vulnérabilités non corrigées | Élevé | Moyenne | **Élevée** | C-003 |
| **R-004** | Accès non autorisé depuis Wi‑Fi invité | Moyen | Faible à Moyenne | **Moyenne** | C-004 |
| **R-005** | Réaction inadaptée incident majeur | Très élevé | Moyenne | **Très élevée** | C-005 |
| **R-006** | Non-conformité RGPD (contrats) | Élevé | Faible à Moyenne | **Moyenne** | C-006 |
| **R-007** | Accès non autorisé postes sans surveillance | Moyen | Faible | **Moyenne** | C-007 |

### 4.3 Top 3 des risques critiques

#### R-002 : Perte définitive de données critiques
- **Scénario** : Ransomware chiffre postes + NAS local. Restauration depuis copie hors site échoue (non testée). Données perdues définitivement.
- **Impact** : Perte dossiers patients, interruption soins, non-conformité RGPD/HDS, arrêt d'activité
- **Mesures existantes** : Sauvegardes quotidiennes M365, hebdomadaires NAS, copie hors site
- **Mesures recommandées** : Tests restauration trimestriels, vérification chiffrement offsite, export MedSimple

#### R-005 : Réaction inadaptée incident majeur
- **Scénario** : Ransomware chiffre systèmes. Équipe ne sait pas qui contacter, ne respecte pas délai CNIL (72h), communique mal aux patients.
- **Impact** : Violation RGPD, sanctions CNIL, perte confiance patients, interruption activité
- **Mesures existantes** : Procédure incidents (incomplète), exercice table-top réalisé
- **Mesures recommandées** : Compléter procédure (délais, RACI), créer kit de crise, exercices trimestriels

#### R-001 : Compromission comptes utilisateurs
- **Scénario** : Attaquant obtient identifiants via phishing. Sans MFA, accès immédiat au compte, exfiltration données patients.
- **Impact** : Accès non autorisé données santé, violation RGPD, interruption activité
- **Mesures existantes** : MFA activée pour admins (40% utilisateurs)
- **Mesures recommandées** : MFA obligatoire 100% comptes, politique Conditional Access

### 4.4 Risques résiduels acceptables

Après mise en œuvre des recommandations, les risques suivants resteront à un niveau **acceptable** (surveillance continue) :
- **R-004** : Accès non autorisé Wi‑Fi invité (isolation renforcée, probabilité réduite)
- **R-006** : Non-conformité RGPD (contrats complétés, risque réduit)
- **R-007** : Accès non autorisé postes (verrouillage 5 min, probabilité réduite)

---

## 5. Constats détaillés

**7 constats** ont été formulés selon la structure : Critère → Observation → Preuve → Risque → Recommandation.

### 5.1 Constat C-001 : Absence de MFA obligatoire pour tous les comptes Microsoft 365

**Criticité : Élevée** | **Priorité : P1**

**Résumé** : Seulement 40% des comptes utilisateurs ont activé la MFA. Aucune politique de Conditional Access n'impose la MFA de manière obligatoire.

**Recommandation** : Implémenter une politique de Conditional Access imposant la MFA obligatoire pour 100% des comptes.

**Échéance** : 31 janvier 2026 | **Coût** : 0€

*Détails complets dans `06_fiches_constats.md` (section C-001)*

### 5.2 Constat C-002 : Stratégie de sauvegarde incomplète et absence de test de restauration récent

**Criticité : Très élevée** | **Priorité : P1**

**Résumé** : Dernier test de restauration remonte à 8 mois. Pas de sauvegarde dédiée MedSimple. RTO/RPO non documentés. Chiffrement offsite non vérifié.

**Recommandation** : Compléter stratégie 3-2-1, formaliser tests restauration trimestriels, documenter RTO/RPO.

**Échéance** : 28 février 2026 | **Coût** : 500€/an (si export MedSimple payant)

*Détails complets dans `06_fiches_constats.md` (section C-002)*

### 5.3 Constat C-003 : Retard dans l'application des correctifs de sécurité

**Criticité : Élevée** | **Priorité : P1**

**Résumé** : Retards de 10 à 22 jours sur les correctifs critiques Windows. Aucune politique formelle de gestion des correctifs. Mises à jour "à la demande" non automatisées.

**Recommandation** : Mettre en place politique de correctifs avec application automatique (7 jours pour critiques).

**Échéance** : 15 février 2026 | **Coût** : 0€

*Détails complets dans `06_fiches_constats.md` (section C-003)*

### 5.4 Constat C-004 : Isolation insuffisante du réseau Wi‑Fi invité

**Criticité : Moyenne** | **Priorité : P2**

**Résumé** : WPS activé (risque). Règles pare-feu permettent accès partiel invité → interne. Pas de limitation bande passante. Pas de portail captif.

**Recommandation** : Désactiver WPS, bloquer trafic invité → interne, limiter bande passante.

**Échéance** : 31 janvier 2026 | **Coût** : 0€

*Détails complets dans `06_fiches_constats.md` (section C-004)*

### 5.5 Constat C-005 : Procédure de gestion des incidents incomplète

**Criticité : Très élevée** | **Priorité : P1**

**Résumé** : Procédure manque détails (RACI, délais CNIL, communication). Exercice table-top révèle confusion délai CNIL (72h), pas de kit de crise, décision communication non préparée.

**Recommandation** : Compléter procédure (RACI, délais), créer kit de crise, planifier exercices trimestriels.

**Échéance** : 15 février 2026 | **Coût** : 0€

*Détails complets dans `06_fiches_constats.md` (section C-005)*

### 5.6 Constat C-006 : Clauses RGPD incomplètes dans les contrats

**Criticité : Moyenne** | **Priorité : P2**

**Résumé** : DPA prestataire IT manque clauses (notification incidents, sous-traitants ultérieurs, audit). Pas de registre sous-traitants.

**Recommandation** : Compléter DPA, créer registre sous-traitants, réviser annuellement.

**Échéance** : 28 février 2026 | **Coût** : 0€ à 500€ (si consultation juridique)

*Détails complets dans `06_fiches_constats.md` (section C-006)*

### 5.7 Constat C-007 : Absence de politique de verrouillage automatique des sessions

**Criticité : Moyenne** | **Priorité : P2**

**Résumé** : Verrouillage 10-30 minutes ou absent selon postes. Pas de politique centralisée. Pas de sensibilisation.

**Recommandation** : Implémenter verrouillage 5 min max, sensibiliser personnel, monitorer conformité.

**Échéance** : 31 janvier 2026 | **Coût** : 0€

*Détails complets dans `06_fiches_constats.md` (section C-007)*

---

## 6. Recommandations et plan d'actions

### 6.1 Plan d'actions priorisé

| ID | Action | Responsable | Échéance | Coût | Priorité | Statut |
|---|---|---|---|---|---|---|
| **P-1** | Implémenter MFA obligatoire (100% comptes) | Prestataire IT | 31/01/2026 | 0€ | **P1** | À faire |
| **P-2** | Compléter stratégie sauvegarde + tests trimestriels | Prestataire IT | 28/02/2026 | 500€/an | **P1** | À faire |
| **P-3** | Mettre en place politique correctifs (7j critiques) | Prestataire IT | 15/02/2026 | 0€ | **P1** | À faire |
| **P-4** | Renforcer isolation Wi‑Fi invité | Prestataire IT | 31/01/2026 | 0€ | **P2** | À faire |
| **P-5** | Compléter procédure incidents + kit de crise | Direction | 15/02/2026 | 0€ | **P1** | À faire |
| **P-6** | Compléter clauses RGPD (contrats) | Direction | 28/02/2026 | 0-500€ | **P2** | À faire |
| **P-7** | Implémenter politique verrouillage session (5 min) | Prestataire IT | 31/01/2026 | 0€ | **P2** | À faire |

### 6.2 Planning de mise en œuvre

**Janvier 2026** :
- **Semaine 1-2** : P-1 (MFA), P-4 (Wi‑Fi), P-7 (Verrouillage)

**Février 2026** :
- **Semaine 1-2** : P-3 (Correctifs), P-5 (Incidents)
- **Semaine 3-4** : P-2 (Sauvegardes), P-6 (RGPD)

**Mars 2026** :
- **Suivi** : Vérification mise en œuvre, tests restauration (P-2), exercice incident (P-5)

### 6.3 Indicateurs de suivi

- **Taux MFA activée** : Objectif 100% (P-1)
- **Tests restauration** : 4/an (trimestriel) (P-2)
- **Délai correctifs critiques** : ≤ 7 jours (P-3)
- **Exercices incidents** : 4/an (trimestriel) (P-5)
- **Conformité verrouillage** : 100% postes ≤ 5 min (P-7)

### 6.4 Coûts estimés

- **Configuration/rédaction interne** : 0€ (P-1, P-3, P-4, P-5, P-7)
- **Export MedSimple** : 500€/an (P-2)
- **Consultation juridique** : 0€ à 500€ (P-6, optionnel)

**Total** : **0€ à 1000€** (principalement rédaction et configuration)

---

## 7. Conclusion

### 7.1 Bilan global

L'audit a révélé un **niveau de sécurité global acceptable** pour une organisation de petite taille, avec des **points positifs** (MFA admins, sauvegardes partielles, EDR déployé) mais également **7 constats** nécessitant une attention prioritaire.

**Les risques les plus critiques** concernent :
1. La **gestion des sauvegardes** (tests non réguliers)
2. La **gestion des incidents** (procédure incomplète)
3. L'**authentification** (MFA non obligatoire)
4. La **gestion des correctifs** (retards)

### 7.2 Recommandations prioritaires

**4 actions critiques (P1)** doivent être traitées avant le **28 février 2026** :
- Implémenter MFA obligatoire (P-1)
- Compléter stratégie sauvegarde + tests (P-2)
- Mettre en place politique correctifs (P-3)
- Compléter procédure incidents + kit de crise (P-5)

**3 actions importantes (P2)** peuvent être traitées en parallèle :
- Renforcer isolation Wi‑Fi invité (P-4)
- Compléter clauses RGPD (P-6)
- Implémenter politique verrouillage (P-7)

### 7.3 Perspectives

Après mise en œuvre des recommandations, la clinique disposera d'un **niveau de sécurité renforcé**, aligné sur les bonnes pratiques ISO/IEC 27001/27002, ANSSI, et RGPD, adapté à sa taille et à ses moyens.

**Prochaines étapes recommandées** :
- **Audit de suivi** : 6 mois après mise en œuvre (vérification actions)
- **Amélioration continue** : Révision annuelle des politiques, exercices trimestriels, veille réglementaire

---

## 8. Annexes

### 8.1 Liste des documents de référence

- **01_lettre_de_mission.md** : Lettre de mission (S1)
- **02_note_de_cadrage.md** : Note de cadrage (S1)
- **03_programme_audit.csv** : Programme d'audit (20 contrôles)
- **04_journal_de_bord.csv** : Journal de bord (S2-S4)
- **05_registre_preuves.csv** : Registre de preuves (30 preuves)
- **06_fiches_constats.md** : Fiches constats détaillées (7 constats)
- **10_acces_outils_simules_et_verifications_techniques.md** : Vérifications techniques (14 vérifications)

### 8.2 Glossaire

- **MFA** : Multi-Factor Authentication (Authentification multifacteur)
- **RTO** : Recovery Time Objective (Objectif de temps de récupération)
- **RPO** : Recovery Point Objective (Objectif de point de récupération)
- **DPA** : Data Processing Agreement (Contrat de traitement de données)
- **HDS** : Hébergement de Données de Santé
- **EDR** : Endpoint Detection and Response (Détection et réponse sur les terminaux)
- **GPO** : Group Policy Object (Objet de stratégie de groupe)

### 8.3 Références réglementaires

- **ISO/IEC 27001:2022** : Information security management systems — Requirements
- **ISO/IEC 27002:2022** : Information security controls
- **RGPD** : Règlement (UE) 2016/679 du 27 avril 2016
- **ANSSI** : Agence Nationale de la Sécurité des Systèmes d'Information
- **HDS** : Référentiel Hébergement de Données de Santé (certification)

---

**Fin du rapport**

*Document préparé par l'Équipe Audit SSI — Efrei Paris*  
*Date de finalisation : 5 janvier 2026*  

