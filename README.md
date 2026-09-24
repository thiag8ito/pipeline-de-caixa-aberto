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


Esse projeto mostra para o consumidor final, os dados dos investimentos como valor total, valor da quota, patrimonio liquido, capitação que aquele investimento teve naquele dia, quanto foi resgatado e numero de cotistas.
O projeto iria ajudar analistas, investidores e assim como eu mesmo
A fonte de dados que escolhi foi o informativo diario do banco de dados da CVM e ele foi escolhido por ser um banco de dados real, com grande volume e atualização continua, o que vai me permitir identificar gargalos no projeto
O diferencial do projeto é o fato de estarmos usando stacks 100% open source, o que faz com que o projeto seja moldado nos padroes de projetos da vida real, não sendo tudo controlado