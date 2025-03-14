@startuml

[*] --> App : Sélectionner "Modifier une musique"

state "Mode Gestion Modification" as App {

    [*] --> MenuModifierMusique : Initialisation terminée

    MenuModifierMusique : do/afficherFormulaireModification()
    MenuModifierMusique --> VérificationModification : Cliquer sur "Modifier"

    VérificationModification : do/verifierModification()
    VérificationModification --> ConfirmationModification : Informations valides
    VérificationModification --> ErreurModification : Informations invalides
    
    ConfirmationModification : do/afficherConfirmation()
    ConfirmationModification --> ModificationMusique : Cliquer "Oui"
    ConfirmationModification --> MenuModifierMusique : Cliquer "Non"

    ModificationMusique : do/modifierMusique()
    ModificationMusique --> [*] : Modification terminée

    ErreurModification : do/afficherErreur()
    ErreurModification --> MenuModifierMusique : Cliquer "OK"
}

App --> [*] : Quitter le menu modification

@enduml
