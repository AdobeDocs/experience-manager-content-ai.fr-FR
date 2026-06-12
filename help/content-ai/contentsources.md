---
title: Configurer et gérer vos sources IA dédiée au contenu
description: Découvrez comment configurer l’IA dédiée au contenu d’AEM dans Cloud Manager en configurant votre première source de contenu et en déclenchant l’acquisition.
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM Content AI, Sources de Content AI, Acquisition, Cloud Manager, Adobe Developer Console
source-git-commit: 86c0b8b910583701dc4bd42b61e082cc5429cee8
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 1%

---


# Configurer et gérer vos sources IA dédiée au contenu

Ce guide vous guide tout au long de la configuration des sources d’IA dédiée au contenu dans Cloud Manager, depuis le respect des conditions préalables à la création d’une source de contenu et la confirmation qu’elle est indexée et disponible.

## Conditions préalables {#prerequisites}

Avant de commencer, assurez-vous que les conditions suivantes sont remplies :

* Vous disposez d’un programme Cloud Manager actif avec au moins un environnement AEM as a Cloud Service.
* Vous détenez le rôle **[Administrateur système](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-admin-console/admin-roles)** dans Admin Console pour le programme.
* Le profil de produit d&#39;environnement a été configuré dans ****, voir [Configurer un projet Adobe Developer Console](setup-adc-project.md).

## Étape 1 : ouvrir l’onglet Configuration de l’IA dédiée au contenu {#open-tab}

