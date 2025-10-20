# MasterRank – Île-de-France

🎯 **Objectifs du projet**  
Ce projet vise à créer une plateforme web hypermédia permettant aux étudiants de master (M1/M2) de la région Île-de-France de partager et consulter des évaluations sur leurs expériences universitaires.  
Les données sont structurées via **SQL** et **RDF/Turtle**, offrant une approche sémantique pour relier les universités, les cours et les domaines d’études.  
L’objectif est de faciliter l’accès à des informations fiables et comparables pour les futurs étudiants et la communauté académique.

---

👥 **Public cible**  
- Étudiants  
- Chercheurs  
- Communauté académique locale  

---

🧰 **Technologies utilisées**  

**Front-end**  
- HTML5, CSS3, JavaScript  
- Interface web via Omeka S  

**Back-end**  
- PHP (Omeka S)  

**Base de données**  
- MySQL  

**Technologies API & services**  
- REST API (via Omeka S)  

**Données et multimédia**  
- JSON / XML  
- RDF / Turtle pour structuration sémantique  

**Outils & environnements**  
- Git / GitHub  
- WAMP ou équivalent pour serveur local  

---

⚙️ **Fonctionnalités prévues**  
- Formulaire pour ajouter des évaluations par les étudiants  
- Système de filtres et tris : par département, université, cours, domaine, niveau (M1/M2), année  
- Moteur de recherche pour retrouver des cours ou universités  
- Galerie ou visualisation des évaluations par domaine ou université  
- Export des données en CSV ou RDF  

---

## 🗂️ Structure de données (Mermaid ER Diagram)

```mermaid
erDiagram
    DEPARTMENTS ||--o{ UNIVERSITIES : has
    UNIVERSITIES ||--o{ UNIVERSITY_COURSES : offers
    COURSES ||--o{ UNIVERSITY_COURSES : includes
    STUDENTS ||--o{ EVALUATIONS : writes
    UNIVERSITY_COURSES ||--o{ EVALUATIONS : receives

    DEPARTMENTS {
        int id
        string code
        string name
    }

    UNIVERSITIES {
        int id
        string name
        int department_id
    }

    COURSES {
        int id
        string mention
        enum level
        enum domain
    }

    UNIVERSITY_COURSES {
        int id
        int university_id
        int course_id
    }

    STUDENTS {
        int id
        string name
        string email
    }

    EVALUATIONS {
        int id
        int student_id
        int university_course_id
        year year
        int rating
        text comment
        date evaluation_date
    }
