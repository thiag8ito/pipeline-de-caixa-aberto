Esse projeto foi feito pensando em auxiliar aqueles que fazem parte do mercado de investimentos. O objetivo é simples: pegar os dados que vem brutos e confusos, e transformar em um dashboard que facilite a observação para a maioria do publico alvo daqueles investimentos. Isso seria feito ao coletar os dados brutos vindos da CVM e do Banco Central, processando eles e devolvendo ao consumidor final um dashboard que ajuda a acompanhar o comportamento e a tendencia de um certo ativo. 
O projeto começou com o intuito de aprendizado, onde eu busco aprender sobre como o backend de uma pipeline dessas funciona e acredito que o projeto entrega um ensinamento de como algo feito end-to-end nos ajuda a ter uma ideia do funcionamento.


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