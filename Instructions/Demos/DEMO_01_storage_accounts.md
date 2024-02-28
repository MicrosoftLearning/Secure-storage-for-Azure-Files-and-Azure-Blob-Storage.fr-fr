---
demo:
  title: "Démonstration\_01\_: Créer et configurer des comptes de stockage"
  module: Guided Project - Azure Files and Azure Blobs
---
## Démonstration : Créer et configurer des comptes de stockage 

Dans cette démonstration, explorez les comptes de stockage.

1. [Diapositive de support] Avant de commencer cette démonstration, vous pouvez discuter de l’organisation du stockage et des facteurs à prendre en compte. 

1. Accédez au **Portail Azure**.

1. Dans la zone de recherche, saisissez **Comptes de stockage**. Au fur et à mesure de la saisie, la liste est filtrée.

1. Sélectionnez **Comptes de stockage**.

1. Sélectionnez **Créer**.

1. Expliquez comment le Portail Azure offre une interface d’assistant facile à utiliser. Rappelez aux participants que les éléments marqués d’un astérisque rouge sont obligatoires.

1. Sélectionnez l’**abonnement**.

1. Sélectionnez le **groupe de ressources**.

1. Entrez un nom pour votre compte de stockage. Discutez des restrictions de nommage des comptes de stockage.

1. Sélectionnez une région pour votre compte de stockage. Passez en revue la région que les participants doivent utiliser dans le labo. Apprenez-en davantage sur les [zones géographiques Azure](https://azure.microsoft.com/explore/global-infrastructure/geographies/).

1. [Diapositive de support] Sélectionnez le niveau de performance **standard**. En savoir plus sur les [types de compte de stockage](https://learn.microsoft.com/azure/storage/common/storage-account-overview).

1. [Diapositive de support] Sélectionnez **Redondance** comme **Stockage localement redondant**. En savoir plus sur la [redondance du stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-redundancy).

1. Accédez à l’onglet **Avancé**. Dans la section **Sécurité** , mettez en surbrillance ces paramètres. Notez que nous ne couvrons que quelques éléments pour permettre aux participants de démarrer leur premier labo. 

    - **Exigez un transfert sécurisé pour les opérations d’API REST**. Par défaut, les requêtes de compte de stockage ne sont acceptées qu’à partir d’une connexion sécurisée. En savoir plus sur le [transfert sécurisé](https://learn.microsoft.com/azure/storage/common/storage-require-secure-transfer).

    - **Activez l’accès de la clé du compte de stockage**. Expliquez comment ce paramètre peut désactiver l’accès au compte de stockage. Par exemple, l’accès au compte de stockage du service informatique pourrait être désactivé. Parlez de l’importance de la protection de la clé. En savoir plus sur la [gestion des clés d’accès au compte de stockage](https://learn.microsoft.com/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).

    - **Version TLS minimale**. Expliquez que Transport Layer Service sert à sécuriser les communications sur le réseau. TLS est une version améliorée de SSL. Vos développeurs peuvent vous demander les versions disponibles. En savoir plus sur [Transport Layer Service](https://learn.microsoft.com/azure/storage/common/transport-layer-security-configure-minimum-version).

1. Expliquez que d’autres onglets seront abordés au fur et à mesure des labos.

1. Sélectionnez **Vérifier** et assurez-vous qu’il n’y a pas d’erreurs de validation. Parlez des erreurs de validation possibles. 

1. Sélectionnez **Créer** et attendez que le compte de stockage soit déployé. Attirez l’attention sur les messages de notification.

1. Montrez comment **accéder à la ressource**. Discutez des autres moyens d’accéder à la ressource.

>**Remarque** : les participants doivent maintenant être en mesure de compléter le LAB_01.
