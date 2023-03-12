# Smart-Irrigation-System
"Smart-Irrigation-System-JohnDoe" é um projeto de irrigação automatizado com ESP32 e Raspberry Pi que utiliza sensores para monitorar as condições do solo e do ar, ajustando a quantidade de água e nutrientes fornecidos às plantas de forma inteligente e eficiente.

## Introdução

O projeto  tem como objetivo automatizar o processo de irrigação em cultivos, utilizando tecnologias como sensores de umidade do solo, temperatura, umidade do ar e luminosidade. Com base nos dados coletados pelos sensores, é possível ajustar o sistema de irrigação para fornecer a quantidade ideal de água e nutrientes às plantas em diferentes fases do ciclo de cultivo. O projeto também envolve a implementação de um sistema de monitoramento remoto, permitindo que o sistema de irrigação seja monitorado e controlado a partir de um dispositivo móvel ou computador. A documentação do projeto inclui instruções detalhadas de instalação, configuração e uso do sistema, bem como informações sobre a adaptação do sistema de irrigação às necessidades específicas das plantas cultivadas.


## O projeto pode ser dividido nas seguintes partes

1. `Hardware`: consiste na implementação dos sensores de umidade do solo, temperatura e umidade do ar, bem como na construção do sistema de irrigação automatizado.

2. `Software embarcado`: envolve a programação do ESP32 para coletar dados dos sensores e transmiti-los via MQTT para o servidor Raspberry Pi.

3. `Servidor`: consiste no Raspberry Pi, que recebe os dados dos sensores e os processa para controlar o sistema de irrigação e fertilização. O servidor também pode ser responsável pela análise de dados coletados, identificação de padrões e tendências e tomada de decisões informadas sobre o manejo do solo e da água.

4. `API RESTful`: é a interface de programação de aplicativos que permite que outros sistemas e aplicativos interajam com o servidor. Nesse caso, a API é responsável por controlar o sistema de irrigação e fertilização.

5. `Aplicação web`: é uma aplicação desenvolvida em Spring Boot que permite visualizar e controlar o sistema de irrigação e fertilização remotamente. Também é possível visualizar os dados coletados pelos sensores e realizar análises e visualizações dos mesmos.

6. `Documentação`: é a parte do projeto que inclui a documentação do hardware, software e do projeto em geral, bem como a documentação da API e do aplicativo web. Isso inclui instruções de instalação, guias de uso e descrições detalhadas de como o projeto foi implementado.

## Etapas para implementar o projeto

1. `Definir o tipo de cultivo e as necessidades de irrigação e fertilizacao `: É importante entender as necessidades específicas das plantas que serão cultivadas, como a quantidade ideal de água e nutrientes em diferentes fases do ciclo de cultivo. Essas informações são fundamentais para determinar quais sensores serão utilizados e como o sistema de irrigação será configurado.

2. `Selecionar os componentes necessários`: É importante selecionar os componentes corretos, como o microcontrolador ESP32, sensores de umidade do solo, temperatura, umidade do ar e luminosidade, sistema de irrigação automatizado, servidor Raspberry Pi, módulo GSM ou conexão Wi-Fi, entre outros.

4. `Montar e configurar o hardware`: A montagem do hardware deve seguir as especificações de cada componente e deve ser feita com cuidado para garantir que tudo esteja funcionando corretamente. É importante configurar corretamente cada componente, como o microcontrolador ESP32 e o servidor Raspberry Pi.

5. `Programar o microcontrolador ESP32`: O microcontrolador ESP32 deve ser programado para coletar os dados dos sensores e transmiti-los para o servidor Raspberry Pi via protocolo MQTT.

4. `Programar o servidor Raspberry Pi`: O servidor Raspberry Pi deve ser programado para receber e processar os dados coletados pelos sensores e controlar o sistema de irrigação. Além disso, deve-se desenvolver a API RESTful em Spring Boot para controlar o sistema de irrigação e fertilização.

