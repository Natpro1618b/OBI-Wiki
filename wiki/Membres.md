# 👥 O.B.I. -- Membres


Voici la liste des nations membres actuelles :

* **Prismara**
* **A Altaiea**
 





# 🗺️ O.B.I. -- Carte Interactive des Territoires
<div id="map"></div>

<script>
    // Initialisation de la carte (coordonnées Minecraft centrées sur 0,0)
    var map = L.map('map', {
        crs: L.CRS.Simple,
        minZoom: -3
    });

    var bounds = [[-1000, -1000], [1000, 1000]]; // Taille de la zone affichée
    map.fitBounds(bounds);

    // Fonction pour ajouter un territoire (Chunks ou Zones)
    function addTerritory(x1, z1, x2, z2, color, name) {
        var rect = L.rectangle([[z1, x1], [z2, x2]], {
            color: color,
            weight: 2,
            fillOpacity: 0.5
        }).addTo(map);
        rect.bindPopup("<b>Territoire :</b> " + name);
    }

    // --- CONFIGURATION DES ZONES ---
    // addTerritory(X_début, Z_début, X_fin, Z_fin, "couleur", "Nom")
    
    addTerritory(0, 0, 160, 160, "#55ff55", "Prismara - Capitale");
    addTerritory(200, -100, 400, 100, "#5555ff", "A Altaiea - Port");
    addTerritory(-300, -300, -100, -100, "#ff5555", "Zone de Conflit");

    // Grille de repère (Optionnel)
    L.gridLayer({
        tileSize: 128,
        attribution: 'Grille O.B.I.'
    }).addTo(map);
</script>

### 📋 Liste des Nations
* **Prismara** (Vert)
* **A Altaiea** (Bleu)

