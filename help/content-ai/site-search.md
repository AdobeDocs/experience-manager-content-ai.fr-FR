---
title: Commencer avec la recherche optimisée par l’IA dédiée au contenu d’AEM
description: 'Ce guide explique comment activer la recherche sur votre site à l’aide de l’IA dédiée au contenu : connectez votre contenu, puis choisissez un composant de recherche pour le présenter aux visiteurs et visiteuses.'
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: IA dédiée au contenu d’AEM, Recherche optimisée par l’IA dédiée au contenu d’AEM, GenSearch, Recherche rapide, Sources d’IA dédiée au contenu, Acquisition, Cloud Manager
source-git-commit: 51fa66b5ac0ef77e438db76530788826da65f91e
workflow-type: ht
source-wordcount: '1487'
ht-degree: 100%

---


# Commencer avec la recherche optimisée par l’IA dédiée au contenu d’AEM

La recherche traditionnelle sur un site met en correspondance les mots qu’un visiteur ou une visiteuse saisit avec les mots présents dans votre contenu. Cela fonctionne correctement lorsque les visiteurs et visiteuses utilisent la même terminologie que votre contenu, mais dévie lorsqu’ils posent une question, expriment une intention ou expriment simplement les choses différemment. La recherche est l’un des signaux les plus clairs de l’intention des visiteurs et visiteuses sur un site. Par conséquent, un échec de correspondance signifie souvent un échec du parcours : le contenu n’est pas découvert, l’engagement est abandonné et les conversions sont perdues. Les visiteurs et visiteuses s’attendent de plus en plus à ce que la recherche comprenne ce qu’ils veulent dire, pas seulement ce qu’ils ont saisi. C’est ce même principe basé sur l’intention qui rend les réponses génératives possibles.

La recherche optimisée par l’IA dédiée au contenu d’AEM ne remplace pas l’expérience de recherche de votre site. Elle l’améliore, en passant de la correspondance de mots-clés à la compréhension de la signification et de l’intention et la réponse directe aux questions. La recherche sémantique permet une récupération basée sur l’intention en plus de votre expérience de recherche existante, présentant ainsi le contenu pertinent même lorsqu’une requête ne partage pas la formulation exacte du contenu. La recherche générative s’appuie sur le même principe de récupération pour produire des réponses contextuelles générées et basées sur le contenu de votre site. Il s’agit d’une étape distincte et non du même processus que la récupération sémantique.

Pour les visiteurs et visiteuses, cela se traduit par une meilleure pertinence, une prise en charge du langage naturel, moins de recherches sans résultat et des réponses plus rapides. Pour votre entreprise, cela se traduit par une meilleure correspondance d’intention, une découverte de contenu plus fiable et une base de recherche prête pour l’IA, sans devoir reconstruire votre expérience de recherche à partir de zéro. Et pour finir, pour votre équipe, il s’agit d’une mise à niveau incrémentielle : votre composant de recherche existant peut passer progressivement de fonctionnalités lexicales à des fonctionnalités sémantiques et génératives plutôt qu’une implémentation totalement nouvelle.

Pour y parvenir, deux décisions s’imposent : comment votre contenu entre dans l’IA dédiée au contenu et quel composant le présente aux visiteurs et visiteuses. Connectez votre contenu, puis ajoutez un composant de recherche à une page. Votre site est alors prêt à fournir aux visiteurs et visiteuses les résultats les plus pertinents et des réponses basées sur l’intention.

## Prérequis {#prerequisites}

Avant de commencer, assurez-vous que les conditions suivantes sont remplies :