5. `Desenvolver o aplicativo web`: O aplicativo web permite visualizar e controlar o sistema de irrigação e fertilização remotamente. É importante desenvolver uma interface de usuário intuitiva e fácil de usar.

6. `Testar e ajustar o sistema`: Depois que tudo estiver configurado e programado, é importante testar o sistema e ajustá-lo de acordo com as necessidades específicas das plantas cultivadas. É importante monitorar o sistema e fazer ajustes conforme necessário para garantir que as plantas estejam recebendo a quantidade ideal de água e nutrientes.

Ao integrar todas essas partes, o "Sistema de irrigação inteligente com ajuste baseado no ciclo de cultivo das plantas e monitoramento remoto" permite que o processo de irrigação seja automatizado e ajustado de acordo com as necessidades das plantas em diferentes fases do ciclo de cultivo. 

Além disso, o sistema de monitoramento remoto permite que o sistema de irrigação seja monitorado e controlado a partir de qualquer lugar, o que é particularmente útil se o usuário estiver longe do local onde as plantas estão crescendo.


## Etapa 1: Definir o tipo de cultivo e as necessidades de irrigação e fertilizacao

### Necessidades de Irrigação específica
Antes de projetar o sistema de irrigação, é importante definir o tipo de cultivo que será cultivado e suas necessidades de irrigação específicas. Para este projeto, consideraremos o cultivo de alguns legumes como: alface, tomate, cenoura, coentro, salsinha e cebolinha.


| Fator                        | Alface                       | Tomate                       | Cenoura                      | Coentro                      | Salsinha                     | Cebolinha                    |
|------------------------------|------------------------------|------------------------------|------------------------------|------------------------------|------------------------------|------------------------------|
| Umidade do solo              | 70-80% da capacidade de campo | 70-80% da capacidade de campo | 60-70% da capacidade de campo | 60-70% da capacidade de campo | 60-70% da capacidade de campo | 60-70% da capacidade de campo |
| Temperatura                  | 15-25°C                      | 20-27°C                      | 15-20°C                      | 20-25°C                      | 15-20°C                      | 15-20°C                      |
| Umidade relativa do ar       | 70-80%                       | 70-80%                       | 70-80%                       | 70-80%                       | 70-80%                       | 70-80%                       |
| Luminosidade                 | 8000-10000 lux               | 10000-15000 lux              | 8000-10000 lux               | 8000-10000 lux               | 8000-10000 lux               | 8000-10000 lux               |
| pH do solo                   | 6-7                          | 6-7                          | 6-7                          | 6-7                          | 6-7                          | 6-7                          |
| Condutividade elétrica da água | <2 dS/m                     | <2,5 dS/m                    | <2 dS/m                      | <2 dS/m                      | <2 dS/m                      | <2 dS/m                      |

### Necessidade de Fertilização

