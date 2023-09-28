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
