---
lab:
  title: "Exercice\_02b\_: Fournir du stockage privé pour les documents internes de l’entreprise"
  module: Guided Project - Azure Files and Azure Blobs
---


L’entreprise a besoin de stockage pour ses bureaux et services. Ce contenu est privé et ne doit pas être partagé sans le consentement de l’entreprise. Ce stockage nécessite une haute disponibilité en cas de panne régionale. L’entreprise souhaite utiliser ce stockage pour sauvegarder son site web public. 

## Diagramme de l'architecture

![Diagramme avec un compte de stockage et deux conteneurs d’objets blob](../Media/task-3.png)

## Tâches d'apprentissage
- Créez un compte de stockage pour les documents privés de l’entreprise.
- Configurez la redondance pour le compte de stockage. 
- Configurez une signature d’accès partagé afin que les partenaires aient un accès restreint à un fichier. 
- Sauvegarder le stockage du site web public.
- Implémenter la gestion de cycle de vie pour déplacer le contenu vers le niveau de stockage sporadique.

## Instructions de l’exercice

> **Remarque** : ces instructions requièrent que vous ayez terminé le **Lab 02a**, Fournir du stockage pour les documents internes.

## Créez un compte de stockage et configurez la haute disponibilité.

1. Créez un compte de stockage pour les documents d’entreprise privés internes.
    - Dans le portail, recherchez et sélectionnez **Comptes de stockage**.  
    - Sélectionnez **+ Créer**. 
    - Sélectionnez le **Groupe de ressources** que vous avez créé au labo précédent.   
    - Définissez le **Nom du compte de stockage** sur `private`. Ajoutez un identificateur au nom pour vous assurer qu’il est unique. 
    - Sélectionnez **Vérifier**, puis **Créer** pour créer le compte de stockage. 
    - Attendez que le compte de stockage soit déployé, puis sélectionnez **Accéder à la ressource**.

1. Ce stockage nécessite une haute disponibilité en cas de panne régionale. L’accès en lecture dans la région secondaire n’est pas exigé. Configurez le niveau de **redondance** approprié. 

    - Dans le compte de stockage, dans la section **Gestion des données**, sélectionnez le panneau **Redondance**. 
    - Vérifiez que **Stockage géoredondant (GRS)** est sélectionné.
    - **Actualisez** la page. 
    - Passez en revue les informations d’emplacement principal et secondaire. 
    - **Enregistrez** les changements apportés.

## Créez un conteneur de stockage, chargez un fichier et limitez l’accès à ce fichier. 

1. Créez un conteneur de stockage privé pour les données d’entreprise. 

    - Dans le compte de stockage, dans la section **Stockage des données**, sélectionnez le panneau **Conteneurs**. 
    - Sélectionnez **+ Conteneur**. 
    - Vérifiez que le **Nom** du conteneur est `private`.
    - Vérifiez que le **Niveau d’accès public** est défini sur **Privé (aucun accès anonyme)**.
    - Si vous en avez le temps, passez en revue les paramètres **Avancés**, mais conservez les valeurs par défaut. 
    - Sélectionnez **Créer**. 

1.  Pour effectuer des tests, chargez un fichier dans le conteneur **privé**. Le type de fichier n’a pas d’importance. Choisissez par exemple un petit fichier image ou texte. Faites un test pour vérifier que le fichier n’est pas accessible au public. 

    - Sélectionnez le conteneur.
    - Sélectionnez **Charger**.
    - **Parcourez les fichiers** et sélectionnez-en un.
    - **Chargez** le fichier.
    - Sélectionnez le fichier chargé.
    - Sous l’onglet **Vue d’ensemble**, copiez l’**URL**.
    - Collez l’**URL** dans un nouvel onglet de navigateur. 
    - Vérifiez que le fichier ne s’affiche pas et que vous recevez une erreur. 

