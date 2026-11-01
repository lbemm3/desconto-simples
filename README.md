[README.md](https://github.com/user-attachments/files/34229961/README.md)
# Calculadora de Desconto Comercial Simples

Calculadora educacional, em um único arquivo HTML, para resolver problemas de **desconto comercial simples** (também chamado de *desconto por fora*), com a **resolução passo a passo** de cada cálculo.

Desenvolvida pelo **Prof. Laerte Bemm** — Departamento de Matemática, Universidade Estadual de Maringá (UEM).

---

## Sumário

- [Sobre o projeto](#sobre-o-projeto)
- [Funcionalidades](#funcionalidades)
- [Fundamentação matemática](#fundamentação-matemática)
- [Tipos de problema](#tipos-de-problema)
- [Como usar](#como-usar)
- [Exemplos resolvidos](#exemplos-resolvidos)
- [Validações e mensagens de erro](#validações-e-mensagens-de-erro)
- [Convenções adotadas](#convenções-adotadas)
- [Tecnologias](#tecnologias)
- [Estrutura do repositório](#estrutura-do-repositório)
- [Publicação online](#publicação-online)
- [Contribuindo](#contribuindo)
- [Autoria e créditos](#autoria-e-créditos)
- [Licença](#licença)

---

## Sobre o projeto

Na prática financeira, **descontar um título** (uma duplicata ou uma nota promissória, por exemplo) significa antecipar o seu recebimento antes da data de vencimento. Em troca da antecipação, o portador abre mão de parte do valor: essa diferença é o **valor do desconto**.

No **desconto comercial simples**, o desconto incide sempre sobre o **valor nominal** do título, e não sobre o valor efetivamente recebido. Por isso, a **taxa efetiva** cobrada na operação é sempre **maior** que a taxa de desconto anunciada, e a calculadora mostra essa comparação em cada resultado.

O objetivo é didático: além de entregar o resultado, a ferramenta exibe cada fórmula aplicada com os valores substituídos, para que o estudante acompanhe o raciocínio.

## Funcionalidades

- Cinco tipos de problema, selecionáveis por botões.
- Resolução detalhada passo a passo, com fórmula, substituição e resultado.
- Cálculo automático da **taxa efetiva** e comparação com a taxa nominal.
- Prazo em **meses** ou em **dias**, conforme o tipo de problema (com conversão automática, base de 30 dias por mês).
- Aceita **vírgula ou ponto** como separador decimal (ex.: `2,5` ou `2.5`).
- Resultados formatados no padrão brasileiro (`R$ 1.234,56`).
- Validação dos dados com mensagens de erro claras.
- Layout responsivo, que funciona em computador, tablet e celular.
- Sem dependências, sem instalação e sem conexão com servidor: tudo roda no navegador.

## Fundamentação matemática

### Notação

| Símbolo | Significado |
|:-------:|-------------|
| **FV** | Valor nominal do título (valor de face, no vencimento) |
| **VC** | Valor comercial (valor líquido creditado ao portador) |
| **VD** | Valor do desconto |
| **n** | Prazo de antecipação (em períodos) |
| **i** | Taxa de desconto por período (na forma decimal nas fórmulas) |
| **i<sub>f</sub>** | Taxa efetiva da operação |

### Fórmulas

```
VD = FV · n · i               valor do desconto
VC = FV · (1 − n · i)         valor comercial (líquido creditado)
FV = VC / (1 − n · i)         valor nominal, dado o valor comercial
n  = VD / (FV · i)            prazo de antecipação
i  = VD / (FV · n)            taxa de desconto
i_f = (FV / VC − 1) / n       taxa efetiva (sempre maior que i)
```

### Por que a taxa efetiva é maior?

Como o desconto é calculado sobre FV, mas o portador recebe apenas VC (que é menor que FV), a base sobre a qual o custo realmente incide é VC. Assim:

```
i_f = VD / (VC · n)  >  VD / (FV · n) = i
```

### Condição de existência

Para que o valor comercial seja positivo, é necessário que **n · i < 1**. A calculadora verifica essa condição e avisa quando ela é violada.

## Tipos de problema

| # | Objetivo | Dados de entrada | Unidade do prazo |
|:-:|----------|------------------|:----------------:|
| 1 | Calcular **VD** e **VC** | FV, n, i | meses |
| 2 | Calcular o **prazo n** | FV, VC, i | resultado em meses e em dias |
| 3 | Calcular **VC** | FV, n, i | dias |
| 4 | Calcular **FV** | VC, n, i | dias |
| 5 | Calcular a **taxa i** | FV, VC, n | meses |

A taxa de desconto **i** é sempre informada em **% ao mês** (a.m.).

## Como usar

### Opção 1: abrir direto no navegador

1. Baixe o arquivo `desconto-comercial-simples.html` (ou clone o repositório).
2. Dê um duplo clique no arquivo. Ele abre no navegador padrão.

### Opção 2: clonar o repositório

```bash
git clone https://github.com/<seu-usuario>/<nome-do-repositorio>.git
cd <nome-do-repositorio>
```

Depois, abra o arquivo HTML no navegador. Não é preciso instalar nada.

### Usando a calculadora

1. Escolha o tipo de problema nos botões do topo.
2. Preencha os campos solicitados (use valores positivos).
3. Clique em **▶ Calcular**.
4. Leia a resolução passo a passo exibida abaixo do botão.

## Exemplos resolvidos

Os valores abaixo podem ser digitados diretamente na calculadora para conferência.

### Tipo 1: VD e VC

**Dados:** FV = R$ 2.000,00; n = 3 meses; i = 2,5% a.m.

- VD = 2.000 · 3 · 0,025 = **R$ 150,00**
- VC = 2.000 − 150 = **R$ 1.850,00**
- i<sub>f</sub> = (2.000 / 1.850 − 1) / 3 ≈ **2,7027% a.m.**

### Tipo 2: prazo de antecipação

**Dados:** FV = R$ 6.800,00; VC = R$ 6.000,00; i = 3,2% a.m.

- VD = 6.800 − 6.000 = R$ 800,00
- n = 800 / (6.800 · 0,032) ≈ **3,6765 meses**, ou cerca de **110,29 dias**

### Tipo 3: valor comercial com prazo em dias

**Dados:** FV = R$ 34.000,00; n = 41 dias; i = 4,7% a.m.

- n = 41 / 30 ≈ 1,3667 mês
- VD = 34.000 · 1,3667 · 0,047 ≈ **R$ 2.184,07**
- VC = 34.000 − 2.184,07 ≈ **R$ 31.815,93**

### Tipo 4: valor nominal

**Dados:** VC = R$ 70.190,00; n = 138 dias; i = 5,2% a.m.

- n = 138 / 30 = 4,6 meses
- Fator de desconto = 1 − 4,6 · 0,052 = 0,7608
- FV = 70.190 / 0,7608 ≈ **R$ 92.258,14**

### Tipo 5: taxa de desconto

**Dados:** FV = R$ 1.000,00; VC = R$ 880,00; n = 4 meses

- VD = 1.000 − 880 = R$ 120,00
- i = 120 / (1.000 · 4) = **3% a.m.**
- i<sub>f</sub> = (1.000 / 880 − 1) / 4 ≈ **3,4091% a.m.**

## Validações e mensagens de erro

A calculadora impede resultados sem sentido econômico:

| Situação | Mensagem exibida |
|----------|------------------|
| Campo vazio, texto inválido, zero ou valor negativo | Pede o preenchimento de todos os campos com valores positivos |
| n · i ≥ 1 (tipos 1, 3 e 4) | Informa que a condição é violada e que o resultado não tem sentido econômico |
| VC ≥ FV (tipos 2 e 5) | Informa que o valor comercial deve ser menor que o valor nominal |

## Convenções adotadas

- **Mês comercial de 30 dias**: a conversão entre dias e meses usa `n(meses) = n(dias) / 30`.
- **Taxa de desconto em % ao mês**: o programa divide por 100 internamente.
- **Separador decimal**: a vírgula é convertida em ponto antes do cálculo.
- **Formatação de saída**: números exibidos em `pt-BR`, com 2 casas decimais para valores monetários e 4 casas para taxas e prazos.

## Tecnologias

- HTML5
- CSS3 (Grid e Flexbox, layout responsivo)
- JavaScript puro (*vanilla*), sem frameworks nem bibliotecas externas

## Estrutura do repositório

```
.
├── desconto-comercial-simples.html   # aplicação completa (HTML + CSS + JS)
└── README.md                         # este arquivo
```

> Dica: para publicar com o GitHub Pages usando a URL raiz, renomeie o arquivo HTML para `index.html`.

## Publicação online

### GitHub Pages

1. No repositório, abra **Settings → Pages**.
2. Em **Source**, escolha **Deploy from a branch**.
3. Selecione a branch `main` e a pasta `/ (root)`, e salve.
4. Após alguns minutos, a calculadora ficará disponível em `https://<seu-usuario>.github.io/<nome-do-repositorio>/`.

### Outras opções

Por ser um único arquivo estático, o projeto também pode ser hospedado em Vercel, Netlify, Cloudflare Pages ou em qualquer servidor web comum.

## Contribuindo

Sugestões e correções são bem-vindas:

1. Faça um *fork* do repositório.
2. Crie uma branch para a sua alteração: `git checkout -b minha-melhoria`.
3. Faça o *commit*: `git commit -m "Descreve a melhoria"`.
4. Envie para o seu fork: `git push origin minha-melhoria`.
5. Abra um *Pull Request*.

Ideias para evoluções futuras:

- Versão para **desconto comercial composto**.
- Exportação da resolução em PDF.
- Opção de prazo em dias também nos tipos 1, 2 e 5.
- Modo escuro.

## Autoria e créditos

**Prof. Laerte Bemm**
Departamento de Matemática, Universidade Estadual de Maringá (UEM)

Ferramenta de uso educacional.

## Licença

Defina aqui a licença do projeto. Sugestão: [MIT](https://opensource.org/licenses/MIT) para uso livre, ou [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.pt-br) caso queira exigir atribuição ao autor.
