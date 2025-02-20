# Analisador Léxico com Autômato de Moore

Este projeto implementa um analisador léxico utilizando um autômato de Moore para reconhecer tokens em um arquivo de código fonte com extensão `.cm`. O analisador é capaz de identificar palavras-chave, operadores, números, identificadores e outros elementos léxicos, além de tratar erros de caracteres inválidos.

## Estrutura do Projeto

- `tests/`: Contém os arquivos de teste para verificar o funcionamento do analisador léxico.
- `README.md`: Este arquivo, com instruções sobre como rodar o projeto e os testes.
- `main.py`: O script principal que processa o arquivo de entrada e gera a saída léxica.

## Dependências

O projeto utiliza as seguintes bibliotecas:

```python
from sys import argv
import sys
import os
from automata.fa.Moore import Moore
```

Certifique-se de ter o Python instalado. O projeto não possui dependências externas além da biblioteca padrão do Python.

## Como Executar o Projeto

### Executando o Analisador Léxico

Para rodar o analisador léxico em um arquivo `.cm`, utilize o seguinte comando:

```bash
python analex.py arquivo.cm
```

Se desejar usar a flag `-k` (opcional), execute:

```bash
python analex.py -k arquivo.cm
```

O script processará o arquivo e imprimirá os tokens reconhecidos ou mensagens de erro, caso ocorram.

### Executando os Testes

Para rodar os testes automatizados, utilize o comando:

```bash
python -m pytest
```

Isso executará todos os testes na pasta `tests/` e verificará se o analisador léxico está funcionando corretamente.

## Exemplo de Uso

### Arquivo de Entrada (`exemplo.cm`):

```c
int main() {
    int x = 10;
    if (x > 5) {
        return x;
    }
}
```

### Saída Esperada:

```
INT
ID
LPAREN
RPAREN
LBRACES
INT
ID
ATTRIBUTION
NUMBER
SEMICOLON
IF
LPAREN
ID
GREATER
NUMBER
RPAREN
LBRACES
RETURN
ID
SEMICOLON
RBRACES
RBRACES
```

### Erros:

Se o arquivo contiver caracteres inválidos, o analisador irá gerar uma mensagem de erro indicando a linha e a posição do caractere inválido:

```
Erro[linha][coluna]: Caractere inválido: [caractere]
```

## Testes

Os testes estão localizados na pasta `tests/` e cobrem diversos cenários, incluindo:

- Reconhecimento de palavras-chave (`int`, `if`, `else`, etc.).
- Reconhecimento de operadores (`+`, `-`, `*`, `/`, etc.).
- Reconhecimento de números e identificadores.
- Tratamento de erros de caracteres inválidos.

Para rodar os testes, utilize:

```bash
python -m pytest
```

Ou para testar um arquivo específico:

```bash
python analex.py -k ./tests/prog-001.cm
```

## Licença

Este projeto está licenciado sob a Licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.

---

Esperamos que este projeto seja útil para você! Se tiver alguma dúvida ou sugestão, não hesite em entrar em contato.

