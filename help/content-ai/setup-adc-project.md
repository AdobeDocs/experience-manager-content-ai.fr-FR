---
title: Configuration d’un projet Adobe Developer Console pour l’IA dédiée au contenu AEM
description: Découvrez comment configurer un projet Adobe Developer Console et authentifier les appels API vers AEM Content AI Services à l’aide de l’authentification de serveur à serveur ou par clé API.
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM Content AI, Adobe Developer Console, authentification, serveur à serveur, clé API, jeton d’accès
source-git-commit: 445aeafe64eb8a68d0770c1f1afb54d68e0b054f
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 3%

---


# Configuration d’un projet Adobe Developer Console {#configure-adc-project}

Pour appeler l’API Content AI Services d’AEM, vous avez besoin d’informations d’identification émises par un projet Adobe Developer Console (ADC). Cette page vous guide tout au long de la création du projet, de la sélection d’une méthode d’authentification et de la génération des informations d’identification que vous incluez dans chaque requête API.

Accédez à [](https://developer.adobe.com/console/) pour lancer votre organisation.

## Conditions préalables {#prerequisites}

Avant de commencer, vérifiez les points suivants :

* Vous avez accès à [](https://developer.adobe.com/console/) pour votre organisation.
* Vous êtes ajouté en tant que **développeur** sur le profil de produit AEM Content AI Services dans **Adobe Admin Console**. Sans ce rôle, la carte d’API **[!UICONTROL AEM Content AI Services]** apparaît désactivée et l’option d’authentification **[!UICONTROL serveur à serveur]** est masquée.
* Vous connaissez les numéros de programme et d’environnement du profil de produits que vous souhaitez sélectionner (par exemple, `AEM User - publish - Program 12345 - Environment 67890`).

## Choisir une méthode d’authentification {#choose-auth}

AEM Content AI Services prend en charge deux méthodes d’authentification. Sélectionnez celui qui correspond à votre intégration :

| Méthode | Idéal pour |
| --- | --- |
| [Serveur à serveur](#s2s-auth) | Services principaux qui appellent l’API sans interaction de l’utilisateur. Renvoie un jeton d’accès de courte durée. |
| [ Clé API ](#api-key-auth) | Intégrations côté client ou basées sur un navigateur qui appellent directement l’API . Renvoie une clé de longue durée étendue aux domaines autorisés. |

## Authentification de serveur à serveur {#s2s-auth}

1. Sélectionnez **[!UICONTROL API et services]**, puis **[!UICONTROL API]**.

   ![Developer Console présentant les API et les services](../assets/e2e-env-setup-28.png)

1. Filtrez par **AEM Content AI Services**, puis sélectionnez **[!UICONTROL Créer un projet]** pour démarrer un nouveau projet, ou **[!UICONTROL Ajouter une API]** si vous ajoutez le service à un projet existant.

   >[!NOTE]
   >
   >Si la carte d’API est désactivée avec un message « Licence requise », votre environnement AEM as a Cloud Service risque de ne pas être modernisé. Voir [ Modernisation de l’environnement AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#modernization-of-aem-as-a-cloud-service-environment).

1. Dans la boîte de dialogue **[!UICONTROL Configurer l’API]**, sélectionnez l’authentification **[!UICONTROL Serveur à serveur]**.

   ![Boîte de dialogue Configurer l’API avec l’option Serveur à serveur sélectionnée](../assets/e2e-env-setup-29.png)

   >[!TIP]
   >
   >Si l’option Serveur à serveur n’est pas disponible, l’utilisateur configurant l’intégration n’est pas ajouté en tant que développeur au profil de produit. Voir [Activer l’authentification de serveur à serveur](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation).

1. Si nécessaire, renommez les informations d’identification. Sélectionnez **[!UICONTROL Suivant]**.

   ![Étape Adobe Developer Console pour renommer les nouvelles informations d&#39;identification de serveur à serveur avant de sélectionner Suivant](../assets/e2e-env-setup-30.png)

1. Sélectionnez le profil de produit **[!UICONTROL Utilisateur AEM - publication - Programme XXX - Environnement XXX]** et/ou **[!UICONTROL Utilisateur AEM - auteur - Programme XXX - Environnement XXX]**, puis sélectionnez **[!UICONTROL Enregistrer]**.

   ![Sélecteur de profil de produit affichant les profils de publication et de création de l’utilisateur AEM pour le programme et l’environnement cibles](../assets/e2e-env-setup-31.png)

1. Examinez la configuration de l’API et de l’authentification.

   ![Écran de vérification résumant l’API sélectionnée, le type d’authentification et le nom des informations d’identification](../assets/e2e-env-setup-33.png)

   ![Consulter les détails de l’écran affichant les profils de produit affectés pour les informations d’identification](../assets/e2e-env-setup-34.png)

### Générer un jeton d’accès {#generate-token}

1. Dans votre projet ADC, accédez à **[!UICONTROL Informations d’identification]** et sélectionnez **[!UICONTROL Générer un jeton d’accès]**.

   ![Page des informations d’identification avec le bouton Générer un jeton d’accès en surbrillance](../assets/e2e-env-setup-32.png)

1. Incluez le jeton dans l’en-tête `Authorization` de chaque requête API :

   ```http
   Authorization: Bearer YOUR_ACCESS_TOKEN
   ```

   >[!WARNING]
   >
   >Stockez le jeton en toute sécurité. Il expire et doit être régénéré périodiquement.

## Authentification par clé API {#api-key-auth}

1. Lors de l’ajout de l’API Content AI Services AEM à votre projet, sélectionnez **[!UICONTROL Clé API]** dans la boîte de dialogue **[!UICONTROL Sélectionner le type d’authentification]**.

   ![Sélectionnez le type d’authentification de la clé API](../assets/onboarding-api-key-01.png)

1. Confirmez les informations d’identification de la clé API.

   ![Ajout d’informations d’identification de clé API](../assets/onboarding-api-key-02.png)

1. Pour limiter les origines qui peuvent utiliser la clé, configurez les domaines autorisés.

   ![Configurer les domaines autorisés](../assets/onboarding-api-key-03.png)

1. Votre clé API (ID client) s’affiche sous **[!UICONTROL Informations d’identification connectées]**. Sélectionnez **[!UICONTROL Copie]**.

   ![Copier la clé API à partir des informations d’identification connectées](../assets/onboarding-api-key-04.png)

1. Incluez la clé dans chaque requête API :

   ```http
   x-api-key: YOUR_API_KEY
   ```

   Votre projet est maintenant prêt. Utilisez la clé avec chaque requête à AEM Content AI Services.

## Étapes suivantes {#next-steps}

* [Contrôler vos sources de contenu](contentsources.md) - Configurez une source de contenu dans Cloud Manager et déclenchez l’acquisition.
* [Référence de l’API Content AI](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) - Utilisez votre jeton d’accès ou votre clé API pour interroger le contenu indexé.
