## Objetivo
O exercício consiste em comparar prompts vagos com prompts refinados e analisar como o refinamento melhora a precisão, organização e utilidade das respostas.

---
## 1. Geração de Código
### Prompt inicial (vago)
<img width="695" height="491" alt="image" src="https://github.com/user-attachments/assets/d8688e89-e450-40d1-b7c5-4453090de3fa" />

### Prompt (refinado)
<img width="570" height="657" alt="image" src="https://github.com/user-attachments/assets/f6255a7a-ec9c-4022-bfdb-56cbf9e75454" />

---
## 2. Refatoração de Código
### Prompt inicial (vago)
<img width="566" height="657" alt="image" src="https://github.com/user-attachments/assets/01a4b881-e8e7-44fd-9dba-dcc6f03d3380" />

### Prompt (refinado)
<img width="470" height="661" alt="image" src="https://github.com/user-attachments/assets/346afcdf-c6e4-4baa-a083-b07cb7a27ee0" />

---
## 3. Documentação Técnica
### Prompt inicial (vago)
Para explicar como esse código funciona, vamos decompor a lógica da **Versão Robusta**, que é a que melhor aplica conceitos de engenharia de software e segurança de dados.

O código é dividido em três partes principais que trabalham juntas para garantir que o programa não falhe.

---

### 1. A Função de Validação (`obter_numero`)
Esta função é um "filtro" de segurança. Em vez de apenas aceitar o que o usuário digita, ela garante que o programa só prossiga se os dados forem válidos.

* **`while True:`**: Cria um loop infinito que só é interrompido quando um valor válido é retornado.
* **`try...except ValueError`**: É o coração do tratamento de erros. Se o usuário digitar "abc", o Python normalmente geraria um erro e fecharia o programa. O `except` captura esse erro específico (`ValueError`) e exibe uma mensagem amigável em vez de quebrar.
* **`return float(...)`**: Converte a string digitada em número decimal e encerra a função, enviando o valor de volta para quem a chamou.

### 2. A Função Principal (`calcular_soma`)
Aqui é onde a lógica de negócio acontece. 

