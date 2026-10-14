# GoodWe ChargeGrid Intelligence
### Challenge FIAP 2026 — Sprint 4: Solução Final Integrada e Inovadora

> **Entrega mista:** este repositório atende à **Sprint 4 das disciplinas PCP e SERS**. Os artefatos e a documentação são compartilhados pelas duas entregas.

> **Status:** prova de conceito acadêmica baseada em simulações. Não representa uma instalação comercial nem uma integração operacional com equipamentos GoodWe.

**Equipe 7 — Turma 1CCPX**

| Integrante | RM |
|---|---|
| Gabriel Barbosa Furin | 572941 |
| Gabriel de Almeida Santos | 569395 |
| Herbert Soares de Jesus | 571507 |
| Lucas Kiodi Moraca | 571004 |
| Renan Fracalossi Mano da Silva | 569610 |

---

## Sobre o projeto
O ChargeGrid Intelligence é uma proposta de gestão inteligente para infraestrutura de recarga de veículos elétricos. A prova de conceito reúne uma interface de monitoramento, uma representação tridimensional do eletroposto e uma camada lógica denominada **Energy Engine**, concebida para demonstrar estratégias de balanceamento de cargas (*Load Balancing*) e redução de picos de demanda (*Peak Shaving*), considerando geração solar e armazenamento.

O projeto foi desenvolvido no contexto do Challenge FIAP em parceria com a GoodWe. A compatibilidade com tecnologias GoodWe é apresentada como referência arquitetural e conceitual; não se afirma integração real com inversores, baterias, carregadores, SEMS Portal/SEMS+ ou OCPP.

## Objetivos
- Demonstrar uma arquitetura conceitual de gestão de energia para múltiplos carregadores.
- Visualizar geração solar, armazenamento, demanda e distribuição de potência.
- Simular balanceamento dinâmico de cargas e redução de picos.
- Discutir eficiência energética, sustentabilidade, viabilidade e limitações.
- Documentar a prova de conceito e suas possibilidades de evolução.

## Componentes do projeto
- **Dashboard web** (`Dashboard/`): interface de gestão e monitoramento em React + TypeScript + Vite. Visualização de indicadores, estações, balanceamento, logs, previsão e faturamento com dados simulados.
- **Eletroposto 3D** (`index_V8_1_SPRINT3.html` + `ChargeGrid_Web.glb`): representação visual navegável da infraestrutura e do fluxo de uma sessão de recarga (HTML + Three.js).
- **Simulador Python** (`src/simulador/`): script de terminal que isola a lógica de gerenciamento energético (potência disponível, Load Balancing e Peak Shaving) como camada de referência, auditável de forma independente das interfaces.
- **Documentação** (`docs/`): documentação técnica final, casos de uso e diagramas.

> **Sobre o Python deste repositório:** o que roda como solução demonstrável são as interfaces em JavaScript (Dashboard web e Eletroposto 3D). O código em `src/simulador/` é uma **camada de lógica de referência** — não é um back-end conectado às interfaces nem é executado por elas. Ele documenta e torna auditável a lógica energética; as interfaces simulam seu próprio comportamento de forma independente.

> A presença de uma interface ou registro demonstrativo não comprova integração física ou comunicação com serviços externos.

## Como executar

### Dashboard web
Acesso direto pelo navegador (versão publicada):
```
https://goodwe-grid-smart.lovable.app/
```
Execução local a partir da pasta `Dashboard/` (requer Node.js):
```
cd Dashboard
npm install
npm run dev
```

### Eletroposto 3D
`index_V8_1_SPRINT3.html` e `ChargeGrid_Web.glb` devem estar no mesmo diretório. Suba um servidor HTTP local e acesse pelo navegador:
```
python -m http.server 8000
```
```
http://localhost:8000/index_V8_1_SPRINT3.html
```
> Abrir o `.html` com duplo clique (via `file://`) pode bloquear o carregamento do modelo 3D. Use sempre o servidor HTTP.

### Simulador Python
Não há dependências externas — o script usa apenas a biblioteca padrão do Python (>= 3.9):
```
python src/simulador/chargegrid_simulador.py
```

## Resultados simulados
Um dos cenários documentados compara uma demanda de referência de **296 kW** com um cenário gerenciado de **190 kW**, diferença de **106 kW** (aproximadamente **35,8%**). Os valores representam um cenário de simulação e devem ser interpretados dentro das premissas utilizadas no projeto, não como desempenho medido em campo.

A documentação de sustentabilidade apresenta estimativas de energia renovável e emissões evitadas baseadas em fatores de consumo e emissão (ICCT 2023, MCTI 2023). Esses valores são indicativos e dependem das premissas adotadas; não constituem medição de impacto real.

