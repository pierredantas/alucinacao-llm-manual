# 04 · Benchmarks & métricas

Os principais frameworks de avaliação, e onde nove modelos de ponta se posicionam no Índice de Alucinação Vectara/Hugging Face.

## Benchmarks & frameworks de avaliação

| Benchmark | Veículo | Foco |
|---|---|---|
| [RAGTruth (Niu et al.)](https://arxiv.org/abs/2401.00396) | ACL 2024 | Primeiro corpus de grande escala voltado a avaliar alucinações em RAG. |
| [HaluEval (Li et al.)](https://aclanthology.org/2023.emnlp-main.397/) | EMNLP 2023 | QA, sumarização e diálogo contra referências, em larga escala. |
| [HaLoGen (Ravichander et al.)](https://aclanthology.org/2025.acl-long.71/) | ACL 2025 | Taxonomia refinada, com decomposição atômica via FactScore. |
| [Revisão de Fidelidade (Malin et al.)](https://doi.org/10.1109/JSTSP.2025.3579203) | IEEE JSTSP 2025 | Pesquisa sistemática de métricas de alinhamento factual. |
| [HalluBench (Şenyayla & Onan)](https://doi.org/10.32604/cmc.2026.081260) | CMC 2026 | Confiabilidade comparativa sob prompts adversariais e domínios específicos. |

## Índice de alucinação dos modelos ([Vectara / HF](https://huggingface.co/spaces/vectara/leaderboard))

| Modelo | Arquitetura | Taxa de alucinação | Consistência factual |
|---|---|---:|---:|
| Phi-4 (Microsoft) | SLM denso, 14B | 3,7% | 96,3% |
| Llama-3.3-70B-Instruct (Meta) | LLM denso, 70B | 4,1% | 95,9% |
| Mistral Large 2411 | LLM denso, 123B | 4,5% | 95,5% |
| Qwen 2.5-72B-Instruct (Alibaba) | LLM denso, 72B | 5,4% | 94,6% |
| DeepSeek-V3 | MoE, 671B (37B ativos) | 6,1% | 93,9% |
| Gemini 2.5 Pro (Google) | MoE multimodal | 7,0% | 93,0% |
| GPT-4o, 2024-08-06 (OpenAI) | MoE multimodal | 9,6% | 90,4% |
| Claude 3.5 Sonnet (Anthropic) | Denso / MoE | 9,8% | 90,2% |
| DeepSeek-R1 | Raciocínio MoE, 671B (37B) | 11,3% | 88,7% |

!!! tip "Conclusão para a Defesa"
    Escala e raciocínio multi-etapa não eliminam alucinações. Modelos compactos bem regularizados (ex.: Phi-4) superam modelos de raciocínio profundo (ex.: DeepSeek-R1) em RAG fechado, devido ao menor espaço de busca estocástica desancorada.
