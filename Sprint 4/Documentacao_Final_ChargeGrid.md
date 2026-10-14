# ChargeGrid Intelligence — Documentação Técnica Final
## Challenge FIAP 2026 | Sprint 4 — Solução Final Integrada e Inovadora

**Equipe:** 7 · **Turma:** 1CCPX · **Entrega indicada:** 15/10/2026  
**Natureza:** prova de conceito acadêmica baseada em simulação.

## 1. Resumo executivo
O ChargeGrid Intelligence é uma proposta de gestão inteligente de energia para infraestrutura de recarga de veículos elétricos. A prova de conceito reúne uma interface de monitoramento, uma representação tridimensional do eletroposto e uma camada lógica chamada **Energy Engine**. O objetivo é demonstrar, em cenários simulados, como o balanceamento dinâmico de cargas e estratégias de *Peak Shaving* podem ajudar a distribuir a potência disponível, considerando geração fotovoltaica, armazenamento de energia e demanda do edifício.

O projeto foi desenvolvido no contexto do Challenge FIAP em parceria com a GoodWe. A relação com tecnologias GoodWe é uma referência de arquitetura e de ecossistema, não uma alegação de conexão operacional com produtos reais.

## 2. Problema e objetivo
A conexão simultânea de diversos veículos elétricos pode elevar a demanda de potência de uma instalação. Sem gestão coordenada, isso pode contribuir para picos de demanda e exigir avaliação da capacidade elétrica disponível. O ChargeGrid propõe representar uma camada de inteligência que distribui a potência entre carregadores e considera recursos energéticos disponíveis.

**Objetivos específicos**
- Integrar visualmente os componentes demonstrativos do protótipo.
- Monitorar indicadores simulados de geração, armazenamento e consumo.
- Demonstrar balanceamento de cargas e redução de picos.
- Avaliar possíveis benefícios energéticos e ambientais com premissas explícitas.
- Registrar limitações e próximos passos para uma futura validação.

## 3. Arquitetura proposta
### 3.1 Dashboard web
Apresenta indicadores e visualizações de geração solar, armazenamento, potência demandada, distribuição entre carregadores, cenários e eventos simulados.

### 3.2 Eletroposto 3D
Representa visualmente a infraestrutura de carregamento e complementa a interface de monitoramento. A visualização tridimensional é demonstrativa.

### 3.3 Energy Engine
Camada lógica conceitual responsável por calcular ou representar a distribuição de potência disponível entre carregadores. A proposta inclui estratégias de *Load Balancing* e *Peak Shaving*, considerando as variáveis presentes nos cenários simulados.

### 3.4 Ecossistema energético
O cenário documentado considera geração solar, bateria/ESS, rede elétrica, demanda do edifício e veículos elétricos. A arquitetura faz referência conceitual a tecnologias GoodWe, como carregadores, inversores, armazenamento e plataformas de monitoramento, sem afirmar que esses equipamentos estejam conectados ao protótipo.

### 3.5 Protocolos e automação
Os registros apresentados como inspirados em OCPP e os indicadores de automação são demonstrativos. Não se deve inferir que há sessão OCPP real, conexão SEMS Portal/SEMS+ ou comunicação com carregadores físicos, a menos que isso seja comprovado por implementação adicional.

## 4. Funcionamento demonstrado
O fluxo conceitual pode ser resumido em:
1. Carregar ou definir um cenário de geração, armazenamento e demanda.
2. Exibir os indicadores energéticos no dashboard.
3. Distribuir a potência disponível entre os veículos/carregadores por meio da lógica proposta.
4. Comparar a demanda de referência com o cenário gerenciado.
5. Exibir indicadores e registros que apoiam a análise do resultado.

Esse fluxo descreve a prova de conceito e deve ser ajustado se a versão final do código demonstrar um comportamento diferente.

## 5. Resultados e indicadores
### 5.1 Redução de pico
Um cenário documentado compara **296 kW** de demanda de referência com **190 kW** no cenário gerenciado.

- Diferença: **106 kW**
- Redução relativa: **aproximadamente 35,8%**

Cálculo: (296 − 190) / 296 × 100 ≈ 35,8%.

Esses valores são resultados do cenário simulado descrito nas fases anteriores. Não são medições de campo e não comprovam, isoladamente, que a instalação possa operar sem reforço de rede.

### 5.2 Geração renovável e armazenamento
A Fase 1 apresenta um cenário com geração solar de **28,4 kW**, armazenamento com **70% de SOC** e potência indicada de **12 kW**, além de participação renovável indicada de **38%**. Esses números devem permanecer vinculados ao cenário e à tela em que foram obtidos; não devem ser somados ou comparados com valores de outra simulação sem explicitar diferenças de premissas.

### 5.3 Divergências entre cenários
Os materiais das fases anteriores mostram valores como **42,5 kW** para distribuição entre veículos e **75,4 kW** para uma composição de fornecimento energético. A documentação disponível não permite concluir que ambos descrevam exatamente o mesmo instante ou o mesmo conjunto de cargas. Portanto:
- identificar cada valor pelo nome do cenário, pelos componentes incluídos e pelo momento da simulação;
- revisar legendas e unidades nas figuras;
- não apresentar os valores como diretamente comparáveis até que a equipe confirme a origem.

