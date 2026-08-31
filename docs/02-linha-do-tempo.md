# 02 · Linha do tempo da literatura

## Da alerta teórica à taxonomia madura

Cinco artigos pré-LLM estabeleceram o vocabulário do problema; de 2021 a 2026 ele evoluiu para taxonomia canônica, benchmarks e frameworks de autocorreção.

## Artigos fundacionais (era pré-LLM)

| Artigo | Veículo / ano | Contribuição |
|---|---|---|
| [Wiseman et al.](https://aclanthology.org/D17-1239/) | EMNLP 2017 | Divergências estruturais e erros de seleção de conteúdo em geração neural baseada em dados. |
| [Dusek et al.](https://arxiv.org/abs/1810.01170) | E2E NLG 2018 | Avaliação comparativa de erros semânticos e atributos alucinados a partir de dados estruturados. |
| [Maynez et al.](https://aclanthology.org/2020.acl-main.173/) | ACL 2020 | Métricas formais de fidelidade e factualidade, antes de "alucinação" virar termo padrão. |
| [Bender et al.](https://doi.org/10.1145/3442188.3445922) | FAccT 2021 | "Stochastic Parrots" — alerta ético-técnico pioneiro sobre texto plausível sem ancoragem. |
| [Abnar & Zuidema](https://aclanthology.org/2020.acl-main.385/) | ACL 2020 | "Attention rollout/flow" — base metodológica para atribuição via mapas de atenção. |

## Linha do tempo — alertas às soluções

**2021 — [Bender et al. (FAccT)](https://doi.org/10.1145/3442188.3445922)**
Primeiro grande alerta ético e técnico sobre geração desancorada em modelos de grande escala.

**2023 — [Ji et al. (ACM CSUR)](https://doi.org/10.1145/3571730) & [SelfCheckGPT](https://aclanthology.org/2023.emnlp-main.557/)**
Taxonomia canônica intrínseca/extrínseca e método seminal de amostragem black-box zero-resource.

**2024 — [Mündler et al.](https://arxiv.org/abs/2305.15852) & [RAGTruth (ACL)](https://arxiv.org/abs/2401.00396)**
Detecção de auto-contradição lógica interna e primeiro corpus de referência para alucinações em RAG.

**2025 — [Woesle et al.](https://doi.org/10.1109/ACCESS.2025.3601206) & [Malin et al.](https://doi.org/10.1109/JSTSP.2025.3579203)**
Revisão sistemática PRISMA (IEEE Access) e análise de métricas de fidelidade (IEEE JSTSP).

**2026 — [Naser (Springer)](https://doi.org/10.1007/s10579-026-09938-4) & [Pulkundwar et al. (arXiv)](https://arxiv.org/abs/2512.02527)**
Síntese recente sobre definições, causas e mitigação, com novos datasets e autocorreção generativa.

## De taxonomia empírica a definição formal

A literatura sobre alucinação em LLMs passa por uma virada estrutural entre 2023 e 2026: de catalogar o fenômeno empiricamente para tentar defini-lo formalmente.

**2023 — a era da taxonomia.** [Ji et al. (ACM CSUR)](https://doi.org/10.1145/3571730) e [Zhang et al., "Siren's Song in the AI Ocean" (arXiv 2309.01219)](https://doi.org/10.48550/arXiv.2309.01219), publicado poucos meses depois, consolidam causas, métodos de detecção e estratégias de mitigação em taxonomias abrangentes. O objetivo é organizar um campo emergente e disperso, não explicar por que a alucinação é estruturalmente difícil de eliminar.

**2024–2025 — a virada causal.** Os trabalhos que fundamentam [Por que os LLMs alucinam](01-conceitos.md#por-que-os-llms-alucinam) aparecem nesta janela: [Kalai & Vempala (STOC 2024)](https://doi.org/10.1145/3618260.3649777) provam uma cota formal de calibração, e [Xu, Jain & Kankanhalli (2024)](https://doi.org/10.48550/ARXIV.2401.11817) formalizam um argumento de inevitabilidade via teoria da computabilidade. A pergunta muda de "quais tipos de alucinação existem" para "por que a alucinação é, em algum grau, matematicamente inevitável".

**2026 — definição estrutural.** [Yi (IEEE Access)](https://doi.org/10.1109/ACCESS.2026.3707249) rejeita explicitamente o enquadramento de "deficiência de conhecimento" ou "falha de alinhamento" das taxonomias de 2023, e propõe uma definição estrutural formal de alucinação como falha de fechamento em um espaço de coordenadas semânticas, com um "FIP Gate" em tempo de inferência como mitigação proposta.

!!! tip "Por que essa virada importa para a Defesa"
    Uma taxonomia diz o que observar. Uma definição formal diz o que é matematicamente possível evitar, e o que não é. Para certificação de IA militar, a segunda pergunta é a que importa: nenhum processo de V&V consegue provar a ausência de um fenômeno que a literatura já demonstrou ser, em parte, formalmente inevitável.

## Revisões sistemáticas e taxonomias principais

!!! info "Ji et al., 2023 — ACM CSUR · 2.000+ citações"
    Pesquisa canônica que estabeleceu a taxonomia base intrínseca/extrínseca para tarefas de PLN.

!!! info "Woesle et al., 2025 — IEEE Access · Revisão PRISMA"
    Primeira revisão sistemática empregando metodologia formal PRISMA para categorizar detecção e mitigação.

!!! info "Naser, 2026 — Springer LRE · Estado da arte"
    Síntese recente consolidando datasets de teste, ferramentas de verificação black-box e autocorreção iterativa.
