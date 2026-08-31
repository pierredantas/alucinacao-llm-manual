# Glossário

Termos e siglas técnicas usados no manual, com a definição no sentido em que aparecem aqui e um link de volta para o capítulo de origem. Cresce junto com os capítulos: por ora cobre os termos introduzidos no [01 · Conceitos fundamentais](01-conceitos.md).

**Alucinação (extrínseca)**
: Alegação introduzida pelo modelo que é inverificável contra os dados de origem, por não estar presente neles nem contradizê-los diretamente. Ver [Taxonomia estrutural](01-conceitos.md#taxonomia-estrutural).

**Alucinação (factualidade)**
: Geração confiante de um fato falso sobre o mundo, por erro de memória paramétrica do modelo, não por desvio em relação a um documento de referência. Ver [Taxonomia estrutural](01-conceitos.md#taxonomia-estrutural).

**Alucinação (intrínseca)**
: Resposta do modelo que contradiz diretamente o material de referência fornecido no prompt ou no contexto. Ver [Taxonomia estrutural](01-conceitos.md#taxonomia-estrutural).

**C2**
: Comando e Controle (*Command and Control*). Cadeia de decisão militar que recebe a saída de um modelo de IA como insumo tático; o ponto onde uma alucinação silenciosa se converte em decisão operacional errada. Ver [Confiabilidade vs. dignidade de confiança](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca).

**Calibração**
: Propriedade de um modelo cuja confiança relatada corresponde à probabilidade real de acerto. Um modelo calibrado que erra 2% das vezes relata incerteza alta exatamente nesses casos, em vez de responder com a mesma confiança que usa quando acerta. Ver [Calibração e incerteza epistêmica](01-conceitos.md#calibracao-e-incerteza-epistemica).

**Confabulação**
: Subtipo específico de alucinação, definido por Farquhar et al. (2024) como geração arbitrária e incorreta. É o alvo específico do detector por entropia semântica, não sinônimo de toda alucinação. Ver [Calibração e incerteza epistêmica](01-conceitos.md#calibracao-e-incerteza-epistemica).

**Diagonalização**
: Técnica de prova da teoria da computabilidade usada para mostrar que uma função não pode ser computada por nenhum algoritmo de uma classe dada. Base do argumento de Xu, Jain & Kankanhalli (2024) de que nenhum LLM pode aprender todas as funções computáveis. Ver [Por que os LLMs alucinam](01-conceitos.md#por-que-os-llms-alucinam).

**Entropia semântica**
: Medida de incerteza que agrupa gerações de um modelo por equivalência de significado, não por forma textual, antes de calcular a entropia. Evita que paráfrases da mesma resposta correta sejam contadas como incerteza. Introduzida por Kuhn, Gal & Farquhar (ICLR 2023). Ver [Calibração e incerteza epistêmica](01-conceitos.md#calibracao-e-incerteza-epistemica).

**Estimador de Good-Turing**
: Método estatístico clássico para estimar a probabilidade de eventos raros ou nunca observados, a partir da frequência de eventos observados uma única vez em uma amostra. Kalai & Vempala (2024) o usam para derivar uma cota inferior formal na taxa de alucinação de qualquer modelo bem calibrado, sobre fatos arbitrários pouco frequentes no treino. Ver [Calibração e incerteza epistêmica](01-conceitos.md#calibracao-e-incerteza-epistemica).

**ISO/IEC TS 5723**
: Especificação técnica internacional de vocabulário de *trustworthiness* (dignidade de confiança), publicada em 2022. Define *reliability* como uma entre várias características de trustworthiness, não como sinônimo dela. Ver [Confiabilidade vs. dignidade de confiança](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca).

**LLM**
: Modelo de linguagem de grande escala (*Large Language Model*). Modelo estatístico treinado para prever a próxima unidade de texto em uma sequência, usado como base dos sistemas de geração de linguagem discutidos no manual. Ver [O que é alucinação em LLMs?](01-conceitos.md#o-que-e-alucinacao-em-llms).

**MTBF**
: Tempo médio entre falhas (*Mean Time Between Failures*). Métrica de engenharia de confiabilidade tradicional, usada como um dos componentes formais da característica *reliable*. Ver [Confiabilidade vs. dignidade de confiança](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca).

**NIST AI RMF**
: *AI Risk Management Framework* do National Institute of Standards and Technology dos EUA. Define *trustworthy* por sete características centrais (válido e confiável, seguro, seguro e resiliente, responsável e transparente, explicável e interpretável, com privacidade reforçada, e justo com viés controlado). Ver [Confiabilidade vs. dignidade de confiança](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca).

**PFD**
: Probabilidade de falha sob demanda (*Probability of Failure on Demand*). Métrica de confiabilidade usada em sistemas de segurança crítica para medir a chance de falha no momento em que a atuação é exigida. Ver [Confiabilidade vs. dignidade de confiança](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca).

**Reliable**
: Habilidade de um item operar conforme requerido, sem falhas, por um intervalo de tempo dado, sob condições determinadas, conforme ISO/IEC TS 5723. Necessária, mas não suficiente, para um sistema ser *trustworthy*. Ver [Confiabilidade vs. dignidade de confiança](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca).

**SISFRON**
: Sistema Integrado de Monitoramento de Fronteiras do Exército Brasileiro. Usado no manual como exemplo concreto de sistema de fusão de sensores cuja acurácia cai sob dossel amazônico denso, ilustrando o risco de alucinação sem calibração de incerteza. Ver [Gap observado — SISFRON](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca).

**Trustworthy**
: Sistema sociotécnico multidimensional cuja confiança geral é tão forte quanto sua característica mais fraca entre um conjunto de dimensões (as sete do NIST AI RMF). Ver [Confiabilidade vs. dignidade de confiança](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca).
