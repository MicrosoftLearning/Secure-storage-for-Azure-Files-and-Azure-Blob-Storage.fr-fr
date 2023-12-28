---
demo:
  title: "Démonstration\_04\_: Créer et configurer le chiffrement et sécuriser l’accès aux applications"
  module: Guided Project - Azure Files and Azure Blobs
--- 

## Démonstration : Créer et configurer le chiffrement et sécuriser l’accès aux applications. 

Dans cette démonstration, explorez le chiffrement et la sécurité des applications.

> **Remarque** : dans cette démonstration, vous allez créer une identité managée, un coffre de clés et une clé. Pour gagner du temps, vous pouvez créer ces ressources à l’avance. 

## Créez un coffre de clés, une clé et une identité managée.

1. Créez un compte de stockage Azure. Ces ressources seront utilisées pour afficher les fonctionnalités de stockage sécurisées.

1. [Diapositive de support] Avant de commencer, passez en revue la façon dont la nouvelle application développeur doit accéder en toute sécurité au stockage dont elle a besoin. L’accès à l’application se fait par le biais d’une identité managée. L’identité managée utilise une clé de chiffrement stockée dans Azure Key Vault. Azure Key Vault est un service cloud utilisé pour gérer les clés, les secrets et les certificats. Ce processus remplace la nécessité de stocker les informations de sécurité dans le code de l’application.  Tous les participants ne connaissent pas forcément ces concepts.

1. Créez une **identité managée**. En savoir plus sur les [identités managées](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview).

1. Créez un **coffre de clés** en conservant les paramètres par défaut. En savoir plus sur [Azure Key Vault](https://learn.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).

1. Attendez que le coffre de clés soit déployé, puis sélectionnez **Accéder à la ressource**.

1. Dans le panneau **Objets**, attirez l’attention sur les **clés, les secrets et les certificats**.

1. Sélectionnez **Clés**, puis **+ Générer/Importer**.

1. Donnez un **nom** à la clé, puis **créez**-la. Utilisez les valeurs par défaut.

## Configurez le compte de stockage pour l’identité managée et le coffre de clés, attribuez des autorisations.

1. Revenez au compte de stockage.

1. Dans le panneau **Sécurité + mise en réseau**, sélectionnez **Chiffrement**.

    - Sélectionnez **Clés gérées par le client**. Discutez de la différence entre une clé gérée par Microsoft et des clés gérées par le client. Par exemple, une clé gérée par Microsoft est utilisée pour le chiffrement et le déchiffrement automatiques du stockage. Une clé gérée par le client peut être utilisée par une application. En savoir plus sur les [clés gérées par le client](https://learn.microsoft.com/azure/storage/common/customer-managed-keys-overview).

    - Pour le **type de stockage de clé**, sélectionnez **Coffre de clés**. Les clés peuvent être stockées dans des logiciels (coffre de clés) ou dans du matériel (module de sécurité matériel). Nous utilisons le coffre de clés.

    - Sélectionnez votre **coffre de clés** et une **clé**.

    - Sous **Type d’identité**, sélectionnez **Identité managée affectée par le système**. Il s’agit de la valeur par défaut qui configure l’identité managée afin qu’elle puisse accéder au coffre de clés.

1. [Diapositive de support] À ce stade, vous avez donné à l’identité managée l’accès au coffre de clés et associé à l’identité avec le compte de stockage. Nous devons maintenant donner à l’identité managée l’accès au compte de stockage. En savoir plus sur les [attributions de rôles Azure](https://learn.microsoft.com/azure/role-based-access-control/role-assignments).

1. Revenez à votre compte de stockage et sélectionnez **Contrôle d’accès (IAM)** . En savoir plus sur les [rôles intégrés Azure](https://learn.microsoft.com/azure/role-based-access-control/built-in-roles).

    - Sélectionnez **Ajouter** et **Ajouter une attribution de rôle**. Sous l’onglet **Type d’affectation**, indiquez que nous affectons un rôle de poste.

    - Accédez à l’onglet **Rôle** et recherchez l’**objet blob**. Sélectionnez le rôle **Lecteur de données d’objets blob de stockage**.

    - Passez à l’onglet **Membres** et attribuez un accès à l’**identité managée**.

    - Sélectionnez **Sélectionner des membres**, puis sélectionnez votre **identité managée affectée par l’utilisateur**.

## Configurez un stockage immuable.

1. [Diapositive de support] Les développeurs doivent pouvoir stocker des données critiques pour l’entreprise qui ne peuvent pas être modifiées pendant une période spécifiée par l’utilisateur. Le stockage immuable vous permet de protéger vos données contre le remplacement ou la suppression. Discutez des stratégies de rétention basées sur le temps et des stratégies de conservation légale. En savoir plus sur le [stockage immuable](https://learn.microsoft.com/azure/storage/blobs/immutable-storage-overview).

1. Dans votre **compte de stockage**, sélectionnez le panneau **Conteneur**.

1. **Créez** un conteneur appelé **hold** et **chargez**-y un fichier.

1. Accédez à votre conteneur **hold** et sélectionnez le panneau **Stratégie d’accès**.

1. Sous la section **Stockage d’objets blob immuables**, sélectionnez **+ Ajouter une stratégie**.

1. Sélectionnez **Conservation basée sur le temps** comme **Type de stratégie**.

1. Définissez la **Période de conservation** sur **5 jours**.

1. Veillez à **Enregistrer** vos modifications.

1. Essayez de supprimer le fichier du conteneur.

1. Vérifiez que la stratégie vous empêche de le supprimer.

## Configurez une étendue de chiffrement pour le chiffrement d’infrastructure.

1. Les développeurs doivent également prendre en compte le chiffrement de l’infrastructure au niveau du conteneur. Discutez des étendues de chiffrement et du chiffrement de l’infrastructure. En savoir plus sur les [étendues de chiffrement](https://learn.microsoft.com/azure/storage/blobs/encryption-scope-overview).

1. Continuez dans le **compte de stockage**.

1. Dans la section **Sécurité + mise en réseau**, sélectionnez **Chiffrement**.

1. Passez à l’onglet **Étendues de chiffrement**, puis sélectionnez **+ Ajouter**.

1. Donnez un **nom** à votre **étendue de chiffrement**.

1. Assurez-vous que le **Chiffrement d’infrastructure** est **activé**. Attirez l’attention sur la mention « Cette option ne peut pas être modifiée après la création de la portée de chiffrement ».

>**Remarque** : les participants doivent maintenant être en mesure de compléter le LAB_04. 
