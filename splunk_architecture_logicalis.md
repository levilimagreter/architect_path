
# Splunk Architecture Enablement

## Objetivo
Treinar para atingir o nível de Arquiteto de Splunk Plataforma.

---

## Plano Completo de Desenvolvimento

### Fase 1 – Fundamentos Sólidos
**Meta:** Dominar os conceitos essenciais da plataforma Splunk.

- Conceitos básicos: UF, HF, IF, Indexers, Search Heads
- Arquiteturas: Standalone, Distributed, Clustering
- Licenciamento Splunk e métricas
- Arquivos críticos: `indexes.conf`, `inputs.conf`, `outputs.conf`, `serverclass.conf`
- Hands-on: instalação e configuração mínima de Splunk e Universal Forwarder
- Construção de uma topologia inicial em papel

---

### Fase 2 – Especialização em Deployments e Arquitetura
**Meta:** Capacidade de desenhar arquiteturas resilientes e escaláveis.

- Deployment Server na prática
- Cluster de Indexers (multisite, alta disponibilidade)
- Cluster de Search Heads
- Gerenciamento de certificados (SSL)
- Arquiteturas SVA Splunk para diferentes volumes
- Heavy e Intermediate Forwarders
- Segurança: HEC, RBAC, capabilities

---

### Fase 3 – Especialização de Performance e Troubleshooting
**Meta:** Ser capaz de diagnosticar, tunar e escalar o ambiente.

- Parsing pipeline e indexing pipeline
- Tuning de filas: ingestion, indexing, searching
- Search concurrency tuning
- Troubleshooting avançado: licensing issues, queue blockages, bucket recovery
- Sizing e capacity planning realista

---

# Sessão de Hoje – 1h

## Tema
**Arquitetura Splunk: Como Escolher o Modelo Certo para Cada Cenário**

## Estrutura da Sessão

| Tempo | Atividade |
|:-----:|:----------|
| 5 min | Introdução: o que define uma arquitetura boa |
| 15 min | Conceitos de topologias e tipos de forwarders |
| 20 min | Estudo de 3 mini-cenários reais |
| 15 min | Simulado ao vivo: arquitetar cenário real |
| 5 min | Recapitulação e teaser para a próxima sessão |

---

## Conteúdo Detalhado

### Introdução (5 min)
- O que é uma arquitetura eficiente: escalabilidade, resiliência, performance, operação simplificada.

### Modelos de Topologias (15 min)
- Standalone vs Distributed vs Clustered
- Quando e como usar:
  - Universal Forwarder (UF)
  - Heavy Forwarder (HF)
  - Intermediate Forwarder (IF)

### Estudo de 3 Cenários Reais (20 min)
- **Empresa pequena (50GB/dia):**
  - UF > IDX standalone > SH
- **Empresa média (500GB/dia):**
  - UF > HF (parseo) > IDX Cluster > SH Cluster
- **Empresa grande (1TB/dia multisite):**
  - UF > IF > HF > IDX Cluster multisite > SH Cluster multisite

### Simulado ao Vivo (15 min)
- Caso: "Uma empresa projeta crescer de 100GB/dia para 500GB/dia em 2 anos."
- Atividade: participantes sugerem uma arquitetura.
- Discussão e comparação com a arquitetura recomendada.

### Encerramento (5 min)
- Reforço: elasticidade e escalabilidade como pilares.
- Teaser para próxima sessão: **Deep Dive em Indexer Cluster**.

---

# Próximos Passos
- Consolidar conceitos hoje vistos.
- Na próxima sessão: detalhes de configuração de cluster de Indexers.
