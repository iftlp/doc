@startuml

[*] --> App : Accéder à la gestion de la base de données

state "Mode Gestion" as App {

    [*] --> MenuGestion : Initialisation terminée

    MenuGestion --> AjoutMusique : Sélectionner "Ajouter une musique"
    AjoutMusique --> MenuGestion : Retour au menu principal
    note bottom of AjoutMusique
        Cet état est décomposé dans un autre diagramme
    end note

    MenuGestion --> RechercheMusique : Sélectionner "Rechercher une musique"
    MenuGestion : do/afficherMenu()
    RechercheMusique: do/chercherMusique(text)
    RechercheMusique --> RésultatRecherche : Musique trouvée
    RésultatRecherche --> MenuGestion : Retour au menu principal
    RechercheMusique --> ErreurRecherche : Musique non trouvée
    ErreurRecherche --> MenuGestion : Retour au menu principal
    ErreurRecherche : do/afficherErreur()

    RésultatRecherche --> ModificationMusique : Sélectionner "Modifier la musique"
    ModificationMusique --> MenuGestion : Retour au menu principal
    note bottom of ModificationMusique
        Cet état est décomposé dans un autre diagramme
    end note

    RésultatRecherche --> SuppressionMusique : Sélectionner "Supprimer la musique"
    SuppressionMusique --> MenuGestion : Retour au menu principal
    note bottom of SuppressionMusique
        Cet état est décomposé dans un autre diagramme
    end note
}

App --> [*] : Quitter la gestion

@enduml
