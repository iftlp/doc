@startuml

[*] --> App : Sélectionner "Ajouter une musique"

state "Mode Gestion Ajout" as App {

    [*] --> MenuAjoutMusique : Initialisation terminée

    MenuAjoutMusique : do/afficherFormulaireAjout()
    MenuAjoutMusique --> VérificationAjout : Cliquer sur "Ajouter"

    VérificationAjout : do/verifierAjout()
    VérificationAjout --> ConfirmationAjout : Informations valides
    VérificationAjout --> ErreurAjout : Informations invalides
    
    ConfirmationAjout : do/afficherConfirmation()
    ConfirmationAjout --> AjoutMusique : Cliquer "Oui"
    ConfirmationAjout --> MenuAjoutMusique : Cliquer "Non"

    AjoutMusique : do/ajouterMusique()
    AjoutMusique --> [*] : Ajout terminée

    ErreurAjout : do/afficherErreur()
    ErreurAjout --> MenuAjoutMusique : Cliquer "OK"
}

App --> [*] : Quitter le menu ajout

@enduml