1. Connectez-vous à [](https://my.cloudmanager.adobe.com/) et sélectionnez votre programme.

   ![Accueil Cloud Manager affichant la carte du programme](../assets/content-ai-onboarding-step-1.png)

1. Dans la **[!UICONTROL Présentation du programme]**, accédez à la section **[!UICONTROL Environnements]** et sélectionnez l’environnement à configurer.

   ![Présentation du programme avec un environnement de production mis en surbrillance](../assets/content-ai-onboarding-step-2.png)

1. Sur la page des détails de l’environnement, sélectionnez l’onglet **[!UICONTROL Configuration de l’IA dédiée au contenu]**.

   ![Page de détails de l’environnement avec l’onglet Configuration de l’IA dédiée au contenu en surbrillance](../assets/content-ai-onboarding-step-3.png)

## Étape 2 - Création d’un Source IA dédiée au contenu {#create-source}

Une source de contenu définit le site web que l’IA dédiée au contenu explore et indexe.

1. Dans l’onglet **[!UICONTROL Configuration de l’IA dédiée au contenu]**, sélectionnez **[!UICONTROL Créer un Source]**.

   ![Onglet Configuration de l’IA dédiée au contenu affichant le bouton Créer Source](../assets/content-ai-onboarding-step-4.png)

1. Dans la boîte de dialogue **[!UICONTROL Créer/ajouter un nouveau Source IA dédiée au contenu]**, renseignez les champs suivants :

   | Champ | Description |
   | --- | --- |
   | **[!UICONTROL Nom de la configuration de l’IA dédiée au contenu]** | Identifiant unique de cette source (par exemple, `my-site-index`). Impossible de modifier après la création. |
   | **[!UICONTROL Description]** | *(Facultatif)* Brève description de la source de contenu. |
   | **[!UICONTROL Adresse du site web]** | URL racine du site web auquel explorer (par exemple, `https://www.example.com/`). |
   | **[!UICONTROL Exclure les URL]** | *(Facultatif)* les modèles d’URL à ignorer lors de l’explorée. |
   | **[!UICONTROL Fréquence d’actualisation]** | Fréquence à laquelle l’IA dédiée au contenu explore à nouveau la source : hebdomadaire, quotidienne, quotidienne 4×, 60 minutes ou 15 minutes. |

   ![Boîte de dialogue Créer un Source IA dédiée au contenu avec les champs de nom et d’adresse du site web renseignés et le bouton Créer un Source en surbrillance](../assets/content-ai-onboarding-step-5-0.png)

   ![Liste déroulante Fréquence d’actualisation affichant les options disponibles](../assets/content-ai-onboarding-step-5-1.png)

1. Sélectionnez **[!UICONTROL Créer un Source]**.

## Étape 3 - Déclencher L’Acquisition {#trigger-acquisition}

Une fois la source créée, son statut devient **Nouveau**. Exécutez une acquisition initiale pour démarrer l’indexation.

1. Dans la liste des sources, cliquez sur l’icône **plus d’actions** (...) en regard de votre source, puis sélectionnez **[!UICONTROL Déclencher l’acquisition]**.

   ![Liste des sources de l’IA dédiée au contenu avec le menu Plus d’actions ouvert et Trigger l’acquisition mis en surbrillance](../assets/content-ai-onboarding-step-7.png)

1. Dans la boîte de dialogue **[!UICONTROL Acquisition du déclencheur]**, passez en revue les détails de la source (**[!UICONTROL Source de contenu]**, **[!UICONTROL Dernière exécution]** et **[!UICONTROL Prochaine exécution planifiée]**) et sélectionnez **[!UICONTROL Déclencheur]**.

   ![Boîte de dialogue de confirmation de déclenchement d’acquisition](../assets/content-ai-onboarding-step-8.png)

## Étape 4 - Surveiller le statut de l’indexation {#monitor-status}

Une fois l’acquisition commencée, le statut de la source se met à jour en temps réel.

| État | Signification |
| --- | --- |
| **Nouveau** | Source créé ; aucune acquisition n’a encore été exécutée. |
| **Indexation** | L’acquisition est en cours. Le contenu est en cours d’explore et d’indexation. |
| **Disponible** | L’indexation est terminée. La source est prête à répondre aux requêtes de recherche. |

![Liste des sources de contenu affichant le statut de l’indexation](../assets/content-ai-onboarding-step-9.png)

![Liste des sources de contenu affichant le statut Disponible](../assets/content-ai-onboarding-step-10.png)

Attendez que le statut atteigne **Disponible** avant de rechercher l’index ou de tester l’API.

## Étape 5 - Recherche de contenu indexé {#search-content}

Une fois le statut de la source **Disponible**, vous pouvez exécuter des requêtes de recherche directement depuis Cloud Manager pour vérifier que le contenu a été indexé correctement.

1. Dans la liste source, sélectionnez **[!UICONTROL Rechercher]** en regard de votre source.

   ![Liste Sources de contenu avec le bouton Rechercher mis en surbrillance sur une source disponible](../assets/content-ai-onboarding-step-13.png)

1. Saisissez une requête dans le champ de recherche. Les résultats affichent une liste d’éléments correspondants avec un score et un type de contenu correspondants (par exemple, **PAGE** ou **PDF**). La sélection d’un résultat ouvre un aperçu à droite.

   ![Panneau de recherche avec une requête, les résultats correspondants avec des scores de correspondance et un volet de prévisualisation pour le résultat supérieur](../assets/content-ai-onboarding-step-14.png)

## Modification ou suppression d’un Source {#modify-source}

Pour mettre à jour une configuration source après sa création :

1. Dans la liste source, cliquez sur l’icône **autres actions** (...) en regard de la source, puis sélectionnez **[!UICONTROL Modifier]**.

   ![Liste Sources de contenu avec le menu Autres actions ouvert et Modifier mis en surbrillance](../assets/content-ai-onboarding-step-11.png)

1. Dans la boîte de dialogue **[!UICONTROL Modifier le Source de l’IA dédiée au contenu]**, mettez à jour les **[!UICONTROL Description]**, **[!UICONTROL Adresse du site web]**, **[!UICONTROL Exclure les URL]** ou **[!UICONTROL Fréquence d’actualisation]** selon les besoins. Le **[!UICONTROL Nom de la configuration de l’IA dédiée au contenu]** est en lecture seule et ne peut pas être modifié.

1. Sélectionnez **[!UICONTROL Enregistrer]** pour appliquer les modifications, ou sélectionnez **[!UICONTROL Supprimer]** dans le coin inférieur gauche de la boîte de dialogue pour supprimer entièrement la source.

   >[!WARNING]
   >
   >La suppression d’une source est permanente. Tout le contenu indexé pour cette source est supprimé et ne peut plus servir de requêtes de recherche.

   ![ Boîte de dialogue Modifier le Source de l’IA dédiée au contenu avec les champs modifiables en surbrillance et un bouton Supprimer dans le coin inférieur gauche](../assets/content-ai-onboarding-step-12.png)

La liste source est mise à jour pour prendre en compte vos modifications. Si vous avez supprimé la source, elle n’apparaît plus dans la liste.

## Étapes suivantes {#next-steps}

* [Configuration d’un projet Adobe Developer Console](setup-adc-project.md) - Créez le projet ADC et les informations d’identification dont vous avez besoin pour appeler l’API .
* [Référence de l’API Content AI](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) - Interrogez votre contenu indexé à l’aide de points d’entrée de recherche sémantiques, de texte intégral ou hybrides.

## Résolution des problèmes {#troubleshooting}

* **Source reste dans [!UICONTROL Indexation] pendant une période prolongée.** Réessayez l’acquisition à partir du menu (...). Si le statut ne progresse pas après une seconde exécution, vérifiez que l’**[!UICONTROL adresse du site web]** est accessible au public et que les modèles **[!UICONTROL Exclure les URL]** ne filtrent pas chaque page.
* **Source revient à [!UICONTROL Nouveau] après une exécution.** Le robot d&#39;exploration n’a pu récupérer aucune page de l’URL racine configurée. Vérifiez que l’URL répond avec `200 OK` et que le site ne bloque pas les requêtes automatisées.
* **[!UICONTROL Search] ne renvoie aucun résultat pour une source [!UICONTROL Available].** Indexation réussie, mais aucun contenu ne correspondait à la requête. Effectuez une requête plus large ou vérifiez que les URL explorées incluent les pages attendues.
