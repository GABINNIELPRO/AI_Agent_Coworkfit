<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->
<div align="center">

[![LinkedIn][linkedin-shield]][linkedin-url]
[![GitHub][github-shield]][github-url]

</div>

<!-- PROJECT HEADER -->
<br />
<div align="center">
  <h1 align="center">CoworkFit – Public Overview</h1>

  <p align="center">
    <strong>Agent IA conversationnel</strong> de mise en relation avec des experts :
    classification d'intention par LLM, recherche hybride sémantique + mots-clés et architecture microservices.
    <br />
    Projet sélectionné et présenté à <strong>VivaTech 2026</strong>.
    <br />
    <br />
    <a href="#démonstration"><strong>Voir la démo »</strong></a>
    &middot;
    <a href="#architecture">Architecture</a>
    &middot;
    <a href="#contact">Contact</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Sommaire</summary>
  <ol>
    <li>
      <a href="#à-propos">À propos</a>
      <ul>
        <li><a href="#technologies">Technologies</a></li>
      </ul>
    </li>
    <li><a href="#fonctionnalités">Fonctionnalités</a></li>
    <li><a href="#architecture">Architecture</a></li>
    <li><a href="#comment-fonctionne-lagent">Comment fonctionne l'agent</a></li>
    <li><a href="#démonstration">Démonstration</a></li>
    <li><a href="#accès-au-code">Accès au code</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## À propos

Ce dépôt public présente la description et l'architecture d'un **agent IA conversationnel** développé en freelance (mai – juin 2026) pour **CoworkFit**, et présenté à **VivaTech 2026**.

**Le besoin :** permettre à un utilisateur d'exprimer un besoin en langage naturel, puis le guider : discuter, planifier, ou être mis en relation avec l'expert le plus pertinent.

**La solution :** un agent qui comprend l'intention de chaque message, l'oriente vers le bon traitement et, pour la mise en relation, retrouve les profils d'experts correspondant au besoin grâce à une recherche hybride.

<p align="right">(<a href="#readme-top">retour en haut</a>)</p>

### Technologies

[![Python][python-shield]][python-url]
[![FastAPI][fastapi-shield]][fastapi-url]
[![PostgreSQL][postgres-shield]][postgres-url]
[![Elasticsearch][elastic-shield]][elastic-url]
[![Nginx][nginx-shield]][nginx-url]
[![Docker][docker-shield]][docker-url]

<p align="right">(<a href="#readme-top">retour en haut</a>)</p>

<!-- FEATURES -->
## Fonctionnalités

- **Classification d'intention par LLM** : chaque requête est routée vers l'une des 3 catégories (conversation, planification, mise en relation avec des experts)
- **Recherche hybride** : sémantique (embeddings 3072 dimensions dans PostgreSQL + pgvector) et lexicale (Elasticsearch)
- **Fusion pondérée des scores** (α = 0,6 / 0,4) pour combiner les deux recherches
- **Génération de réponses** par LLM à partir des profils retrouvés
- **Ingestion des profils** via API, stockage dans PostgreSQL et préparation pour l'agent

<p align="right">(<a href="#readme-top">retour en haut</a>)</p>

<!-- ARCHITECTURE -->
## Architecture

Le back-end repose sur **3 services FastAPI** conteneurisés avec Docker et exposés derrière **Nginx**. Chaque service a une responsabilité unique :

| Service | Rôle |
|---|---|
| Preprocessing | Ingestion et préparation des profils, calcul des embeddings |
| Retrieval | Recherche sémantique (pgvector) et lexicale (Elasticsearch), fusion des résultats |
| Génération | Classification d'intention, routage et génération des réponses par LLM |

| Couche | Technologies |
|---|---|
| Back-end | FastAPI (3 services) |
| Base vectorielle et relationnelle | PostgreSQL + pgvector |
| Recherche lexicale | Elasticsearch |
| Reverse proxy | Nginx |
| Orchestration | Docker, Docker Compose |

<!-- TODO : ajouter un schéma d'architecture ici -->

<p align="right">(<a href="#readme-top">retour en haut</a>)</p>

<!-- HOW IT WORKS -->
## Comment fonctionne l'agent

```
Message utilisateur
        │
        ▼
Classification d'intention (LLM)
        │
        ├── Conversation ─────────► Réponse conversationnelle
        ├── Planification ────────► Aide à la planification
        └── Mise en relation ─────► Recherche hybride
                                          │
                                          ├── Sémantique (pgvector, embeddings 3072D)
                                          └── Mots-clés (Elasticsearch)
                                                  │
                                          Fusion pondérée (α = 0,6 / 0,4)
                                                  │
                                                  ▼
                                    Profils d'experts pertinents
```

<p align="right">(<a href="#readme-top">retour en haut</a>)</p>

<!-- DEMO -->
## Démonstration

<!-- TODO : ajouter les vidéos / captures (VivaTech, conversation, planification, mise en relation) -->

### Présentation

### Prise d'informations

https://github.com/user-attachments/assets/b622cb63-1335-465a-87b9-3568b0d259ab

### Chat avec l'agent

https://github.com/user-attachments/assets/3f7cc753-16ae-4dbe-8cba-11702c886d35


### Matching de professionnels

https://github.com/user-attachments/assets/99068484-3f0c-4b54-b044-051da39ff9c8


### Planification d'évènements

https://github.com/user-attachments/assets/cc8fdea9-0543-47d2-88e3-e0a45005fb9a







### Parcours de l'agent

| Conversation | Planification | Mise en relation |
|---|---|---|
| *À venir* | *À venir* | *À venir* |

<p align="right">(<a href="#readme-top">retour en haut</a>)</p>

<!-- CODE ACCESS -->
## Accès au code

Le code source complet est hébergé dans un **dépôt privé**, car il s'agit d'un projet réalisé pour un client.

Un accès peut être accordé **sur demande** dans le cadre d'un processus de recrutement : voir [Contact](#contact).

<p align="right">(<a href="#readme-top">retour en haut</a>)</p>

<!-- CONTACT -->
## Contact

**Gabin Niel** – Ingénieur IA (RAG, agents IA, data)

- Email : gabin.niel.pro@gmail.com
- LinkedIn : [gabin-niel](https://www.linkedin.com/in/gabin-niel-749062233/)
- GitHub : [GABINNIELPRO](https://github.com/GABINNIELPRO)

<p align="right">(<a href="#readme-top">retour en haut</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[linkedin-shield]: https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white
[linkedin-url]: https://www.linkedin.com/in/gabin-niel-749062233/
[github-shield]: https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white
[github-url]: https://github.com/GABINNIELPRO
[python-shield]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://www.python.org/
[fastapi-shield]: https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white
[fastapi-url]: https://fastapi.tiangolo.com/
[postgres-shield]: https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white
[postgres-url]: https://www.postgresql.org/
[elastic-shield]: https://img.shields.io/badge/Elasticsearch-005571?style=for-the-badge&logo=elasticsearch&logoColor=white
[elastic-url]: https://www.elastic.co/elasticsearch
[nginx-shield]: https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white
[nginx-url]: https://nginx.org/
[docker-shield]: https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white
[docker-url]: https://www.docker.com/
