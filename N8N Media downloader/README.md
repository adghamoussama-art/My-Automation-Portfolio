Description du Workflow : Ce flux de travail n8n gère de manière autonome les messages reçus par un bot Telegram. Il utilise une logique conditionnelle pour séparer les messages textuels, traités par une Intelligence Artificielle, des liens de réseaux sociaux dont il extrait automatiquement les vidéos.
1. Analyse et Tri Initial
Déclencheur (Telegram Trigger) : S'active à la réception de chaque message.
Condition (Nœud IF) : Vérifie la structure du message. Si le texte n'est pas un lien, le flux se dirige vers la branche IA. Si c'est un lien, il est envoyé vers le nœud Switch pour identification de la plateforme.
2. Branche IA : Traitement du Texte
Génération : Le texte est transmis au nœud Message a model (via Google Gemini) qui génère une réponse adaptée.
Envoi : Le nœud Send a text message retourne la réponse textuelle à l'utilisateur sur Telegram.
3. Branche Médias : Extraction de Vidéos
Le nœud Switch oriente le lien vers l'un des trois canaux spécifiques selon la plateforme détectée :
Instagram : Le nœud HTTP Request effectue une requête API pour extraire la vidéo à partir du lien, puis le nœud Send a video transmet le fichier final.
TikTok : Le processus utilise deux nœuds successifs. Le nœud HTTP Request1 récupère l'adresse de téléchargement, puis le nœud HTTP Request2 télécharge la vidéo sous forme de données binaires (data) avant son envoi via le nœud Send a video2.
YouTube : Un nœud Code JavaScript extrait l'identifiant unique (ID) du lien. Cet ID est injecté dans le nœud HTTP Request3 pour appeler l'API de téléchargement, et le fichier est envoyé par le nœud Send a video1.
Synthèse : Cette architecture crée un assistant hybride capable de répondre aux questions des utilisateurs et de servir de téléchargeur universel de médias de façon entièrement automatisée.