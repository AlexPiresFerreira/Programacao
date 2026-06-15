
#### Tipo

| Texto     | str()                        | "Texto", 'Texto', '''Texto''', """Text""" |
| --------- | ---------------------------- | ----------------------------------------- |
| Númerico  | int(), float(), complex      | 10, 10.5                                  |
| Sequência | list, tuple, range           |                                           |
| Mapa      | dict                         |                                           |
| Coleção   | set, fronzenset              |                                           |
| Booleano  | bool                         | (true) ou (false)                         |
| Binário   | bytes, bytearray, memoryview |                                           |

#### Converter os tipos 

**Ex.**

```
preco = 10.30
print(preco)
>>> 10.3

preco = int(preco)
print(preco)
>>> 10
```

#### Variável 

- [name] = [valor]
- O padrão de nomes deve ser snake case (**Ex. limite_saque_diario**)
- Escolher nomes sugestivos


#### Constante

- Imutável
- Python não tem constantes
- [NAME] = [valor]
-  Nome de constantes todo em maiúsculo(**Ex. BRAZILIAN_STATES**)

#### input

- O valor em string 
- input([Valor :])

