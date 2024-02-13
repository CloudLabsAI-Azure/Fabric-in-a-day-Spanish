![](Media/lab-07-1.png "Lab Environment")

# Sommaire

- Introduction
- Power BI

    - Tâche 1 : créer automatiquement un état
    - Tâche 2 : masquer les tables (indicateurs) par défaut
    - Tâche 3 : configurer l’arrière-plan d’un nouvel état
    - Tâche 4 : ajouter un en-tête à l’état
    - Tâche 5 : ajouter des KPI à l’état
    - Tâche 6 : ajouter un graphique en courbes à l’état
    - Tâche 7 : configurer la colonne Year de la table Date
    - Tâche 8 : configurer la colonne Short_Month_Name de la table Date
    - Tâche 9 : mettre en forme le graphique en courbes
    - Tâche 10 : ajouter de nouvelles données pour simuler le mode Direct Lake
- Nettoyer l’environnement de labo
- Références

# Introduction
Nous avons ingéré des données de différentes sources de données dans Lakehouse, découvert Lakehouse, créé un modèle de données et défini une planification d’actualisation pour les sources de données. Nous allons maintenant créer un état.

À la fin de ce labo, vous saurez : 

- comment créer automatiquement un état ;
- comment créer un état à partir d’un canevas vide ;
- comment bénéficier du mode Direct Lake entraînant une actualisation automatique des données.

# Power BI

# Tâche 1 : créer automatiquement un état

Commençons par utiliser l’option de création automatique d’un état. Plus tard dans le labo, nous allons recréer l’état dont nous disposons dans Power BI.

1. Revenons à l’**espace de travail Fabric** que vous avez créé dans le labo précédent.
2. Vous allez probablement vous retrouver sur la page d’accueil de Data Factory. En bas du volet gauche, cliquez sur l’icône **Dataؘ Factory**.
3. La boîte de dialogue Expérience Fabric s’ouvre alors. Cliquez sur **Power BI**. Vous êtes alors redirigé vers la **page d’Accueil Power BI**.
 
    ![](Media/lab-07-2.png "Lab Environment")

4. Cliquez sur **Nouveau rapport** dans le menu supérieur.

    ![](Media/lab-07-3.png "Lab Environment")
 
5. Vous êtes alors redirigé vers l’écran **Créer votre premier rapport**. Des options permettent de saisir des données manuellement et créer un état ou choisir un modèle sémantique publié. Nous avons créé un modèle sémantique dans les labos précédents. Utilisons-le. Sélectionnez l’option **Choisir un modèle sémantique publié**.

    ![](Media/lab-07-4.png "Lab Environment")
 
6. Choisissez un jeu de données à utiliser sur la page de votre état qui s’ouvre. Notez que nous disposons de quatre options. Sélectionnez **lh_FAIAD** :
    - **lh_FAIAD**: il s’agit de la lakehouse comportant le jeu de données que nous avons créé et que nous souhaitons utiliser pour l’état.
    - **Units by Supplier**: il s’agit du jeu de données que nous avons créé à l’aide de T-SQL.
    - **DataflowsStagingWarehouse**: il s’agit de l’entrepôt intermédiaire créé par défaut puisque nous ne l’avons pas utilisé, car nous n’avons pas mis en lots de données.
    - **DataflowsStagingLakehouse**: il s’agit de la lakehouse intermédiaire créée par défaut puisque nous ne l’avons pas utilisée, car nous n’avons pas mis en lots de données.

7. Cliquez sur la **flèche en regard du bouton Créer automatiquement un état**. Notez que deux options sont disponibles : Créer automatiquement un état et Créer un rapport vide. Essayons la création automatique, donc sélectionnons **Créer automatiquement un état**.

    ![](Media/lab-07-5.png "Lab Environment")

