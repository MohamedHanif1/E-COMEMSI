# Mise en oeuvre d'une architecture Micro Service avec Spring Cloud #

### Créer une application de e-commerce basée sur les micro services : ###

1. Consul Discovery
2. Spring Cloud Config
3. Spring Cloud Gateway
4. Customer-service
5. Inventory Service
6. Order Service
7. Consul Config (Billing Service)
8. Vault (Billing Service)
9. Frontend Web avec Angular
##    ##

<details>
 <summary>1-Consul</summary><br>
![image](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/98591e13-39d8-4bd3-bff8-dada5c2660e2)
)<br>
</details>

<details>
<summary>2-Config service</summary><br>

-Ce fichier contient le lien du référentiel qui regroupe tous les fichiers de configuration d'autres services :<br>
![1](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/be17d06c-5d95-4084-b267-ec66351c3a48)
<br><br>
-l'annotation @EnableConfigServer active le serveur de configuration, tandis que l'annotation @EnableDiscoveryClient active le client de découverte pour faciliter la gestion des microservices dans un environnement distribué.<br>

![2](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/5c7090d8-ba90-47e0-a983-74ac1baafa18)
<br><br>
-aprés le démmarage de config service il s'ajoute au niveau de consul.<br>

</details>

<details>
  <summary>3-Customer service</summary>
  -L'entité Customer :<br>

![3](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/b2e5b297-215c-4422-a12b-94431632d880)
<br>
-La ligne spring.config.import=optional:configserver:http://localhost:8080 dans un fichier de configuration indique que Customer-service  doit importer sa configuration depuis un serveur de configuration

distant (Config Server) .<br><br>
![4](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/f88c3b83-97e6-4991-9e2f-27568aa913ba)<br>
Le fichier de configuration distant :<br>
![5](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/8d5bfcda-26a5-4f46-9f58-b4fab4b1bac4)<br>

</details>


<details>
  <summary>4-inventory service</summary>

![6](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/62d21cc9-171d-4a61-9228-1ece5ef14292)<br>
![7](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/ff31b894-a342-4e49-8b2f-bf5bec87e7e7)<br>
-L'entité Product :<br><br>
![8](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/1ce3c060-6e95-4ba3-9cc9-6cfa29686185)<br>
![9](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/847bf1de-1d35-4a72-a372-5e120de10651)<br>


</details>
<details>
  <summary>5-Gateway service</summary>

![10](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/27269efd-d9cf-43e3-b9d6-feadb9a57721)<br><br>
Gateway service configure une passerelle (gateway) utilisant Spring Cloud Gateway et utilise la découverte de service pour configurer dynamiquement les routes de la passerelle à partir d'un service de découverte. Cela offre une flexibilité et une évolutivité accrues dans un environnement de microservices où de nouveaux services peuvent être ajoutés sans avoir à mettre à jour manuellement la configuration de la passerelle.
![11](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/cf061aa7-3af9-482a-ab65-e9bce4df6493)<br><br>
![12](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/e6bc08ee-f939-4a25-a876-be994ee87b9f)<br><br>


</details>
<details>
  <summary>6-Order service</summary>

![13](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/6e33d47d-7482-4352-804e-0176dbec2fa0)<br><br>
![14](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/360d3a25-0344-4c4e-9c6c-2471bcbad012)<br><br>
cette interface Feign définit les méthodes permettant d'interagir avec le service "costumer-service" via des requêtes HTTP GET:
![15](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/c310f013-a19e-49f2-99d9-c7343c5ab59c)<br><br>
L'application initialise des données de commande de manière aléatoire en utilisant des clients Feign pour récupérer des informations depuis d'autres services (customer et inventory). <br>
![16](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/dfdaaf57-1983-47d4-be2f-a3d3c893ad90)


</details>

<details>
  <summary>7-Billing service</summary>

démarrage du vault :
![17](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/22458dce-e286-48a8-b645-8af4f0bf4db7)<br><br>
![18](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/bbcddefd-0188-4365-a5e8-f2bfa24a3d9c)<br><br>
-Dans le fichier de configuration, on définit le token Vault :

![19](https://github.com/MohamedHanif1/E-COMEMSI/assets/106152378/d80704de-a2df-49b8-809d-d2329a07c759)<br><br>

-Configuration des secrets avec Vault et Consul  :

</details>

<details>
  <summary>8-Client Angular:</summary>
.....
</details>
