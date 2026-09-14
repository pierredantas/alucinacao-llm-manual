# 04 · Benchmarks & métricas

Os principais frameworks de avaliação, e onde nove modelos de ponta se posicionam no Índice de Alucinação Vectara/Hugging Face.

## Métricas de mensuração

Antes de comparar benchmarks, vale separar o que cada família de métrica mede de fato. A distinção central é entre sobreposição de superfície textual e fidelidade factual real, as duas raramente coincidem.

| Família | Métrica | O que mede | Limite |
|---|---|---|---|
| Sobreposição lexical | ROUGE, BLEU | N-gramas compartilhados com uma referência. | Insensível a paráfrase; cega a uma inversão factual que preserva o vocabulário. |
| Similaridade semântica | [BERTScore (Zhang, Kishore, Wu, Weinberger & Artzi, ICLR 2020)](https://arxiv.org/abs/1904.09675) | Similaridade token a token em embeddings contextuais do BERT. | Correlaciona melhor com julgamento humano que ROUGE, mas mede semelhança de significado, não fidelidade à fonte: uma paráfrase logicamente invertida pode pontuar alto. |
| Entailment / NLI | [Maynez, Narayan, Bohnet & McDonald (ACL 2020)](https://aclanthology.org/2020.acl-main.173/) | Classifica cada sentença gerada como implicada, neutra ou contraditória frente ao documento de origem, via modelo de inferência textual. | Herda os erros do modelo de NLI usado como juiz; degrada em domínios fora da distribuição de treino do classificador. |
| Fatos atômicos | [FActScore (Min et al., EMNLP 2023)](https://doi.org/10.18653/v1/2023.emnlp-main.741) | Decompõe a geração em afirmações atômicas e verifica cada uma contra uma base de conhecimento, relatando a fração factualmente suportada. | Depende da cobertura e atualidade da base de conhecimento externa; custo computacional cresce com o número de fatos atômicos extraídos. |
| QA-based | [QAGS (Wang, Cho & Lewis, ACL 2020)](https://doi.org/10.18653/v1/2020.acl-main.450) | Gera perguntas a partir do texto produzido, responde-as contra a fonte e contra o próprio texto, e mede a divergência entre as respostas. | A qualidade da métrica é limitada pela qualidade do gerador e do respondedor de perguntas usados internamente. |
| Incerteza / entropia semântica | [Kuhn, Gal & Farquhar (ICLR 2023)](https://arxiv.org/abs/2302.09664); [Farquhar, Kossen, Kuhn & Gal (Nature, 2024)](https://doi.org/10.1038/s41586-024-07421-0) | Agrupa amostras geradas por equivalência de significado e mede a entropia sobre os clusters resultantes; alta entropia semântica sinaliza confabulação. | Exige múltiplas amostras por consulta, o que multiplica o custo de inferência; mede confabulação especificamente, não toda a taxonomia de alucinação do [capítulo 01](01-conceitos.md#taxonomia-estrutural). |
| Predição conforme | [TECP (Xu & Lu, Mathematics 2025)](https://doi.org/10.3390/math13203351) | Entropia a nível de token combinada com predição conforme, produzindo intervalos de cobertura com garantia estatística formal. | A garantia é distribucional (exchangeability), não pontual; sob desvio de distribuição tático (o gap SISFRON do [capítulo 01](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca)), a cobertura nominal deixa de valer. |
| LLM-as-judge | [G-Eval (Liu, Iter, Xu, Wang, Xu & Zhu, EMNLP 2023)](https://doi.org/10.18653/v1/2023.emnlp-main.153) | Usa um LLM forte, com cadeia de raciocínio e um paradigma de preenchimento de formulário, como avaliador de outras gerações. | Alinhamento alto com julgamento humano reportado no artigo original, mas herda os vieses e as próprias alucinações do modelo avaliador; não é uma garantia independente. |

Duas famílias adicionais aparecem como benchmarks fundacionais, não como métricas de escore contínuo: [TruthfulQA (Lin, Hilton & Evans, ACL 2022)](https://doi.org/10.18653/v1/2022.acl-long.229) mede se um modelo reproduz falsidades comuns imitadas de padrões humanos, adversarialmente selecionadas; [FEVER (Thorne, Vlachos, Christodoulopoulos & Mittal, NAACL-HLT 2018)](https://doi.org/10.18653/v1/n18-1074) é um marco anterior aos LLMs no mesmo espaço de problema: verificação de alegações contra evidência recuperada, com um desenho independente do usado por HaluEval e RAGTruth na seção seguinte.

!!! danger "Referência versus livre de referência"
    ROUGE, BLEU, BERTScore e FActScore exigem um documento-fonte ou resposta padrão-ouro: adequadas a RAG fechado, onde a fonte está disponível no momento da avaliação. [SelfCheckGPT (Manakul, Liusie & Gales, EMNLP 2023)](https://aclanthology.org/2023.emnlp-main.557/), a entropia semântica e a predição conforme inferem confiabilidade a partir da própria distribuição de amostragem do modelo, sem fonte externa. A escolha entre as duas famílias não é de preferência metodológica: um pipeline de C2 que precisa avaliar uma resposta em tempo real, sem uma referência pronta, só pode usar a segunda família.

!!! tip "Conclusão para o IME"
    Predição conforme e entropia semântica são as únicas famílias com garantia estatística explícita de cobertura, pré-requisito para compor um orçamento de confiabilidade certificável (QP1 e QP4, [capítulo 06](06-agenda-pesquisa.md#sete-questoes-abertas-qp1qp7)). Métricas de referência (FActScore, QAGS, BERTScore) continuam necessárias para auditoria offline e construção de datasets de teste, como os da seção seguinte, mas não substituem monitoramento em runtime sem fonte disponível.

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

## O ranking não é permanente, e não generaliza para domínio militar

A própria equipe da Vectara documenta as limitações do índice acima. [Tamber et al. (EMNLP 2025, Industry Track)](https://doi.org/10.18653/v1/2025.emnlp-industry.54) descrevem o leaderboard original, baseado no detector HHEM, ativo desde 2023, e introduzem uma metodologia revisada, o FaithJudge, motivada por limitações observadas no método de detecção original. O ranking de nove modelos na tabela acima é uma fotografia de um método específico em um momento específico, não uma propriedade estável dos modelos.

O índice também mede um cenário genérico: consistência factual em RAG de propósito geral. Nenhuma das cinco linhas da tabela de benchmarks acima usa prompts adversariais de domínio militar. [HalluBench (Şenyayla & Onan)](https://doi.org/10.32604/cmc.2026.081260) é a exceção parcial: mede confiabilidade comparativa sob prompts adversariais e domínios específicos, mas não domínio militar per se.

!!! danger "Um número de leaderboard não é uma certificação"
    O gap SISFRON descrito no [capítulo 01](01-conceitos.md#confiabilidade-vs-dignidade-de-confianca), alta acurácia no Cerrado aberto, falha sob dossel amazônico, é exatamente o tipo de queda de desempenho fora de distribuição que um índice de propósito geral não captura. Uma taxa de alucinação de 3,7% em benchmark aberto não informa a taxa de alucinação do mesmo modelo sob o domínio, o vocabulário e as condições adversariais de um sistema de Defesa específico. Essa medição não existe hoje na literatura pública.
