# P-028 : PV Exercice table-top ransomware
**Date : 19 décembre 2025** | **Source : Équipe audit** | **Type : Document**

---

## Procès-verbal — Exercice table-top ransomware

### Informations générales
- **Date** : 19 décembre 2025
- **Heure** : 10:00 - 11:00
- **Participants** : Direction, Référent SI, Prestataire IT, Équipe audit
- **Scénario** : Ransomware chiffre les postes et le NAS local

### Scénario
1. **Détection** : Alertes EDR à 08:30 (poste accueil compromis)
2. **Propagation** : Ransomware se propage sur réseau (5 postes affectés)
3. **Impact** : NAS local chiffré, accès MedSimple bloqué

### Actions réalisées (simulation)
1. ✅ **Isolation** : Déconnexion réseau (10 min)
2. ✅ **Analyse** : Identification ransomware (15 min)
3. ⚠️ **Notification CNIL** : Confusion sur délai (certains pensaient 7 jours au lieu de 72h)
4. ⚠️ **Communication patients** : Décision non préparée (qui décide ? quel message ?)
5. ⚠️ **Restauration** : Procédure non documentée (étapes, contacts)

### Points forts identifiés
- Réaction rapide (isolation réseau)
- Coordination Direction/IT

### Points d'amélioration identifiés
- 🔴 **Délai CNIL** : Clarifier 72h (article 33 RGPD)
- 🔴 **Kit de crise** : Créer (contacts urgents, modèles communication)
- 🔴 **Communication patients** : Définir procédure (qui décide, quel message, quand)
- 🟡 **Procédure restauration** : Documenter (étapes, contacts prestataire)

### Actions à suivre
1. Compléter procédure incidents (délais CNIL, RACI)
2. Créer kit de crise (contacts, modèles)
3. Planifier exercices trimestriels (scénarios variés)

---

*Document anonymisé — Audit SSI Efrei Paris*
