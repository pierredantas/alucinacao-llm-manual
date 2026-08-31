# 05 · Duas propostas de pesquisa

## Escopo e fronteiras

Alucinação em LLMs de Defesa pode ser atacada por dois programas de pesquisa distintos, com métricas, entregáveis e critérios de sucesso próprios. Nenhum dos dois é substituto do outro: [Reliable vs. Trustworthy](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca) marcam eixos ortogonais, e um LLM pode ser robusto sem ser confiável.

## Proposta A — AI Robusta (reliable)

Engenharia de confiabilidade técnica: prova formal e mensurável de que o sistema opera dentro de limites de falha especificados.

- **Padrões quantificáveis** — a característica *reliability* de [ISO/IEC TS 5723:2022](https://www.iso.org/standard/81608.html), "habilidade de um item operar conforme requerido, sem falhas, por um intervalo de tempo dado, sob condições determinadas": limites formais para MTBF, PFD e taxa de erro sob desvio de distribuição.
- **Verificação em runtime & guardrails** — módulos watchdog determinísticos, monitorando ativação latente antes da atuação física.
- **Incerteza calibrada & abstenção segura** — predição conforme e entropia semântica, para recusa segura ao romper limites de confiança.
- **Benchmarks reprodutíveis** — taxa de alucinação e consistência factual medidas contra corpora fechados, no padrão do [índice Vectara/HF](04-benchmarks.md#indice-de-alucinacao-dos-modelos-vectara-hf).

!!! tip "Critério de sucesso"
    Um número, com intervalo de confiança, que não muda de significado entre laboratórios: MTBF, PFD, taxa de alucinação por benchmark fechado.

## Proposta B — AI Confiável (trustworthy)

Engenharia sociotécnica: o sistema opera dentro de um conjunto mais amplo de expectativas de stakeholders, das quais *reliability* é apenas uma.

- **Sete características do [NIST AI RMF](https://airc.nist.gov/airmf-resources/airmf/3-sec-characteristics/)** — válido e confiável (*valid and reliable*), seguro, seguro e resiliente, responsável e transparente, explicável e interpretável, com privacidade reforçada, e justo com viés controlado. *Valid and reliable* é a linha de base; as outras seis não têm equivalente formal único.
- **Explicabilidade operacional** — mecanismos que expõem *como* uma decisão foi produzida e *por que* faz sentido no contexto tático, não apenas um escore de confiança.
- **Responsabilização (accountability)** — cadeia auditável de decisão, de custódia dos dados e de intervenção humana, exigida por doutrina de C2.
- **Gestão de viés e equidade** — quando aplicável a classificação de alvos ou priorização, viés sistemático é um risco de trustworthiness distinto de erro aleatório.

!!! tip "Critério de sucesso"
    Conformidade documentada e auditável a um framework de governança (NIST AI RMF, ISO/IEC 42001), verificada por avaliação de terceiros: não redutível a um único número.

## Onde as duas propostas se cruzam

| | Proposta A — Robusta | Proposta B — Confiável |
|---|---|---|
| Pergunta central | O sistema falha dentro do limite especificado? | O sistema atende às expectativas legítimas dos stakeholders? |
| Evidência | Métrica quantitativa, reproduzível | Auditoria, documentação, avaliação multi-stakeholder |
| Cobre calibração de incerteza? | Sim — é o núcleo da proposta | Sim, mas como uma entre sete características |
| Cobre explicabilidade e viés? | Não | Sim |
| Insuficiente sozinha porque | Alta acurácia com calibração nula ainda passa nas métricas ([ver gap SISFRON](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca)) | Conformidade documental não impede falha física se a base de reliability não estiver provada |

!!! danger "As duas propostas não substituem uma a outra"
    Um LLM pode ser certificado A (reliable) e falhar em B (trustworthy) se não expõe por que decidiu algo. Pode ser certificado B e falhar em A se a documentação de governança não é lastreada em prova formal de MTBF/PFD. Para IA de Defesa, ambas as propostas são necessárias; nenhuma das duas, isoladamente, é suficiente.