* Ela chama a função `obter_numero` duas vezes, uma para cada variável (`n1` e `n2`). Isso evita repetição de código (princípio DRY - *Don't Repeat Yourself*).
* **Lógica de Formatação**: A linha `int(soma) if soma.is_integer() else soma` é um operador ternário. Ela serve apenas para estética: se o resultado for `10.0`, ela exibe apenas `10`. Se for `10.5`, mantém as casas decimais.

### 3. O Bloco de Execução (`if __name__ == "__main__":`)
Este é um padrão fundamental em Python. Ele verifica se o script está sendo executado diretamente. 

* Se você importar este arquivo em outro projeto, o cálculo da soma não começará sozinho.
* Isso torna seu código modular e profissional, permitindo que as funções sejam testadas ou usadas em outros sistemas sem executar o script inteiro por acidente.

---

### Fluxo de Execução
Imagine o caminho que os dados percorrem desde o teclado até a tela:

1.  O programa inicia no bloco principal e chama `calcular_soma()`.
2.  `calcular_soma` pede um número e "pula" para dentro de `obter_numero`.
3.  O usuário digita algo. O `try` verifica se é número.
4.  Se for erro, o `while` repete. Se for correto, o valor volta para `calcular_soma`.
5.  O processo se repete para o segundo número.
6.  O cálculo é feito e o resultado é exibido com a formatação limpa.

Essa estrutura é muito comum em **sistemas de back-end**, onde você nunca pode confiar totalmente na entrada que vem do usuário final.

### Prompt (refinado)
Esta documentação foi elaborada para fornecer uma visão clara e técnica do funcionamento do script de soma de listas em Python, ideal para desenvolvedores que estão iniciando na linguagem.

---

## 1. Objetivo do Código
O script tem como finalidade principal realizar a **adição aritmética** de todos os elementos contidos em uma sequência numérica (lista). 

Ele foi projetado seguindo princípios de **programação defensiva**, garantindo que o programa não tente processar dados inexistentes, o que evita erros de execução (*runtime errors*) e melhora a experiência do usuário final.

---

## 2. Descrição da Função: `somar_lista(numeros)`

A função é o bloco lógico central do código. Abaixo, detalhamos seus componentes:

### Parâmetros
* **`numeros` (list):** Espera-se uma lista contendo objetos do tipo `int` (inteiros) ou `float` (ponto flutuante).

### Lógica Interna
1.  **Verificação de Vacuidade:** Antes de qualquer cálculo, o código utiliza a estrutura condicional `if not numeros:`. Em Python, coleções vazias possuem valor booleano `False`. Esta etapa previne que a função retorne resultados inesperados em listas nulas.
2.  **Processamento com `sum()`:** A função utiliza o método nativo `sum()`. Esta é uma função embutida altamente otimizada que percorre a lista e acumula os valores em uma única operação.

### Retorno
* Retorna um **valor numérico** (a soma total) caso a lista contenha dados.
* Retorna uma **String de aviso** caso a lista esteja vazia.

---

## 3. Exemplos de Uso

Para implementar esta função em seu projeto, você pode seguir os padrões abaixo:

### Cenário A: Lista Populada
Ideal para quando você recebe dados de um formulário ou banco de dados.
```python
dados = [5, 10, 15]
resultado = somar_lista(dados)
# Saída esperada: 30
```

### Cenário B: Lista Vazia
Demonstra o comportamento do código quando nenhum dado é fornecido.
```python
dados_vazios = []
resultado = somar_lista(dados_vazios)
# Saída esperada: "A lista está vazia. Não há nada para somar."
```

### Cenário C: Números Decimais
A função é versátil e aceita diferentes tipos numéricos simultaneamente.
```python
dados_mistos = [1.5, 2, 3.5]
resultado = somar_lista(dados_mistos)
# Saída esperada: 7.0
```

> **Nota Técnica:** Para aplicações que exigem alta precisão matemática com números decimais (como sistemas financeiros), recomenda-se o uso do módulo `decimal` em conjunto com esta lógica.

---
## 4. Comparação de Tecnologias
### Prompt inicial (vago)
Ao comparar **Java** e **Python**, estamos olhando para duas das linguagens mais influentes do mundo, mas com filosofias de design opostas. Enquanto o Python foca na **velocidade de desenvolvimento** e legibilidade, o Java foca na **robustez** e performance em larga escala.

Abaixo, apresento uma comparação detalhada entre as duas:

---

### 1. Filosofia e Sintaxe
* **Python:** É uma linguagem **interpretada** e de **tipagem dinâmica**. A sintaxe é limpa e utiliza indentação obrigatória, o que a torna muito parecida com o inglês. É ideal para prototipagem rápida.
* **Java:** É uma linguagem **compilada** (para bytecode) e de **tipagem estática**. É muito mais verbosa; o que você faz em 3 linhas de Python, pode levar 10 em Java. Tudo no Java deve estar dentro de uma classe, seguindo rigidamente a Orientação a Objetos.



---

### 2. Performance e Execução
| Característica | Python | Java |
| :--- | :--- | :--- |
| **Velocidade** | Mais lenta (interpretada linha a linha). | Mais rápida (compilada para Bytecode e otimizada pela JIT). |
| **Tipagem** | Dinâmica (você não declara o tipo da variável). | Estática (você deve declarar `int`, `String`, etc). |
| **Gerenciamento** | Automático (Garbage Collector). | Automático (Garbage Collector altamente otimizado). |
| **Portabilidade** | "Roda em qualquer lugar" com o interpretador. | "Write Once, Run Anywhere" via JVM (Java Virtual Machine). |

---

### 3. Ecossistema e Aplicações
Cada linguagem domina nichos específicos do mercado:

* **Onde o Python brilha:**
    * **Data Science e IA:** Bibliotecas como Pandas, NumPy e TensorFlow são o padrão da indústria.
    * **Automação e Scripts:** Excelente para tarefas rápidas de sistema.
    * **Desenvolvimento Web (Back-end):** Frameworks como Django e Flask.

* **Onde o Java brilha:**
    * **Sistemas Corporativos:** Grandes bancos e sistemas de ERP preferem Java pela segurança e escalabilidade.
    * **Android:** Até a ascensão do Kotlin, Java era a linguagem primária para apps Android.
    * **Sistemas Distribuídos:** Ferramentas de Big Data como Apache Hadoop e Spark são construídas sobre a JVM.

---

### 4. Curva de Aprendizado
Para quem está começando, o **Python** costuma ser a porta de entrada preferida, pois permite focar na lógica de programação sem se preocupar com detalhes complexos de memória ou declarações de tipos. 

O **Java**, por outro lado, força o programador a entender conceitos profundos de estrutura de dados e arquitetura desde o primeiro dia. Isso pode ser mais difícil no início, mas cria uma base técnica muito sólida para quem deseja seguir carreira em Engenharia de Software.

### Qual escolher?
* Escolha **Python** se você quer resultados rápidos, trabalha com análise de dados ou está começando agora.
* Escolha **Java** se você pretende trabalhar em grandes corporações, desenvolver aplicativos Android robustos ou quer entender a fundo como o software interage com a memória e o sistema.

### Prompt (refinado)
Ao escolher entre Java e Python para sistemas corporativos, a decisão geralmente passa pelo equilíbrio entre a velocidade de desenvolvimento e a performance bruta de execução.

Abaixo, apresento uma comparação detalhada focada no ecossistema de desenvolvimento de sistemas de grande porte:

### Comparativo: Java vs. Python

| Característica | Java | Python |
| :--- | :--- | :--- |
| **Paradigma** | Principalmente **Orientado a Objetos** (robusto e estrito), com suporte a funcional. | **Multiparadigma** (Funcional, Orientado a Objetos, Imperativo). Muito flexível. |
| **Desempenho** | **Alto.** O código é compilado para Bytecode e otimizado pela JVM (JIT), sendo superior em tarefas pesadas. | **Moderado.** É uma linguagem interpretada. Em tarefas computacionais intensas, costuma ser mais lenta que o Java. |
| **Curva de Aprendizado** | **Moderada/Alta.** Sintaxe verbosa e tipagem estática exigem mais estudo e mais linhas de código. | **Baixa.** Sintaxe limpa, próxima ao inglês, o que permite prototipagem rápida e fácil leitura. |
| **Aplicações Corporativas** | Sistemas bancários, back-ends de alta escala, Android, grandes sistemas legados e segurança. | Data Science, Inteligência Artificial, automação de processos (RPA) e APIs rápidas (Django/FastAPI). |

---

### Análise de Arquitetura

Para sistemas corporativos, o Java ainda é o padrão ouro devido ao seu gerenciamento de memória altamente sofisticado e à sua capacidade de lidar com múltiplas requisições simultâneas (concorrência) de forma eficiente. 

Por outro lado, Python dominou o setor corporativo moderno não pela velocidade de execução, mas pela **velocidade de entrega**. Em um cenário de Big Data, por exemplo, o Python é frequentemente usado para orquestrar o fluxo de dados, enquanto as bibliotecas pesadas por baixo dele são escritas em C ou C++.



### Qual escolher?

* **Escolha Java se:** O sistema precisa de máxima escalabilidade, segurança rigorosa de tipos e será mantido por grandes equipes durante décadas.
* **Escolha Python se:** O foco é integração com IA/ML, se você precisa colocar um produto no mercado rapidamente (*Time-to-Market*) ou se a legibilidade do código é a prioridade absoluta da equipe.

---
## 5. Criação de Testes Automatizados
### Prompt inicial (vago)
Para testar um código de forma profissional, especialmente em Python, utilizamos a biblioteca padrão **unittest**. Criar testes automatizados garante que, se você mudar algo no futuro, saberá imediatamente se quebrou alguma funcionalidade.

Aqui está um script de teste para a função de soma que desenvolvemos:

```python
import unittest
from io import StringIO
from unittest.mock import patch
# Supondo que seu código original esteja em um arquivo chamado 'calculadora.py'
# ou definido no mesmo script. Aqui testaremos a lógica da soma.

def somar(a, b):
    return a + b

class TestCalculadora(unittest.TestCase):

    def test_soma_numeros_positivos(self):
        self.assertEqual(somar(10, 5), 15)

    def test_soma_numeros_negativos(self):
        self.assertEqual(somar(-1, -1), -2)

    def test_soma_float(self):
        self.assertAlmostEqual(somar(10.5, 2.5), 13.0)

    def test_soma_zero(self):
        self.assertEqual(somar(10, 0), 10)

    # Teste avançado: Simulando entrada de usuário (mocking)
    @patch('builtins.input', side_effect=['5', '10'])
    def test_fluxo_input(self, mock_input):
        # Aqui simulamos o usuário digitando 5 e 10
        n1 = float(mock_input())
        n2 = float(mock_input())
        self.assertEqual(n1 + n2, 15.0)

if __name__ == '__main__':
    unittest.main()
```

---

### Por que fazer isso?

Como você está estudando **Análise e Desenvolvimento de Sistemas**, entender testes é um diferencial enorme. O mercado valoriza muito o **TDD (Test Driven Development)**.

* **`unittest`**: É o framework padrão do Python.
* **`assertEqual(a, b)`**: Verifica se o resultado da sua função é exatamente o que você espera.
* **`patch`**: É uma técnica para "enganar" o programa. Como o `input()` para o código e espera um humano, usamos o `patch` para dizer ao Python: "quando o programa pedir um input, finja que eu digitei 5".

---

### Como rodar:
1.  Salve o código de teste em um arquivo (ex: `test_calculadora.py`).
2.  No terminal, execute:
    ```bash
    python test_calculadora.py
    ```
3.  Se tudo estiver certo, você verá uma mensagem como: `Ran 5 tests in 0.001s - OK`.

Isso ajuda a garantir que a lógica do seu sistema de cadastro ou qualquer projeto acadêmico esteja sempre correta antes de você entregar ao professor.

### Prompt (refinado)
Para criar testes unitários em Python, a biblioteca padrão `unittest` é a escolha mais comum. Ela permite estruturar os casos de teste em classes e fornece diversos métodos de asserção para verificar os resultados.

Abaixo, apresento o código da função e a sua respectiva classe de teste.

```python
import unittest

def calcular_media(lista):
    """Calcula a média aritmética de uma lista de números."""
    if not lista:
        return 0
    return sum(lista) / len(lista)

class TestCalcularMedia(unittest.TestCase):
    
    def test_media_valores_positivos(self):
        # Caso clássico com números inteiros
        self.assertEqual(calcular_media([10, 20, 30]), 20.0)
    
    def test_lista_vazia(self):
        # Verifica se a função lida corretamente com a lista vazia (conforme definido na função)
        self.assertEqual(calcular_media([]), 0)
        
    def test_valores_negativos(self):
        # Verifica se a soma e divisão de negativos funciona (ex: -10 + -20 = -30 / 2 = -15)
        self.assertEqual(calcular_media([-10, -20]), -15.0)
        
    def test_valores_mistos(self):
        # Verifica o comportamento com positivos e negativos misturados
        self.assertEqual(calcular_media([-5, 5]), 0.0)

    def test_lista_um_elemento(self):
        # Caso de borda: apenas um número
        self.assertEqual(calcular_media([100]), 100.0)

if __name__ == '__main__':
    unittest.main()
```

### Explicação dos Componentes:

1.  **`unittest.TestCase`**: Ao herdar desta classe, o `unittest` reconhece que todos os métodos que começam com o prefixo `test_` são casos de teste que devem ser executados.
2.  **`self.assertEqual(a, b)`**: Este é o método principal de verificação. Ele compara o resultado da função (`a`) com o valor esperado (`b`). Se forem diferentes, o teste falha e indica o erro.
3.  **Tratamento de Lista Vazia**: No código da função `calcular_media`, adicionei uma verificação inicial `if not lista`. Isso evita o erro `ZeroDivisionError`, que ocorreria ao tentar dividir a soma por `len(lista)` (que seria zero).
4.  **Execução**: O bloco `if __name__ == '__main__': unittest.main()` permite que você execute o arquivo diretamente pelo terminal (ex: `python nome_do_arquivo.py`) para ver o relatório de testes (OK ou Fails).
