# 03 · Detecção & mitigação

Cinco métodos principais de detecção, e três famílias de estratégias de mitigação testadas na literatura recente.

## Métodos de detecção

| Método | Veículo | Mecanismo central |
|---|---|---|
| [SelfCheckGPT (Manakul et al.)](https://aclanthology.org/2023.emnlp-main.557/) | EMNLP 2023 | Amostragem estocástica black-box; consistência semântica cruzada sem fonte externa. |
| [Auto-Contradição (Mündler et al.)](https://arxiv.org/abs/2305.15852) | ICLR 2024 | Detecta contradições lógicas dentro de uma única resposta; supera checagens multi-prompt. |
| [LLM-Check (Sriramanan et al.)](https://openreview.net/forum?id=LYx4w3CAgy) | NeurIPS 2024 | Investiga o gap entre métodos de detecção e eficácia de mitigação em runtime. |
| [Detecção Multimodal (Chakraborty et al.)](https://doi.org/10.1145/3716846) | ACM CSUR 2025 | Estende a detecção a agentes decisores autônomos e modelos visão-linguagem. |
| [TECP (Xu & Lu)](https://doi.org/10.3390/math13203351) | Mathematics 2025 | Entropia a nível de token + predição conforme, com garantias formais de cobertura. |

## Estratégias de mitigação

### 1. Decodificação controlada

[DoLa](https://arxiv.org/abs/2309.03883) & [CAD](https://arxiv.org/abs/2305.14739) — contraste entre camadas iniciais/finais, ou com/sem contexto. +12–17% de acurácia factual, sem retreinamento.

### 2. Ciclos de auto-refinamento

[Self-Refine](https://arxiv.org/abs/2303.17651) & [Reflexion](https://arxiv.org/abs/2303.11366) — o LLM atua como gerador e crítico, via reforço verbal e memória de execução.

### 3. Verificação em múltiplas etapas

[CoVe](https://arxiv.org/abs/2309.11495) & [RARR](https://arxiv.org/abs/2210.08726) — cadeia de verificação e revisão aumentada por recuperação, elaborando perguntas de checagem contra fontes externas antes da resposta final.
