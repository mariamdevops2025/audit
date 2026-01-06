# P-018 : Configuration Wi‑Fi
**Date : 14 décembre 2025** | **Source : Pare-feu/Routeur** | **Type : Capture**

---

## Configuration réseau Wi‑Fi — Clinique Santé Plus

### Réseau interne
**SSID** : `SANTEPLUS-INTERNE`
- **Chiffrement** : WPA2-PSK
- **Mot de passe** : [Masqué]
- **WPS** : ❌ **Désactivé** (bonne pratique)
- **Isolation clients** : Désactivée (postes peuvent communiquer entre eux)

### Réseau invité
**SSID** : `SANTEPLUS-INVITES`
- **Chiffrement** : WPA2-PSK
- **Mot de passe** : [Masqué]
- **WPS** : ⚠️ **Activé** (risque)
- **Isolation clients** : Activée (clients invités isolés entre eux)
- **VLAN** : VLAN 100 (séparé du réseau interne)

### Observations
- ✅ Réseau invité sur VLAN séparé
- ⚠️ WPS activé sur réseau invité (risque d'attaque par force brute)
- ⚠️ Règles pare-feu à vérifier (isolation invité → interne)

---

*Capture anonymisée — Audit SSI Efrei Paris*
