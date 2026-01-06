# P-025 : PV Test de restauration
**Date : 18 décembre 2025** | **Source : Prestataire IT** | **Type : Document**

---

## Procès-verbal de test de restauration

### Informations générales
- **Date du test** : 18 décembre 2025
- **Heure** : 09:00 - 10:00
- **Responsable** : [Nom prestataire anonymisé]
- **Témoins** : Équipe audit SSI

### Scénario testé
- **Type** : Restauration d'un fichier depuis sauvegarde NAS (poste accueil)
- **Fichier test** : Document anonymisé (fichier fictif de test)
- **Date sauvegarde source** : 8 décembre 2025 (sauvegarde hebdomadaire)

### Résultats
- **Statut** : ✅ **Succès**
- **Durée restauration** : 12 minutes
- **Intégrité** : Fichier restauré intact (hash MD5 vérifié)
- **RTO observé** : 12 minutes (objectif : 24h)
- **RPO observé** : 7 jours (sauvegarde hebdomadaire)

### Observations
- ✅ Restauration fonctionnelle
- ⚠️ Dernier test précédent : Avril 2025 (8 mois)
- ⚠️ Pas de test de restauration complète système (seulement fichier)
- ⚠️ RTO/RPO non documentés formellement

### Recommandations
- Planifier tests restauration **trimestriels**
- Tester restauration complète système (scénario ransomware)
- Documenter RTO/RPO formellement

---

*Document anonymisé — Audit SSI Efrei Paris*
