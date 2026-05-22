# Système Intelligent de Suivi et d'Analyse des Tâches (Task Tracker)

Ce workflow agentique gère l'orchestration, l'analyse et le routage intelligent des tâches et des messages utilisateurs. En évitant un flux déterministe rigide, il utilise la puissance d'un LLM et d'un routeur dynamique pour classifier les requêtes, gérer l'historique, stocker les données dans une base NoSQL (MongoDB), créer des alertes sur Notion en cas d'anomalies, et journaliser localement les exécutions.

---

## 🤵 Équipe projet
**Réalisé par :** FATIMA EZZAHRA ELMENOUN, MERYEM GHANEM, KOLA ISMAIL

---

## 🚀 Architecture Globale du Workflow

Le workflow est structuré autour d'un pipeline d'extraction de contexte suivi d'un aiguillage intelligent vers trois branches d'exécution dédiées :

                    [ Chat Input ]
                          │
                          ▼
                  [ Prompt Template ]
                          │
                          ▼
                   [ Groq Model ]
                          │
                          ▼
                   [ Smart Router ]
                          │
   ┌──────────────────────┼──────────────────────┐
   ▼                      ▼                      ▼
[Task Execution]       [Anomaly Route]        [Historical Query]
│                      │                      │
[Parser Node]          [Parser Node]          [MongoDB Query]
│                      │                      │
[MongoDB Query]      [Notion Page Creator]    [Chat Output]
│
[Save To File]


---

## 🛠️ Description Détaillée des Composants

### 1. Phase d'Entrée & Analyse (Core Pipeline)
* **Chat Input** : Récupère le message texte brut envoyé par l'utilisateur.
* **Prompt Template** : Structure la requête en combinant le message utilisateur avec des instructions système rigoureuses (Chain-of-Thought) pour extraire la tâche, la date, la priorité et détecter d'éventuelles incohérences.
* **Groq Model** : Modèle de langage (LLM) à haute performance qui traite le prompt et génère une réponse structurée évaluant l'intention de l'utilisateur.
* **Smart Router** : Composant central de décision qui analyse le retour du LLM et redirige dynamiquement le flux vers l'une des trois routes logiques sans utiliser de structures `if/else` câblées.

### 2. Branche 1 : Task Execution Route (Succès)
* S'active lorsque la requête est valide et contient une action claire à planifier.
* **Parser** : Nettoie et formate les données extraites par le LLM en un document JSON standardisé.
* **MongoDB Query (Insert)** : Insère la nouvelle tâche (avec sa priorité, sa date d'échéance et son statut) directement dans la collection de la base de données.
* **Save To File** : Journalise localement l'opération sur le disque pour assurer la traçabilité de l'exécution.

### 3. Branche 2 : Anomaly Route (Gestion des Erreurs)
* S'active si le message utilisateur est contradictoire, incomplet, ou s'il s'agit d'un bruit textuel non exploitable.
* **Parser** : Convertit les métadonnées de l'anomalie et le message d'origine en un payload structuré pour les API externes.
* **Notion Page Creator** : Communique avec l'API de Notion pour créer automatiquement une nouvelle ligne/page dans une base de données Notion centralisée afin d'alerter l'équipe ou de stocker le ticket d'erreur.

### 4. Branche 3 : Historical Query (Consultation)
* S'active lorsque l'utilisateur demande à consulter ses tâches passées ou à filtrer son historique.
* **MongoDB Query (Find/Aggregate)** : Interroge la base de données NoSQL pour récupérer les enregistrements correspondants aux critères.
* **Chat Output** : Renvoie le résultat final directement dans l'interface de discussion de l'utilisateur de manière lisible.

---

## ⚙️ Configuration & Prérequis

Pour déployer et exécuter ce fichier de workflow, les secrets et configurations suivants doivent être renseignés dans les nœuds respectifs :

* **Groq API** : Une clé d'API valide configurée sur le nœud `GroqModel`.
* **MongoDB** : L'URI de connexion (`mongodb+srv://...`), le nom de la base de données et de la collection cible.
* **Notion API** : Le Token d'intégration Notion (`Notion Secret`) et l'identifiant unique de la base de données Notion (`Database ID`).
* **Permissions Locales** : Droits d'écriture requis sur l'environnement d'exécution pour le nœud `SaveToFile`.