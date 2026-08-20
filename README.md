Qualification de Leads Automatisée via n8n et IA
Ce projet présente un workflow d'automatisation conçu sur n8n pour capturer, qualifier et traiter automatiquement les prospects en fonction de leur budget, en intégrant l'intelligence artificielle pour l'analyse des besoins.

Flux de Travail

1. Entrée et Notification
Formulaire n8n : Le prospect renseigne son nom, son email, son budget et le type de besoin.
Slack : Notification instantanée avec l'ensemble des données envoyée sur un canal dédié.
Aiguillage (Node IF) : Orientation automatique du lead selon sa capacité financière (seuil à 5000 dollars).

2. Branche Premium (Budget supérieur à 5000 dollars)
Double Opt-in : Envoi d'un email de confirmation au format HTML. Le système se met en pause via un nœud Wait jusqu'au clic sur le bouton relié à un Webhook.
Suggestions de Projets : Après validation, le prospect reçoit une liste d'idées de business (E-commerce, etc.) incluant une option "Other".
Analyse d'Idée par l'IA : Le choix de l'option "Other" ouvre une interface de réponse automatique dans Gmail. Un Gmail Trigger intercepte la description du projet envoyée par le prospect. L'IA valide le sérieux de la demande (attribution de la valeur it_is_lead). Si la condition est remplie, l'IA génère un rapport d'analyse détaillant les forces, les faiblesses et un conseil stratégique, envoyé au prospect dans un template HTML professionnel.

3. Branche Secondaire (Budget inférieur à 5000 dollars)
Stockage : Enregistrement immédiat des coordonnées du prospect dans un tableau Google Sheets.
Rapport Quotidien : Chaque jour à 19h00, un nœud JavaScript extrait les données et les transforme en texte.
Décision Finale : L'IA convertit ces informations en un tableau HTML épuré envoyé directement au propriétaire du projet, lui permettant de décider rapidement des profils à recontacter.

Stack Technique
Orchestration : n8n
Communication : Slack, Gmail
Base de données : Google Sheets
Intelligence Artificielle : AI et LLM Nodes (n8n)
Formatage : JavaScript, templates HTML / CSS
