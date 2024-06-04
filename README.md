# Criando-uma-Calculadora-com-Go

Vou criar um artigo bem estruturado sobre como criar uma calculadora em Go, organizando o código em módulos e alinhando todo o conteúdo à esquerda. Vou dividir o artigo em seções para facilitar a leitura.

---

# Criando uma Calculadora em Go com Módulos

Neste artigo, vamos aprender a criar uma calculadora simples em Go que suporta as operações de soma, subtração, multiplicação e divisão. Vamos organizar o código em módulos para manter tudo bem estruturado.

## 1. Estrutura do Projeto

Primeiro, vamos criar a estrutura básica do nosso projeto:

```
meu_projeto/
├── main.go
└── calc/
    └── calc.go
```

## 2. Módulo `calc`

O módulo `calc` conterá a lógica para realizar as operações matemáticas. Vamos criar um arquivo chamado `calc.go` dentro da pasta `calc`.

```go
// calc.go
package calc

func Add(a, b float64) float64 {
    return a + b
}

func Subtract(a, b float64) float64 {
    return a - b
}

func Multiply(a, b float64) float64 {
    return a * b
}

func Divide(a, b float64) float64 {
    if b != 0 {
        return a / b
    }
    return 0
}
```

## 3. Arquivo `main.go`

No arquivo `main.go`, vamos criar a interface de linha de comando para interagir com a calculadora.

```go
// main.go
package main

import (
    "fmt"
    "os"
    "strconv"

    "meu_projeto/calc" // Substitua pelo caminho correto do seu projeto
)

func main() {
    if len(os.Args) != 4 {
        fmt.Println("Uso: calculadora <operacao> <valor1> <valor2>")
        os.Exit(1)
    }

    operation := os.Args[1]
    a, _ := strconv.ParseFloat(os.Args[2], 64)
    b, _ := strconv.ParseFloat(os.Args[3], 64)

    switch operation {
    case "add":
        fmt.Printf("Resultado da soma: %.2f\n", calc.Add(a, b))
    case "subtract":
        fmt.Printf("Resultado da subtração: %.2f\n", calc.Subtract(a, b))
    case "multiply":
        fmt.Printf("Resultado da multiplicação: %.2f\n", calc.Multiply(a, b))
    case "divide":
        fmt.Printf("Resultado da divisão: %.2f\n", calc.Divide(a, b))
    default:
        fmt.Println("Operação inválida. Use: add, subtract, multiply ou divide.")
    }
}
```

## 4. Executando a Calculadora

Compile o projeto e execute-o passando os argumentos corretos:

```
go build
./seu_executavel add 10 5
```

Isso deve criar uma calculadora funcional em Go que suporta as operações especificadas. Lembre-se de substituir `meu_projeto` pelo caminho correto do seu projeto.

---

Espero que este artigo tenha sido útil para alguém!
