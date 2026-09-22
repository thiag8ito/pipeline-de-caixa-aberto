Visão geral do que vai ser construido

Fonte(s) de dados  
      ↓  
[Airflow] extrai → armazenamento bruto → carrega no Postgres  
      ↓  
Transformações (camadas) → tabelas de consumo  
      ↓  
BI de negócio        /    BI operacional (saúde do pipeline)

Tudo roda em containers com limites de recursos definidos por você. A camada de auditoria 
(o que alimenta o dashboard operacional) é um desafio de design seu.
