# Checkpoint 5: Análise Econômica com Modelos Computacionais

### Visão Geral do Projeto

Este projeto explora a aplicação de diferentes técnicas computacionais para modelar e estimar indicadores econômicos sob condições de incerteza. Através de três exercícios progressivamente mais complexos, comparamos métodos estocásticos (baseados em aleatoriedade) com abordagens determinísticas (baseadas em cenários discretos) para projetar o Produto Interno Bruto (PIB) e a Balança de Pagamentos.

O objetivo principal é entender as vantagens, desvantagens e a aplicabilidade de cada método, conectando a teoria da ciência da computação com a prática da modelagem econômica.

### Estrutura do Notebook

O notebook está organizado em três seções principais, cada uma correspondendo a um exercício:

* **Exercício 1:** Estima o crescimento do PIB no curto prazo (1 ano) usando Simulação de Monte Carlo e o algoritmo de Divisão e Conquista.
* **Exercício 2:** Estima a distribuição da Balança de Pagamentos, cujos componentes (exportações e importações) seguem distribuições normais, usando Monte Carlo e Programação Dinâmica (Bottom-Up).
* **Exercício 3:** Projeta cenários de longo prazo (10 anos) para o PIB (com crescimento composto) e para a Balança de Pagamentos acumulada, comparando Monte Carlo com uma abordagem de "Brute Force" por particionamento de tempo.

### Metodologia e Conceitos Aplicados

Ao longo dos exercícios, foram aplicados os seguintes conceitos e técnicas:

* **Simulação de Monte Carlo:** Principal método estocástico utilizado, servindo como benchmark nos três exercícios. Baseia-se na Lei dos Grandes Números, onde um grande volume de simulações aleatórias converge para o resultado real esperado. É uma ferramenta extremamente poderosa para modelar sistemas complexos e com múltiplas fontes de incerteza.

* **Abordagens Determinísticas (Baseadas em Cenários):** Em contraste com o Monte Carlo, estas técnicas aproximam problemas contínuos ao dividi-los em um número finito de cenários discretos.
    * **Divisão e Conquista (Ex. 1):** Abordagem sistemática que "amostra" um intervalo de possibilidades de forma uniforme. Mostrou-se perfeitamente preciso para problemas simples e simétricos.
    * **Programação Dinâmica (Bottom-Up) (Ex. 2):** Técnica onde a solução final é construída a partir da combinação de soluções de subproblemas. No nosso caso, discretizamos as distribuições de exportação e importação em cenários baseados em quartis e combinamos todos eles para formar a distribuição final.
    * **"Brute Force" Particionado (Ex. 3):** Uma abordagem combinatória onde o horizonte de tempo foi dividido, e os resultados da primeira metade foram sistematicamente recombinados com os cenários da segunda metade, criando uma árvore de possibilidades.

* **Qualidade de Software:** O código foi desenvolvido seguindo boas práticas, incluindo a modularização em funções, o uso de um decorator (`@time_it`) para análise de performance, e comentários claros para explicar a lógica de cada etapa.

### Resumo dos Exercícios e Conclusões

#### Exercício 1: Crescimento do PIB (Curto Prazo)
**Conclusão:** Para estimar a média de uma variável com distribuição uniforme simples, o método determinístico de **Divisão e Conquista** foi superior, alcançando o resultado exato devido à simetria do problema. O Monte Carlo forneceu uma excelente aproximação, validando sua eficácia.

#### Exercício 2: Balança de Pagamentos
**Conclusão:** Ambos os métodos, **Monte Carlo** e **Programação Dinâmica**, foram notavelmente precisos, com seus resultados (média e desvio padrão) muito próximos dos valores teóricos. Isso demonstrou que mesmo uma aproximação discreta com poucos cenários (16 no total para a PD) pode ser surpreendentemente eficaz para estimar os momentos centrais de uma distribuição.

#### Exercício 3: Cenários de Longo Prazo (10 Anos)
**Conclusão:** A força do **Monte Carlo** torna-se evidente em problemas de longo prazo e dependentes de trajetória (como o crescimento composto do PIB). Ele gera uma distribuição de resultados suave e realista. A abordagem "Brute Force" discreta capturou bem a média, mas subestimou a variância (o risco), pois seu número limitado de cenários não conseguiu representar os eventos mais extremos (de cauda) da distribuição.

### Conclusão Geral do Projeto

Este projeto destaca um trade-off fundamental na modelagem computacional:

* **Métodos Estocásticos (Monte Carlo):** Excelentes para problemas complexos, com muitas variáveis ou dependência temporal. Fornecem uma visão realista da distribuição completa dos resultados, incluindo riscos de cauda. Sua precisão aumenta com o número de simulações.
* **Métodos Determinísticos/Discretos:** Podem ser muito eficientes e, por vezes, mais precisos para problemas simples e bem-comportados. No entanto, são uma *aproximação* da realidade e podem ter dificuldade em capturar toda a gama de possibilidades, potencialmente subestimando a variância e o risco.

A escolha do método ideal depende, portanto, da complexidade do problema e dos objetivos da análise.

### Como Executar o Notebook

As células de código neste notebook foram projetadas para serem executadas em sequência. Cada exercício contém as importações de biblioteca necessárias no início de seu bloco de código para garantir que possa ser executado de forma independente, sem depender da execução de células de exercícios anteriores.
