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

## Detecção não é mitigação, e mitigação tem custo

A tabela de métodos de detecção acima mede se um método identifica uma alucinação já gerada. Nenhuma delas, sozinha, impede a geração. [LLM-Check (Sriramanan et al.)](https://openreview.net/forum?id=LYx4w3CAgy) documenta esse gap diretamente: detectar com precisão não implica ter uma rota barata de correção em tempo real, os dois problemas têm restrições computacionais diferentes.

Mitigar tampouco é de graça. [Mahmoud, Khalil, Semage, Karimpanal & Rana (Findings ACL: EACL 2026)](https://aclanthology.org/2026.findings-eacl.53/) mostram, empiricamente, que técnicas que aumentam a veracidade factual de um LLM frequentemente enfraquecem o comportamento de recusa de segurança do mesmo modelo. A causa apontada pelos autores é sobreposição nos componentes internos que codificam informação de alucinação e de recusa: ajustar um afeta o outro.

!!! danger "A pergunta certa não é 'qual método detecta melhor'"
    É: qual combinação de detecção, mitigação e abstenção calibrada ([capítulo 01](01-conceitos.md#calibracao-e-incerteza-epistemica)) cabe no orçamento de latência e na tolerância a falso negativo de segurança de um pipeline militar, sem degradar a recusa em cenários que exigem recusa.

## Garantias formais em RAG

O grosso dos cinco métodos de detecção acima produz um escore, não uma garantia. [C-RAG (Kang, Gürel, Yu, Song & Li, ICML 2024)](https://proceedings.mlr.press/v235/kang24a.html) é uma exceção: usando o mesmo arcabouço de predição conforme citado no [capítulo 01](01-conceitos.md#calibracao-e-incerteza-epistemica), os autores certificam uma cota superior de confiança para o risco de geração em sistemas RAG, e provam formalmente que RAG atinge risco certificado menor que um LLM puro, sob condições declaradas. É o análogo, em recuperação aumentada, do que TECP faz a nível de token: trocar acurácia empírica por uma cota com garantia estatística.