1. Un partenaire externe a besoin d’accéder en lecture et en écriture au fichier pendant au moins les prochaines 24 heures. Configurez et testez une signature d’accès partagé (SAS). Découvrez plus d’informations sur les [Signatures d’accès partagé](https://learn.microsoft.com/azure/storage/common/storage-sas-overview).

    - Sélectionnez votre fichier blob chargé et passez à l’onglet **Générer une signature d’accès partagé**. 
    - Dans la liste déroulante **Autorisations**, vérifiez que le partenaire dispose uniquement des autorisations de **Lecture**.
    - Vérifiez que la section **Date/heure de début et d’expiration** indique les prochaines 24 heures. 
    - Sélectionnez **Générer un jeton SAS et une URL**.
    - Copiez l’**URL de la SAS Blob** dans un nouvel onglet de navigateur.
    - Vérifiez que vous pouvez accéder au fichier. Si vous avez chargé un fichier image, il s’affiche dans le navigateur. Les autres types de fichiers seront téléchargés.

## Configurez les niveaux d’accès de stockage et la réplication de contenu.

1. Pour réduire les coûts, après 30 jours, déplacez les blobs du niveau chaud vers le niveau de stockage sporadique. En savoir plus sur la gestion du [cycle de vie du Stockage Blob Azure](https://learn.microsoft.com/azure/storage/blobs/lifecycle-management-policy-configure?tabs=azure-portal).

    - Revenez au **compte de stockage**.
    - Dans la section **Vue d’ensemble**, notez que le **Niveau d’accès par défaut** est défini sur **Chaud**. 
    - Dans la section **Gestion des données**, sélectionnez le panneau **Gestion de cycle de vie**.
    - Sélectionnez **Ajouter une règle**. 
    - Définissez le **Nom de la règle** sur `movetocool`.
    - Définissez l’**Étendue de la règle** sur **Appliquer la règle à tous les objets blob du compte de stockage**.
    - Cliquez sur **Suivant**.
    - Veillez à sélectionner **Dernière modification**.
    - Définissez **Il y a plus de (jours)** sur **30**.
    - Dans la liste déroulante **Puis**, sélectionnez **Déplacer vers le stockage sporadique**.
    - Si vous en avez le temps, passez en revue les autres options du cycle de vie dans la liste déroulante. 
    - Sélectionnez **Ajouter** pour ajouter la règle.
  
1. Les fichiers du site web public doivent être sauvegardés dans un autre compte de stockage. En savoir plus sur la [réplication d’objets](https://learn.microsoft.com/azure/storage/blobs/object-replication-configure?tabs=portal).

    - Dans votre compte de stockage, **créez** un nouveau conteneur appelé `backup`. Utilisez les valeurs par défaut. Reportez-vous au Lab 02a si vous avez besoin d’instructions détaillées. 
    - Accédez au compte de stockage de votre **site web public**. Ce compte de stockage a été créé dans l’exercice précédent. 
        - Dans la section **Gestion des données**, sélectionnez le panneau **Réplication d’objets**. 
        - Sélectionnez **Créer des règles de réplication**.
        - Définissez le **Compte de stockage de destination** sur le compte de stockage **privé**.
        - Définissez le **Conteneur source** sur **public** et le **Conteneur de destination** sur **backup**.
        - Cliquez sur **Créer** pour créer la règle de réplication. 
    - Si vous en avez le temps, vous pouvez charger un fichier dans le conteneur **public** (facultatif). Revenez au compte de stockage **privé** et actualisez le conteneur de **sauvegarde**. Dans quelques minutes, le fichier de votre site web public apparaîtra dans le dossier de sauvegarde. 

>**Remarque** :pour des exercices supplémentaires, suivez le module [Configurer le stockage d’objets blob Azure](https://learn.microsoft.com/training/modules/configure-blob-storage/). Le module propose une simulation de labo interactif qui vous permet de vous familiariser davantage avec la création d’un stockage d’objets blob. 

## Développer votre apprentissage avec Copilot

Copilot peut vous aider dans votre parcours d’apprentissage. Copilot peut fournir des informations techniques de base, des étapes générales, des avantages et des inconvénients, de l’aide à la résolution des problèmes, des cas d’utilisation, des exemples de codage, etc. Pour accéder à Copilot, ouvrez un navigateur Edge et choisissez Copilot (en haut à droite). Prenez quelques minutes pour essayer ces invites.
+ Quelles fonctionnalités de sécurité sont disponibles pour protéger le stockage Azure ?
+ Qu’est-ce qu’une SAP Azure et comment est-elle utilisée ?

## En savoir plus grâce à l’apprentissage auto-rythmé

+ [Configurer la sécurité de Stockage Azure](https://learn.microsoft.com/training/modules/configure-storage-security/) Découvrez comment configurer les fonctionnalités de sécurité courantes du stockage Azure, telles que les signatures d'accès au stockage.
+ [Gérer le cycle de vie du stockage Blob Azure](https://learn.microsoft.com/training/modules/configure-storage-security/) Apprenez à gérer la disponibilité des données tout au long du cycle de vie du stockage Blob Azure.

## Points clés

Félicitations, vous avez terminé le labo. Voici les principaux points à retenir de ce labo. 
+ Le stockage Azure offre de nombreuses fonctionnalités de protection des données, notamment le chiffrement, le contrôle d’accès, la sécurité réseau, la surveillance et les alertes. 
+ Une signature d’accès partagé (SAS) fournit un accès délégué sécurisé aux ressources de votre compte de stockage. Avec une SAP, vous avez un contrôle granulaire sur la manière dont un client peut accéder à vos données.
+ La gestion de cycle de vie de Stockage Blob Azure offre une stratégie basée sur des règles que vous pouvez utiliser pour faire passer les données blob aux niveaux d’accès appropriés ou faire expirer les données à la fin de leur cycle de vie.
+ La réplication d’objets copie de façon asynchrone des objets blob de blocs entre un compte de stockage source et un compte de destination.
