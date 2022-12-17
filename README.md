# gateway 
Ce fichier readme.md résume l'entiereté des étapes allant de la création des différents web services,à la création de la gateway,du service de registre Eureka et la partie front-end avec Angular.
#Partie 1 : Création des web services: #Web service customer:
Création de la classe 'Customer' qui sera la classe dédiée au client et représenté par son id,nom et mot de passe:
![image](https://user-images.githubusercontent.com/84769421/208237039-23074fd1-ca28-40fe-a377-5bd900dd9050.png)

Création de Customer Repository:
![image](https://user-images.githubusercontent.com/84769421/208237210-2ce21691-153b-4b97-8d91-7f59dbec90c9.png)

Notre fichier 'CustomerServiceApplication' va nous permettre de créer quelques clients afin de tester notre partie backend et frontend:
![image](https://user-images.githubusercontent.com/84769421/208237259-b8a3ab00-d497-4011-bf7d-5fd499cf54ac.png)

Le fichier application.propreties va nous permettre d'allouer un port à notre web service (dans ce cas 8081),le nom du service,préciser la base de données et préciser si le web service doit s'authentifier ou non avec l'attribut 'spring.cloud.discovery.enabled'
![image](https://user-images.githubusercontent.com/84769421/208237289-31cfe56b-997f-4380-ad54-bfaa98f0761a.png)

#Web service inventory:

Création de la classe 'Inventory' qui sera la classe dédiée au produit et représenté par son id,nom,prix et quantité:
![image](https://user-images.githubusercontent.com/84769421/208237381-5c8e8938-f507-4714-be11-e716470abebe.png)

Création de Product Repository :
![image](https://user-images.githubusercontent.com/84769421/208237462-18d4e5f0-8978-4494-8415-f5fe31ae31a2.png)

Notre fichier 'InventoryServiceApplication' va nous permettre de créer quelques produits afin de tester notre partie backend et frontend:
![image](https://user-images.githubusercontent.com/84769421/208237502-85f42689-c128-49fa-85d2-ac261d845dd3.png)

Le fichier application.propreties va nous permettre d'allouer un port à notre web service (dans ce cas 8082),le nom du service,préciser la base de données et préciser si le web service doit s'authentifier ou non avec l'attribut 'spring.cloud.discovery.enabled'
![image](https://user-images.githubusercontent.com/84769421/208237521-385b2729-5da2-4973-829f-9db80586988d.png)

#Web service Billing:
Création de la classe 'Bill' qui sera la classe dédiée à la facture et représenté par son id,sa date de création,la liste des produits commandés, l'id du client ainsi que le client :


![image](https://user-images.githubusercontent.com/84769421/208237562-539b7d33-77ed-4acd-b30f-aff2e537d51d.png)

Création de la classe 'ProduitItem' qui sera la classe dédiée au produit et représenté par son id,sa quantité,son prix,l'id du produit ainsi que la facture du produit :
![image](https://user-images.githubusercontent.com/84769421/208237646-e6d2da15-b6b5-4b58-997e-4ca82139b89a.png)

Création de Bill Repository :
![image](https://user-images.githubusercontent.com/84769421/208237663-411cb93e-9c5a-4a42-ac0d-25ab3a3bd713.png)


Création de ProductItem Repository:
![image](https://user-images.githubusercontent.com/84769421/208237685-dd38d002-bbf1-4617-9c57-4b59de46d130.png)

Création de 'CustomerRESTClient' et 'ProductItemRESTClient' avec OpenFeign qui va nous permettre de communiquer avec les microservices via REST :
![image](https://user-images.githubusercontent.com/84769421/208237715-db8e1e59-5e3e-4291-b5a5-d3edbe83d8b3.png)

![image](https://user-images.githubusercontent.com/84769421/208237758-1bf86ca9-6efa-40a6-8b76-2ac8946955af.png)

Création du Rest Controller :
![image](https://user-images.githubusercontent.com/84769421/208237914-e88b1f36-6c12-473d-bca5-68409bab0458.png)

Notre fichier 'BillingServiceApplication' va nous permettre de créer quelques factures afin de tester notre partie backend et frontend:
![image](https://user-images.githubusercontent.com/84769421/208238059-1e5ff771-17c0-440a-8e36-5a47b4437b84.png)

Le fichier application.propreties va nous permettre d'allouer un port à notre web service (dans ce cas 8083),le nom du service,préciser la base de données et préciser si le web service doit s'authentifier ou non avec l'attribut 'spring.cloud.discovery.enabled'
![image](https://user-images.githubusercontent.com/84769421/208238072-174ba6c4-9e15-4363-b8da-ad07b997c252.png)

#Création de la gateway et du service d'authentification Eureka
Gateway : Configuration des micro services,des ports ainsi que résolution du problème CORS:
    Notre fichier 'GatewayServiceApplication' va nous permettre de configurer dynamiquement les routes:
    ![image](https://user-images.githubusercontent.com/84769421/208238096-abd84937-be75-4a7a-88aa-d3835195ccd2.png)

    Notre fichier de configuration 'app.yml' va servir à définir pour chaque route son id,son uri ainsi que son path:
    ![image](https://user-images.githubusercontent.com/84769421/208238135-9b763b26-f589-4294-a715-6adcdbab664c.png)

    Le fichier application.properties va nous permettre d'allouer un port à notre web service (dans ce cas 8885),le nom du service et préciser si le web service doit s'authentifier ou non avec l'attribut 'spring.cloud.discovery.enabled'
    ![image](https://user-images.githubusercontent.com/84769421/208238160-c492f637-c73e-4b4b-ad2c-3aee44701079.png)

    Notre fichier de configuration 'application.yml' va servir pour résoudre le problème de CORS et ainsi accepter les requetes venant de la partie front end à la partie backend afin qu'elle soient autorisées:
    ![image](https://user-images.githubusercontent.com/84769421/208238218-80e71fa5-c952-4412-9017-4ce8a208f24a.png)
    -Eureka : Service de registre et d'authentification des services:
    
    Le fichier application.propreties va nous permettre d'allouer un port à notre web service (dans ce cas 8761) et de lui indiquer que ce n'est pas la peine de s'auto authentifier:
    ![image](https://user-images.githubusercontent.com/84769421/208238285-b31a54a1-49b0-43cc-94ed-1be0eb8dfa1f.png)

#Partie 2 : Partie Front end avec Angular: 
-Partie produits:
![image](https://user-images.githubusercontent.com/84769421/208238321-2a144c88-ab44-4fff-8de0-9512177bb542.png)

-Partie client:
![image](https://user-images.githubusercontent.com/84769421/208238333-6cc47204-ea04-4652-9013-394b80f2e18a.png)

-Partie facture:
![image](https://user-images.githubusercontent.com/84769421/208238345-cc9ed225-9d6f-48ac-a9cc-91c38371bd9e.png)

-Partie informations facture:
![image](https://user-images.githubusercontent.com/84769421/208238413-b017df31-4180-4c71-a6bd-60be895d897f.png)