8. Power BI commence alors à créer automatiquement l’état. Notez qu’une option permet de présélectionner des données, le cas échéant. Une fois l’état prêt, une boîte de dialogue s’affiche en haut de l’écran à droite. Cliquez sur **Afficher le rapport maintenant**.

    ![](Media/lab-07-6.png "Lab Environment")
 
    >**Point de contrôle** : vous disposez d’un état qui ressemble à la capture d’écran ci-dessous. Quelques KPI et quelques visuels de tendance sont disponibles. Il s’agit d’un bon point de départ si vous analysez un nouveau modèle.

    >**Remarque** :  dans le menu supérieur, notez que vous pouvez modifier l’état ou afficher certaines données sous forme de tables. N’hésitez pas à explorer ces options.

9. Une fois que vous êtes prêt, **réduisez** toutes les tables de la section **Données** à droite. Notez que nous disposons de cinq nouvelles tables qui ne font pas partie du modèle que nous avons créé. Il s’agit de tables par défaut ajoutées pour faciliter l’analyse des performances. Nous allons les supprimer prochainement de la vue d’état.

10. Enregistrons cet état. Dans le menu supérieur, cliquez sur **Enregistrer**.

11. La boîte de dialogue Enregistrer votre rapport s’ouvre alors. Nommez l’état **rpt_Sales_Auto_Report**. 

    >**Remarque** : nous ajoutons le préfixe rpt, à savoir l’abréviation du terme « report » (état) en anglais, au nom de l’état.

12. Assurez-vous que l’état est enregistré dans **\<your workspace name\>**.

13. Cliquez sur **Enregistrer**.
 
    ![](Media/lab-07-7.png "Lab Environment")

# Tâche 2 : masquer les tables (indicateurs) par défaut

Créons un état comme celui dont nous disposons dans Power BI Desktop. Pour ce faire, commençons avec un canevas vide. Avant de commencer à créer un état, supprimons les tables par défaut (capture d’écran ci-dessus) de la vue d’état. Cette opération est effectuée dans la section de modélisation de la lakehouse.

1. En bas du volet gauche, cliquez sur l’icône **Power BI**. La boîte de dialogue Fabric s’ouvre alors.

2. Cliquez sur **Data Engineering**. Vous êtes alors redirigé vers la page d’accueil Data Engineering.
  
    ![](Media/lab-07-8.png "Lab Environment")

3. Faites défiler vers le bas jusqu’à la section **Accès rapide**.

4. Cliquez sur **lh_FAIAD -> Point de terminaison analytique SQL**. Nous nous trouvons alors dans la vue Données de la lakehouse.

5. En **bas du volet gauche**, cliquez sur **Modèle** pour accéder à la vue Modèle.

Notez que le canevas de conception comporte les tables par défaut. (Vous devrez peut-être faire défiler vers la droite ou vers le bas pour les voir.)
  
![](Media/lab-07-9.png "Lab Environment")

6. Cliquez avec le bouton droit sur la table **long_running_queries** et sélectionnez **Masquer dans la vue Rapport**.
  
    ![](Media/lab-07-10.png "Lab Environment")

7. De même, sélectionnez l’option **Masquer dans la vue Rapport** pour les tables suivantes :
    - fabric_query_starting
    - fabric_query_completed
    - exec_requests_history
    - frequently_run_queries

# Tâche 3 : configurer l’arrière-plan d’un nouvel état

1. Nous pouvons commencer à créer un état à partir de la vue Modèle. Dans le menu supérieur, cliquez sur **Accueil -> Nouveau rapport**. Vous êtes alors redirigé vers le canevas d’état Power BI dans une nouvelle fenêtre/un nouvel onglet de votre navigateur.
 
    ![](Media/lab-07-11.png "Lab Environment")

2. Si vous ne l’avez pas encore ouvert, ouvrez le fichier **FAIAD.pbix** situé dans le dossier **Report** sur le **Bureau** de votre environnement de labo.

Cet état va nous servir de référence. Nous allons commencer par ajouter l’arrière-plan du canevas. Nous allons créer l’en-tête de l’état, ajouter quelques KPI et créer le graphique en courbes Sales over time. Pour gagner du temps et étant entendu que vous avez de l’expérience dans la création de visuels dans Power BI Desktop, nous n’allons pas créer tous les visuels. 
  
![](Media/lab-07-12.png "Lab Environment")

3. Revenez au **canevas Power BI** dans votre navigateur.