| Nutrientes           | Alface                                 | Tomate                                 | Cenoura                                | Coentro                                | Salsinha                               | Cebolinha                              |
|----------------------|----------------------------------------|----------------------------------------|----------------------------------------|----------------------------------------|----------------------------------------|----------------------------------------|
| Nitrogênio (N)        | 100-150 kg/ha                          | 200-300 kg/ha                          | 100-150 kg/ha                          | 60-90 kg/ha                            | 80-120 kg/ha                           | 60-90 kg/ha                            |
| Fósforo (P)           | 50-75 kg/ha                            | 100-150 kg/ha                          | 75-100 kg/ha                           | 30-45 kg/ha                            | 40-60 kg/ha                            | 30-45 kg/ha                            |
| Potássio (K)          | 200-250 kg/ha                          | 250-350 kg/ha                          | 150-200 kg/ha                          | 50-75 kg/ha                            | 70-100 kg/ha                           | 50-75 kg/ha                            |
| Cálcio (Ca)           | 400-600 kg/ha                          | 1000-2000 kg/ha                        | 500-800 kg/ha                          | 300-400 kg/ha                          | 400-600 kg/ha                          | 300-400 kg/ha                          |
| Magnésio (Mg)         | 100-150 kg/ha                          | 200-300 kg/ha                          | 100-150 kg/ha                          | 30-45 kg/ha                            | 40-60 kg/ha                            | 30-45 kg/ha                            |
| Enxofre (S)           | 50-75 kg/ha                            | 100-150 kg/ha                          | 75-100 kg/ha                           | 20-30 kg/ha                            | 30-45 kg/ha                            | 20-30 kg/ha                            |
| Ferro (Fe)            | 2-4 kg/ha                              | 4-6 kg/ha                              | 2-4 kg/ha                              | 1-1,5 kg/ha                            | 1,5-2,5 kg/ha                          | 1-1,5 kg/ha                            |
| Manganês (Mn)         | 1-2 kg/ha                              | 2-3 kg/ha                              | 1-2 kg/ha                              | 0,5-0,75 kg/ha                         | 0,75-1,25 kg/ha                        | 0,5-0,75 kg/ha                         |
| Zinco (Zn)            | 0,5-1 kg/ha                            | 1-1,5 kg/ha                            | 0,5-1 kg/ha                            | 0,25-0,4 kg/ha                         | 0,4-0,6 kg/ha                          | 0,25-0,4 kg/ha                         |
| Cobre (Cu)            | 0,1-0,2 kg/ha                          | 0,2-0,3 kg/ha                          | 0,1-0,2 kg/ha                          | 0,05-0,075 kg/ha                       | 0,075-0,125 kg/ha                      | 0,05-0,075


Lembre-se de que essas são apenas faixas gerais e que cada cultivar pode ter necessidades específicas, por isso é importante fazer uma pesquisa detalhada para entender as necessidades específicas de cada legume e ajustar o sistema de irrigação adequadamente.

Cada um desses legumes tem suas próprias necessidades específicas de irrigação e fertilização, por isso é importante fazer uma pesquisa para entender as necessidades de cada cultivo e ajustar o sistema de irrigação adequadamente.

## Tipo de irrigação


Com base nas necessidades específicas de irrigação do cultivo selecionado (no caso, alface, tomate, cenoura, coentro, salsinha e cebolinha), é possível projetar um escolher um tipo de irrigação adequado para garantir que as plantas recebam a quantidade ideal de água.

Um tipo de irrigação comumente usado é o gotejamento, que fornece água diretamente às raízes das plantas. Esse sistema é altamente eficiente e ajuda a economizar água, pois reduz a evaporação da água na superfície do solo. Além disso, esse sistema permite a aplicação precisa de água, evitando o desperdício e proporcionando um ambiente de cultivo uniforme.

Para projetar um sistema que usa a  irrigação por gotejamento para os cultivos selecionados (alface, tomate, cenoura, coentro, salsinha e cebolinha), é importante considerar as necessidades específicas de cada planta em relação à quantidade de água. 

Por exemplo, a alface precisa de cerca de 1-1,5 cm de água por semana, enquanto o tomate pode precisar de até 2,5 cm de água por semana, dependendo das condições climáticas e do estágio de crescimento da planta.

Além disso, é importante considerar o espaçamento das plantas, a profundidade das raízes e o tipo de solo para determinar a quantidade de água que deve ser fornecida em cada ponto de irrigação. A partir dessas informações, é possível projetar um sistema de irrigação por gotejamento com a quantidade ideal de emissores e tubos, permitindo que a água seja fornecida de forma eficiente e uniforme às plantas.

| Cultivo   | Espaçamento (cm) | Profundidade de irrigação (cm) | Frequência de irrigação (dias) | Quantidade de água (cm/semana) |
|-----------|------------------|--------------------------------|--------------------------------|--------------------------------|
| Alface    | 20-30            | 10-15                          | 2-3                            | 1-1,5                          |
| Tomate    | 60-90            | 15-20                          | 3-4                            | 2-2,5                          |
| Cenoura   | 5-10             | 20-25                          | 5-7                            | 2-3                            |
| Coentro   | 10-15            | 10-15                          | 1-2                            | 1-1,5                          |
| Salsinha  | 5-10             | 10-15                          | 1-2                            | 1-1,5                          |
| Cebolinha | 10-15            | 10-15                          | 1-2                            | 1-1,5                          |


