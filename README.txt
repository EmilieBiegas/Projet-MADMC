Projet réalisé dans le cadre de l'UE Modèles et algorithmes pour la décision multicritère et collective (MADMC).
Sujet du TME : Recherche locale de Pareto (PLS)
Sujet du projet : Élicitation incrémentale et recherche locale pour le problème du sac à dos multi-objectifs

Ce repository est constitué de plusieurs fichiers : InstancesMOKP répertorie toutes les instances permettant les tests, 2KP200-TA-0.dat est l'instance principalement utilisée pour les tests, MADMC_Projet.ipynb est le fichier code final pour ce projet, MADMC_Rapport.pdf est le rapport final du projet, MADMC_Sujet.pdf est l'énoncé du projet, TME_MADMC.ipynb est le fichier code d'un TME utile à la réalisation de ce projet, TME_MADMC_Sujet.pdf est l'énoncé de ce TME, articleProjet1.pdf et articleProjet2.pdf sont deux articles sur lesquels on s'est basé pour ce projet.

Le fichier code MADMC_Projet.ipynb est sous la forme d'un Notebook qui suit le plan du sujet, il suffit de tout exécuter pour voir s'afficher les réponses aux questions 2.a. (fonction questionA), 2.b. (fonction questionB) ainsi que les comparaisons de méthodes (fonction ComparaisonsMéthodes), comme indiquées dans le rapport.

Sinon, voici les fonctions les plus utiles :
-Pour obtenir une instance tirée du fichier nomFichier à nbObj objets, nbCrit critères : LectureInstanceParticuliere(nomFichier, nbObj, nbCrit) retourne n,W,w,v

-Pour générer des poids pour la fonction d'agrégation fctAgregation ("OWA", "SP", ou "Ch") sur nbCriteres critères : generePoids(nbCriteres, fctAgregation) retourne les poids générés

-Pour effectuer la 1ère procédure de résolution : 
--On détermine d'abord une approximation des points non-dominés (au sens de Pareto) : 
--- Avec des listes : XeList = PLS(W, w, v) retourne une approximation de l’ensemble des solutions efficaces, ou avec des ND-Tree : XeND, Ye = PLS_ND_Tree(W, w, v) retourne une approximation de l’ensemble des solutions efficaces ainsi que les points images de ces solutions dans l'espace des critères
--Puis, on détermine la solution préférée du décideur parmi ceux-ci (Xe) à l’aide d’une procédure d’élicitation incrémentale : ElicitationIncrementale(Xe, v, fctAgregation, poids=poidsCourrant) retourne la solution préférée et le nombre de questions posées pour y parvenir 
        
-Pour effectuer la 2eme procédure de résolution avec des listes : PLS_Combine(W, w, v, fctAgregation, poids=poidsCourrant) retourne la solution (optimale localement) à conseiller au décideur ainsi que le nombre de questions posées pour y parvenir 
        
-Pour effectuer la 2eme procédure de résolution avec des ND-tree : PLS_Combine_ND_Tree(W, w, v, fctAgregation, poids=poidsCourrant) retourne la solution (optimale localement) à conseiller au décideur ainsi que le nombre de questions posées pour y parvenir 
        
