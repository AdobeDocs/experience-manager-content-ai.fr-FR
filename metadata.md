---
cloud: Experience Cloud
solution: Experience Manager
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
usetq: true
type: Documentation
git-repo: https://github.com/AdobeDocs/experience-manager-content-ai.fr-FR
index: true
recommendations: noDisplay
source-git-commit: a47559544a9e972285ba570f16a38272b35794a8
workflow-type: tm+mt
source-wordcount: 81
ht-degree: 2%

---


# Métadonnées à usage interne

Les métadonnées dans le système de création GitHub sont hiérarchiques et sont définies selon les niveaux de précédent croissants suivants.

1. metadata.md
1. ToC
1. Article

Les métadonnées définies dans le fichier metadata.md s’appliquent à l’ensemble du référentiel, mais elles peuvent être remplacées au niveau de la table des matières et de l’article. Tout remplacement des métadonnées doit être effectué au niveau le plus bas possible.

Les métadonnées du référentiel experience-manager-content-ai.en sont le minimum requis.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

ToCs

* `sub-product`
* `user-guide-title`

Article

* `title`
* `description`
