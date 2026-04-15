-- Tabella Utenti
CREATE TABLE Utenti (
    id_utente INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    data_registrazione DATE NOT NULL
);

-- Tabella Post
CREATE TABLE Post (
    id_post INT PRIMARY KEY AUTO_INCREMENT,
    id_utente INT NOT NULL,
    testo TEXT NOT NULL,
    data_ora DATETIME NOT NULL,
    FOREIGN KEY (id_utente) REFERENCES Utenti(id_utente)
        ON DELETE CASCADE
);

-- Tabella Commenti
CREATE TABLE Commenti (
    id_commento INT PRIMARY KEY AUTO_INCREMENT,
    id_post INT NOT NULL,
    id_utente INT NOT NULL,
    testo TEXT NOT NULL,
    data_ora DATETIME NOT NULL,
    FOREIGN KEY (id_post) REFERENCES Post(id_post)
        ON DELETE CASCADE,
    FOREIGN KEY (id_utente) REFERENCES Utenti(id_utente)
        ON DELETE CASCADE
);

-- Tabella Like ai Post
CREATE TABLE Like_Post (
    id_utente INT,
    id_post INT,
    data_like DATETIME DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id_utente, id_post),
    FOREIGN KEY (id_utente) REFERENCES Utenti(id_utente)
        ON DELETE CASCADE,
    FOREIGN KEY (id_post) REFERENCES Post(id_post)
        ON DELETE CASCADE
);