* Vous disposez d’un programme Cloud Manager actif avec au moins un environnement AEM as a Cloud Service.
* Votre utilisateur ou utilisatrice se voit affecter le profil de produit **[!UICONTROL Utilisateurs et utilisatrices AEM]** (pour afficher les sources de contenu) et/ou **[!UICONTROL Administrateurs et administratrices AEM]** (pour les créer et les modifier), affecté au niveau de **publication**. L’IA dédiée au contenu indexe le contenu publié, et non le contenu créé. Voir [Affecter un utilisateur ou une utilisatrice à un profil de produit AEM](contentsources.md#assign-product-profile) pour la procédure complète.
* Le profil de produit d’environnement a été configuré dans **Adobe Admin Console**.

>[!NOTE]
>
>L’accès à Cloud Manager seul n’est pas suffisant. Un utilisateur ou une utilisatrice a également besoin d’un profil de produit AEM affecté au niveau de publication pour afficher ou gérer les sources de contenu.

## Étape 1a : connecter un index existant {#option-a}

Les index de référentiel existants apparaissent automatiquement dans la liste Sources de contenu en tant que Type de source AEM, indiqué par ce qu’ils indexent, comme les pages, les ressources ou les fragments de contenu. Ils commencent à l’état **Restreint** et verrouillés, ne pouvant pas encore faire l’objet d’une recherche via l’IA dédiée au contenu.

1. Connectez-vous à [Cloud Manager](https://my.cloudmanager.adobe.com/), sélectionnez votre programme et ouvrez l’onglet **[!UICONTROL Configuration de l’IA dédiée au contenu]** pour l’environnement que vous souhaitez configurer.
1. Recherchez la source sur laquelle vous souhaitez effectuer une recherche (par exemple, **Pages**) et sélectionnez son icône de verrouillage. Seuls les utilisateurs et utilisatrices disposant du profil de produit **[!UICONTROL Administrateurs et administratrices AEM]** peuvent effectuer cette opération. Les **[!UICONTROL Utilisateurs et utilisatrices AEM]** peuvent afficher les sources de contenu, sans modifier leur capacité de recherche.
1. Lisez la boîte de dialogue **Rendre la source interrogeable ?** attentivement. Elle vous informe que les listes de contrôle d’accès (ACL) Apache Oak ne seront pas appliquées pour cet index une fois qu’il sera interrogeable. Tout utilisateur ou toute utilisatrice authentifié pourra récupérer l’intégralité de son contenu. Cochez la case **Je comprends que les contrôles d’accès (ACL) ne sont pas appliqués et que tout le contenu de cette source peut faire l’objet de recherches** puis sélectionnez **Rendre interrogeable**.
1. Confirmez les changements de statut en **Disponible**. Une icône d’avertissement reste en regard de la source pour rappeler en permanence que les listes de contrôle d’accès sont ignorées pour celle-ci.
1. Exécutez une recherche de test pour vérifier que les résultats sont correctement renvoyés.

>[!WARNING]
>
>Rendre un index existant interrogeable de cette manière contourne entièrement les listes de contrôle d’accès Apache Oak pour cette source : tout utilisateur ou toute utilisatrice authentifié peut récupérer l’intégralité de son contenu par le biais d’une recherche, quelles que soient ses autorisations de référentiel normales. N’effectuez cette opération que pour les sources que souhaitez effectivement exposer entièrement.

>[!NOTE]
>
>Ce processus convient si vous disposez déjà d’un index avec le contenu de votre site, par exemple, le contenu de votre page. Utilisez cet index au lieu de configurer un mécanisme d’exploration distinct.

## Étape 1b : explorer un site web {#option-b}

Utilisez ce processus si vous ne disposez pas déjà d’un index de recherche pour votre site. Le robot d’exploration de l’IA dédiée au contenu en crée et en actualise un pour vous. Ce processus d’exploration est également appelé **acquisition** dans Cloud Manager et dans ce guide.

1. Ouvrez l’onglet **[!UICONTROL Configuration de l’IA dédiée au contenu]** comme dans l’étape 1a.
1. Sélectionnez **[!UICONTROL Créer un Source]** et renseignez les champs. Seuls les utilisateurs et utilisatrices disposant du profil de produit **[!UICONTROL Administrateurs et administratrices AEM]** peuvent ajouter de nouvelles sources de contenu.

   | Champ | Description |
   | --- | --- |
   | **[!UICONTROL Nom de la configuration d’IA dédiée au contenu]** | Identifiant unique de cette source. Impossible à changer après la création. |
   | **[!UICONTROL Adresse du site web]** | URL racine à explorer, par exemple, `https://www.example.com/`. |
   | **[!UICONTROL URL à exclure]** | *(Facultatif)* Modèles d’URL à ignorer lors de l’exploration. |
   | **[!UICONTROL Fréquence d’actualisation]** | Hebdomadaire, quotidienne, 4 fois par jour, toutes les 60 minutes ou toutes les 15 minutes. |

1. Sélectionnez **[!UICONTROL Créer une source]**. L’acquisition démarre automatiquement et la source passe à **Indexation**.
1. Surveillez le statut jusqu’à ce qu’il atteigne **Disponible** :

   | Statut | Signification |
   | --- | --- |
   | **Nouveau** | La source vient d’être créée ; l’acquisition automatique n’a pas encore commencé. |
   | **Indexation** | Exploration et indexation en cours. |
   | **Disponible** | Indexation terminée ; prête à répondre aux requêtes de recherche. |

1. Sélectionnez l’icône de **recherche** en regard de la source et exécutez une requête de test pour confirmer que votre contenu a été correctement indexé.

>[!CAUTION]
>
>Source bloquée au statut **[!UICONTROL Indexation]** ? Réessayez tout d’abord l’acquisition à partir du menu (…). Si elle ne progresse toujours pas, vérifiez que l’adresse du site web est accessible au public et que vos modèles **[!UICONTROL Exclure les URL]** ne filtrent pas toutes les pages.

## Étape 2 : choisir un composant de recherche {#choose-component}

Deux composants permettent d’effectuer une recherche sur une page, conçus sur des bases différentes :

| | Recherche rapide (v3) avec recherche sémantique | Recherche optimisée par l’IA dédiée au contenu d’AEM |
| --- | --- | --- |
| Foundation | Composant principal de recherche rapide existant, mis à niveau vers la version 3 | Nouveau composant autonome : appelle directement les API d’IA dédiée au contenu |
| Source de contenu | Contenu de votre site existant, déjà dans un index, enrichi pour la correspondance sémantique | Source d’IA dédiée au contenu (étape 1a ou 1b) |
| Réponse générative | Non ; améliore uniquement la qualité de correspondance de la liste de résultats existante | Oui ; résumé facultatif généré par l’IA avec des sources et une clause de non-responsabilité |
| Idéal | Sites utilisant déjà la recherche rapide et souhaitant une mise à niveau incrémentielle plus légère | Composant suggéré pour l’ensemble des fonctionnalités d’IA dédiée au contenu : recherche sémantique, recherche générative et recherche en langage naturel (NLS) |

## Recherche rapide (v3) avec recherche sémantique {#quicksearch}

Si votre site utilise déjà le composant Recherche rapide [!DNL AEM] classique, la v3 ajoute un bouton d’activation/de désactivation de **Recherche optimisée par l’IA** que les visiteurs et visiteuses peuvent activer ; aucun nouveau composant, proxy ni nouvelle source de contenu n’est requis.

* La recherche s’exécute toujours via le même chemin JCR/QueryBuilder qu’actuellement ; rien ne change dans la servlet de résultat ou dans la manière dont les résultats sont rendus.
* Lorsqu’un visiteur ou une visiteuse active le bouton (bascule), le composant préfixe la requête avec un marqueur spécial qui l’achemine vers une correspondance sémantique au lieu du texte intégral du mot-clé brut.
* Il n’y a pas de résumé de réponse générative de réponse dans ce processus. Il améliore la qualité de correspondance de la liste de résultats existante ; il n’ajoute pas de réponse d’IA générative.
* **L’étape 1 (intégration de l’IA dédiée au contenu) ne s’applique pas à ce processus.** Il n’y a pas de source de contenu à créer ou à connecter. Ce composant interroge directement votre index de page existant.

>[!NOTE]
>
>Si la recherche sémantique ne fonctionne pas comme prévu après avoir activé le bouton, ouvrez un ticket d’assistance.

Ce processus convient si vous souhaitez une mise à niveau incrémentielle de la recherche sémantique sans utiliser de nouveau composant ou de nouvelles sources de contenu. Ce n’est pas le processus approprié si vous souhaitez disposer de l’expérience de réponse générative ; pour cela, utilisez la recherche optimisée par l’IA dédiée au contenu d’AEM.

## Recherche optimisée par l’IA dédiée au contenu d’AEM {#gensearch}

La recherche optimisée par l’IA dédiée au contenu d’AEM est un composant principal d’[!DNL AEM] qui permet aux visiteurs et visiteuses de rechercher une source de contenu directement à partir d’une page, avec des fonctionnalités de recherche sémantique et de recherche générative.

>[!VIDEO](https://video.tv.adobe.com/v/3497308)

>[!NOTE]
>
>Les fonctionnalités de recherche générative sont achetées séparément via un SKU d’IA. Contactez votre représentant ou représentante du service commercial Adobe pour l’activer pour votre compte.

### Prérequis {#gensearch-prerequisites}

* Composants principaux d’[!DNL AEM] installés dans votre projet.
* Au moins une source de contenu déjà créée et au statut **Disponible**.
* Configuration OSGi du **client d’IA dédiée au contenu d’AEM** (`ContentAIClientImpl`) sur les instances de création et de publication, avec des informations d’identification d’API valides et une source de contenu par défaut.

Pour obtenir le guide de configuration complet, mise à disposition du composant pour les créateurs et créatrices, raccordement de sa bibliothèque cliente et configuration de la boîte de dialogue, consultez la [documentation sur les composants principaux](https://www.adobe.com/go/aem_cmp_library_fr).

## Félicitations. {#congratulations}

Vous avez correctement configuré vos fonctionnalités de recherche sémantique et générative.

>[!VIDEO](https://video.tv.adobe.com/v/3497306)

## Étapes suivantes {#next-steps}

* [Configurer un projet Adobe Developer Console](setup-adc-project.md) : créez le projet ADC et les informations d’identification dont vous avez besoin pour appeler directement l’API d’IA dédiée au contenu.
* [Référence de l’API d’IA dédiée au contenu](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) : interrogez votre contenu indexé à l’aide de points d’entrée de recherche sémantique, générative ou hybride.
* [Documentation sur les composants principaux](https://www.adobe.com/go/aem_cmp_library_fr) : en savoir plus sur les composants proxy et les politiques de modèle.
