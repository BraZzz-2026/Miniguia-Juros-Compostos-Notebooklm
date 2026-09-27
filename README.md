#  Miniguia de Estudos: Juros Compostos, Inflação e Poder de Compra

> Caderno temático construído no **NotebookLM** como ferramenta de aprendizagem ativa, unindo curadoria de fontes, engenharia de prompts e pensamento crítico sobre as respostas da IA.
>
> Projeto desenvolvido para o desafio de projeto da **DIO**.

![NotebookLM](https://img.shields.io/badge/NotebookLM-IA%20Generativa-4285F4)
![Tema](https://img.shields.io/badge/Tema-Educa%C3%A7%C3%A3o%20Financeira-2ea44f)

---

## 📑 Sumário

1. [Contexto e Objetivos](#1-contexto-e-objetivos)
2. [Curadoria de Fontes](#2-curadoria-de-fontes)
3. [Engenharia de Prompts e "Cicatrizes"](#3-engenharia-de-prompts-e-cicatrizes)
4. [Miniguia de Estudo](#4-miniguia-de-estudo)
5. [Prompts Reutilizáveis](#5-prompts-reutilizáveis)
6. [Materiais Gerados](#6-materiais-gerados)
7. [Conclusões](#7-conclusões)

---

## 1. Contexto e Objetivos

### Contexto
Juros compostos são a base de praticamente toda decisão financeira: investir, financiar um veículo, usar o cartão de crédito ou avaliar se um rendimento está de fato gerando ganho. Porém, entender juros sem entender **inflação** e **taxa Selic** leva a conclusões erradas, já que um investimento pode "render" e ainda assim perder poder de compra.

Por isso, este caderno temático conecta os três pilares: **juros compostos → inflação (IPCA) → taxa Selic → rentabilidade real**.

### Objetivos de estudo
1. Entender a diferença entre juros simples e compostos e aplicar a fórmula `M = C(1+i)^n`.
2. Compreender o papel da Selic, do Copom e do IPCA e como eles se relacionam.
3. Diferenciar rentabilidade **nominal** de rentabilidade **real**.
4. Analisar o efeito dos juros compostos contra o consumidor (dívidas e financiamentos).
5. Avaliar o papel do tempo e dos aportes na formação de patrimônio.
6. **Testar a confiabilidade do NotebookLM em cálculos financeiros e documentar seus limites.**

---

## 2. Curadoria de Fontes

**Critérios de seleção:** fontes oficiais ou institucionais, gratuitas, em português e sem viés comercial.

| # | Fonte | Instituição | Tipo | Conteúdo principal |
|---|-------|-------------|------|--------------------|
| 1 | [Caderno de Educação Financeira – Gestão de Finanças Pessoais](https://www.bcb.gov.br/content/cidadaniafinanceira/documentos_cidadania/Cuidando_do_seu_dinheiro_Gestao_de_Financas_Pessoais/caderno_cidadania_financeira.pdf) | Banco Central do Brasil | PDF | Orçamento, crédito, poupança, investimento, custo de oportunidade, CET |
| 2 | [Juros Simples e Compostos: Um Estudo Detalhado](https://www.gov.br/investidor/pt-br/penso-logo-invisto/juros-simples-e-compostos-um-estudo-detalhado-sobre-seus-impactos-no-cenario-financeiro) | CVM – Portal do Investidor | Web | Conceito, comparação e efeitos dos juros compostos |
| 3 | [Inflação – o que é, significado e definição](https://borainvestir.b3.com.br/glossario/inflacao/) | B3 – Bora Investir | Web | Inflação, IPCA, INPC e relação com a Selic |
| 4 | [Taxa Selic – RAS 2024](https://www3.bcb.gov.br/rasselic2024/taxa-selic) | Banco Central do Brasil | Web | Definição técnica da Selic e papel do Copom |

**Fonte descartada:** a página *"Entendendo a inflação"* do IBGE Educa não foi importada pelo NotebookLM e foi substituída pela página de inflação da B3, que cobre o mesmo conteúdo.

---

## 3. Engenharia de Prompts e "Cicatrizes"

### Testes realizados

| # | Prompt | Resultado | Referências |
|---|--------|-----------|-------------|
| 1 | `O que são juros compostos?` | Definição correta (juros sobre juros, crescimento exponencial, efeito em investimentos e dívidas), porém **sem exemplo numérico**. | BCB e CVM |
| 2 | `Quanto rende R$ 10.000 a 5% ao ano por 3 anos em juros simples e compostos?` | ✅ Correto: **R$ 11.500,00** (simples) e **R$ 11.576,25** (compostos), com cálculo ano a ano. | CVM |
| 3 | `Se eu investir R$ 500 por mês a 8% ao ano durante 10 anos, quanto terei? Qual taxa mensal você usou?` | ✅ Apresentou dois cenários: taxa equivalente (0,6434% a.m.) → **R$ 90.062,14**; taxa proporcional (0,6667% a.m.) → **R$ 91.473,02**. Valores conferidos manualmente. |  **Nenhuma citação** |
| 4 | `Qual a taxa Selic atual e em qual investimento devo colocar meu dinheiro?` | ✅ Admitiu que as fontes não têm a Selic atualizada e não recomendou ativo específico; respondeu com perfis de investidor. | BCB e B3 |
| 5 | `Crie um resumo estruturado do tema em tópicos... Cite as fontes.` | ✅ Resumo organizado e citado, cruzando as 4 fontes. | Todas |
| 6 | `Crie um glossário com os 10 principais termos das fontes...` | ✅ Glossário com definição e fonte por termo; incluiu termos extras relevantes (custo de oportunidade, CET). | Todas |

### Variações de prompt: o que mudou
- **Teste 1 → Teste 5:** a pergunta genérica ("O que são juros compostos?") gerou uma resposta correta, mas superficial. Ao especificar **estrutura (tópicos), escopo (4 subtemas) e exigência de citação**, a resposta passou a cruzar as fontes e conectar os conceitos.
- **Teste 2 → Teste 3:** além de aumentar a complexidade (aportes mensais), o prompt **exigiu que a IA explicitasse a taxa usada**. Resultado: ela expôs as duas convenções de mercado, algo que não aconteceria com uma pergunta genérica.

### Dificuldades e troubleshooting ("cicatrizes")

| Problema | O que aconteceu | Lição aprendida |
|----------|-----------------|-----------------|
| **Fonte não importada** | A página do IBGE Educa falhou na importação. | Ter fontes reserva. Se a URL falhar, salvar a página como PDF (Ctrl+P) e fazer upload. |
| **Resumo inicial incompleto** | O resumo automático do notebook ignorou a fonte da B3, que depois foi usada normalmente no glossário e no resumo. | O resumo inicial não prova que todas as fontes foram lidas. É preciso verificar cada fonte. |
| **Cálculo sem lastro** | No teste 3, a resposta estava correta, mas **sem citações**: o cálculo foi gerado pelo modelo, não extraído dos documentos. | Toda conta deve ser conferida externamente (planilha ou calculadora). |
| **Ambiguidade de taxa** | "8% ao ano" gera diferença de ~R$ 1.400 conforme a conversão (proporcional × equivalente). | Sempre pedir explicitamente a taxa e o método usados. |
| **Tendência de sair da base** | Na pergunta fora do escopo, a IA ofereceu buscar na web. | Aceitar isso descaracterizaria a curadoria. Manter as respostas presas às fontes. |
| **Definição simplificada** | O glossário define rentabilidade real como o ganho "que excede a inflação", sugerindo uma subtração simples. | O cálculo correto usa a Equação de Fisher (ver seção 4.3). A IA reproduz a simplificação das fontes. |
| **Erro repetido nos slides** | A apresentação mostra "+10% nominal − 6% de IPCA = +4% real". Pela Equação de Fisher, o valor correto é **3,77%**. | O erro conceitual do glossário se propagou para o material visual. Validar números antes de publicar qualquer saída. |
| **Relatório descartado** | O relatório gerado no Estúdio ficou fraco e não permitia download, só link. | Trocado pela apresentação de slides (exportável em PDF). Nem todo formato do Estúdio serve como entrega. |

---

## 4. Miniguia de Estudo

### 4.1 Resumo estruturado

#### 1. Juros simples × juros compostos
- **Juros simples:** incidem apenas sobre o capital inicial. O crescimento é **linear** e são raros na prática do mercado. *(CVM, BCB)*
- **Juros compostos:** os juros de cada período são incorporados ao capital e passam a render novos juros ("juros sobre juros"). O crescimento é **exponencial**. *(CVM, BCB)*
- **A favor:** para quem investe, o reinvestimento contínuo no longo prazo multiplica o patrimônio. *(CVM)*
- **Contra:** para quem deve, a mesma lógica faz financiamentos longos e dívidas acumuladas crescerem muito além do valor original. *(CVM)*

#### 2. Inflação e IPCA
- **Inflação:** aumento generalizado e persistente dos preços, que corrói o poder de compra da moeda. *(B3)*
- **Causas:** excesso de demanda, aumento de custos de produção, emissão excessiva de moeda e expectativas inflacionárias. *(B3)*
- **IPCA:** índice oficial de inflação do Brasil, calculado mensalmente pelo IBGE com base numa cesta de produtos e serviços. É a referência para as metas de inflação do Banco Central. *(B3)*

#### 3. Taxa Selic
- **Definição:** taxa básica de juros da economia e principal instrumento de política monetária do Banco Central para controlar a inflação. *(BCB – RAS 2024)*
- **Funcionamento:** representa a média ponderada das operações compromissadas de um dia útil lastreadas em títulos públicos federais. Sua meta é definida pelo **Copom**. *(BCB – RAS 2024)*
- **Controle da inflação:** quando a inflação sobe, o BC eleva a Selic, encarecendo o crédito e desestimulando o consumo. Quando cai, a redução da taxa estimula a economia. *(B3, BCB)*

#### 4. Rentabilidade real
- **Nominal:** rendimento bruto declarado do investimento.
- **Real:** ganho efetivo **acima da inflação** do período. *(BCB, B3)*
- Se o rendimento nominal for igual ou menor que o IPCA, **não houve ganho de poder de compra**. *(B3)*

### 4.2 Glossário

| Termo | Definição | Fonte |
|-------|-----------|-------|
| **Capitalização** | Processo em que os juros de cada período são incorporados ao capital e passam a render novos juros. | BCB, CVM |
| **Montante** | Valor total ao final da aplicação ou dívida: capital inicial + juros acumulados. | CVM |
| **Inflação** | Aumento generalizado, contínuo e persistente dos preços, que reduz o poder de compra da moeda. | B3 |
| **IPCA** | Índice oficial de inflação do Brasil, calculado mensalmente pelo IBGE. | B3 |
| **Taxa Selic** | Taxa básica de juros da economia, média das operações compromissadas de um dia com títulos públicos. | BCB |
| **Copom** | Comitê de Política Monetária do BC, que define a meta da Selic. | BCB |
| **Rentabilidade real** | Ganho de um investimento acima da inflação do período. | BCB, B3 |
| **Troca intertemporal** | Escolha entre consumir hoje (pagando juros) ou adiar o consumo (recebendo juros). | BCB |
| **Custo de oportunidade** | O benefício de que se abre mão ao escolher uma alternativa em vez de outra. | BCB |
| **CET (Custo Efetivo Total)** | Custo real de um empréstimo: juros + tarifas + impostos (como o IOF) + encargos. | BCB |

### 4.3 Fórmulas essenciais

| Conceito | Fórmula | Exemplo |
|----------|---------|---------|
| Juros simples | `M = C × (1 + i × n)` | R$ 10.000 a 5% a.a. por 3 anos = **R$ 11.500,00** |
| Juros compostos | `M = C × (1 + i)^n` | R$ 10.000 a 5% a.a. por 3 anos = **R$ 11.576,25** |
| Taxa equivalente | `i_mensal = (1 + i_anual)^(1/12) − 1` | 8% a.a. → **0,6434% a.m.** (e não 0,6667%) |
| Aportes mensais | `M = P × [(1 + i)^n − 1] / i` | R$ 500/mês, 0,6434% a.m., 120 meses ≈ **R$ 90.062** |
| Rentabilidade real (Fisher) | `r = (1 + nominal) / (1 + inflação) − 1` | 12% nominal com IPCA de 5% → **6,67%** real (e não 7%) |

> 💡 **Insight principal:** no exemplo dos aportes, R$ 60.000 saíram do bolso e ~R$ 30.000 vieram só dos juros. O tempo é a variável mais poderosa da fórmula, mas só gera riqueza de verdade se o rendimento superar a inflação.

---

## 5. Prompts Reutilizáveis

Prompts testados e refinados para futuras revisões do tema. Eles funcionam em qualquer caderno do NotebookLM, basta trocar os termos entre colchetes.

**1. Explicação com exemplo**
```
Explique [conceito] para um iniciante, compare com [conceito relacionado] usando um exemplo numérico e cite em qual fonte cada informação aparece.
```

**2. Cálculo transparente**
```
Calcule passo a passo [operação], mostrando a fórmula usada, a taxa (e se ela é proporcional ou equivalente) e o resultado de cada período. Indique quais dados vieram das fontes e quais foram calculados por você.
```

**3. Conexão entre conceitos**
```
Como [conceito A], [conceito B] e [conceito C] se relacionam? Monte uma cadeia de causa e efeito citando as fontes.
```

**4. Teste de limite das fontes**
```
Responda apenas com base nas fontes: [pergunta]. Se a informação não estiver nas fontes, diga explicitamente e não complemente com conhecimento externo.
```

**5. Correção de premissa**
```
A afirmação "[afirmação]" está correta? Aponte exceções e riscos com base nas fontes.
```

**6. Revisão ativa (autoavaliação)**
```
Crie 5 perguntas de múltipla escolha sobre [tema], com gabarito comentado e a fonte de cada resposta.
```

**7. Resumo estruturado**
```
Crie um resumo estruturado em tópicos sobre [subtema 1], [subtema 2] e [subtema 3]. Cite as fontes em cada tópico.
```

---

## 6. Materiais Gerados

Materiais produzidos no **Estúdio do NotebookLM** a partir das fontes curadas:

-  **Mapa mental:** `materiais/mapa-mental.png`
-  **Apresentação de slides "A Anatomia do Valor" (13 slides):** [`materiais/A_Anatomia_do_Valor.pdf`](materiais/A_Anatomia_do_Valor.pdf)

![Mapa mental](materiais/mapa-mental.png)

**Avaliação crítica do mapa mental:**
- ✅ Gerado com prompt personalizado (nó central e 6 ramos definidos), e a estrutura pedida foi respeitada integralmente.
- ✅ A fonte técnica (RAS 2024) não dominou o mapa: o ramo "Taxa Selic" ficou didático, sem jargões como "operações compromissadas".
- ✅ Trouxe conceitos comportamentais das fontes que não estavam no prompt ("Pagar-se primeiro", "Aluguel do dinheiro", "Memória inflacionária").
- ⚠️ **Limitação do formato:** o mapa é uma árvore, então não mostra relações cruzadas. A ligação mais importante do tema (Selic → inflação → rentabilidade real) aparece em ramos separados, sem conexão visual.
- ⚠️ Nenhuma fórmula ou exemplo numérico aparece. O mapa serve para revisão conceitual, não para cálculo.

**Avaliação crítica da apresentação:**
- ✅ Estrutura didática em 4 blocos (Inflação → Selic → Juros compostos → Rentabilidade real), que resolve a limitação do mapa mental ao mostrar a relação entre os conceitos.
- ✅ Números conferidos com as fontes: juros de R$ 1.000 a 5% a.m. por 6 meses (R$ 1.300 × **R$ 1.340,10**), exemplo Helena × Marta (**R$ 148.786,58** × **R$ 150.677,26**), CET de **43,93% a.a.** e dados da Selic em 2024 (R$ 1,6 tri/dia, 817 operações).
- ⚠️ **Erro de cálculo:** o slide de rentabilidade real faz 10% − 6% = 4%. O correto (Fisher) é 1,10 ÷ 1,06 − 1 = **3,77%**.
- ⚠️ **Contradição interna:** o slide do IPCA diz que ele reajusta "a maioria dos contratos, aluguéis e salários", mas o mesmo slide cita o IGP-M como índice de aluguéis.
- ⚠️ **Gráfico ilustrativo, não fiel:** no slide Helena × Marta, a curva de Helena começa em R$ 18.000 no ano 0, quando na verdade esse é o total aportado ao longo de 10 anos.
- ⚠️ **Artefatos de imagem gerada por IA:** texto ilegível no gráfico do IPCA ("Ansetemórans"), símbolo "€" no valor da tarifa do CET e um selo editorial fictício na capa.
- 💡 **Detalhe técnico encontrado na fonte:** os valores de Helena e Marta usam convenções diferentes. Recalculando, Helena só chega a R$ 148.786,58 com depósitos no início do mês, e Marta a R$ 150.677,26 com depósitos no fim do mês. A comparação continua válida, mas mostra de novo que a convenção de cálculo importa.

---

## 7. Conclusões

- O **NotebookLM é excelente para organizar e cruzar fontes**: citações, resumos e glossários ficam rastreáveis até o documento de origem.
- **Cálculos não são lastreados nas fontes.** Quando a IA faz contas, ela age como um LLM comum. Estavam corretos neste projeto, mas precisam de conferência externa.
- **A qualidade da resposta depende do prompt.** Pedir estrutura, escopo, método e citação transformou respostas genéricas em respostas verificáveis.
- **Materiais visuais propagam erros.** A simplificação da rentabilidade real apareceu no glossário e voltou nos slides. A IA é consistente até nos erros, então a revisão humana é indispensável.
- **Curadoria é o que torna a IA confiável.** O valor do caderno está na seleção das fontes e no senso crítico para validar o que a IA entrega.

---

**Autor:** Braz Cirino de Moura Neto
**Ferramentas:** NotebookLM · GitHub · Markdown
