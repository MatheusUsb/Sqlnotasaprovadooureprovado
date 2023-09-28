# Sqlnotasaprovadooureprovado

CREATE TABLE notas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nota DECIMAL(5, 2),
    aprovado VARCHAR(10)
);

-- Trigger
CREATE TRIGGER trigger_aprovacao
AFTER INSERT ON notas
BEGIN
    UPDATE notas
    SET aprovado = CASE 
        WHEN NEW.nota >= 6 THEN 'Aprovado'
        ELSE 'Reprovado'
        END
    WHERE id = NEW.id;
END;

Inserindo valores ficticios:
INSERT INTO notas (nota) VALUES (7.5);
INSERT INTO notas (nota) VALUES (5.0);
INSERT INTO notas (nota) VALUES (8.7);
INSERT INTO notas (nota) VALUES (3.2);
INSERT INTO notas (nota) VALUES (9.1);

Opção de utilizar o case:

UPDATE notas
SET aprovado = CASE
    WHEN nota >= 6 THEN 'Aprovado'
    ELSE 'Reprovado'
END;
