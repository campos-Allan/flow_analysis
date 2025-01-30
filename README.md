# ANÁLISE FLOW

Rápida análise dos podcasts dos Estúdios Flow, para analisar engajamento, e tentativa de criação de um modelo de Florestas Aleatórias ou Redes Neurais para prever dados de engajamento baseado em certos atributos. Mais explicações nesse vídeo: https://youtu.be/2rNdSB4OaTE

Os arquivos .csv são os dados que eu busquei na API do Youtube no projetos passado. Aqui só estão os gráficos com uma breve explicação, a análise foi feita no vídeo do youtube.

## Obtendo dados

Através da API do Youtube, obtive total de views, inscritos e vídeos feitos de cada canal e logo em seguida foi possível obter a ID de cada vídeo produzido pelo canais analisados, através dessa ID consegui consolidar dados de views, likes, comentários, duração, título e data de publicação de cada vídeo, resultando em um grande DataFrame com dados individuais de cada vídeo dos 3 canais analisados.

## Análise inicial

Quantidade de publicações realizadas divididas por modalidade (Short = <60s, Vídeo = <50min, o resto entra como Live)

![1](https://i.imgur.com/ASbzsS8.png)

Total de views, com e sem o Flow podcast

![2](https://i.imgur.com/Fj1YJKM.png)

![5](https://i.imgur.com/5PeFyyI.png)

Total de views sem divisão por tipo de publicação, sem o Flow

![6](https://i.imgur.com/11odhH7.png)

Views divididos pela quantidade de conteúdo publicada em segundos

![3](https://i.imgur.com/p815R4I.png)

![4](https://i.imgur.com/Em2pr3L.png)

Criei uma medida de engajamento/s para poder juntar likes, comentários, views e duração do vídeo. Seguindo a fórmula (Views + 1.5 * Likes + 2 * Comentários) / Duração em s

![7](https://i.imgur.com/93ERiRA.png)

Engajamento/s apenas para lives

![8](https://i.imgur.com/pToWDgP.png)

## Previsão de views, likes, comentários, engajamento/s

Não foi possível criar um modelo com bom desempenho para prever tais medidas a partir das variáveis exploradas aqui, isso é, qual tipo de podcast do estúdios Flow aquela publicação pertence, o tipo de publicação (Live, vídeo ou short), a data de publicação e duração. Testei normalizações nos dados, diferentes recortes da base de dados, modelos de Redes Neuras e Florestas Aleatórias, mas não foi possível atingir um bom desempenho. O modelo só conseguia prever uma das variáveis desejadas quando se inseria outra que deveria ser prevista (ex: prever número de views tendo as varíaveis anteriores + o número de likes ou comentários daquela publicação, a partir dessa mexida o desempenho melhorava muito, mas não fazia sentido ter esse tipo de informação para utilizar o modelo para prever de antemão o resultado de engajamento de um vídeo).
