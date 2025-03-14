@startuml
|Utilisateur|
start
:Appuie sur le bouton d'identification;

|Application|
:Enregistre un extrait audio;

|Programme d'identification|
:Analyse l'extrait;

|Base de données|
:Recherche en base de données;

|Programme d'identification|
:Retourne le résultat;

|Application|
if (Erreur du programme ?) then ([Oui])
  :Affiche l'erreur;
else ([Non])
  if (Correspondance trouvée ?) then ([Oui])
      :Ajoute la chanson à l'historique;
      :Affiche les informations;
  else ([Non])
      :Affiche une erreur;
  endif
endif

stop

|Utilisateur|
start
:Consulte son historique;

|Base de données|
:Retourne l'historique;

|Application|
:Affiche l'historique;
stop

@enduml
