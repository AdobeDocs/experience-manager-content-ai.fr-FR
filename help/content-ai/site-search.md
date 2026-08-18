---
title: Prise en main d’AEM Content Recherche optimisée par l'IA
description: 'Ce guide explique comment activer la recherche sur votre site à l’aide de l’IA dédiée au contenu : connectez votre contenu, puis choisissez un composant de recherche pour le présenter aux visiteurs.'
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM Content AI, AEM Content Recherche optimisée par l'IA, GenSearch, Recherche rapide, Sources Content AI, Acquisition, Cloud Manager
source-git-commit: 51fa66b5ac0ef77e438db76530788826da65f91e
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 6%

---


# Prise en main d’AEM Content Recherche optimisée par l&#39;IA

La recherche traditionnelle sur le site associe les mots qu’un visiteur saisit aux mots de votre contenu. Cela fonctionne bien lorsque les visiteurs utilisent la même terminologie que votre contenu, mais cela se répartit au moment où ils posent une question, expriment une intention ou expriment simplement les choses différemment. La recherche est l’un des signaux les plus clairs de l’intention des visiteurs sur un site. Par conséquent, une correspondance échouée signifie souvent un échec du parcours : le contenu n’est pas découvert, l’engagement est abandonné et les conversions sont perdues. Les visiteurs s&#39;attendent de plus en plus à ce que la recherche comprenne ce qu&#39;ils veulent dire, pas seulement ce qu&#39;ils ont tapé - et cette même base tenant compte de l&#39;intention est ce qui rend les réponses génératives possibles en premier lieu.

AEM Content Recherche optimisée par l&#39;IA ne remplace pas l’expérience de recherche de votre site. Il l’améliore, en passant de la correspondance de mots-clés à la compréhension de la signification et de l’intention, en passant par la réponse directe aux questions. La recherche sémantique permet une récupération tenant compte de l’intention en plus de votre expérience de recherche existante, ce qui fait apparaître le contenu pertinent même lorsqu’une requête ne partage pas le libellé exact du contenu. La recherche générative s’appuie sur la même base de récupération pour produire des réponses contextuelles générées basées sur le propre contenu de votre site. Il s’agit d’une étape distincte et non de la même chose que la récupération sémantique.

Pour les visiteurs, cela signifie une meilleure pertinence, une prise en charge du langage naturel, moins de recherches sans résultat et des réponses plus rapides. Pour votre entreprise, cela signifie une meilleure correspondance d’intention, une découverte de contenu plus forte et une base de recherche prête pour l’IA, sans devoir reconstruire votre expérience de recherche à partir de zéro. Pour votre équipe, il s’agit d’une mise à niveau incrémentielle : votre composant de recherche existant peut passer de lexical, sémantique et génératif pas à pas, plutôt que d’avoir besoin d’une implémentation entièrement nouvelle.

Pour y parvenir, il faut prendre deux décisions : comment votre contenu entre dans l’IA dédiée au contenu et quel composant l’apporte aux visiteurs. Connectez votre contenu, puis ajoutez un composant de recherche à une page. Votre site est alors prêt à fournir aux visiteurs les résultats les plus pertinents et les réponses basées sur l’intention.

## Prérequis {#prerequisites}

Avant de commencer, assurez-vous que les conditions suivantes sont remplies :

