# 👥 O.B.I. -- Membres
Voici la liste des nations membres actuelles :

* **Prismara**
* **A Altaiea**

---

---
### 🗺️ Carte des Territoires O.B.I.
<div id="map"></div>

<script>
    // Initialisation de la carte (Système Minecraft)
    var map = L.map('map', { 
        crs: L.CRS.Simple, 
        minZoom: -3 
    });

    // Fonction pour dessiner un pays
    // addZone(X, Z, Largeur, Hauteur, Couleur, Nom)
    function addZone(x, z, w, h, color, name) {
        var bounds = [[-z - h, x], [-z, x + w]]; 
        L.rectangle(bounds, {color: color, weight: 2, fillOpacity: 0.5})
         .addTo(map)
         .bindPopup("<b>" + name + "</b>");
    }

    // AJOUTE TES PAYS ICI :
    addZone(0, 0, 160, 160, "#55ff55", "Prismara");
    addZone(200, -100, 150, 150, "#5555ff", "A Altaiea");

    // Centrer la carte sur les membres
    map.setView([-50, 100], -1);
</script>