4. Cliquez sur l’**icône Mettre en forme la page** dans le volet Visualisation.

5. Développez la section **Arrière-plan du canevas**.

6. Cliquez sur **Parcourir** depuis l’option **Image**. La boîte de dialogue Explorateur de fichiers s’ouvre alors.

7. Accédez au dossier **Report** sur le **Bureau** de votre environnement de labo. 

8. Sélectionnez **Summary Background.png**.

9. Définissez la liste déroulante **Ajustement de l’image** sur **Ajuster**.

10. Réglez le curseur Transparence sur __0%__.
  
    ![](Media/lab-07-13.png "Lab Environment")

# Tâche 4 : ajouter un en-tête à l’état

1. Ajoutons l’en-tête dans la marge supérieure. Dans le **menu**, cliquez sur **Zone de texte**.

2. Saisissez **Fabrikam Company** comme première ligne de la zone de texte.

3. Saisissez **Sales Report** comme deuxième ligne de la zone de texte.

4. Mettez en surbrillance **Fabrikam Company** et définissez les champs **Police** sur **Segoe UI** et **Taille de la police** sur **18, gras**.

5. Mettez en surbrillance **État sur les ventes** et définissez les champs **Police** sur **Segoe UI** et **Taille de la police** sur **14**.
6. Une fois la **zone de texte** sélectionnée, développez **Effets** dans le volet Format à droite.

7. Réglez le curseur **Arrière-plan** sur **Désactivé**.

8. Redimensionnez la **zone de texte pour l’adapter à la marge supérieure**.
 
    ![](Media/lab-07-14.png "Lab Environment")
 
# Tâche 5 : ajouter des KPI à l’état

1. Ajoutons le KPI Ventes. Cliquez sur **l’espace blanc** dans le canevas pour détourner le focus de la zone de texte.

2. Dans la **section Visualisations**, sélectionnez le visuel **Carte multiligne**.

3. Dans la section **Données**, développez la **table Sales**.

4. Sélectionnez la mesure **Sales**.
  
    ![](Media/lab-07-15.png "Lab Environment")

5. Une fois le visuel **Carte multiligne** sélectionné, cliquez sur l’icône **Mettre en forme le visuel dans** la section Visualisations.

6. Développez la section **Étiquettes de catégorie**.

7. Redéfinissez le champ **Taille de la police** sur **14**.

8. Cliquez sur la liste déroulante **Couleur**. La boîte de dialogue Palette de couleurs s’ouvre alors.

9. Définissez la valeur Hex sur **#004753**.
  
    ![](Media/lab-07-16.png "Lab Environment")

10. Développez la section **Cartes**.

11. Réglez le curseur **Barre d’accentuation** sur **Désactivé**.
  
    ![](Media/lab-07-17.png "Lab Environment")

12. Cliquez sur **Général** dans le volet Visualisations.

13. Développez la section **Effets**.

14. Réglez le curseur **Arrière-plan** sur **Désactivé**.

15. Redimensionnez le **visuel** et déplacez-le vers la **case gauche, comme illustré dans la capture d’écran**.
  
    ![](Media/lab-07-18.png "Lab Environment")

16. Ajoutons un autre KPI. Sélectionnez la **carte multiligne Sales** que vous venez de créer. **Copiez** le visuel à l’aide du raccourci clavier **Ctrl + C**.

17. **Collez** le visuel à l’aide du raccourci clavier **Ctrl + V**. Notez que le visuel est collé sur le canevas.

18. Une fois le **nouveau visuel** mis en surbrillance, supprimez la mesure **Sales** dans la section **Volet Visualisation -> Générer un élément visuel -> Champs**.

19. Dans la section **Données**, développez la table **Sales** et sélectionnez la mesure **Units**.

20. Redimensionnez le **visuel** et **placez-le dans la case située sous le visuel Sales**.
  
    ![](Media/lab-07-19.png "Lab Environment")

# Tâche 6 : ajouter un graphique en courbes à l’état

Créons un graphique en courbes pour visualiser les ventes dans le temps par revendeur.

1. Cliquez sur l’**espace blanc** dans le canevas pour détourner le focus du visuel Carte multiligne.

