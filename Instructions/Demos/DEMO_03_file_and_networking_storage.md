---
demo:
  title: "Démonstration\_03\_: Créer et configurer des fichiers et des réseaux de stockage"
  module: Guided Project - Azure Files and Azure Blobs
--- 

## Démonstration : Créer et configurer des fichiers et des réseaux de stockage.

Dans cette démonstration, explorez le stockage Azure Files et la mise en réseau du stockage.

> **Remarque** : dans cette démonstration, vous allez créer un compte de stockage et un réseau virtuel avec un sous-réseau. Ils peuvent être créés au préalable pour gagner du temps. 

## Passez en revue Azure Files et créez un compte de stockage dédié au partage de fichiers.

1. [Diapositive de support] Avant de commencer la démonstration, discutez de ce qu’est le stockage Azure File et de la différence avec le stockage d’objets blob Azure. En savoir plus sur les [scénarios de stockage Azure](https://learn.microsoft.com/azure/storage/common/storage-introduction).

1. Accédez au **Portail Azure**.

1. **Créez** un compte de stockage Azure. Ce compte sera utilisé pour répondre aux exigences relatives aux fichiers partagés.

1. [Diapositive de support] Pour **Niveau de performance**, sélectionnez **Premium**. 

1. Pour **Type de compte Premium**, sélectionnez **Partages de fichiers**. Les partages de fichiers premium sont destinés aux applications d’entreprise ou de partage de fichiers hautes performances. Notre scénario concerne un partage de fichiers au sein de l’entreprise. 

1. Pour **Redondance**, sélectionnez **Stockage redondant interzone**. Rappelez aux participants que cette méthode est recommandée pour les scénarios de haute disponibilité et qu’elle permet de se prémunir contre les défaillances du centre de données.

1. Accédez à l’onglet **Protection des données**.

1. Faites remarquer que l’option **Activer la suppression réversible pour les partages de fichiers** est **activée**.

1. **Passez en revue** le compte de stockage, puis cliquez sur **Créer**.

## Configurez le partage de fichiers

1. Continuez dans le compte de stockage.

1. Dans le panneau **Stockage des données**, sélectionnez **Partages de fichiers**.

1. Sélectionnez **Partage de fichiers** et nommez le partage de fichiers **finance**.

1. Parlez de la **capacité provisionnée** et de la facturation d’un partage de fichiers premium en fonction de la taille des fichiers provisionnés, quelle que soit la capacité utilisée. Si vous en avez le temps, discutez des autres paramètres. 

1. Parlez du **protocole**, sélectionnez **SMB**.

1. Sélectionnez **Créer**.

## Configurez les paramètres de partage de fichiers et créez un instantané.

1. Sélectionnez le partage de fichiers **finance**.

1. Passez en revue les paramètres en haut de la page. Par exemple, **Charger** et **Modifier la taille et le niveau de performance**.

1. Parlez de l’objectif des instantanés. En savoir plus sur les [instantanés de partage de fichiers](https://learn.microsoft.com/azure/storage/files/storage-snapshots-files).

1. Dans le panneau **Opérations**, sélectionnez **Instantanés**.

1. Sélectionnez **Ajouter un instantané**, puis **OK**. L’ajout d’un commentaire est facultatif.

1. Au cours de ce labo, les participants chargeront des fichiers, en feront des instantanés et les restaureront.

## Configurez l’accès au réseau pour le stockage.

1. [Diapositive de support] Avant de configurer la mise en réseau du stockage, examinez les différentes options. Passez en revue certaines des options de mise en réseau configurées précédemment. 

1. Recherchez les **réseaux virtuels** dans le portail.

1. Utilisez l’onglet **Informations de base** pour créer un réseau virtuel nommé **corpnet**. Créez un **sous-réseau** appelé **finance**. Faites remarquer que ce réseau est déjà créé.

1. Revenez au compte de stockage.

1. Dans le panneau **Sécurité + mise en réseau**, sélectionnez **Mise en réseau**.

1. Sélectionnez **Activé à partir de réseaux virtuels et d’adresses IP sélectionnés**.

1. Sur la page **Ajouter un réseau**, ajoutez le réseau virtuel **corpnet** et le sous-réseau **finance**.

1. **Activez le point de terminaison**. Expliquez que la création d’un nouveau point de terminaison de service peut prendre jusqu’à 15 minutes.

1. Examinez les paramètres du **pare-feu**.

1. Passez en revue la section **Routage du réseau** et vérifiez que le routage du réseau Microsoft est utilisé.



1. Si vous en avez le temps, faites une démonstration rapide du **Navigateur de stockage**. 

>**Remarque** : les participants doivent maintenant être en mesure de compléter le LAB_03. 
