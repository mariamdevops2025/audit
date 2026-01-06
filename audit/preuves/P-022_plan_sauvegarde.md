# P-022 : Plan de sauvegarde
**Date : 5 décembre 2025** | **Source : Prestataire IT** | **Type : Document**

---

## Stratégie de sauvegarde — Clinique Santé Plus

### Sauvegardes quotidiennes
**Périmètre** : Documents SharePoint/OneDrive (Microsoft 365)
- **Fréquence** : Automatique (quotidienne, 02:00)
- **Rétention** : 30 jours (versioning M365)
- **Localisation** : Cloud Microsoft (géolocalisation UE)

### Sauvegardes hebdomadaires
**Périmètre** : Postes critiques (accueil + direction)
- **Fréquence** : Hebdomadaire (dimanche, 03:00)
- **Type** : Image complète (système + données)
- **Destination** : NAS local (baie réseau)
- **Rétention** : 4 semaines (4 images)

### Copie hors site
**Périmètre** : Images NAS + exports MedSimple (si applicable)
- **Fréquence** : Hebdomadaire (lundi, 04:00)
- **Destination** : Cloud prestataire (chiffrement annoncé)
- **Rétention** : 12 semaines

### Sauvegardes applicatives
**MedSimple** :
- Sauvegardes gérées par l'éditeur/hébergeur (HDS)
- Pas de sauvegarde export locale dédiée

### RTO/RPO
- **RTO** : Non documenté formellement (objectif estimé : 24h)
- **RPO** : Non documenté formellement (objectif estimé : 24h)

---

*Document anonymisé — Audit SSI Efrei Paris*
