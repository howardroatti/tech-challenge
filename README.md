## Tech Challenge - Desafio Técnico (Detecção de Fraude Financeira)
<hr>
<br>
<br>

### Objetivo do Projeto: desenvolver uma solução em Machine Learning para predizer se uma transação financeira é ou não é Fraudulenta
<hr>
<br>
<br>

## Hipótese
Um modelo de aprendizagem de máquina que utiliza técnicas de classificação, poderia ser treinado com um conjunto de dados históricos de transações financeiras rotuladas como "Fraude" ou "Não Fraude". Com base nesses dados, o modelo seria capaz de identificar padrões ou características nas transações que indicam se uma transação é fraudulenta ou não.

Para avaliar a eficácia do modelo, poderíamos medir sua precisão, recall e F1-score em um conjunto de dados de teste. Se o modelo se sair bem nesses testes, poderíamos implantá-lo em tempo real para monitorar transações em andamento e alertar os usuários sobre transações suspeitas.

Ainda podemos usar um modelo de decisão de negócios para determinar se as transações suspeitas devem ser bloqueadas ou não. Por exemplo, podemos ponderar o custo de bloquear uma transação legítima (25% de lucro perdido) versus permitir uma transação fraudulenta (100% de perda), a fim de tomar uma decisão de negócios informada.

Esta é apenas uma hipótese e o modelo real pode precisar de ajustes adicionais com base em uma análise mais detalhada dos dados e necessidades de negócios específicas.

As métricas de recall, F1-score, sensibilidade e precisão são medidas comumente utilizadas para avaliar a performance de modelos de classificação em problemas de detecção de fraudes. No entanto, essas métricas não são diretamente relacionadas ao lucro ou perda financeira.

Para utilizar essas métricas para calcular o lucro ou perda financeira, é necessário estabelecer uma relação entre as previsões do modelo (transações rotuladas como "fraude" ou "não fraude") e os resultados reais (se a transação é realmente fraudulenta ou não).

Supondo que cada transação não fraudulenta tem um lucro de 25% e cada transação fraudulenta tem uma perda de 100%, podemos utilizar as seguintes definições:

    - Verdadeiro Positivo (VP): transação classificada como fraude que é realmente fraudulenta. Nesse caso, a perda seria de 100%.
    - Falso Positivo (FP): transação classificada como fraude que não é realmente fraudulenta. Nesse caso, não há perda ou lucro.
    - Verdadeiro Negativo (VN): transação classificada como não fraude que é realmente não fraudulenta. Nesse caso, o lucro seria de 25%.
    - Falso Negativo (FN): transação classificada como não fraude que é realmente fraudulenta. Nesse caso, há uma perda de 100%.

Com base nessas definições, podemos calcular as seguintes métricas:

    - Recall: proporção de transações fraudulenta que foram corretamente identificadas pelo modelo. O recall é dado por VP / (VP + FN). Quanto maior o recall, menor será a quantidade de fraudes não detectadas, reduzindo a perda.
    - Precisão: proporção de transações classificadas como fraude que são realmente fraudulentas. A precisão é dada por VP / (VP + FP). Quanto maior a precisão, menor será o número de transações legítimas bloqueadas, evitando perdas desnecessárias.
    - F1-score: média harmônica entre recall e precisão, que considera tanto a capacidade de detectar fraudes quanto a precisão das classificações. O F1-score é dado por 2 x (precisão x recall) / (precisão + recall).
    - Sensibilidade: proporção de transações legítimas que foram corretamente identificadas pelo modelo. A sensibilidade é dada por VN / (VN + FP). Quanto maior a sensibilidade, maior será a quantidade de transações legítimas não bloqueadas, gerando mais lucro.

Essas métricas podem ser usadas para avaliar a eficácia do modelo de detecção de fraudes em termos de lucro e perda. No entanto, é importante lembrar que outros fatores, como o custo de bloquear uma transação legítima ou a gravidade das consequências de uma fraude não detectada, também devem ser considerados na tomada de decisões de negócios.
<hr>
<br>
<br>

## Desenvolvimento
O projeto foi desenvolvido utilizando um conjunto de dados disponibilizado pelo Mercado Livre, proveniente do sistema de prevenção de fraudes.
<hr>

O repositório está organizado da seguinte forma:
- [Datasets](Datasets/): diretório com o dataset disponibilizado e o dataset gerado pelos experimentos
- [Documentos](Documentos/): documentos gerados durante os experimentos
- [Notebook](Notebook/): contém o notebook utilizado para criar o pipeline do experimento
<hr>

Para o desenvolvimento do projeto, foram criadas funções reutilizáveis para auxílio nas análises, previsões, métricas e comparações.

Todo o restante desenvolvimento e das análises está descrito no [Notebook](Notebook/MeLi-Technical_Challenge.ipynb).
<hr>
<br>
<br>

## Execução
Antes de executar o notebook, certifique-se de ter feito uma cópia do repositório, bem como a instalação dos pacotes descritos em [requirements.txt](requirements.txt). Feito isso, basta reexecutar o notebook para que os resultados sejam gerados conforme os experimentos feitos, que levaram as avaliações e conclusão.
<hr>
<br>
<br>

## Conclusão
Com o pipeline construído, foram efetuados 30 experimentos. Desses, dois modelos se destacaram, aparecendo na seleção final. São eles: LGBM, Oversampling Missing e XGBoost, Oversampling Missing.

De acordo com os dados obtidos, ambos tem a possibilidade de maximizar os lucros (ou mitigar as perdas), detectando corretamente uma média de ~85% de transações bloqueadas corretamente, com AUC de ~82%.

Foi possível perceber que o LGBM, Oversampling Missing é mais consistente do que o XGBoost, Oversampling Missing, visto que em todas as trinta execuções foram obtidas as mesmas métricas. Dessa forma, a sugestão de implementação seria do modelo LGBM com aplicação da estratégia de balanceamento de classes Oversampling.

<br>
<br>

## Contato
Esse projeto foi desenvolvido por: __Howard Roatti__

E-Mail: howardcruzroatti@gmail.com
<hr>