---
title: Vue d’ensemble de l’IA dédiée au contenu d’AEM
description: Découvrez l’IA dédiée au contenu d’AEM, son importance et comment commencer à l’activer et à la contrôler pour votre environnement AEM as a Cloud Service.
topic: Overview
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: IA dédiée au contenu d’AEM, vue d’ensemble, source de contenu, recherche sémantique, acquisition, Cloud Manager
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: ht
source-wordcount: '885'
ht-degree: 100%

---


# IA dédiée au contenu d’AEM - Introduction

## Contenu intelligent, IA native {#ai-ready}

Le premier contact de la clientèle avec une marque s’opère par le biais de l’IA, avant même de se rendre sur son site web. Assistants de conversation, présentations par l’IA, agents, recherche conversationnelle, assistants IA : ils récupèrent, résument et représentent le contenu de la marque au nom de la marque. Leurs réponses ne sont exactes, à jour et dans le ton de la marque que si le contenu auquel ils peuvent accéder l’est également.
L’IA dédiée au contenu d’AEM se propose de résoudre ce problème. Elle traite le contenu de marque comme étant le socle sur lequel reposent les expériences d’IA et fournit aux clients et clientes AEM les outils nécessaires pour bâtir celui-ci plus rapidement du côté création et diffuser ce contenu ancré proprement aux expériences axées sur l’IA destinées à la clientèle du côté publication.

**Côté création**, l’IA dédiée au contenu d’AEM s’appuie sur des sources approuvées par la marque pour la création de contenu. La création assistée par l’IA, la découverte en langage naturel dans le contenu de pages, les fragments et les ressources existants, ainsi que la génération basée sur la marque permettent aux équipes de produire des variations pour de nouveaux canaux, audiences et régions sans quitter AEM et sans s’écarter de ce qui est déjà approuvé.

**Côté publication**, le même contenu est structuré, régi et adressable pour d’être exploité par l’IA. Les fragments, les métadonnées, les taxonomies et les sources approuvées sont exposés sous des formes que les systèmes de récupération, les agents et les interfaces conversationnelles peuvent utiliser en toute confiance. Ainsi, lorsque l’IA parle au nom de la marque, elle est fidèle à son discours.

### Signification pour les clientes et clients AEM {#what-it-means}

Le contenu approuvé est le rempart ultime de la marque contre les hallucinations. Lorsque l’IA repose sur du contenu AEM qui a fait l’objet d’un ancrage, les réponses restent par défaut exactes, à jour et dans le ton de la marque.
La création suit le rythme de la demande de l’ère de l’IA. Les équipes génèrent des copies et des images pour un plus grand nombre d’audiences et de moments dans l’expérience de création, en puisant à des sources approuvées plutôt qu’en commençant à partir d’une page vide.
Le processus de découverte s’adapte à la façon dont les personnes et les machines effectuent leurs demandes. La recherche en langage naturel basée sur l’intention dans les ressources, fragments, pages et formulaires transforme le contenu existant en un fichier réutilisable.
La personnalisation évolue en fonction de la réutilisation, et non de la duplication. Les composants approuvés se recombinent en variantes au lieu de se multiplier en copies non suivies.
Les canaux de publication incluent désormais des surfaces d’IA. Le contenu est diffusé sous des formes que les humains, les agents et les expériences médiées par l’IA peuvent tous utiliser, sans pipeline distinct pour chacun.

**Le point essentiel : le contenu de marque existant et approuvé n’a jamais été aussi précieux qu’aujourd’hui. Chaque fragment, ressource et page approuvé qui réside déjà dans AEM devient la source de vérité dont dépendent les expériences pilotées par l’IA. C’est grâ ce à l’IA dédiée au contenu d’AEM que cette bibliothèque est réutilisable, détectable et prête à alimenter ce qui vient ensuite.**

## Aperçu de l’IA dédiée au contenu d’AEM {#at-a-glance}

