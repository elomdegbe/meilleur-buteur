<section class="card" id="project-overview">
  <h2>Football Data Scraper &amp; Player Ranking (FBref)</h2>
  <p>
    Ce projet Python permet d’extraire, traiter et analyser les statistiques des joueurs 
    des cinq grands championnats européens (Premier League, La Liga, Bundesliga, Serie A, Ligue 1)
    pour les saisons 2017–2025.
  </p>
  <p>
    Le dépôt comprend deux volets complémentaires :
    un <strong>scraper</strong> pour collecter les données depuis FBref et 
    un <strong>script de ranking</strong> pour nettoyer, normaliser et classer les joueurs selon leurs performances.
  </p>
</section>

<section class="card" id="execution">
  <h3>1. Exécution</h3>
  <p>
    Pour lancer le scraping et générer les fichiers CSV :
  </p>
  <pre><code>python3 meilleur_buteur.py</code></pre>
  <p>
    Pour calculer le classement des joueurs :
  </p>
  <pre><code>python3 ranking.py</code></pre>
  <p>
    Le premier script télécharge les données et enregistre un CSV par catégorie de statistiques. 
    Le second lit ces fichiers, nettoie les données, calcule les scores et produit un fichier final 
    <code>final.csv</code> contenant la note globale et le classement.
  </p>
</section>

<section class="card" id="duration">
  <h3>2. Durée d’exécution</h3>
  <p>
    L’extraction d’une catégorie prend environ <strong>6 minutes</strong>, 
    et environ <strong>30 minutes</strong> pour toutes les catégories. 
    Ce temps dépend de la connexion Internet et de la charge du site FBref.
  </p>
</section>

<section class="card" id="configuration">
  <h3>3. Paramétrage</h3>
  <p>
    Certains paramètres peuvent être personnalisés directement dans le code source :
  </p>

  <p><strong>Saisons à analyser :</strong></p>
  <pre><code>years = range(2017, 2025)</code></pre>

  <p><strong>Catégories de statistiques :</strong></p>
  <pre><code>categories = ["possession", "passing", "gca", "shooting", "playingtime"]</code></pre>

  <p><strong>Ligues concernées :</strong></p>
  <pre><code>leagues = {
  "Premier-League": "9",
  "La-Liga": "12",
  "Bundesliga": "20",
  "Serie-A": "11",
  "Ligue-1": "13"
}</code></pre>
  <p>
    Vous pouvez retirer ou ajouter des ligues en connaissant leur identifiant FBref.
  </p>
</section>

<section class="card" id="workflow">
  <h3>4. Fonctionnement général</h3>
  <p>
    Le script parcourt automatiquement les saisons définies, 
    scrape les statistiques des joueurs pour chaque ligue et catégorie (possession, passes, tirs, GCA, temps de jeu) 
    puis exporte les résultats dans des fichiers CSV distincts.
  </p>
  <p>
    Le script de ranking fusionne ensuite ces fichiers, nettoie les données (format des noms, nationalités, positions), 
    normalise les valeurs, calcule des scores par catégorie et établit un classement global.
  </p>
  <p>
    Les catégories sont pondérées pour produire différents scores : 
    <em>Performance</em> (GCA), <em>Impact</em> (temps de jeu), <em>Finition</em> (tirs), 
    <em>Dribble</em> (possession) et <em>Creativity</em> (passes).
  </p>
</section>

<section class="card" id="outputs">
  <h3>5. Fichiers générés</h3>
  <p>
    Le scraper produit un fichier CSV par catégorie, nommé par exemple :
  </p>
  <pre><code>top_5_leagues_[category]_2017-2025.csv</code></pre>
  <p>
    Le script de ranking génère ensuite un fichier par score intermédiaire 
    (<code>gca_scoring.csv</code>, <code>shooting_scoring.csv</code>, etc.)
    et un fichier final :
  </p>
  <pre><code>final.csv</code></pre>
  <p>
    Chaque ligne représente un joueur avec son équipe, sa saison, sa ligue et ses scores calculés.
  </p>
</section>

<section class="card" id="tech-stack">
  <h3>6. Technologies</h3>
  <p>
    Le projet utilise <strong>Python 3.10+</strong> et s’appuie sur :
  </p>
  <ul>
    <li><strong>crawl4ai</strong> — scraping asynchrone</li>
    <li><strong>BeautifulSoup4</strong> — parsing HTML</li>
    <li><strong>asyncio</strong> — gestion des tâches concurrentes</li>
    <li><strong>pandas</strong> — manipulation des données</li>
    <li><strong>shortuuid</strong> — génération d’identifiants uniques</li>
    <li><strong>csv</strong> — export des résultats</li>
  </ul>
</section>

<section class="card" id="installation">
  <h3>7. Installation</h3>
  <p>
    1. Assurez-vous d’avoir installé Python :
    <a href="https://www.python.org" target="_blank" rel="noopener">https://www.python.org</a>
  </p>
  <p>
    2. Clonez le dépôt :
  </p>
  <pre><code>git clone [URL du dépôt GitHub]
cd nom_du_projet</code></pre>
  <p>
    3. Installez les dépendances :
  </p>
  <pre><code>pip install -r requirements.txt</code></pre>
  <p>
    4. Installez et configurez la bibliothèque <strong>crawl4ai</strong> 
    en suivant la documentation officielle :
    <a href="https://docs.crawl4ai.com" target="_blank" rel="noopener">https://docs.crawl4ai.com</a>
  </p>
  <p>
    5. Exécutez ensuite :
  </p>
  <pre><code>python3 meilleur_buteur.py
python3 ranking.py</code></pre>
</section>

<section class="card" id="limitations">
  <h3>8. Remarques</h3>
  <p>
    Le fonctionnement dépend de la structure du site FBref. 
    Si la structure HTML change, une mise à jour du code sera nécessaire.
  </p>
  <p>
    Le processus requiert une connexion Internet stable 
    et peut être long selon le nombre de saisons et de catégories choisies.
  </p>
  <p>
    Ce projet est destiné à un usage <strong>éducatif</strong> uniquement. 
    Merci de respecter les conditions d’utilisation de FBref.
  </p>
</section>

<section class="card" id="authors">
  <h3>9. Auteurs</h3>
  <p>
    Projet développé par <strong>Ibrahim</strong>, <strong>Stephen</strong> et <strong>Elom</strong>.
    Retrouvez leurs contributions sur GitHub.
  </p>
</section>

<section class="card" id="support">
  <h3>10. Support</h3>
  <p>
    Si ce projet vous a été utile, vous pouvez le soutenir en ajoutant une étoile ⭐ sur GitHub.
    Les suggestions, issues et pull requests sont les bienvenues pour l’améliorer.
  </p>
</section>
