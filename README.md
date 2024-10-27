import folium

# Création de la carte centrée sur le globe
world_map = folium.Map(location=[20, 0], zoom_start=2)

# Définition des emplacements des data centers pour chaque entreprise (fictif pour exemple)
data_centers = {
    "AWS": [[37.7749, -122.4194], [52.5200, 13.4050], [35.6895, 139.6917]],  # USA, Allemagne, Japon
    "Microsoft Azure": [[47.6062, -122.3321], [51.5074, -0.1278], [22.3193, 114.1694]],  # USA, UK, Hong Kong
    "Google Cloud": [[37.7749, -122.4194], [48.8566, 2.3522], [35.6762, 139.6503]],  # USA, France, Japon
    "Meta (Facebook)": [[45.4215, -75.6972], [53.3498, -6.2603], [1.3521, 103.8198]],  # Canada, Irlande, Singapour
    "IBM Cloud": [[40.7128, -74.0060], [51.1657, 10.4515], [34.0522, -118.2437]],  # USA, Allemagne, USA
    "Alibaba Cloud": [[39.9042, 116.4074], [22.3964, 114.1095], [1.3521, 103.8198]],  # Chine, Hong Kong, Singapour
    "Oracle Cloud": [[37.7749, -122.4194], [55.7558, 37.6176], [33.8688, 151.2093]]  # USA, Russie, Australie
}

# Boucle pour ajouter les marqueurs de chaque data center
for provider, locations in data_centers.items():
    for location in locations:
        folium.Marker(
            location=location,
            popup=f"{provider} Data Center",
            icon=folium.Icon(color="blue", icon="cloud")
        ).add_to(world_map)

# Sauvegarder la carte en HTML
world_map.save("data_centers_world_map.html")
world_map
