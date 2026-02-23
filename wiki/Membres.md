# 👥 O.B.I. -- Membres
Voici la liste des nations membres actuelles :
* Prismara
* A Altaiea

---

### 🗺️ Carte des Territoires
<div id="map" style="height: 500px; width: 100%; background: #222; border: 2px solid #55ff55;"></div>

<script>
    // Cette fonction va s'auto-exécuter pour vérifier si Leaflet est là
    (function initMap() {
        const mapDiv = document.getElementById('map');
        
        // Si Leaflet n'est pas chargé, on l'ajoute dynamiquement
        if (typeof L === 'undefined') {
            console.log("Leaflet manquant, chargement...");
            const script = document.createElement('script');
            script.src = "https://unpkg.com/leaflet@1.9.4/dist/leaflet.js";
            const link = document.createElement('link');
            link.rel = "stylesheet";
            link.href = "https://unpkg.com/leaflet@1.9.4/dist/leaflet.css";
            document.head.appendChild(script);
            document.head.appendChild(link);
            
            script.onload = () => setupMap();
        } else {
            setupMap();
        }

        function setupMap() {
            // Destruction de l'ancienne carte si elle existe
            if (window.myMap) { window.myMap.remove(); }

            const map = L.map('map', { 
                crs: L.CRS.Simple, 
                minZoom: -5
            });
            window.myMap = map;

            // Système NationsGlory (1 chunk = 16 blocs)
            function addChunkZone(x, z, x2, z2, color, name) {
                const north = -z * 16;
                const west = x * 16;
                const south = -(z2 + 1) * 16;
                const east = (x2 + 1) * 16;
                L.rectangle([[south, west], [north, east]], {
                    color: color, weight: 2, fillOpacity: 0.4
                }).addTo(map).bindPopup("<b>" + name + "</b>");
            }

            // --- AJOUTE TES ZONES ICI ---
            addChunkZone(0, 0, 10, 10, "#55ff55", "Prismara");
            addChunkZone(15, -5, 25, 5, "#5555ff", "A Altaiea");

            map.setView([-100, 100], -2);
            
            // Force l'affichage correct
            setTimeout(() => { map.invalidateSize(); }, 500);
        }
    })();
</script>