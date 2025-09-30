%% Diagramme de Flux Mermaid - Génération de Posts Facebook via IA
%% Expert: Visualisation de Processus
%% Version finale - Compatibilité maximale

graph TD
    %% --- 1. Définition des styles ---
    classDef subprocess fill:#1abc9c,color:#fff,stroke:#16a085,stroke-width:2px
    classDef data fill:#f39c12,color:#333,stroke:#e67e22,stroke-width:2px
    classDef startend fill:#34495e,color:#fff,stroke:#2c3e50,stroke-width:2px
    classDef finaloutput fill:#2ecc71,color:#fff,stroke:#27ae60,stroke-width:2px,font-weight:bold

    %% --- 2. Définition du flux logique complet ---
    Start([Début]) --> A[Remplissage du formulaire]
    
    subgraph Phase 1 [Soumission Utilisateur]
        A --> B{Données: Requête et Email}
    end

    B --> C[Formatage du prompt pour Gemini]

    subgraph Phase 2 [Génération de Contenu par IA]
        C --> D[Appel API Gemini]
        D --> E{Données: JSON structuré}
    end

    E --> F[Réception du JSON]

    subgraph Phase 3 [Traitement et Formatage]
        F --> F1[Extraire le titre]
        F1 --> F2[Boucler sur les paragraphes]
        F2 --> F3[Concaténer les hashtags]
        F3 --> G[Assemblage du code HTML]
    end

    G --> H{Sortie: Contenu HTML final}
    
    subgraph Phase 4 [Finalisation]
        H --> End([Post prêt à l-emploi])
    end

    %% --- 3. Application des classes de style ---
    class Start,End startend
    class A,C,D,F,F1,F2,F3,G subprocess
    class B,E data
    class H finaloutput

    %% --- 4. Légende Explicative ---
    subgraph Legend [Légende]
        direction LR
        L1( ) --- L1_Label[Processus / Étape]
        L2( ) --- L2_Label{Données / Entrée-Sortie}
        L3( ) --- L3_Label([Début / Fin])
        L4( ) --- L4_Label{Post HTML final Succès}

        style L1 fill:#1abc9c,color:#fff,stroke:#16a085,stroke-width:2px
        style L2 fill:#f39c12,color:#333,stroke:#e67e22,stroke-width:2px
        style L3 fill:#34495e,color:#fff,stroke:#2c3e50,stroke-width:2px
        style L4 fill:#2ecc71,color:#fff,stroke:#27ae60,stroke-width:2px
    end