### 5.4 Economia e retorno financeiro
A Fase 2 identifica uma inconsistência na estimativa de **R$ 68.200/mês** e retorno de **0,2 mês**. Por isso, tais números não são apresentados aqui como resultados validados. A documentação anterior também usa uma premissa de R$ 50 por kW para estimar impacto econômico; essa premissa deve ser descrita como hipótese simplificada, não como tarifa universal ou economia garantida. A economia real depende da modalidade tarifária, demanda contratada, regras de ultrapassagem, período de medição e perfil de uso.

## 6. Sustentabilidade
A Fase 2 estima emissões evitadas a partir de consumo energético por quilômetro e fatores de emissão de veículos a combustão e elétricos. O documento reporta, sob as premissas escolhidas, uma estimativa de aproximadamente **877 kg CO₂e/dia** ou **320 t CO₂e/ano** para a comparação veicular. Esses números devem ser apresentados exclusivamente como estimativas modeladas; não representam emissões medidas pelo protótipo e precisam ser validados contra as referências originais, a composição da frota, a quilometragem e os limites do cálculo.

A Fase 2 também apresenta uma estimativa separada relacionada ao fator de emissão do Sistema Interligado Nacional e ao uso de energia solar. Como essa análise utiliza outra fronteira de cálculo, ela não deve ser somada à estimativa veicular sem metodologia explícita para evitar dupla contagem.

A proposta relaciona-se aos ODS 7 (Energia Limpa e Acessível), 11 (Cidades e Comunidades Sustentáveis) e 13 (Ação Contra a Mudança Global do Clima).

## 7. Diferenciais da proposta
- Balanceamento dinâmico da potência entre carregadores.
- Estratégia de redução de picos (*Peak Shaving*).
- Consideração conceitual de geração solar e armazenamento.
- Dashboard com visualização de indicadores e comparação de cenários.
- Representação tridimensional da infraestrutura.
- Possibilidade de explorar modos de operação e previsão de demanda, conforme os recursos efetivamente demonstrados.
- Documentação explícita das premissas e limitações da simulação.

## 8. Viabilidade e limitações
A proposta é tecnicamente plausível como arquitetura conceitual, mas a viabilidade de implantação ainda não foi comprovada. São necessários dimensionamento elétrico, análise de demanda e tarifas, validação dos equipamentos compatíveis, testes de segurança, integração real com os sistemas de gestão, avaliação de cibersegurança e um piloto com dados medidos.

**Limitações conhecidas**
- Os valores de potência e os resultados são simulados.
- Não há comprovação de conexão física a carregadores, inversores ou baterias.
- OCPP é usado como referência para registros; a comunicação real não está demonstrada.
- Não há integração operacional confirmada com SEMS Portal/SEMS+.
- As estimativas econômicas e ambientais dependem de hipóteses e fontes externas.
- A divergência de cenários 42,5 kW/75,4 kW precisa de identificação explícita nas figuras originais.

## 9. Próximos passos
1. Conferir que todos os gráficos indiquem cenário, unidade, período e componentes incluídos.
2. Revisar a origem dos valores de 42,5 kW e 75,4 kW com os responsáveis pelos documentos.
3. Corrigir ou remover a estimativa de ROI não validada.
4. Validar as fontes bibliográficas completas dos fatores de emissão.
5. Testar a solução com dados medidos e, futuramente, em ambiente piloto.
6. Avaliar integração real, segurança, tarifação e custos de implantação.

## 10. Entrega e vídeo
**Vídeo técnico (até 5 minutos):** `https://youtu.be/Mh6m9RmmPfA`

O link deve ser substituído pelo endereço final compartilhável e testado em janela anônima ou com uma conta sem acesso de edição. A documentação deve ser mantida junto ao código no repositório Sprint 3 usado como base para a entrega Sprint 4.

## 11. Referências
- GoodWe. Materiais institucionais e informações sobre soluções de energia e carregamento. https://en.goodwe.com/
- Open Charge Alliance. Informações sobre o protocolo OCPP. https://openchargealliance.org/
- International Council on Clean Transportation (ICCT). Estudos sobre veículos e emissões. https://theicct.org/
- Agência Nacional de Energia Elétrica (ANEEL). Regulação e informações ao consumidor. https://www.gov.br/aneel/
- Nações Unidas Brasil. Objetivos de Desenvolvimento Sustentável. https://brasil.un.org/pt-br/sdgs
- **Documentação interna do projeto:** Fase 1 — Integração e Funcionamento; Fase 2 — Sustentabilidade e Inovação. Completar/confirmar as referências específicas citadas nesses documentos antes da apresentação final dos fatores quantitativos.

---
**Nota de transparência:** esta documentação descreve uma prova de conceito acadêmica. Resultados simulados não equivalem a desempenho real, validação comercial ou certificação de produto.