2. Dans la **section Visualisations**, sélectionnez **Graphique en courbes**.

3. Dans la section **Données**, développez la table **Date**.

4. Cliquez sur le champ **Year**. Notez que le champ Year est une somme par défaut et ajouté à l’axe Y. Résolvons ce problème.
  
    ![](Media/lab-07-20.png "Lab Environment")

# Tâche 7 : configurer la colonne Year de la table Date

1. Accédez à l’onglet du navigateur avec **la vue Modèle de la lakehouse**.

2. Dans le volet gauche Explorateur, développez **lhFAIAD -> Schemas -> dbo -> Tables -> Date**.

3. Cliquez sur la colonne **Year**.

4. Dans le volet **Propriétés** à droite, développez la section **Options avancées**.

5. Dans la liste déroulante **Totaliser par**, sélectionnez **Aucun**.
  
    ![](Media/lab-07-21.png "Lab Environment")

6. Revenez à l’onglet du navigateur avec le **canevas Power BI**.

7. Dans le menu supérieur, cliquez sur **Actualiser**. Notez maintenant que Year n’est pas un champ de somme. 

8. Une fois le visuel **Graphique en courbes** sélectionné, **supprimez Somme de l’année** de l’axe Y.

9. Sélectionnez le champ **Year** pour l’ajouter à l’**axe X**.

10. Développez la table **Sales** et sélectionnez la mesure **Sales**.
  
    ![](Media/lab-07-22.png "Lab Environment")

# Tâche 8 : configurer la colonne Short_Month_Name de la table Date

1. Ajoutons le mois à ce graphique. Dans la table Date, faites glisser le **champ Short_Month_Name** sous **Year** sur l’**axe X**. Notez que le visuel est trié selon Sales. Trions-le selon Short_Month_Name.

2. Cliquez sur les **points de suspension (…)** dans le coin supérieur droit du visuel.

3. Sélectionnez **Trier axe -> Year Short_Month_Name**.

4. Cliquez sur les **points de suspension (…)** dans le coin supérieur droit du visuel.

5. Sélectionnez **Trier axe -> Tri croissant**.
  
    ![](Media/lab-07-23.png "Lab Environment")

  >**Remarque** : les mois sont triés par ordre alphabétique. Résolvons ce problème.
  
   ![](Media/lab-07-24.png "Lab Environment")

6. Accédez à l’onglet du navigateur avec **la vue Modèle de la lakehouse**.

7. Dans le volet gauche Explorateur, développez **lhFAIAD -> Schémas -> dbo -> Tables -> Date**.

8. Sélectionnez la colonne **Short_Month_Name**.

9. Dans le volet **Propriétés** à droite, développez la section **Options avancées**.

10. Dans la liste déroulante **Trier par colonne**, sélectionnez **Month**.
  
    ![](Media/lab-07-25.png "Lab Environment")

11. Revenez à l’onglet du navigateur avec le **canevas Power BI**.

12. Dans le menu supérieur, cliquez sur **Actualiser**. Notez maintenant que les mois sont triés correctement.
   
    ![](Media/lab-07-26.png "Lab Environment")

# Tâche 9 : mettre en forme le graphique en courbes

Notez à quel point il est facile de mettre à jour le modèle sémantique lors de la création des états. Cela donne des interactions fluides comme Power BI Desktop.

1. Une fois le visuel **Graphique en courbes** sélectionné, développez la table **Reseller** dans la section **Données**.
2. Faites glisser le champ **Reseller -> Reseller Company** vers la section **Légende**.
  
    ![](Media/lab-07-27.png "Lab Environment")

3. Une fois le visuel **Graphique en courbes** sélectionné, cliquez sur l’icône **Mettre en forme le visuel -> Général** dans la section **Visualisations**.

4. Développer la section **Titre**.

5. Définissez le texte **Titre** sur **Sales over time**.

6. Développez la section **Effets**.

7. Réglez le curseur **Arrière-plan** sur **Désactivé**.
  
    ![](Media/lab-07-28.png "Lab Environment")

8. Dans la section **Visualisations**, cliquez sur l’icône **Mettre en forme le visuel -> Objet visuel**.