Essa tabela apresenta informações importantes para a definição do sistema de irrigação por gotejamento, como o espaçamento entre as plantas, a profundidade de irrigação necessária, a frequência de irrigação e a quantidade de água ideal por semana para cada tipo de cultivo selecionado. Essas informações podem ajudar no dimensionamento do sistema de irrigação, permitindo que a água seja fornecida de forma eficiente e adequada para cada tipo de planta.

- `Espaçamento (cm)`: se refere à distância entre as plantas e influencia a quantidade de água que deve ser fornecida em cada ponto de irrigação. Quanto maior o espaçamento, maior a quantidade de água necessária para irrigar todas as plantas de forma adequada.

- `Profundidade de irrigação (cm)`: se refere à profundidade em que a água deve ser aplicada no solo para atingir as raízes das plantas. Essa profundidade varia de acordo com o tipo de planta e o tipo de solo. É importante que a água seja aplicada na profundidade adequada para garantir que as raízes recebam água suficiente para o crescimento saudável da planta.

- `Frequência de irrigação (dias)`: se refere à frequência com que a água deve ser fornecida às plantas. Essa frequência varia de acordo com o tipo de planta e as condições climáticas. Em geral, as plantas precisam ser irrigadas com mais frequência durante períodos de alta temperatura ou baixa umidade do ar.

- `Quantidade de água (cm/semana)`: se refere à quantidade ideal de água que deve ser fornecida às plantas por semana. Essa quantidade varia de acordo com o tipo de planta e as condições climáticas. É importante que a quantidade de água fornecida seja adequada para garantir que as plantas recebam água suficiente para o crescimento saudável da planta.

## Etapa 2: Selecionar os componentes necessários

Com base nas necessidades das plantas selecionadas, podemos utilizar os seguintes sensores para coletar dados ambientais e ajustar o sistema de irrigação:

| Sensor                   | Descrição                                                                                                                             | Informações Importantes                                           |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| DHT11 ou DHT22           | Sensor de temperatura e umidade do ar que possui uma interface digital para leitura dos dados.                                         | Temperatura e umidade do ar.                                     |
| LDR (Resistor Dependente de Luz)  | Sensor de luminosidade que varia sua resistência de acordo com a intensidade de luz incidente.                                        | Intensidade da luz ambiente.                                      |
| FC-28 | Sensor de umidade do solo que mede a umidade do solo com alta precisão e possui uma saída analógica para leitura dos dados.             | Umidade do solo.                                                 |
| Sensor de fluxo de vazão | Sensor que mede a vazão de água em litros por minuto e pode ser instalado na tubulação de entrada ou saída da bomba.                 | Quantidade de água fornecida às plantas.                          |
| Sensor de pH             | Sensor que mede o pH do solo e pode ser utilizado para ajustar o pH do solo e garantir que as plantas estejam recebendo nutrientes. | Acidez ou alcalinidade do solo.                                   |
| Sensor de condutividade elétrica | Sensor que mede a salinidade do solo e pode ser utilizado para garantir que as plantas estejam recebendo nutrientes.              | Quantidade de nutrientes no solo.                                 |

Esta tabela apresenta uma lista de sensores que podem ser utilizados em conjunto para coletar informações importantes sobre o ambiente e as plantas em um sistema de irrigação automatizado. As informações coletadas podem ser utilizadas para ajustar o sistema de irrigação e garantir que as plantas recebam a quantidade ideal de água, nutrientes e luz em cada fase do ciclo de cultivo.




Etapa 3: Montar e configurar o hardware


Etapa 4: Programar o microcontrolador ESP32



Etapa 5: Programar o servidor Raspberry Pi



Etapa 6: Desenvolver o aplicativo web



Etapa 7: Testar e ajustar o sistema


´ 
