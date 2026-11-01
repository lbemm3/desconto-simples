[README_desconto_simples (1).md](https://github.com/user-attachments/files/34230086/README_desconto_simples.1.md)
# 📉 Calculadora de Desconto Comercial Simples

Calculadora educacional, em um único arquivo HTML, para resolver problemas de **desconto comercial simples** (desconto "por fora") com **resolução passo a passo**.

Desenvolvida pelo **Prof. Laerte Bemm** — Departamento de Matemática, Universidade Estadual de Maringá (UEM).

---

## 📑 Sumário

- [📌 Sobre o projeto](#-sobre-o-projeto)
- [✨ Funcionalidades](#-funcionalidades)
- [🧮 Fórmulas utilizadas](#-fórmulas-utilizadas)
- [🗂️ Tipos de problema](#️-tipos-de-problema)
- [✏️ Exemplos](#️-exemplos)
- [🚀 Como usar](#-como-usar)
- [⚠️ Validações e observações](#️-validações-e-observações)
- [🛠️ Tecnologias](#️-tecnologias)
- [📁 Estrutura sugerida do repositório](#-estrutura-sugerida-do-repositório)
- [🔗 Projeto relacionado](#-projeto-relacionado)
- [👤 Autoria](#-autoria)
- [📄 Licença](#-licença)

---

## 📌 Sobre o projeto

Descontar um título (duplicata, nota promissória etc.) significa antecipar o seu recebimento antes do vencimento, abrindo mão de parte do valor em troca da antecipação. Nesta calculadora:

| Símbolo | Significado |
|:-------:|-------------|
| $\mathrm{FV}$ | Valor nominal (valor de face / resgate no vencimento) |
| $\mathrm{VC}$ | Valor comercial (valor líquido efetivamente recebido) |
| $\mathrm{VD}$ | Valor do desconto, $\mathrm{VD} = \mathrm{FV} - \mathrm{VC}$ |
| $i$ | Taxa de desconto por período (% a.m.) |
| $n$ | Prazo de antecipação, em **meses** ou em **dias** (conforme o tipo) |
| $i_f$ | Taxa efetiva da operação |

No **desconto comercial simples**, a taxa $i$ incide sempre sobre o **valor nominal** $\mathrm{FV}$, e não sobre o valor comercial. Por isso a taxa efetiva cobrada é **sempre maior** que a taxa de desconto anunciada: $i_f > i$.

---

## ✨ Funcionalidades

- Cinco tipos de problema, selecionáveis por botões.
- Resolução detalhada passo a passo: fórmula, substituição e resultado.
- Cálculo automático da **taxa efetiva** e comparação com a taxa nominal.
- Prazo em **meses** ou **dias** (conversão automática, base de 30 dias por mês).
- Aceita **vírgula ou ponto** como separador decimal.
- Resultados no padrão brasileiro (`R$ 1.234,56`).
- Layout responsivo: computador, tablet e celular.
- Sem dependências e sem servidor: tudo roda no navegador.

---

## 🧮 Fórmulas utilizadas

### Valor do desconto

O desconto cresce linearmente com o prazo e incide sobre o valor nominal:

$$
\mathrm{VD} = \mathrm{FV}\cdot n\cdot i
$$

### Valor comercial

$$
\mathrm{VC} = \mathrm{FV}-\mathrm{VD} = \mathrm{FV}\cdot\underbrace{(1-n\cdot i)}_{\text{fator de desconto}}
$$

### Valor nominal (dado o valor comercial)

Isolando $\mathrm{FV}$ na expressão anterior:

$$
\mathrm{FV} = \frac{\mathrm{VC}}{1-n\cdot i}
$$

### Prazo de antecipação

$$
n = \frac{\mathrm{VD}}{\mathrm{FV}\cdot i}
$$

### Taxa de desconto

$$
i = \frac{\mathrm{VD}}{\mathrm{FV}\cdot n}
$$

### Taxa efetiva

A taxa efetiva toma como base o valor realmente recebido, $\mathrm{VC}$:

$$
i_f = \frac{1}{n}\left(\frac{\mathrm{FV}}{\mathrm{VC}}-1\right) = \frac{\mathrm{VD}}{\mathrm{VC}\cdot n} = \frac{i}{1-n\cdot i}
$$

Como $\mathrm{VC}<\mathrm{FV}$ (ou, de forma equivalente, $0<1-n\cdot i<1$), tem-se $i_f>i$.

### Condição de existência

Para que $\mathrm{VC}>0$ é necessário que

$$
n\cdot i < 1
$$

### Resumo

| Grandeza | Fórmula |
|:--------:|:-------:|
| $\mathrm{VD}$ | $\mathrm{FV}\cdot n\cdot i$ |
| $\mathrm{VC}$ | $\mathrm{FV}(1-n\cdot i)$ |
| $\mathrm{FV}$ | $\dfrac{\mathrm{VC}}{1-n\cdot i}$ |
| $n$ | $\dfrac{\mathrm{VD}}{\mathrm{FV}\cdot i}$ |
| $i$ | $\dfrac{\mathrm{VD}}{\mathrm{FV}\cdot n}$ |
| $i_f$ | $\dfrac{1}{n}\left(\dfrac{\mathrm{FV}}{\mathrm{VC}}-1\right)=\dfrac{i}{1-n\cdot i}$ |

---

## 🗂️ Tipos de problema

A calculadora possui cinco modos, selecionáveis por botões:

| Tipo | Dados de entrada | Resultados | Prazo |
|:----:|------------------|------------|:-----:|
| **1** | $\mathrm{FV}$, $n$, $i$ | $\mathrm{VD}$, $\mathrm{VC}$, $i_f$ | meses |
| **2** | $\mathrm{FV}$, $\mathrm{VC}$, $i$ | $n$ (em meses e em dias), $i_f$ | resultado |
| **3** | $\mathrm{FV}$, $n$, $i$ | $\mathrm{VD}$, $\mathrm{VC}$, $i_f$ | dias |
| **4** | $\mathrm{VC}$, $n$, $i$ | $\mathrm{FV}$, $\mathrm{VD}$, $i_f$ | dias |
| **5** | $\mathrm{FV}$, $\mathrm{VC}$, $n$ | $i$, $i_f$ | meses |

A taxa de desconto $i$ é sempre informada em **% ao mês**. Em todos os casos, o resultado é apresentado em etapas: dados, conversão do prazo (quando necessária), valores calculados e verificação da taxa efetiva.

---

## ✏️ Exemplos

Os valores abaixo podem ser digitados diretamente na calculadora para conferência.

**Tipo 1** — Título de R$ 2.000,00, antecipado 3 meses, taxa de 2,5% a.m.

$$
\mathrm{VD} = 2000\cdot 3\cdot 0{,}025
$$

- $\mathrm{VD} =$ **R$ 150,00**
- $\mathrm{VC} = 2000-150 =$ **R$ 1.850,00**
- $i_f = \dfrac{1}{3}\left(\dfrac{2000}{1850}-1\right) \approx$ **2,7027% a.m.**

**Tipo 2** — $\mathrm{FV}$ = R$ 6.800,00, $\mathrm{VC}$ = R$ 6.000,00, $i$ = 3,2% a.m.

$$
n = \frac{800}{6800\cdot 0{,}032}
$$

- $n \approx$ **3,6765 meses**, ou cerca de **110,29 dias**
- $i_f \approx$ **3,63% a.m.**

**Tipo 3** — $\mathrm{FV}$ = R$ 34.000,00, $n$ = 41 dias, $i$ = 4,7% a.m.

$$
n=\frac{41}{30}\approx 1{,}3667 \text{ meses}
$$

- $\mathrm{VD} = 34000\cdot 1{,}3667\cdot 0{,}047 \approx$ **R$ 2.184,07**
- $\mathrm{VC} \approx$ **R$ 31.815,93**
- $i_f \approx$ **5,02% a.m.**

**Tipo 4** — $\mathrm{VC}$ = R$ 70.190,00, $n$ = 138 dias, $i$ = 5,2% a.m.

$$
n=\frac{138}{30}=4{,}6 \text{ meses}, \qquad
\mathrm{FV}=\frac{70190}{1-4{,}6\cdot 0{,}052}=\frac{70190}{0{,}7608}
$$

- $\mathrm{FV} \approx$ **R$ 92.258,14**

**Tipo 5** — $\mathrm{FV}$ = R$ 1.000,00, $\mathrm{VC}$ = R$ 880,00, $n$ = 4 meses

$$
i = \frac{120}{1000\cdot 4}
$$

- $i =$ **3% a.m.**
- $i_f = \dfrac{1}{4}\left(\dfrac{1000}{880}-1\right) \approx$ **3,4091% a.m.**

---

## 🚀 Como usar

### Localmente

1. Baixe o arquivo `desconto-comercial-simples.html` (ou clone o repositório):
   ```bash
   git clone https://github.com/SEU-USUARIO/NOME-DO-REPOSITORIO.git
   ```
2. Abra o arquivo no navegador (duplo clique ou `Arquivo → Abrir`).
3. Escolha o tipo de problema, preencha os campos e clique em **▶ Calcular**.

Não há instalação, build nem dependências: basta um navegador moderno.

### Online com GitHub Pages

1. No repositório, vá em **Settings → Pages**.
2. Em **Build and deployment**, selecione **Deploy from a branch**.
3. Escolha a branch `main` e a pasta `/ (root)` e clique em **Save**.
4. Se quiser que o site abra direto na calculadora, renomeie o arquivo para `index.html`.
5. Após alguns instantes, a calculadora estará disponível em:
   ```
   https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/
   ```

---

## ⚠️ Validações e observações

- Todos os campos devem ser preenchidos com valores **positivos**.
- Nos Tipos 1, 3 e 4, deve valer $n\cdot i<1$; caso contrário, $\mathrm{VC}\le 0$ (ou $\mathrm{FV}$ indefinido) e a calculadora exibe um aviso.
- Nos Tipos 2 e 5, deve valer $\mathrm{VC}<\mathrm{FV}$.
- A conversão de dias para meses usa o **mês comercial de 30 dias**: $n_{\text{meses}} = n_{\text{dias}}/30$.
- A taxa $i$ é informada em porcentagem; o programa a converte internamente para a forma decimal.
- Os campos aceitam **vírgula ou ponto** como separador decimal (ex.: `2,5` ou `2.5`).
- Valores monetários são exibidos com 2 casas decimais; taxas e prazos, com 4.
- A ferramenta tem finalidade **didática**; não substitui o cálculo oficial de uma instituição financeira.

---

## 🛠️ Tecnologias

- HTML5
- CSS3 (layout responsivo com Grid e Flexbox)
- JavaScript puro (*vanilla*), sem bibliotecas externas

---

## 📁 Estrutura sugerida do repositório

```
├── index.html     # a calculadora (ou desconto-comercial-simples.html)
├── README.md      # este arquivo
└── LICENSE        # licença (opcional)
```

---

## 🔗 Projeto relacionado

Esta calculadora tem uma versão irmã, a **Calculadora de Desconto Composto Comercial**, que trata o desconto por fora com a taxa incidindo sucessivamente, período a período, em vez de linearmente sobre o valor nominal.

---

## 👤 Autoria

**Prof. Laerte Bemm**
Departamento de Matemática — Universidade Estadual de Maringá (UEM)

---

## 📄 Licença

Defina a licença de sua preferência (por exemplo, [MIT](https://opensource.org/licenses/MIT)) e adicione o arquivo `LICENSE` ao repositório. Para uso estritamente acadêmico, você também pode indicar aqui: *"Material educacional de uso livre, com citação da autoria."*
