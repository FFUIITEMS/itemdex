Interfaz Web

- Visita https://itemdex.netlify.app/ y utiliza el cuadro de búsqueda en la parte superior para encontrar objetos.
- Haz clic en cualquier resultado para ver su información detallada:
  - Nombre, Descripción
  - Nombre del Icono ("IconName"), ID del Objeto ("ItemID")
  - Tipo, Rareza
- La interfaz ofrece una forma sencilla e intuitiva de explorar y consultar todos los objetos disponibles del juego.

Uso de la API en la interfaz web:

- Paginación: "/?page={page}"
- Rareza: "/?rare={rarity}"
- Búsqueda: "/?q={query}"
- Tipo: "/?type={type}"
- Modo: "/?mode={mode}"

---

API Web

- Utiliza los endpoints para integrar los datos. Busca objetos mediante "/api/items?raw={query}" o consulta todos los datos con "/api/data/items".
- También puedes utilizar el archivo "ItemData.json" (https://github.com/FFUIITEMS/itemdex/blob/master/src/assets/itemData.json).

[
  {
    "1": "iconName",
    "2": "itemID",
    "3": "name",
    "4": "description",
    "5": "rarity",
    "6": "type"
  }
]

- La API devuelve datos en formato JSON con los detalles de cada objeto, incluyendo su ID, nombre, descripción, tipo y rareza. Esto permite utilizarlos en aplicaciones automatizadas y en el procesamiento de datos.

Endpoints

- Búsqueda: GET "/api/items?raw={query}"
- Todos los datos: GET "/api/data/items"

Ejemplos

curl "https://itemdex.netlify.app/api/items?raw=Alok"

Respuesta JSON:

{
  "query": "Alok",
  "count": 29,
  "results": [
    {
      "itemID": "102000015",
      "name": "Alok",
      "description": "Descripción del objeto",
      "iconName": "Icon_name",
      "type": "Personajes",
      "rarity": "Épico",
      "openInWeb": "https://itemdex.netlify.app/?q=102000015"
    }
  ]
}

Ejemplos de integración: JavaScript y Python

JavaScript:

async function searchItems(query) {
  const response = await fetch(
    `https://itemdex.netlify.app/api/items?raw=${encodeURIComponent(query)}`
  );
  return await response.json();
}

Python:

import requests

def searchItems(query):
    response = requests.get(
        f"https://itemdex.netlify.app/api/items?raw={query}"
    )
    return response.json()

---

Rarezas y tipos de objetos

Categoría| Tipos| Rareza
Personajes y personalización| Characters, Look Changer| Raro
Ropa| Top, Bottom, Shoe, Head, Mask, Facepaint| Mítico
Apariencias, armas y combate| Weapon Skins, Weapon Crates, Skill Skins, Fist Skins, Grenade Skins, Gloo Walls| Mítico+
Apariencias, equipo y objetos| Bag Skins, Parachute, Skyboard, Skywings| Épico
Apariencias de vehículos| Vehicle Skins| Épico+
Emotes y animaciones| Emote, Super Emote, Arrival Animation, Final Shots| Artefacto
Mascotas| Pets, Pet Skin, Pet Emote, Pet Skill| Poco común
Avatares y perfil| Avatars, Avatar Frame, Profile Pin| Común
Fotos y social| Photo Frame, Photo Pose, Photo Sticker| —
Música y voces| Music, Voice Packs| —
Tarjetas y banners| Battle Cards, Banners| —
Botín y cajas| Loot Box, Loot Crates, Choice Crates| —
Tokens y cupones| Exchange Tokens, Vouchers| —
Paquetes y especiales| Bundles, Hyper Book| —

---

Guía de uso

- Interfaz web: Utilízala para explorar visualmente los objetos y consultar sus detalles.
- API web: Utilízala para integraciones programáticas y automatizaciones.
- La búsqueda admite coincidencias parciales y no distingue entre mayúsculas y minúsculas.
- Una consulta vacía devuelve todos los objetos disponibles, tanto en la web como en la API.
- Utiliza enlaces directos para acceder a los objetos mediante su ID:

"https://itemdex.netlify.app/?q={ItemID}"

---

