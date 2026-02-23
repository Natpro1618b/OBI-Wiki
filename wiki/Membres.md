# 👥 O.B.I. -- Membres
Voici la liste des nations membres actuelles :

* **Prismara**
* **A Altaiea**

---

### 🗺️ Carte des Territoires
<div id="map"></div>

<script>
    // 1. Initialisation de la carte (système de coordonnées Minecraft)
    var map = L.map('map', { 
        crs: L.CRS.Simple, 
        minZoom: -3 
    });

    // 2. Définition des zones (X, Z, Largeur, Hauteur, Couleur, Nom)
    function addZone(x, z, w, h, color, name) {
        // Inversion Z pour correspondre au rendu 2D classique
        var bounds = [[-z - h, x], [-z, x + w]]; 
        L.rectangle(bounds, {color: color, weight: 2, fillOpacity: 0.5})
         .addTo(map)
         .bindPopup("<b>" + name + "</b>");
    }

    // 3. Ajoute tes pays ici (Coordonnées Minecraft)
    // Exemple : Prismara commence à X:0, Z:0 et fait 160x160 blocs
    addZone(0, 0, 160, 160, "#55ff55", "Prismara");
    
    // Exemple : A Altaiea commence à X:200, Z:-100
    addZone(200, -100, 150, 150, "#5555ff", "A Altaiea");

    // 4. Centrer la vue
    map.setView([-50, 100], -1);
</script>