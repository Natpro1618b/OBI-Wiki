# 👥 O.B.I. -- Membres
Voici la liste des nations membres actuelles :
* Prismara
* A Altaiea

---

### 🗺️ Carte des Territoires
<div id="map" style="height: 500px; width: 100%; background: #111; border: 1px solid #333;"></div>

<script>
    setTimeout(function() {
        if (typeof L !== 'undefined') {
            var map = L.map('map', { 
                crs: L.CRS.Simple, 
                minZoom: -4
            });

            // FONCTION SPÉCIALE NATIONSGLORY
            // x, z : Coordonnées du premier chunk
            // x2, z2 : Coordonnées du dernier chunk
            function addChunkZone(x, z, x2, z2, color, name) {
                // On multiplie par 16 pour convertir les chunks en blocs
                var north = -z * 16;
                var west = x * 16;
                var south = -(z2 + 1) * 16;
                var east = (x2 + 1) * 16;

                L.rectangle([[south, west], [north, east]], {
                    color: color, 
                    weight: 1, 
                    fillOpacity: 0.4
                }).addTo(map).bindPopup("<b>" + name + "</b>");
            }

            // --- EXEMPLE DE SAISIE ---
            // Si Prismara va du chunk (10, 10) au chunk (20, 20) :
            addChunkZone(10, 10, 20, 20, "#55ff55", "Prismara");
            
            // Si A Altaiea est un seul gros chunk à (50, -30) :
            addChunkZone(50, -30, 50, -30, "#5555ff", "A Altaiea");

            map.setView([-150, 150], -2);
            setTimeout(function(){ map.invalidateSize(); }, 200);
        }
    }, 100);
</script>