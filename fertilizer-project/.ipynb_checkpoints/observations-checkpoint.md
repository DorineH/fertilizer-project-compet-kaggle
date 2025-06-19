**Obersvation et hypothèses**

Explication des colonnes :
id : Identifiant unique pour chaque ligne (un simple numéro).
Temperature : Température de l’environnement (en °C).
Humidity : Humidité de l’air (en %).
Moisture : Humidité du sol (en %).
Soil Type : Type de sol (ex. : Clayey = argileux, Sandy = sableux, Red = sol rouge).
Crop Type : Type de culture (ex. : Sugarcane = canne à sucre, Millets = mils, etc.).
Nitrogen : Teneur en azote (élément nutritif essentiel pour les plantes).
Potassium : Teneur en potassium (aide à la floraison et la fructification).
Phosphorous : Teneur en phosphore (important pour les racines).
Fertilizer Name : Nom de l’engrais recommandé (ex. : 28-28, DAP, 17-17-17 – cela indique les proportions N-P-K = Azote-Phosphore-Potassium).



<!-- Quels facteurs (météo, sol, culture) semblent le plus discriminants ? -->
La heatmap de corrélation montre que les variables numériques (température, humidité, azote, etc.) sont très peu corrélées entre elles. Cela signifie qu’elles apportent chacune des informations indépendantes, ce qui est bon pour un modèle prédictif.

En revanche, aucune de ces variables ne se distingue comme particulièrement dominante via la corrélation.

Le tableau de données suggère que les facteurs qualitatifs comme "Soil Type" et "Crop Type" influencent fortement le choix de l’engrais.
Ex : Sandy + Millets → souvent 17-17-17 ou 28-28
Clayey + Sugarcane → 28-28

Donc les facteurs les plus discriminants semblent être : Soil Type (Type de sol), Crop Type (Type de culture), Puis les nutriments (N, P, K)

Conclusion : Le type de sol et de culture sont probablement les facteurs les plus déterminants pour choisir un engrais.



<!-- Y-a-t-il des classes d’engrais très rares ? -->
À partir du graphique de répartition des engrais :
Les engrais comme "DAP" et "Urea" sont clairement moins utilisés, consiédérer comme rare..

"14-35-14", "20-20", "10-26-26", "28-28", "17-17-17" ont des comptes proches de 110 000 à 115 000.

"DAP" et "Urea" tournent autour de 90 000 à 95 000, donc beaucoup moins fréquents.



<!-- Des valeurs aberrantes ou distributions inhabituelles ? -->
Matrice de corrélation très proche de 0 partout (hors diagonale) : aucune relation forte → pas de redondance, mais aussi potentiel bruit ou variabilité élevée.

Dans le tableau des données :
2cart entre les valeurs importante : Humidité du sol de 32 à 65, Phosphore de 2 à 18

Aucune valeur anormalement extrême ou incohérente, donc pas de valeur absurde.

Répartition des engrais : relativement équilibrée (sauf les 2 rares).

Résumé :
| Question                   | Réponse                                                                                                  |
| -------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Facteurs discriminants** | Surtout **Soil Type** et **Crop Type**, puis les nutriments (NPK)                                        |
| **Engrais rares**          | Oui : **DAP** et **Urea**                                                                                |
| **Valeurs aberrantes**     | Non détectées visuellement, mais **variabilité importante** (attention au preprocessing si modélisation) |
