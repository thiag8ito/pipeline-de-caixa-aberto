# Fase 0 - Antes do arquivo: suas decisões
1 - Imagem
    - Entendi que existem vários tipos de versões de stacks
    - Podemos usar a stacks jupyter/scipy-notebook
    - A lista de tags disponiveis estao no Quay.io, la tem as versoes da stack, mas ainda nao sei qual versão seria bom usar
    - o nome completo da stack seria jupyter/minimal-notebook:tag

    -  tag usada: scipy-notebook:notebook-7.6.2 
    docker pull quay.io/jupyter/scipy-notebook@sha256:c88fd047a38689b1fe621309eaa91d1f0637c5c1ef3bccb7509cfa92d2b508ca


2 - Porta
    - A porta padrão do jupyter é 8888
    - No docker compose, a propriedade ports: funciona como uma ponte que conecta a maquina fisica ao container. 
    - O formato padrao esquerda:direita serve para direcionar o trafego de rede de fora para dentro do container
    - Eu posso escolher uma porta qualquer na esquerda, desde que ela n esteja sendo usada por mais nenhuma aplicação do meu pc, 
    e a da direita tem que ser 8888, pois é a porta padrao do jupyter

    - o formato exato do valor de [ports:] é uma lista de strings. Como o docker compose aceita multiplos mapeamentos de portas para um mesmo container, 
    cada mapeamento entra como um item separado nessa lista.
   
        version: '3.8'
    services:
    notebook:
        image: jupyter/base-notebook
#       ports:
#        - "8080:8888"
#        - "443:443"  


    - Sempre bom colocar o mapeamento de portas entre aspas. Isso irá garantir que quando usar portas com numeros pequenos,
    o interpretador pode converter o valor para o sistema sexadecimal o que quebraira a configuração


#   - Testando o [docker compose up/down]
    ao testar o docker compose up, criar um notebook dentro do Jupyterlab salvar ele e rodas docker compose down, o notebook foi deletado, o que comprovou em prática que preciso de um volume aqui para o projeto seguir em frente.

    o container sumiu por nao ter um volume configurado dentro do ambiente

#   - sobre o volume:
    docker run --mount type=bind,src=<host-path>,dst=<container-path> é o melhor caminho a ser adotado por --mount ser explicito e ter suporte para todas as opções disponíveis para nós usarmos

    usar o caminho relativo [- ./notebooks:/home/jovyan/work] é mais recomendado por conta da reprodutibilidade dos testes em outras maquinas, ao contrario do caminho absoluto, onde os direotrios podem ser diferentes em maquinas diferentes.

    