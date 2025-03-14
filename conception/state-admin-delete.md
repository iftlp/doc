@startuml

[*] --> App : Sélectionner "Supprimer une musique"

state "Mode Gestion Suppression" as App {

    [*] --> ConfirmationSuppression : Initialisation terminée

    ConfirmationSuppression : do/afficherConfirmation()
    ConfirmationSuppression --> SuppressionMusique : Cliquer "Oui"
    ConfirmationSuppression --> [*] : Cliquer "Non"

    SuppressionMusique : do/supprimerMusique()
    SuppressionMusique --> [*] : Suppression terminée

    SuppressionMusique --> ErreurSuppression : Suppression invalide

    ErreurSuppression : do/afficherErreur()
    ErreurSuppression --> [*] : Cliquer "OK"
}

App --> [*] : Quitter le menu suppression

@enduml
