flowchart TD
    %% === WORKFLOW PRINCIPAL ===
    Start[("Début du Processus")] --> Form{{"Formulaire de Saisie"}}
    Form --> Validation("Validation des Données")
    Validation --> Decision{{"Données Valides ?"}}
    
    %% === BRANCHE ERREUR ===
    Decision -->|Non| ErrorMsg["Affichage des Erreurs"]
    ErrorMsg --> Form
    
    %% === WORKFLOW PRINCIPAL - SUITE ===
    Decision -->|Oui| ProcessData["Traitement des Données"]
    ProcessData --> CRMUpdate["Mise à Jour du CRM"]
    CRMUpdate --> NotifWorkflow["Déclenchement des Notifications"]
    
    %% === SOUS-WORKFLOW CRM ===
    CRMUpdate --> PrepareData["Préparation des Données CRM"]
    PrepareData --> GoogleSheet["Ajout dans Google Sheet"]
    GoogleSheet --> AddTimestamp["Ajout Date et Heure"]
    AddTimestamp --> CRMSuccess["Confirmation CRM"]
    
    %% === SOUS-WORKFLOW NOTIFICATIONS ===
    NotifWorkflow --> AdminAlert["Génération Alerte Admin"]
    NotifWorkflow --> UserConfirm["Génération Confirmation Utilisateur"]
    
    %% === DÉTAIL ALERTE ADMIN ===
    AdminAlert --> PrepareAdminMail["Préparation Email Admin"]
    PrepareAdminMail --> SendAdminMail["Envoi Email Admin"]
    SendAdminMail --> AdminNotified["Admin Notifié"]
    
    %% === DÉTAIL CONFIRMATION UTILISATEUR ===
    UserConfirm --> CheckUserPref{{"Type de Confirmation ?"}}
    CheckUserPref -->|Email| PrepareUserMail["Préparation Email Utilisateur"]
    CheckUserPref -->|SMS| PrepareUserSMS["Préparation SMS Utilisateur"]
    
    PrepareUserMail --> SendUserMail["Envoi Email Utilisateur"]
    PrepareUserSMS --> SendUserSMS["Envoi SMS Utilisateur"]
    
    SendUserMail --> UserNotified["Utilisateur Confirmé"]
    SendUserSMS --> UserNotified
    
    %% === FINALISATION ===
    CRMSuccess --> CheckNotifications{{"Notifications Envoyées ?"}}
    AdminNotified --> CheckNotifications
    UserNotified --> CheckNotifications
    
    CheckNotifications -->|Oui| ProcessComplete[("Processus Terminé")]
    CheckNotifications -->|Non| NotifError["Gestion des Erreurs de Notification"]
    NotifError --> ProcessComplete
    
    %% === DONNÉES D'ENTRÉE ===
    FormFields{{"Nom - Prénom - Age - Email - Numéro"}} --> Form
    
    %% === CONFIGURATION N8N ===
    N8NTrigger["Trigger N8N"] --> Start
    
    %% === STYLES ===
    classDef processMain fill:#2E86AB,stroke:#1C5F7A,stroke-width:2px,color:#FFFFFF
    classDef processSecondary fill:#4CAF50,stroke:#388E3C,stroke-width:2px,color:#FFFFFF
    classDef processDetail fill:#FFC107,stroke:#FF8F00,stroke-width:2px,color:#000000
    classDef decision fill:#FF9800,stroke:#E65100,stroke-width:2px,color:#FFFFFF
    classDef data fill:#9C27B0,stroke:#6A1B9A,stroke-width:2px,color:#FFFFFF
    classDef error fill:#F44336,stroke:#C62828,stroke-width:2px,color:#FFFFFF
    classDef success fill:#4CAF50,stroke:#2E7D32,stroke-width:2px,color:#FFFFFF
    classDef startEnd fill:#607D8B,stroke:#37474F,stroke-width:3px,color:#FFFFFF
    
    %% === APPLICATION DES STYLES ===
    class Start,ProcessComplete startEnd
    class Form,Validation,ProcessData,CRMUpdate,NotifWorkflow processMain
    class PrepareData,GoogleSheet,AddTimestamp,AdminAlert,UserConfirm processSecondary
    class PrepareAdminMail,SendAdminMail,PrepareUserMail,PrepareUserSMS,SendUserMail,SendUserSMS,AddTimestamp processDetail
    class Decision,CheckUserPref,CheckNotifications decision
    class FormFields,N8NTrigger data
    class ErrorMsg,NotifError error
    class CRMSuccess,AdminNotified,UserNotified success