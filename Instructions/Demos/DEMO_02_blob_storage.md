---
demo:
  title: "Démonstration\_02\_: Créer et configurer le stockage d’objets blob"
  module: Guided Project - Azure Files and Azure Blobs
---


## Démonstration : Créer et configurer le stockage d’objets blob.

Dans cette démonstration, explorez le stockage d’objets blob.

## Passez en revue les paramètres de stockage d’objets blob

1. [Diapositive de support] Avant de commencer la démonstration, passez en revue les utilisations et l’organisation du stockage d’objets blob. Parmi nos groupes d’entreprises, lesquels auront besoin stockage d’objets blob ?

1. Accédez au **Portail Azure**.

1. Vous pouvez continuer à utiliser le compte de stockage précédent. 

1. Sélectionnez l’onglet **Vue d’ensemble**.

1. [Diapositive de support] Dans la section **service BLOB**, mettez en surbrillance le paramètre **Niveau d’accès par défaut**. Expliquez comment le contenu de l’entreprise peut se trouver dans le niveau d’accès chaud. Les informations d’audit peuvent se trouver dans le niveau froid. Les journaux d’activité ou la documentation marketing saisonnière peuvent se trouver dans le niveau archive. En savoir plus sur les [niveaux d’accès pour le stockage d’objets blob](https://docs.microsoft.com/azure/storage/blobs/access-tiers-overview).

1. [Diapositive de support] Dans la section **service BLOB**, mettez en surbrillance les paramètres de **suppression réversible**. Cela serait important pour le site web public au cas où quelque chose serait accidentellement supprimé ou remplacé. Les participants s’entraîneront à effectuer des suppressions réversibles dans le labo. En savoir plus sur la [suppression réversible des objets blobs](https://learn.microsoft.com/azure/storage/blobs/soft-delete-blob-overview).

1. Dans la section **Service Blob**, attirez l’attention sur le paramètre **Contrôle de version**. Ce paramètre peut être important pour le service marketing. Il peut être nécessaire d’assurer le suivi de la documentation sur les produits.

## Créez un conteneur d’objets blob, chargez un fichier et configurez l’accès.

1. Dans votre compte de stockage, localisez le panneau **Stockage des données**.

1. Sélectionnez **Conteneurs**, puis **+ Conteneur**.

1. **Nommez** votre nouveau conteneur
2. **public**. Il s’agit d’un stockage pour le site web public.

1. Définissez le niveau d’accès sur **Conteneur (accès anonyme en lecture pour les conteneurs et les objets blob)**. Décrivez brièvement les niveaux d’accès. Ce point est abordé plus en détail dans la dernière démonstration. 

1. Sélectionnez **Créer**.

1. Attendez que le conteneur soit déployé, puis continuez à travailler dans le conteneur **public**.

1. **Chargez un objet blob**. Si vous en avez le temps, discutez des options. 

1. Sélectionnez le **fichier chargé** et **copiez l’URL**.

1. Ouvrez un **nouvel onglet de navigateur**, collez l’URL et vérifiez que le fichier chargé s’affiche.

1. Revenez au conteneur **public** et **changez le niveau d’accès** en **Privé (pas d’accès anonyme)**.

1. **Actualisez l’onglet de l’URL** et confirmez que l’accès à la ressource est désormais **refusé**.

## Configurer la gestion de cycle de vie.

1. [Diapositive de support] Commencez par discuter de la gestion du cycle de vie. Le groupe marketing dispose d’une documentation saisonnière sur les produits. Par exemple, la ligne de vêtements et d’accessoires d’hiver. Ce contenu peut être archivé jusqu’à la saison suivante. L’archivage du contenu est facile à réaliser avec une règle de gestion du cycle de vie. En savoir plus sur les [stratégies de gestion du cycle de vie des objets blobs](https://learn.microsoft.com/azure/storage/blobs/lifecycle-management-overview).

1. Continuez à travailler dans le compte de stockage.

1. Dans le panneau **Gestion des données**, sélectionnez **Gestion de cycle de vie**.

1. Sous l’onglet **Détails**, nommez la règle **movetoarchive**.

1. Discutez de l’**étendue de la règle** et de la façon dont vous pouvez **limiter les objets blob avec des filtres**. Par exemple, ne déplacer que le contenu d’un conteneur spécifique.

1. Accédez à l’onglet **Objets blobs de base**.

1. Expliquez comment la règle déplacera automatiquement les objets blob sur la base de la dernière modification ou de la date de création.

1. Ouvrez la liste déroulante **Puis** et présentez les options. Essayez de donner des exemples basés sur le scénario de notre labo. Par exemple, le service informatique pourrait vouloir que les objets blob soient supprimés au bout de 30 jours, car il s’agit d’un compte de test.

## Configurez un accès limité au contenu.

1. Passez en revue les cas d’utilisation de l’accès limité. Par exemple, le contenu de l’entreprise doit être partagé avec des fournisseurs ou des partenaires tiers. L’accès peut être limité à une période et une action spécifiques (lecture, écriture). En savoir plus sur les [Signatures d’accès partagé](https://learn.microsoft.com/azure/storage/common/storage-sas-overview).

1. Continuez avec le **compte de stockage**.

1. Dans le panneau **Sécurité + mise en réseau**, sélectionnez **Signature d’accès partagé**.

1. Passez en revue les **Services autorisés** et les **Types de ressources autorisés**. Expliquez qu’une SAS peut être limitée à un compte de stockage, à un conteneur, à un fichier ou à un objet blob individuel.

1. Passez en revue les **Autorisations autorisées**.

1. Sélectionnez **Objet blob et conteneur** et **Lecture**.

1. Passez en revue les paramètres de **date/heure de début** et d’**expiration**.

1. Sélectionnez **Générer la chaîne de connexion et SAP**.

1. **Enregistrez** les changements apportés. 

1. Copiez l’**URL de la SAS du service BLOB** dans un nouvel onglet de navigateur.

1. Expliquez pourquoi le contenu est affiché alors qu’il s’agit d’un conteneur privé.

## Configurez la réplication d’objets blob. 

1. [Diapositive de support] Avant de poursuivre la démonstration, passez en revue les cas d’utilisation de la réplication d’objets blob. Par exemple, le contenu du site web public doit être sauvegardé. Expliquez que les comptes de stockage peuvent se trouver dans différentes régions Azure, mais cela n’est pas obligatoire. En savoir plus sur la [réplication d’objets](https://learn.microsoft.com/azure/storage/blobs/object-replication-overview).

1. **Créez** un compte de stockage.

1. **Créez** un **conteneur** de **sauvegarde** dans le compte de stockage.

1. Revenez au premier compte de stockage et au conteneur **public**. 

1. Dans le panneau **Gestion des données**, sélectionnez **Réplication d’objets**.

1. Sélectionnez **Créer des règles de réplication**.

    - Compte de stockage de destination : votre deuxième compte de stockage

    - Conteneur source : **public**

    - Conteneur de destination : **backup**

1. **Créez** la règle. Expliquez que la réplication du conteneur source peut prendre 5 à 10 minutes. Expliquez que les participants prendront ce temps pendant le labo. 

> **Remarque** : les participants doivent maintenant être en mesure de compléter les LAB_02a et LAB_02b. 

  