9. Développez la section **Axe X**.

10. Réglez le curseur **Titre** sur **Désactivé**.

11. Développez la section **Lignes**.

12. Développez la section **Couleurs**.

13. Définissez la couleur **Wingtip Toys** sur **#004753**.

14. Définissez la couleur **Tailspin Toys** sur **#F17925**.

15. Redimensionnez le **visuel** et déplacez-le vers la **case supérieure droite, comme illustré dans la capture d’écran**.

16. Faites défiler le visuel vers la droite et **notez que nous disposons de données jusqu’en avril 2023**.
  
    ![](Media/lab-07-29.png "Lab Environment")

17. Enregistrons l’état en sélectionnant **Fichier -> Enregistrer** dans le menu.

18. La boîte de dialogue Enregistrer votre rapport s’ouvre alors. Nommez l’état **rpt_Sales_Report**. 

  >**Remarque** : nous ajoutons le préfixe rpt, à savoir l’abréviation du terme « report » (état) en anglais, au nom de l’état.

19. Assurez-vous que l’état est enregistré dans **\<your workspace name\>**.

20. Cliquez sur **Enregistrer**.
  
    ![](Media/lab-07-30.png "Lab Environment")

Comme indiqué précédemment, nous n’allons pas créer tous les visuels dans ce labo. À votre guise, n’hésitez pas à créer d’autres visuels. 

# Tâche 10 : ajouter de nouvelles données pour simuler le mode Direct Lake

En général, en mode Import, une fois les données de la source actualisées, nous devons actualiser le modèle Power BI après quoi les données de l’état sont mises à jour. Avec le mode Direct Query, une fois les données actualisées dans la source, elles sont disponibles dans l’état Power BI. Cependant, le mode Direct Query est généralement lent. Pour résoudre ce problème, Microsoft Fabric a introduit le mode Direct Lake. Direct Lake est un moyen rapide de charger les données du lac directement dans le moteur Power BI, prêtes à l’analyse. Explorons cela.

Dans un scénario réel, les données sont mises à jour à la source. Puisque nous sommes dans un environnement de formation, nous allons simuler cela en le connectant à un fichier Parquet avec les données de mai 2023.

1. Accédez à l’onglet du navigateur avec **la vue de modèle de la lakehouse**.
2. Sélectionnez **\<your workspace name\>** dans le volet gauche.
3. Sélectionnez **df_Sales_ADFS**, afin que nous puissions modifier le flux de données en ajoutant le nouveau fichier Parquet.
  
    ![](Media/lab-07-31.png "Lab Environment")

4. Si vous ne l’avez pas encore ouvert, ouvrez le fichier **FAIAD.pbix** situé dans le dossier **Report** sur le Bureau de votre environnement de labo. 

5. Dans le ruban, cliquez sur **Accueil -> Transformer les données**. Une fenêtre Power Query s’ouvre alors.

6. Dans le volet gauche, sous le dossier **DirectLake**, sélectionnez la requête **MayInvoice**.

7. **Cliquez avec le bouton droit** et sélectionnez **Copier**. 
  
    ![](Media/lab-07-32.png "Lab Environment")

8. Revenez à l’**écran Dataflow** dans le navigateur.

9. Dans le volet Dataflow, appuyez sur **Ctrl + V**. (À l’heure actuelle, le clic droit sur Coller n’est pas pris en charge.)
Supprimons maintenant la référence à ADLS Base Folder (2) et utilisons ADLS Base Folder.

10. Sélectionnez la requête **MayInvoice**.

11. Dans le volet droit, sous **Étapes appliquées**, cliquez sur **Source**.

12. Dans la barre de formule, remplacez **#"ADLS Base Folder (2)"** par **#"ADLS Base Folder"**

13. Cochez la **case** en regard de la barre de formule ou appuyez sur Entrée.
  
    ![](Media/lab-07-33.png "Lab Environment")

14. Dans le volet gauche, sous la section Requêtes, **cliquez avec le bouton droit sur la requête ADLS Base Folder (2)** et sélectionnez **Supprimer**.

