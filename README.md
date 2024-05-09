# algorithme-
Contrôle d'algorithme 
ALGORITHM sentence_analysis

    FUNCTION lenght(text STRING)
    VAR
        sentenceLength :INTEGER
        character: STRING
    BEGIN
        FOR EACH character OF text  DO
            WHILE (character<>' ') DO
                sentenceLength <- sentenceLength+1
            END_WHILE
        END_FOR
        RETURN sentenceLength
    END

    FUNCTION vowels_number(text STRING) : INTEGER
    VAR
        i, nbr : INTEGER
    BEGIN
        nbr <- 0
        FOR i FROM 0 TO lenght(text)-1  DO
            IF (text[i]='a' OR text[i]='e' OR text[i]='i' OR text[i]='o' OR text[i]='u' OR text[i]='y' OR text[i]='A' OR text[i]='E' OR text[i]='I' OR text[i]='O' OR text[i]='U' OR text[i]='Y') 
            THEN
                nbr <- nbr+1
            END_IF
        END_FOR
        RETURN nbr
    END

    FUNCTION words_number(text STRING) : INTEGER
    VAR
        wordsNumber <- 0
        character : STRING
    BEGIN
    //Tant que text n'est pas vide
    IF (text <> '') THEN
        // Lire la phrase caractère par caractère jusqu'à ce que le point soit rencontré
        WHILE (character <> '.') DO
            // Si le caractère est un espace, incrémenter le compteur de mots
            IF (character = ' ') THEN
                wordsNumber <- wordsNumber+1
            END_IF
        END_WHILE
    END_IF
        RETURN wordsNumber
    END

    PROCEDURE sentence_reader ()
    VAR
        sentence, choice : STRING;
    BEGIN
        Write('Entrer une phrase de votre choix sans oublier la majuscule en début et le point "." à la fin')
        Read(sentence)
        IF (sentence=' ') THEN
            Write("la phrase entrée est vide, veuillez en saisir une valide")
            Read(sentence)
        END_IF
    END

VAR
    sentenceLength, wordsNumber, vowelsNumber : INTEGER;
BEGIN
    sentence_reader()
    sentenceLength <- lenght(sentence)
    wordsNumber <- words_number(sentence)
    vowelsNumber <- vowels_number(sentence)
    Write('La longuer de la phrase saisie est '.sentenceLength.' Elle contien '.wordsNumber.' de mots et '.vowelsNumber.' de voyelles')
END