### Nota de consistência
Os documentos das fases anteriores apresentam valores de potência diferentes que **não devem ser comparados como se fossem a mesma grandeza**:
- **42,5 kW** é a **demanda total dos veículos** na sessão (EV01 + EV02 + EV03), ou seja, o que os carros solicitam.
- **75,4 kW** é o **suprimento total disponível** na mesma sessão (Solar 28,4 + Rede 35,0 + ESS 12,0), ou seja, de onde a energia vem.

Os dois números são do mesmo instante (Fase 1, painel "Carregamento ativo") e são coerentes entre si — o suprimento é maior que a demanda, deixando folga. As figuras e legendas devem identificar sempre o cenário, os componentes incluídos e a unidade de medida.

A estimativa de **ROI de 0,2 mês e economia de R$ 68.200/mês não deve ser tratada como validada**: a própria análise da Fase 2 identifica essa inconsistência. Pelo critério de R$ 50/kW de ultrapassagem evitada, os valores defensáveis ficam em torno de **R$ 3.100/mês** (cenário "E Se...?", 62 kW) a **R$ 5.300/mês** (cenário de Infraestrutura, 106 kW), com retorno estimado em alguns meses — sempre como estimativa sob premissas, não como economia garantida.

## Tecnologias e conceitos relacionados
- Gestão e distribuição de potência (*Load Balancing*).
- Redução de picos de demanda (*Peak Shaving*).
- Geração fotovoltaica e armazenamento de energia (ESS).
- Monitoramento e visualização de dados.
- Referência conceitual a ecossistemas de carregamento e gestão energética GoodWe.
- OCPP como referência para registros e comunicação; a implementação apresentada é simulada.

## Sustentabilidade e impacto
A proposta busca demonstrar como a gestão da demanda, a geração solar e o armazenamento podem apoiar uma operação de recarga mais eficiente. As estimativas ambientais apresentadas nas fases anteriores permanecem identificadas como **estimativas baseadas em premissas**, com indicação das fontes e dos fatores utilizados. A viabilidade econômica e os ganhos reais exigem validação com dados medidos e tarifas aplicáveis.

## Limitações
- Prova de conceito acadêmica baseada em cenários simulados.
- Sem hardware físico conectado e sem validação em campo.
- Sem integração operacional confirmada com produtos GoodWe ou SEMS Portal/SEMS+.
- Logs inspirados no padrão OCPP não significam que exista comunicação OCPP real.
- Resultados de potência, economia e carbono dependem das premissas e não são garantias de desempenho.
- Previsão de demanda, assistente virtual e automações são recursos demonstrativos.

## Documentação
- Documentação técnica final: [`docs/Documentacao_Final_ChargeGrid.md`](docs/Documentacao_Final_ChargeGrid.md) · [`.pdf`](docs/Documentacao_Final_ChargeGrid.pdf) · [`.docx`](docs/Documentacao_Final_ChargeGrid.docx)
- Fase 1 — Integração e Funcionamento: [`.pdf`](docs/Fase_1_Integracao_e_Funcionamento.pdf) · [`.docx`](docs/Fase_1_Integracao_e_Funcionamento.docx)
- Fase 2 — Sustentabilidade e Inovação: [`.pdf`](docs/Fase_2_Sustentabilidade_e_Inovacao.pdf) · [`.docx`](docs/Fase_2_Sustentabilidade_e_Inovacao.docx)
- Arquitetura: [`ARQUITETURA.md`](ARQUITETURA.md)
- Validação e escopo: [`VALIDACAO.md`](VALIDACAO.md)
- Casos de uso: [`docs/casos_de_uso.md`](docs/casos_de_uso.md)
- Diagramas: [`docs/diagramas/`](docs/diagramas/)

## Vídeo técnico
**Link do vídeo (até 5 minutos):** https://youtu.be/Mh6m9RmmPfA

## Equipe e contexto acadêmico
- **Challenge:** FIAP + GoodWe — 2026
- **Sprint:** 4 — Solução Final Integrada e Inovadora (entrega mista: PCP e SERS)
- **Equipe:** 7 · **Turma:** 1CCPX
- **Data de entrega indicada:** 15/10/2026

## Referências
- GoodWe — soluções de energia e carregamento de veículos elétricos: https://en.goodwe.com/
- Open Charge Alliance — protocolo OCPP: https://openchargealliance.org/
- ICCT — estudos sobre transporte e emissões: https://theicct.org/
- MCTI — fatores de emissão de CO₂ do SIN: https://www.gov.br/mcti/
- ANEEL — regulação do setor elétrico (RN nº 1.000/2021): https://www.gov.br/aneel/
- Nações Unidas Brasil — Objetivos de Desenvolvimento Sustentável: https://brasil.un.org/pt-br/sdgs

---
Prova de conceito acadêmica. Resultados simulados não equivalem a desempenho real, validação comercial ou certificação de produto.
