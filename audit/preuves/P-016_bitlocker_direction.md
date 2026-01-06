# P-016 : État BitLocker — Poste Direction
**Date : 12 décembre 2025** | **Source : Poste direction** | **Type : Observation**

---

## État du chiffrement BitLocker — Poste Direction

### Commande PowerShell exécutée
```powershell
Get-BitLockerVolume
```

### Résultats

**Volume C:** (Disque système)
- **Statut de chiffrement** : ✅ **Chiffré**
- **Pourcentage chiffré** : 100%
- **Méthode de chiffrement** : XTS-AES 128
- **Protecteurs** : TPM + PIN
- **Date de chiffrement** : 15 janvier 2025

**Volume D:** (Données, si présent)
- **Statut** : Non applicable (pas de volume D:)

### Observations
- ✅ Chiffrement BitLocker activé et complet
- ✅ Protection TPM + PIN (bonne pratique)
- ⚠️ Pas de vérification sur les autres postes (accueil, secrétariat, médecins)

---

*Observation anonymisée — Audit SSI Efrei Paris*
