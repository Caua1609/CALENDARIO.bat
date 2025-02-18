# CALENDARIO.bat
#### Este script em Batch foi desenvolvido para automatizar a criação de uma estrutura de pastas que representa os dias de um mês em um ano específico. Ele permite que o usuário forneça dois parâmetros de entrada: o ano e o mês, e cria um diretório para o ano, um para o mês e subdiretórios para cada dia do mês escolhido.Além disso, o script leva em consideração os anos bissextos para ajustar corretamente o número de dias do mês de fevereiro. O processo é útil para organizar arquivos ou backups de forma estruturada, com cada dia do mês representado como uma pasta separada.

## Objetivo do Script
**O objetivo deste script é:**

Validar o mês fornecido como entrada.

Verificar se o ano é bissexto e, caso afirmativo, ajustar o número de dias do mês de fevereiro.

Criar um diretório para o ano especificado (caso ainda não exista).

Criar subdiretórios para cada dia do mês escolhido.

## Explicação Do Código
**Validação do Mês**

```
if %2 gtr 12 (
    echo Mes invalido O mes deve ser entre 1 e 12
    exit /b
)
```
**Criação Do Diretório Para o Ano** 

```
if not exist "%1" (
    mkdir "%1"
)
```
**Calculo De Numeros De Dias Para Fevereiro**

```
set /a "resto=%1 %% 4"
set /a "resto100=%1 %% 100"
set /a "resto400=%1 %% 400"
set /a "conta = %1+4"
```
**Criação de Diretorios Para o Mês**

```
cd %1
if not exist "%2" (
    mkdir "%2"
)
```

**Definição do Número de Dias do Mês**

```
if "%2" == "1" set dias=31
if "%2" == "2" set dias=%dias_fevereiro%
if "%2" == "3" set dias=31
...
```

**Criação de Diretorios Para Cada dia do Mês**

```
for /l %%i in (1,1,%dias%) do (
    if exist %dias% (
        mkdir %%i
    )
)
```

**Retorno aos Diretorios Anteriores**

```
cd .. 
cd ..
```

## Desafios e Soluções
***Validação de Ano e Mês***: Garantir que os valores de entrada (ano e mês) fossem válidos.

**Para resolver isso, foi feita a verificação do mês ser maior que 12 e a verificação do ano ser bissexto.**

***Cálculo de Ano Bissexto:*** A regra para determinar um ano bissexto envolvia um cálculo complexo, mas foi facilmente implementada com a operação %% para módulo.

![Calendario](https://marketplace.canva.com/EAGPE0MMYx8/2/0/1600w/canva-calend%C3%A1rio-de-2025-moderno-e-elegante-marrom-e-branco-com-feriados-mP8Bt8I2HfQ.jpg)
## O Que Aprendi
***Durante a criação deste script, aprendi a trabalhar com manipulação de diretórios em batch, além de aplicar lógica condicional para validar entradas e calcular se um ano é bissexto. Esse tipo de automação pode ser útil para organizar arquivos de maneira estruturada, especialmente em sistemas que lidam com datas e períodos de tempo.***
