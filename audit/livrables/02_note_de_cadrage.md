**Note de cadrage — Audit SSI**  
**Clinique Santé Plus**  
Date : **24 décembre 2025** — Préparée par : **Équipe Audit SSI (Efrei Paris)**  

## 1. Compréhension du contexte, enjeux et faisabilité
### 1.1 Contexte organisationnel
La **Clinique Santé Plus** est une clinique de petite taille (≈ 10–20 employés ; ≈ 50 patients/jour) assurant des consultations médicales et/ou actes biologiques. Elle exploite un SI composé typiquement :
- Postes de travail (accueil, secrétariat, médecins, comptabilité) ;
- Messagerie et bureautique ;
- Application de gestion patient **(ex. : “MedSimple”)** ;
- Réseau local (switch/routeur, Wi‑Fi, accès Internet) ;
- Sauvegardes (support local et/ou cloud) ;
- Prestataires (maintenance informatique, éditeur logiciel, hébergeur).

### 1.2 Données traitées et contraintes réglementaires
Les données manipulées incluent des **données personnelles** et des **données de santé** (catégories particulières). En conséquence :
- Référentiel **RGPD** : principe de sécurité, confidentialité, minimisation, traçabilité, gestion des violations ;
- Exigences de contractualisation avec les sous-traitants (articles 28 et suivants) ;
- En cas d’hébergement de données de santé par un prestataire : exigences **HDS** à vérifier au niveau contractuel/documentaire (attestations, clauses, responsabilités).

### 1.3 Enjeux SSI
- **Confidentialité** : fuite de dossiers patients, atteinte au secret médical, sanctions réglementaires et perte de confiance.
- **Intégrité** : altération de données médicales/administratives, risques cliniques et erreurs de facturation.
- **Disponibilité** : interruption de soins (rançongiciel, panne), perte de productivité, report de rendez-vous.

### 1.4 Faisabilité et niveau d’assurance visé
La mission vise une **assurance raisonnable** (revue documentaire, entretiens, observations non intrusives). Faisabilité considérée comme acceptable si :
- Documents et informations suffisants sont accessibles (même fictifs) ;
- Interlocuteurs disponibles (direction, référent SI, métiers) ;
- Fenêtre de 4 semaines compatible avec la profondeur attendue ;
- Données sensibles anonymisées dans les livrables si nécessaire.

## 2. Objectifs détaillés
- Évaluer le niveau de sécurité du SI (gouvernance, pratiques, contrôles) ;
- Vérifier l’application des bonnes pratiques et exigences réglementaires pertinentes (RGPD) ;
- Identifier et évaluer les risques majeurs affectant CIA (confidentialité, intégrité, disponibilité) ;
- Proposer un **plan d’actions priorisé**, réaliste et proportionné.

## 3. Périmètre et limites
### 3.1 Périmètre (inclus)
- Processus : accueil/administratif, consultation, gestion des dossiers, facturation, sauvegarde/restauration, gestion des accès, gestion des incidents.
- Systèmes : postes utilisateurs, comptes, réseau interne, accès Internet, application patient, stockage partagé, sauvegardes.
- Organisation : rôles et responsabilités SSI, sensibilisation, procédures, suivi prestataires.

### 3.2 Limites (exclus)
- Tests d’intrusion / exploitation de vulnérabilités ;
- Audit physique détaillé des locaux ;
- Analyse exhaustive d’un hébergeur/prestataire externe (limité aux éléments contractuels et à la gouvernance).

### 3.3 Gestion des changements de périmètre
Toute évolution du périmètre doit être :
- Justifiée (changement d’architecture, indisponibilité, force majeure) ;
- Validée par l’audité ;
- Tracée dans le journal de bord et reflétée dans les livrables.

## 4. Critères d’audit (référentiels)
### 4.1 Référentiels principaux
- **ISO/IEC 27001** : clauses 4 à 10 (contexte, leadership, planification, support, opérations, évaluation, amélioration).
- **ISO/IEC 27002** : sélection de contrôles pertinents pour petite structure, notamment :
  - Contrôle d’accès (gestion des identités, authentification, comptes partagés, droits) ;
  - Gestion des actifs et inventaires ;
  - Sécurité des postes et correctifs (patch management) ;
  - Sauvegarde et restauration ;
  - Sensibilisation et formation ;
  - Gestion des incidents et journaux ;
  - Gestion fournisseurs (contrats, sous-traitance).

### 4.2 Référentiels complémentaires
- Guides **ANSSI** (hygiène informatique, mots de passe, sauvegardes, rançongiciels) ;
- **RGPD** (articles 5, 24, 25, 28, 30, 32, 33/34 — selon disponibilité des éléments) ;
- Politiques/procédures internes de la clinique, contrats et exigences métiers.

## 5. Première analyse de risques (pressentis)
| Risque | Description | Impacts | Exemples de causes |
|---|---|---|---|
| Accès non maîtrisés | Comptes partagés, mots de passe faibles, droits excessifs | Fuite/altération dossiers, non-conformité | Absence MFA, pas de revue des droits |
| Perte de données | Sauvegardes absentes/non testées | Perte d’historique médical, arrêt d’activité | Pas de 3-2-1, pas de tests de restauration |
| Phishing / compromission | Vol d’identifiants, malware | Rançongiciel, fuite données | Sensibilisation faible, filtrage mail insuffisant |
| Postes non à jour | Correctifs manquants | Exploitation vulnérabilités | Patch management absent, antivirus obsolète |
| Indisponibilité SI | Panne/attaque sans PRA | Interruption soins | Pas de PCA/PRA, pas de procédures de continuité |

## 6. Organisation, rôles et responsabilités
Chef d’équipe : Ouali Nesrine 
Rôles (auditeurs) :
- Risques (cartographie / cotation)
- Technique (observations non intrusives)
- Preuves / journal (traçabilité)
- Conformité (ISO/RGPD, recommandations)

Rôle audité :
- Point de contact : **Direction / Référent SI**
- Mise à disposition : documents, accès lecture aux éléments nécessaires, interlocuteurs.

## 7. Approche méthodologique (synthèse)
- Cadrage : compréhension du contexte, périmètre, critères, planning, risques d’audit.
- Terrain : revue documentaire, entretiens, observations techniques non intrusives, collecte de preuves.
- Analyse : constats, évaluation impacts/probabilité, cartographie des risques, recommandations.
- Rapport/restitution : synthèse, priorisation, plan d’actions, discussion décisionnelle.

## 8. Planning prévisionnel (4 semaines)
- **Semaine 1** : cadrage (documents, périmètre, référentiels, planification, préparation entretiens)
- **Semaines 2–3** : terrain (entretiens, revue, observations, preuves, mises à jour du programme)
- **Fin Semaine 3** : analyse risques et constats (validation interne, compléments)
- **Semaine 4** : rapport + restitution (15–20 minutes)

## 9. Hypothèses, risques de mission et mesures de mitigation
| Risque de mission | Effet | Mitigation |
|---|---|---|
| Accès limité aux documents | Constatations incomplètes | Demande de docs early, alternatives, traçabilité des limites |
| Disponibilité faible des interlocuteurs | Retard planning | Planifier J1, créneaux courts, relances |
| Sensibilité des données | Restriction de preuves | Anonymisation, captures masquées, preuves indirectes |
| Périmètre mouvant | Dérive | Procédure de change formalisée (section 3.3) |

Cette note complète la lettre de mission et servira de base au programme d’audit.  

**Cordialement,**  
Équipe Audit SSI — Efrei Paris

