# Gestion des Étudiants avec Spring Boot

Ce projet est une application Spring Boot qui fournit une interface RESTful pour effectuer des opérations CRUD sur une entité `Étudiant` stockée dans une base de données MySQL.

## **Prérequis**

- **Java** : 17 ou supérieur
- **Maven** : pour la gestion des dépendances
- **MySQL** : pour la base de données
- **IDE** : IntelliJ IDEA, Eclipse ou tout autre IDE supportant Spring Boot

## **Démarrage**
### 1. Création du projet avec 'Spring Initializer' 
![image](https://github.com/user-attachments/assets/28c9a240-49c5-4ba1-907a-0caf797fe4c5)

### 2. Création de la base de données MySQL
Créez une base de données MySQL nommée `student` :
```sql
CREATE DATABASE student;
```

Configurez les paramètres de la base de données dans le fichier `src/main/resources/application.properties` :
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/student
spring.datasource.username=root
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

### 3. Lancer l'application
Pour démarrer l'application Spring Boot soit manuellement soit avec :
```bash
mvn spring-boot:run
```

## **API Endpoints**

### 1. Ajouter un étudiant
- **URL** : `/students/save`
- **Méthode** : `POST`
- **Payload Exemple** :
  ```json
  {
    "nom": "LACHGAR",
    "prenom": "Mohamed",
    "dateNaissance": "1985-09-01"
  }
  ```
- **Réponse Exemple** : `201 Created`

### 2. Supprimer un étudiant
- **URL** : `/students/delete/{id}`
- **Méthode** : `DELETE`
- **Réponse** : `204 No Content` (si succès)

### 3. Récupérer tous les étudiants
- **URL** : `/students/all`
- **Méthode** : `GET`
- **Réponse Exemple** :
  ```json
  [
    {
      "id": 1,
      "nom": "LACHGAR",
      "prenom": "Mohamed",
      "dateNaissance": "1985-09-01"
    }
  ]
  ```

### 4. Compter les étudiants
- **URL** : `/students/count`
- **Méthode** : `GET`
- **Réponse Exemple** : `10`

### 5. Récupérer les étudiants par année
- **URL** : `/students/byYear`
- **Méthode** : `GET`
- **Réponse Exemple** :
  ```json
  [
    {
      "year": 1985,
      "count": 5
    }
  ]
  ```

## **Structure du projet**

- **Controllers** :
  - `StudentController` : Gestion des endpoints RESTful.
- **Entities** :
  - `Student` : Représentation de l'entité étudiant.
- **Repositories** :
  - `StudentRepository` : Accès à la base de données avec Spring Data JPA.
- **Services** :
  - `StudentService` : Logique métier pour les opérations CRUD.

## **Tests**

Les tests unitaires pour le contrôleur des étudiants sont implémentés avec **JUnit** et **Mockito**. Voici un aperçu des tests :
- **Test de sauvegarde d'un étudiant**
- **Test de suppression d'un étudiant**
- **Test de récupération de tous les étudiants**
- **Test du comptage des étudiants**
- **Test de la récupération par année**

Pour exécuter les tests :
```bash
mvn test
```

## **Licence**

Ce projet est fourni dans le cadre d'une démonstration de Spring Boot et peut être librement utilisé et modifié.

