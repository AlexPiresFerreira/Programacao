
### A forma mais simples compara um valor de assunto com um ou mais literais:

```
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case 418:
            return "I'm a teapot"
        case _:
            return "Something's wrong with the internet"
```

- Tutorial
	- [PEP 636 – Structural Pattern Matching: Tutorial | peps.python.org](https://peps.python.org/pep-0636/)
