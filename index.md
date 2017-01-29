---
title: Introdução
date: '2017-01-29'
---



## Pipe `%>%`

As duas linhas abaixo são equivalentes:


```r
f(x, y)
x %>% f(y)
```

O operador `%>%` (*pipe* ) usa o resultado do seu lado esquerdo como primeiro argumento da funçăo do lado direito. Ele foi uma das grandes revoluções recentes do R, tornando a leitura de códigos mais lógica, fácil e compreensível. Este operador foi introduzido por Stefan Milton Bache no pacote `magrittr` e já existem diversos pacotes construidos para facilitar a sua utilizaçăo.

O operador `%>%` pertence ao pacote `magrittr`. Certifique-se que esteja instalado.


```r
install.packages("magrittr")
```

No exemplo seguinte o operador calcula a raiz quadrada da soma dos valores de 1 a 4.


```r
library(magrittr)

x <- c(1, 2, 3, 4)
x %>% sum %>% sqrt
```

```
## [1] 3.162278
```

Escrever esse cálculo na forma usual ficaria da seguinte forma:


```r
sqrt(sum(x))
```

```
## [1] 3.162278
```

O caminho que o código `x %>% sum %>% sqrt` seguiu foi enviar o objeto `x` como argumento da função `sum()` e, em seguida, enviar a saida da expressão `sum(x)` como argumento da função `sqrt()`. Observe que não é necessário colocar os parênteses após o nome das funções.

Pela simplicidade do exemplo, a utilização do `%>%` não parece trazer grandes vantagens, pois a expressão `sqrt(sum(x))` é facilmente compreendida. No entanto, se tivermos um grande número de funções aninhadas, a utilizaçăo do `pipe` transforma um código confuso e difícil de ser lido em algo simples e intuitivo. Como exemplo, imagine que você precise escrever uma receita de um bolo usando o R, e cada passo da receita é uma função:


```r
esfrie(asse(coloque(bata(acrescente(recipiente(rep("farinha", 2), "água", "fermento", "leite", "óleo"), "farinha", até = "macio"), duração = "3min"), lugar = "forma", tipo = "grande", untada = TRUE), duração = "50min"), "geladeira", "20min")
```

Tente entender o que é preciso fazer. Depois de desistir, veja como fica escrevendo com o operador `%>%`:


```r
recipiente(rep("farinha", 2), "água", "fermento", "leite", "óleo") %>%
  acrescente("farinha", até = "macio") %>%
  bata(duraço = "3min") %>%
  coloque(lugar = "forma", tipo = "grande", untada = TRUE) %>%
  asse(duração = "50min") %>%
  esfrie("geladeira", "20min")
```

Agora o código realmente parece uma receita de bolo.

Para mais informações sobre o `pipe` e exemplos de utilização, visite a página [Ceci n'est pas un pipe](http://cran.r-project.org/web/packages/magrittr/vignettes/magrittr.html).