15. La boîte de dialogue Supprimer la requête s’affiche alors. Cliquez sur **Supprimer** pour confirmer.
  
    ![](Media/lab-07-34.png "Lab Environment")

16. À présent, ajoutons les données de facturation de mai à la table Invoice. Sélectionnez la requête **Invoice** dans la section Requêtes.

17. Dans le ruban, cliquez sur **Accueil -> Ajouter** des requêtes.

18. La boîte de dialogue Ajouter une requête s’affiche alors. Dans la liste déroulante **Table à ajouter**, sélectionnez **MayInvoice**.

19. Cliquez sur **OK**.
  
    ![](Media/lab-07-35.png "Lab Environment")

20. Cliquez sur **Publier** Dans le coin inférieur droit pour enregistrer et publier les mises à jour. 
  
    ![](Media/lab-07-36.png "Lab Environment")

  >**Remarque** : une fois publié, le flux de données est actualisé. Cette opération peut prendre quelques minutes.

21. Revenez à l’onglet du navigateur avec le **canevas Power BI**.

22. Dans le menu supérieur, cliquez sur **Actualiser**. Notez maintenant que le graphique en courbes comporte des données pour mai 2023. Notez également que le montant des ventes en dollars a augmenté.
  
    ![](Media/lab-07-37.png "Lab Environment")

Au fur et à mesure que chaque flux de données que nous avons créé dans les labos précédents est actualisé dans les délais, les données sont ingérées dans la lakehouse. Le modèle de données de la lakehouse est mis à jour et les états sont actualisés. Nous n’avons pas besoin d’actualiser le modèle de données et de signaler l’actualisation de chacun des flux de données. Voilà l’avantage de Direct Lake.

Revenons sur les défis répertoriés dans l’énoncé du problème :

- **Vous devez actualiser votre jeu de données au moins trois fois par jour pour tenir compte des différentes heures de mise à jour des différentes sources de données.**

Nous avons résolu ce problème à l’aide de Direct Lake. Chaque flux de données individuel est actualisé selon son calendrier. Le jeu de données et l’état n’ont pas besoin d’être actualisés.

- **Vos actualisations prennent beaucoup de temps, car vous devez effectuer chaque fois une actualisation complète pour capturer toutes les mises à jour survenues sur les systèmes sources**.

Encore une fois, nous avons résolu ce problème à l’aide de Direct Lake. Chaque flux de données individuel est actualisé selon son calendrier. Le jeu de données et l’état n’ont pas besoin d’être actualisés, donc nous n’avons pas à nous soucier d’une actualisation complète.

- **Toute erreur dans l’une des sources de données à partir desquelles vous extrayez des données entraîne une interruption de l’actualisation de votre jeu de données. Il arrive souvent que le fichier collaborateur ne soit pas chargé à temps, ce qui aboutit à une interruption de l’actualisation de votre jeu de données**. 

Le pipeline de données permet de résoudre ce problème, en permettant de réessayer d’effectuer une actualisation en cas d’échec et à différents intervalles.

- **Apporter des modifications à votre modèle de données est un processus chronophage, car Power Query prend beaucoup de temps pour actualiser vos aperçus, compte tenu du gros volume de données et des transformations complexes**. 

Nous avons remarqué que les flux de données sont efficaces et faciles à modifier. En général, le chargement de l’aperçu dans les flux de données ne prend pas beaucoup de temps.

- **Vous avez besoin d’un PC Windows pour utiliser Power BI Desktop, même si le standard de l’entreprise est Mac**.

Microsoft Fabric est une offre SaaS. Il nous suffit d’un navigateur pour accéder au service. Nous n’avons pas besoin d’installer de logiciel sur nos bureaux.

# Nettoyer l’environnement de labo

Une fois que vous êtes prêt à nettoyer l’environnement de labo, procédez comme suit :
1. Revenez à l’onglet du navigateur avec le **canevas Power BI. Fermez cet onglet**.

2. Accédez à l’onglet avec la **vue de modèle de la lakehouse**.

3. Sélectionnez **\<your workspace name\>** dans le volet gauche pour accéder à la page d’accueil.
  
    ![](Media/lab-07-38.png "Lab Environment")

