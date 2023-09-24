## Desenvolvimento e Entrega do Checkpoint 2 - Edge Computing and Computer Systems :rooster:
![Badge Concluido](https://img.shields.io/badge/STATUS-CONCLUIDO-GREEN)

**Nomes + RM dos integrantes:**
- Guilherme Akio - 98582
- Matheus Motta - 550352
- Guilherme Morais - 551981
- Fabrício Saavedra - 97631	
- Vinicius Buzato - 99125

**Turma:** 1ESPW

**Ano:** 2023
___
<img src="Cicuito_ESP32.png">

### Descrição do Projeto
Nesta nova etapa do projeto desenvolvido para a Vinheria Agnello, que busca ajudar na modernização do negócio e principalmente na automação do controle de qualidade de seus produtos e matéria-prima, trabalhamos a partir do _feedback_ fornecido após a segunda parte do projeto:

>“ _Isso é mais legal que o anterior, porém eu preciso vir até aqui para ver o que está acontencedo... Seria melhor se vocês mandassem essas mensagens para o meu computador!_”

Sendo assim, o objetivo nesta etapa foi o de transferir as mesmas leituras já feitas pelo sistema físico de monitoramento para a internet, através do de conceitos de IoI (_Internet of Things_) e plataformas desenvolvidas para essa finalidade. Dessa forma, a funcionalidade final do projeto deve er:
- O sistema deve medir três valores imporantes para o monitoramento de qualidade dos produtos:
    - Temperatura do ambiente, através de um sensor DHT11 🌡️
    - A umidade do ambiente, através de um sensor DHT11 💧
    - A luminosidade do ambiente, através de um sensor LDR 💡
- Os valores obtidos pelos sensores serão enviados para uma plataforma online que possui compatibilidade com os sistemas do Arduino, onde serão exibidos por dashboards para que possam ser monitorados pelos responsáveis pela vinheira, através de qualquer dispositivo que tenha conectividade com a internet.

<img src="Dashboards.png">

- Nos dashboards eles póderão verificar:
  - Ultimas leituras de umidade média;
  - Valor da umidade atual;
  - Ultimas leituras de temperatura média;
  - Valor da temperatura atual;
  - Condição da luminosidade (se está em sua faixa ideal ou não).
___
### Desenvolvimento do projeto
O projeto foi desaenvolvido utilizando a aplicação plataforma [Wowki](https://wokwi.com), para planejamento e rascunho da montagem do circuito físico utilizando a placa [ESP32](https://www.espressif.com/en/products/socs/esp32) (que possui conectividade Bluetooh e WiFi), e a plataforma Arduino, juntamente com seus componentes físicos, para a montagem efetiva do circuito.

A elaboração do circuito final, juntamente com seu código de execução, foi feita através de pesquisas por outros projetos que utilizassem sistemas semelhantes, materiais apresentados em sala de aul e a inteligência artificial ChatGPT,  bem como auxílio do professor, também em sala, até que foi possível arquitetar esta versão final adaptada a nossa necessidade. Assim, foi possível que fizéssemos atualizaçõesno circuito apresentado na primeira entrega, acrescentando as novas funcionalidades solicitadas pelo cliente. 

Já a plataforma utilizada para armazenar os dados enviados foi a paltaforma [Tago](https://tago.io), que foi devidamente configurada para receber as informações captadas pelos sensores, e exibí-las de modo intuitivo através de dashboards específicos.
___
### Como executar o projeto
para executar o projeto é mecessário utilzar o software [Arduino IDE](https://www.arduino.cc/en/software), juntamente com o código presente [neste arquivo]Codigo_Arduino.ino) - anexa também sua [versão em txt](Código_Arduino.txt.txt)
  
E também será necessário um kit básico de componentes físicos do Arduino, juntamente com uma placa ESP32, dos quais serão utilizados:

<table>
  <tr>
    <td><b>Componente</b></td>
    <td align=center><b>Quantidade</b></td>
  </tr>
  <tr>
    <td>ESP32</td>
    <td align=center>1</td>
  </tr>
  <tr>
    <td>Resistor 10kΩ</td>
    <td align=center>1</td>
  </tr>
  <tr>
    <td>Fotorresistor</td>
    <td align=center>1</td>
  </tr>
  <tr>
    <td>Sensor DHT11</td>
    <td align=center>1</td>
  </tr>
    <tr>
    <td>Cabo Micro-USB</td>
    <td align=center>1</td>
  </tr>
  <tr>
    <td>Cabos Jumper</td>
    <td align=center>-</td>
  </tr>
</table>

Para a montagem do circuito, basta reproduzir o [modelo do Wowki](Cicuito_ESP32.png) utilizando os combonentes físicos listados. Para execução, é necessário conectar a placa ESP32 a um computador utilizando o cabo micro-USB, inserir o [código de execução](Codigo_Arduino.ino) no programa Arduino e fazer o upload. Lembrando que o código deve ser ajustado de acordo com o ID e senha da rede WiFi que será utilizada (e que é obrigatória para o funcionamento do circuito).

É necessário possuir um cadastro na plataforma Tago, e criar um novo dispositivo digital que irá receber os dados obtidos pelos sensores. O token específico desse dispoitivo criado deve ser copiado e acrescentado na parte correspondente do código de execução e, após passar a receber os dados do circuito, estes podem ser manuseados e exibidos da forma que se preferir.
___
### Pré-requisitos
Para execução do projeto é necessário conhecimento sobre o uso da plataforma Wowki, experiência com o uso do programa Arduino e de seus componentes físicos, e conhecimento básico de como manusear os recursos de dispositivos, "baldes" e _dashboards_ da plataforma TAGO. É necessário também saber usos básicos da linguagem C++ para entendimento do código e ajustes necesários.
