# Gestion des Étudiants avec Spring Boot

Ce projet est une application Spring Boot qui fournit une interface RESTful pour effectuer des opérations CRUD sur une entité `Étudiant` stockée dans une base de données MySQL.

## **Prérequis**

- **Java** : 17 ou supérieur
- **Maven** : pour la gestion des dépendances
- **MySQL** : pour la base de données
- **IDE** : IntelliJ IDEA, Eclipse ou tout autre IDE supportant Spring Boot

## **Démarrage**

### 1. Cloner le projet
Clonez ce dépôt dans votre environnement local :
```bash
git clone <URL_DU_DEPOT>
cd student_management
```

### 2. Ajouter les dépendances Maven
Ce projet utilise les dépendances suivantes dans le fichier `pom.xml` :
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

### 3. Configurer la base de données MySQL
Créez une base de données MySQL nommée `studentdb` :
```sql
CREATE DATABASE studentdb;
```

Configurez les paramètres de la base de données dans le fichier `src/main/resources/application.properties` :
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/studentdb
spring.datasource.username=root
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

### 4. Lancer l'application
Pour démarrer l'application Spring Boot :
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

Cela inclut toutes les parties importantes de votre projet, de l'installation aux tests. Faites-moi savoir si vous voulez personnaliser davantage ce fichier !