4. Dans le menu supérieur, cliquez sur les **points de suspension (…)** en regard de Gérer l’accès et sélectionnez **Paramètres d'espace de travail**.
  
    ![](Media/lab-07-39.png "Lab Environment")

5. La boîte de dialogue Paramètres de l’espace de travail s’ouvre alors. Cliquez sur **Autre** dans le menu gauche.

6. Cliquez sur **Supprimer cet espace de travail**.

7. La boîte de dialogue Supprimer l’espace de travail s’ouvre alors. Cliquez sur **Supprimer**.
L’espace de travail et tous les éléments qu’il comporte sont alors supprimés.
  
    ![](Media/lab-07-40.png "Lab Environment")

# Références

Fabric Analyst in a Day (FAIAD) vous présente certaines des fonctions clés de Microsoft Fabric. Dans le menu du service, la section Aide (?) comporte des liens vers d’excellentes ressources.
  
![](Media/lab-07-41.png "Lab Environment")

Voici quelques autres ressources qui vous aideront lors de vos prochaines étapes avec Microsoft Fabric :

- Consultez le billet de blog pour lire l’intégralité de l’[annonce de la GA de Microsoft Fabric.](https://aka.ms/Fabric-Hero-Blog-Ignite23)

- Explorez Fabric grâce à la [visite guidée.](https://aka.ms/Fabric-GuidedTour)

- Inscrivez-vous pour bénéficier d’un [essai gratuit de Microsoft Fabric.](https://aka.ms/try-fabric)

- Rendez-vous sur le [site web Microsoft Fabric.](https://aka.ms/microsoft-fabric)

- Acquérez de nouvelles compétences en explorant les [modules d’apprentissage Fabric.](https://aka.ms/learn-fabric)

- Explorez la [documentation technique Fabric.](https://aka.ms/fabric-docs)

- Lisez le [livre électronique gratuit sur la prise en main de Fabric.](https://aka.ms/fabric-get-started-ebook)

- Rejoignez la [communauté Fabric](https://aka.ms/fabric-community) pour publier vos questions, partager vos commentaires et apprendre des autres.

Lisez les blogs d’annonces plus détaillés sur l’expérience Fabric :

- [Blog Expérience Data Factory dans Fabric](https://aka.ms/Fabric-Data-Factory-Blog) 

- [Blog Expérience Synapse Data Engineering dans Fabric](https://aka.ms/Fabric-DE-Blog) 

- [Blog Expérience Synapse Data Science dans Fabric](https://aka.ms/Fabric-DS-Blog) 

- [Blog Expérience Synapse Data Warehousing dans Fabric](https://aka.ms/Fabric-DW-Blog) 

- [Blog Expérience Synapse Real-Time Analytics dans Fabric](https://aka.ms/Fabric-RTA-Blog)

- [Blog Annonce Power BI](https://aka.ms/Fabric-PBI-Blog)

- [Blog Expérience Data Activator dans Fabric](https://aka.ms/Fabric-DA-Blog) 

- [Blog Administration et gouvernance dans Fabric](https://aka.ms/Fabric-Admin-Gov-Blog)

- [Blog OneLake dans Fabric](https://aka.ms/Fabric-OneLake-Blog)

- [Blog Intégration de Dataverse et Microsoft Fabric](https://aka.ms/Dataverse-Fabric-Blog)

© 2023 Microsoft Corporation. Tous droits réservés.

En effectuant cette démonstration/ce labo, vous acceptez les conditions suivantes :

La technologie/fonctionnalité décrite dans cette démonstration/ces travaux pratiques est fournie par Microsoft Corporation en vue d’obtenir vos commentaires et de vous fournir une expérience d’apprentissage. Vous pouvez utiliser cette démonstration/ces ateliers uniquement pour évaluer ces technologies et fonctionnalités, et pour fournir des commentaires à Microsoft. Vous ne pouvez pas l’utiliser à d’autres fins. Vous ne pouvez pas modifier, copier, distribuer, transmettre, afficher, effectuer, reproduire, publier, accorder une licence, créer des œuvres dérivées, transférer ou vendre tout ou une partie de cette démonstration/ces ateliers.

LA COPIE OU LA REPRODUCTION DE CETTE DÉMONSTRATION/CES TRAVAUX PRATIQUES (OU DE TOUTE PARTIE DE CEUX-CI) SUR TOUT AUTRE SERVEUR OU AUTRE EMPLACEMENT EN VUE D’UNE AUTRE REPRODUCTION OU REDISTRIBUTION EST EXPRESSÉMENT INTERDITE.

CETTE DÉMONSTRATION/CES TRAVAUX PRATIQUES FOURNISSENT CERTAINES FONCTIONNALITÉS DE PRODUIT/TECHNOLOGIES LOGICIELLES, NOTAMMENT D’ÉVENTUELS NOUVEAUX CONCEPTS ET FONCTIONNALITÉS, DANS UN ENVIRONNEMENT SIMULÉ SANS INSTALLATION OU CONFIGURATION COMPLEXE AUX FINS DÉCRITES CI-DESSUS. LES TECHNOLOGIES/CONCEPTS REPRÉSENTÉS DANS CETTE DÉMONSTRATION/CES TRAVAUX PRATIQUES PEUVENT NE PAS REPRÉSENTER LES FONCTIONNALITÉS COMPLÈTES ET PEUVENT NE PAS FONCTIONNER DE LA MÊME MANIÈRE QUE DANS UNE VERSION FINALE. IL EST ÉGALEMENT POSSIBLE QUE NOUS NE PUBLIIONS PAS DE VERSION FINALE DE CES FONCTIONNALITÉS OU CONCEPTS. VOTRE EXPÉRIENCE D’UTILISATION DE CES FONCTIONNALITÉS DANS UN ENVIRONNEMENT PHYSIQUE PEUT ÉGALEMENT ÊTRE DIFFÉRENTE.

**COMMENTAIRES**. Si vous envoyez des commentaires sur les fonctionnalités, technologies et/ou concepts décrits dans ces ateliers/cette démonstration à Microsoft, vous accordez à Microsoft, sans frais, le droit d’utiliser, de partager et de commercialiser vos commentaires de quelque manière et à quelque fin que ce soit. Vous accordez également à des tiers, sans frais, les droits de brevet nécessaires pour leurs produits, technologies et services en vue de l’utilisation ou de l’interface avec des parties spécifiques d’un logiciel ou d’un service Microsoft incluant les commentaires. Vous n’enverrez pas de commentaires soumis à une licence exigeant que Microsoft accorde une licence pour son logiciel ou sa documentation à des tiers du fait que nous y incluons vos commentaires. Ces droits survivent à ce contrat.

MICROSOFT CORPORATION DÉCLINE TOUTES LES GARANTIES ET CONDITIONS EN CE QUI CONCERNE CETTE DÉMONSTRATION/CES TRAVAUX PRATIQUES, Y COMPRIS TOUTES LES GARANTIES ET CONDITIONS DE QUALITÉ MARCHANDE, QU’ELLES SOIENT EXPLICITES, IMPLICITES OU LÉGALES, D’ADÉQUATION À UN USAGE PARTICULIER, DE TITRE ET D’ABSENCE DE CONTREFAÇON. MICROSOFT N’OFFRE AUCUNE GARANTIE OU REPRÉSENTATION EN CE QUI CONCERNE LA PRÉCISION DES RÉSULTATS, LA CONSÉQUENCE QUI DÉCOULE DE L’UTILISATION DE CETTE DÉMONSTRATION/CES ATELIERS, OU L’ADÉQUATION DES INFORMATIONS CONTENUES DANS CETTE DÉMONSTRATION/CES ATELIERS À QUELQUE FIN QUE CE SOIT.

# CLAUSE D’EXCLUSION DE RESPONSABILITÉ

Cette démonstration/Ce labo comporte seulement une partie des nouvelles fonctionnalités et améliorations disponibles dans Microsoft Power BI. Certaines fonctionnalités sont susceptibles de changer dans les versions ultérieures du produit. Dans ce labo/cette démonstration, vous allez découvrir comment utiliser certaines nouvelles fonctionnalités, mais pas toutes.
