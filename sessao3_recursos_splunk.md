
# Sessão 3 – Cálculo de Recursos para Splunk: CPU, Memória e Disco

## Objetivo
Ensinar como calcular, de forma técnica e otimizada, os recursos mínimos recomendados (CPU, memória e disco) para Search Heads e Indexers em uma arquitetura Splunk.

---

## 1. Por que calcular?

- Evitar superdimensionamento sem necessidade  
- Seguir boas práticas da Splunk  
- Justificar recomendações técnicas para clientes  
- Aumentar eficiência da arquitetura

---

## 2. Recomendações gerais da Splunk

| Papel        | CPU              | Memória RAM       | Disco                   |
|--------------|------------------|-------------------|--------------------------|
| Search Head  | 12 núcleos min   | 12–16 GB (min)    | Rápido (SSD), IOPS alto |
| Indexer      | 12 núcleos min   | 12–16 GB (min)    | 800 IOPS+ por indexer   |

---

## 3. Fórmulas práticas de dimensionamento

### CPU (número de núcleos)

**Search Head**:
```
# de usuários concorrentes × 1.5
```

**Indexer (estimativa simplificada)**:
```
(volume diário de ingestão em GB ÷ GB suportado por indexer) × 12 núcleos
```

> Nota: o divisor depende do tipo de dado. Veja a tabela abaixo.

---

## 4. Capacidade estimada por tipo de dado

### Com 12 CPUs por indexer

| Tipo de dado ou cenário                       | GB/dia por indexer |
|----------------------------------------------|--------------------|
| Logs brutos simples (ex: syslog)              | 80–100 GB          |
| Dados com parsing médio (ex: Apache, Linux)   | 50 GB              |
| Dados pesados (firewall com regex, ES, ITSI)  | 30–40 GB           |
| Parsing avançado (json aninhado, métricas)    | 20–30 GB           |

### Com 16 CPUs por indexer

| Tipo de dado ou cenário                       | GB/dia por indexer |
|----------------------------------------------|--------------------|
| Logs brutos simples (ex: syslog)              | 120–140 GB         |
| Dados com parsing médio (ex: Apache, Linux)   | 70 GB              |
| Dados pesados (firewall com regex, ES, ITSI)  | 50–60 GB           |
| Parsing avançado (json aninhado, métricas)    | 40–50 GB           |

### Com 32 CPUs por indexer

| Tipo de dado ou cenário                       | GB/dia por indexer |
|----------------------------------------------|--------------------|
| Logs brutos simples (ex: syslog)              | 200–250 GB         |
| Dados com parsing médio (ex: Apache, Linux)   | 100–120 GB         |
| Dados pesados (firewall com regex, ES, ITSI)  | 80–100 GB          |
| Parsing avançado (json aninhado, métricas)    | 70–80 GB           |

---

## 5. Memória RAM

**Search Head**:
```
2 GB por núcleo (mínimo de 12 GB)
```

**Indexer**:
```
1 GB por 50 GB de ingestão diária + 2 GB por núcleo
```

---

## 6. Disco (hot/warm por indexer)

```
Disco necessário = Ingestão diária × Dias de retenção hot/warm × 1.5 (fator de compressão)
```

---

## 7. Exercício prático

Cliente tem:
- 700 GB/dia
- 15 usuários simultâneos
- 90 dias de retenção hot/warm

Calcule:
- Quantos indexers?
- Recursos por host (CPU, RAM, disco)?
- Quantos SHs?

---

## 8. Boas práticas finais

- Adicionar margem de crescimento
- Documentar premissas para cada cálculo
- Referência: [Splunk Capacity Planning](https://docs.splunk.com/Documentation/Splunk/latest/Capacity/Referencehardware)