La structure de l’IA dédiée au contenu d’AEM est composée de quatre niveaux, chaque niveau s’appuyant sur le précédent. Elle part du contenu approuvé pour aller à des expériences agentiques.

![Diagramme de la structure à quatre niveaux de l’IA dédiée au contenu d’AEM : sources de l’IA dédiée au contenu à la base, services de base de l’IA dédiée au contenu, orchestration du contenu agentique, et orchestration d’expériences agentiques au sommet](../assets/content-ai-four-layer-architecture-stack.png)

*Lisez la pile de bas en haut : partez du contenu approuvé pour arriver aux expériences agentiques.*

1. Sources de l’IA dédiée au contenu
Les sources de contenu sont des entités gérées dans l’IA dédiée au contenu d’AEM qui se connectent à un ensemble de contenu approuvé. Un source de contenu peut référencer un type de contenu régi par AEM tel que des ressources, des fragments de contenu, des pages, des formulaires, des métadonnées et des taxonomies, ainsi que des sources externes à AEM telles que des sites web tiers, des bases de connaissances ou des portails de documentation. Chaque source de contenu est automatiquement vectorisé et enrichi sémantiquement pour alimenter les expériences d’IA en termes de récupération, d’ancrage et de conversation. Définissez les sources de contenu une seule fois et réutilisez-les dans les API d’IA dédiée au contenu avec l’actualisation et les mises à jour automatiques intégrées.

1. Services de base de l’IA dédiée au contenu
Il s’agit des API et services qui permettent l’intelligence sémantique et l’IA générative dans le contexte du contenu de la marque. En s’appuyant sur les sources de l’IA dédiée au contenu, ces services optimisent la récupération, la génération, la variation conforme à la marque et l’optimisation, le tout fondé sur le contenu approuvé par le client ou la cliente.

1. Orchestration du contenu agentique
MCP et agents qui transforment les exigences de contenu basées sur des cas d’utilisation en une action coordonnée en langage naturel. Ce niveau permet aux auteurs et autrices, et aux autres agents de décrire leurs besoins en langage simple et d’obtenir les services de base appropriés orchestrés pour y répondre.

1. Orchestration des expériences agentiques
Cas d’utilisation innovants qui émergent lorsque le contenu intelligent de la marque s’associe à l’IA à grande échelle. Les solutions AEM elles-mêmes sont créées sur ces services de base. Les clientes et clients peuvent utiliser directement les mêmes API pour créer leurs propres expériences agentiques à partir de leur propre contenu. Des chaînes d’approvisionnement de contenu optimisées par l’IA aux parcours utilisateur conversationnels, c’est à ce niveau que le contenu régi devient un avantage concurrentiel.

Ces niveaux sont conçus pour être connectées : chaque service d’IA puise dans la base de contenu et tout ce qui est produit retourne dans le même système gouverné de sorte que la création côté auteur ou autrice et la diffusion côté publication partagent une source de vérité.

## IA dédiée au contenu d’AEM en action {#action}

Pour obtenir une intégration de l’IA dédiée au contenu fonctionnelle, deux tâches sont nécessaires :

### &#x200B;1. Activer l’IA dédiée au contenu pour votre environnement AEM {#enable}

**Condition requis :** avant de commencer à utiliser l’IA dédiée au contenu, vous devez connaître les informations d’identification d’API de votre environnement AEM as a Cloud Service. Consultez [Configurer un projet Adobe Developer Console](setup-adc-project.md).

### &#x200B;2. Contrôler vos sources d’IA dédiée au contenu {#control}

Configurez et gérez vos sources d’IA dédiée au contenu pour activer les expériences basées sur l’IA. Consultez [Contrôler vos sources de contenu](contentsources.md) pour en savoir plus.

## Découvrir les API de l’IA dédiée au contenu  {#apis}

Explorez l’ampleur fonctionnelle de l’IA dédiée au contenu d’AEM : les API révèlent tout le potentiel de la plateforme. Consultez les [APId’ IA dédiée au contenu](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/).