* Vous disposez d’un programme Cloud Manager actif avec au moins un environnement AEM as a Cloud Service.
* Votre utilisateur est affecté au profil de produit **[!UICONTROL Utilisateurs]** (pour afficher les sources de contenu) et/ou **[!UICONTROL Administrateurs AEM]** (pour les créer et les modifier), affecté au niveau **publication** - l’IA dédiée au contenu indexe le contenu publié, et non le contenu créé. Voir [Affecter un utilisateur à un profil de produit AEM](contentsources.md#assign-product-profile) pour la procédure complète.
* Le profil de produit de l’environnement a été configuré dans ****.

>[!NOTE]
>
>L’accès à Cloud Manager seul n’est pas suffisant. Un utilisateur a également besoin d’un profil de produit AEM affecté au niveau de publication pour afficher ou gérer les sources de contenu.

## Étape 1a - Connexion d’un index existant {#option-a}

Les index de référentiel existants apparaissent automatiquement dans la liste Sources de contenu sous la forme AEM de type Source, indiqué par ce qu’ils indexent, comme les pages, les Assets ou les fragments de contenu. Ils démarrent **Restreint** et verrouillés, pas encore consultables via l’IA dédiée au contenu.

1. Connectez-vous à [](https://my.cloudmanager.adobe.com/), sélectionnez votre programme et ouvrez l’onglet **[!UICONTROL Configuration de l’IA dédiée au contenu]** pour l’environnement que vous souhaitez configurer.
1. Recherchez la source en fonction de laquelle vous souhaitez effectuer une recherche (par exemple, **Pages**) et sélectionnez son icône de verrouillage. Seuls les utilisateurs disposant du profil de produit **[!UICONTROL Administrateurs]** peuvent effectuer cette opération. **[!UICONTROL Les utilisateurs AEM]** peuvent afficher les sources de contenu, sans modifier leur capacité de recherche.
1. Lisez le **Rendre la source consultable ?** dialoguez soigneusement. Elle vous avertit que les listes de contrôle d’accès (ACL) Apache Oak ne seront pas appliquées pour cet index une fois qu’il sera consultable. Tout utilisateur authentifié pourra récupérer l’intégralité de son contenu. Cochez **Je comprends que les contrôles d’accès (ACL) ne sont pas appliqués et que tout le contenu de cette source peut faire l’objet de recherches** puis sélectionnez **Rendre consultable**.
1. Confirmez les modifications de statut en **Disponible**. Une icône d’avertissement reste en regard de la source pour rappeler en permanence que les listes de contrôle d’accès sont ignorées pour celle-ci.
1. Exécutez une recherche de test pour vérifier que les résultats reviennent correctement.

>[!WARNING]
>
>Rendre un index existant consultable de cette manière contourne entièrement les listes de contrôle d’accès Apache Oak pour cette source : tout utilisateur authentifié peut récupérer l’intégralité de son contenu par le biais d’une recherche, quelles que soient ses autorisations de référentiel normales. Ne faites cela que pour les sources que vous êtes à l&#39;aise d&#39;exposer en entier.

>[!NOTE]
>
>Ce chemin d’accès est adapté si vous disposez déjà d’un index avec le contenu de votre site, par exemple, le contenu de votre page. Utilisez cet index au lieu de configurer un mécanisme d’explore distinct.

## Étape 1b - Explorer à un site Web {#option-b}

Utilisez ce chemin d’accès si vous ne disposez pas déjà d’un index de recherche pour votre site. Le robot d&#39;exploration de l’IA dédiée au contenu crée et actualise un modèle pour vous. Ce processus d’explore est également appelé **acquisition** dans Cloud Manager et dans ce guide.

1. Ouvrez l’onglet **[!UICONTROL Configuration de l’IA dédiée au contenu]**, comme à l’étape 1a.
1. Sélectionnez **[!UICONTROL Créer un Source]** et renseignez les champs. Seuls les utilisateurs disposant du profil de produit **[!UICONTROL Administrateurs]** peuvent ajouter de nouvelles sources de contenu.

   | Champ | Description |
   | --- | --- |
   | **[!UICONTROL Nom de la configuration d’IA dédiée au contenu]** | Identifiant unique de cette source. Impossible à changer après la création. |
   | **[!UICONTROL Adresse du site web]** | URL racine à explorer ; `https://www.example.com/`, par exemple. |
   | **[!UICONTROL URL à exclure]** | *(Facultatif)* Modèles d’URL à ignorer lors de l’exploration. |
   | **[!UICONTROL Fréquence d’actualisation]** | Hebdomadaire, Quotidien, Quotidien 4×, 60 min ou 15 min. |

1. Sélectionnez **[!UICONTROL Créer une source]**. L’acquisition démarre automatiquement et la source passe à **Indexation**.
1. Surveillez le statut jusqu’à ce qu’il atteigne **Disponible** :

   | Statut | Signification |
   | --- | --- |
   | **Nouveau** | Source vient de se créer ; l&#39;acquisition automatique n&#39;a pas encore commencé. |
   | **Indexation** | Exploré et indexation en cours. |
   | **Disponible** | Indexation terminée : prêt à répondre aux requêtes de recherche. |

1. Sélectionnez l’icône **recherche** en regard de la source et exécutez une requête de test pour confirmer que votre contenu a été correctement indexé.

>[!CAUTION]
>
>Une source bloquée dans **[!UICONTROL Indexation]** ? Essayez d’abord l’acquisition à partir du menu (...). Si elle ne progresse toujours pas, vérifiez que l’adresse du site web est accessible au public et que vos modèles **[!UICONTROL Exclure les URL]** ne filtrent pas toutes les pages.

## Étape 2 - Sélection d’un composant de recherche {#choose-component}

Deux composants permettent d’effectuer une recherche sur une page, en partant de bases différentes :

| | Recherche rapide (v3) avec recherche sémantique | Recherche optimisée par l&#39;IA de contenu AEM |
| --- | --- | --- |
| Foundation | Composant principal de recherche rapide existant, mis à niveau vers la version 3 | Nouveau composant autonome : appelle directement les API de l’IA dédiée au contenu. |
| Source de contenu | Contenu de votre site existant, déjà dans un index, enrichi pour la correspondance sémantique | Un Source IA dédiée au contenu (étapes 1a ou 1b) |
| Réponse générative | Non : améliore uniquement la qualité de correspondance de la liste de résultats existante. | Oui - résumé facultatif généré par l’IA avec des sources et une clause de non-responsabilité |
| Ajustement optimal | Sites utilisant déjà la recherche rapide et souhaitant une mise à niveau incrémentielle plus légère | Composant suggéré pour l’ensemble des fonctionnalités de l’IA dédiée au contenu : recherche sémantique, recherche générative et recherche en langage naturel (NLS) |

## Recherche rapide (v3) avec recherche sémantique {#quicksearch}

Si votre site utilise déjà le composant Recherche rapide [!DNL AEM] classique, v3 ajoute un bouton d’activation/désactivation **Recherche optimisée par l&#39;IA** que les visiteurs peuvent activer : aucun nouveau composant, proxy ou Source de contenu n’est requis.

* La recherche s’exécute toujours sur le même chemin d’accès JCR/QueryBuilder qu’aujourd’hui : rien ne change dans le servlet de résultat ou dans la manière dont les résultats sont rendus.
* Lorsqu’un visiteur active le bouton (bascule), le composant préfixe la requête avec un marqueur spécial qui l’achemine vers une correspondance sémantique au lieu du texte intégral du mot-clé brut.
* Il n’y a pas de résumé génératif de réponse sur ce chemin. Elle améliore la qualité de correspondance de la liste de résultats existante ; elle n’ajoute pas de réponse d’IA générative.
* **L’étape 1 (intégration de l’IA dédiée au contenu) ne s’applique pas à ce chemin.** Il n’y a pas de Source de contenu à créer ou à connecter. Ce composant interroge directement votre index de page existant.

>[!NOTE]
>
>Si la recherche sémantique ne fonctionne pas comme prévu après avoir activé le bouton , ouvrez un ticket d’assistance.

Ce chemin d’accès est adapté si vous souhaitez une mise à niveau de recherche sémantique incrémentielle sans adopter de nouveau composant ou de nouvelles sources de contenu. Ce n’est pas le bon chemin si vous souhaitez une expérience de réponse générative ; utilisez la Recherche optimisée par l&#39;IA de contenu AEM à cet effet.

## Recherche optimisée par l&#39;IA de contenu AEM {#gensearch}

AEM Content Recherche optimisée par l&#39;IA est un composant principal [!DNL AEM] qui permet aux visiteurs de rechercher un Source de contenu directement à partir d’une page, avec des fonctionnalités de recherche sémantique et de recherche générative.

>[!VIDEO](https://video.tv.adobe.com/v/3497308)

>[!NOTE]
>
>Les fonctionnalités de recherche génératives sont achetées séparément via un SKU d’IA. Contactez votre représentant Adobe pour l’activer pour votre compte.

### Prérequis {#gensearch-prerequisites}

* [!DNL AEM] composants principaux installés dans votre projet.
* Au moins un Source de contenu a déjà été créé et a le statut **Disponible**.
* La configuration OSGi du client d’IA dédiée au contenu AEM **** (`ContentAIClientImpl`) sur les instances de création et de publication, avec des informations d’identification d’API valides et un Source de contenu par défaut.

Pour obtenir le guide de configuration complet (mise à disposition du composant pour les auteurs, câblage de sa bibliothèque cliente et configuration de la boîte de dialogue), consultez la [documentation sur les composants principaux](https://www.adobe.com/go/aem_cmp_library_fr).

## Félicitations. {#congratulations}

Vous avez correctement configuré vos fonctionnalités de recherche sémantique et générative.

>[!VIDEO](https://video.tv.adobe.com/v/3497306)

## Étapes suivantes {#next-steps}

* [Configuration d’un projet Adobe Developer Console](setup-adc-project.md) - Créez le projet ADC et les informations d’identification dont vous avez besoin pour appeler directement l’API IA dédiée au contenu.
* [Référence de l’API Content AI](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) - Interrogez votre contenu indexé à l’aide de points d’entrée de recherche sémantiques, génératifs ou hybrides.
* [Documentation sur les composants principaux](https://www.adobe.com/go/aem_cmp_library_fr) - En savoir plus sur les composants proxy et les politiques de modèle.
