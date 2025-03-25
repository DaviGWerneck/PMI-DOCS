## Query usuarios de teste > 

```

SELECT TOP 100 
    ENTRADA.nuentrada, 
    ENTRADA.cdusuario,
	ENTRADA.dtentrada
FROM sstentps ENTRADA 
LEFT JOIN sscentservicosocial SOCIAL 
    ON ENTRADA.nuentrada = SOCIAL.nuentrada
WHERE SOCIAL.nuentrada IS NULL
ORDER BY ENTRADA.dtentrada DESC

```

