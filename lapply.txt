# R_programming_apply
#Usando as "funções loop" da família -apply

#1) lapply: lista --> lista
#Sintaxe: lapply(x,FUN,...)
# a função FUN é aplicada sobre x, valendo-se dos argumentos opcionais de FUN ("...")
# lapply SEMPRE retorna uma lista ao aplicar FUN sobre x. Se x não for uma lista ou não por possível sua coerção a um objeto tipo lista,
# lapply retorna um erro.

# Criação de uma lista x, de elementos "a" e "b":
x<-list(a=matrix(1:4,2), b=matrix(1,2,3))
#> x
#$a
#     [,1] [,2]
#[1,]    1    3
#[2,]    2    4

#$b
#     [,1] [,2] [,3]
#[1,]    1    1    1
#[2,]    1    1    1

lapply(x, mean, na.rm = TRUE)  # cálculo da média de todos os elementos não NA de "a" e "b"
#$a
#[1] 2.5

#$b
#[1] 1

lapply(x, colMeans, na.rm = TRUE) #cálculo da média sobre as colunas de "a" e "b"
#$a
#[1] 1.5 3.5

#$b
#[1] 1 1 1

#Note que colMeans(x) retorna erro!
colMeans(x)
#Error in colMeans(x) : 'x' deve ser um array de pelo menos duas dimensões.

#Assim como ocorre com as outras funções da família -apply, lapply pode ser aplicada sobre as chamadas "funções anônimas" - funções
#criadas apenas para o comando, "desaparecendo" logo após.

lapply(x, function(anon) anon[ ,1])   # a função "anon" extrai a primeira coluna de "a" e "b" e a retorna na forma de vetor
#$a
#[1] 1 2

#$b
#[1] 1 1

lapply(lapply(x, function(anon) anon[ ,1]),mean, na.rm = TRUE)    #retorna a média da primeira coluna
#$a
#[1] 1.5

#$b
#[1] 1



