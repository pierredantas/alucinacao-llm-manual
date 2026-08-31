# 01 · Conceitos fundamentais

## O que é alucinação em LLMs?

A base conceitual antes de qualquer discussão de risco ou mitigação: o que conta como alucinação, e por que "confiável" não é o mesmo que "digno de confiança".

## Definição canônica

!!! info "Ji et al., ACM Computing Surveys, 2023"
    Conteúdo gerado que é sem sentido, infiel ou factualmente incorreto em relação ao contexto de origem ou à verdade do mundo real.

    [DOI: 10.1145/3571730](https://doi.org/10.1145/3571730)

## Taxonomia estrutural

=== "Intrínseca"
    A resposta contradiz diretamente o material de referência.

    Ex.: inversão de coordenadas de radar do SISFRON.

=== "Extrínseca"
    A resposta introduz alegações inverificáveis, ausentes nos dados.

    Ex.: fabricar números de série de mísseis.

=== "Factualidade"
    Geração confiante de fatos falsos sobre o mundo, por erro de memória paramétrica.

## Confiabilidade vs. dignidade de confiança

| | Reliable — ISO/IEC TS 5723 · NIST §3.1 | Trustworthy — 7 pilares do NIST AI RMF |
|---|---|---|
| Definição | Habilidade de um item operar conforme requerido, sem falhas, por um intervalo de tempo dado, sob condições determinadas. | Sistema sócio-técnico multidimensional, que exige equilíbrio entre sete características centrais. |
| Base | Acurácia, MTBF, generalização, PFD. Necessária, mas não suficiente. | Axioma central: a confiança é tão forte quanto sua característica mais fraca. |

!!! danger "Gap observado — SISFRON"
    Modelos de fusão de sensores atingem alta acurácia no Cerrado aberto, mas falham sob dossel denso amazônico com chuva. Sem calibração de incerteza, alvos alucinados quebram a transparência e a segurança, invalidando o C2 militar.

## Robusto vs. confiável

> "Um LLM pode ser robusto, mas não confiável, se não avisa quando está supondo."

| Sem calibração | Com calibração |
|---|---|
| Um modelo responde 100 consultas táticas com 98 acertos. Nas 2 erradas, emite parecer com 100% de certeza — alta acurácia, calibração nula, risco silencioso. | Em um pipeline de C2, o modelo recusa responder quando sua confiança cai abaixo de um limiar, convertendo alucinações silenciosas em falhas visíveis e auditáveis. |

!!! tip "Conclusão para o IME"
    Um LLM militar com 99% de acurácia que nunca sinaliza incerteza é um passivo tático. Calibração, quantificar a própria ignorância, é a chave da confiabilidade operacional.
