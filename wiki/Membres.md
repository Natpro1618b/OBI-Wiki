# 👥 O.B.I. -- Membres
Voici la liste des nations membres actuelles :
* Prismara
* A Altaiea

---

### 🗺️ Carte des Territoires
<div id="map" style="height: 500px; width: 100%; background: #111; border: 1px solid #333;"></div>

<script>
    // On attend un tout petit peu (100ms) que le HTML soit prêt
    setTimeout(function() {
        if (typeof L !== 'undefined') {
            // Initialisation
            var map = L.map('map', { 
                crs: L.CRS.Simple, 
                minZoom: -3 
            });

            // Dessiner les zones
            function addZone(x, z, w, h, color, name) {
    // Dans Minecraft : X = horizontal, Z = vertical (Sud positif)
    // Leaflet Simple CRS : [Y, X] -> [-Z, X]
    // On définit le rectangle par le coin Nord-Ouest et Sud-Est
    var northWest = [-z, x]; 
    var southEast = [-(z + h), x + w]; 
    
    L.rectangle([northWest, southEast], {
        color: color, 
        weight: 2, 
        fillOpacity: 0.5
    }).addTo(map).bindPopup("<b>" + name + "</b>");
}s

            addZone(0, 0, 160, 160, "#55ff55", "Prismara");
            addZone(200, -100, 150, 150, "#5555ff", "A Altaiea");

            map.setView([-50, 100], -1);
            
            // Correction d'affichage Leaflet (important)
            setTimeout(function(){ map.invalidateSize(); }, 200);
        }
    }, 100);
</script>