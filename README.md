# CLI2-Mbed


"CLI" é uma "Command-Line Interface", ou seja, uma interface pra realizar operações diretamente da prompt de comando. O Mbed possui a própria CLI (atualmente a CLI2) que consegue compilar códigos para placas que utilizam o mbed, facilitando o uso dos usuários. Comparando com o Keil Studio, por exemplo, as vantagens do CLI seriam:

- Maior customização (possibilidade de escolha do ambiente de programação)
- Possibilidade de trabalhar offline
- Não depender dos servidores do ou contas do Keil Studio

Já as desvantagens são:

- Requer o download do Mbed OS (1GB)
- O CLI 2 trabalha em Mbed OS 6, que é diferente do Mbed OS 2 utilizado usualmente na disciplina. 

O fluxo de trabalho com o uso do CLI se resume a baixar o sistema Mbed base, editar os arquivos C++ (como o main.cpp) em qualquer editor de código e, por fim, compilar o código para sua placa de escolha. Abaixo seguem instruções de como instalar e utilizar o CLI 2 do Mbed, baseados na documentação da Arm: https://os.mbed.com/docs/mbed-os/v6.16/build-tools/mbed-cli-2.html 

## 1. Instalando dependências

### 1.0. Caso não tenha, instale python
O python do anaconda pode apresentar problemas. Caso não tenha o python fora o do anaconda (ou não tenha certeza), baixe a última versão do python: https://www.python.org/downloads/

Baixando do site oficial, execute o arquivo .exe. Marque a opção "Add python.exe to PATH" e clique em "Install Now". Após a instalação. clique em "Close"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/c9b5b4b1-82f6-43d2-ac16-a2a34cdb62b4)


### 1.1. Dependências com pip install:
1. Abra a prompt de comando (cmd no Menu Iniciar Windows)
2. Digite e rode os seguintes comandos (para instalar o ninja e o Jinja2):
   
````pip install -U Jinja2````

````python -m pip install ninja````
  
![image](https://github.com/ThiTeiSan/CLI2-Mbed/assets/167451264/234b9324-3ea4-4eec-bb60-dca419b8885e)

### 1.2. Instalando CMAKE:
Vá no link: https://cmake.org/download/

Abaixo de "Binary distributions", clique na última versão que deseja instalar. Para windows, clique no que contenha "Windows x64 Installer"

![image](https://github.com/ThiTeiSan/CLI2-Mbed/assets/167451264/d46311f8-e886-427b-b23e-11d0815b92c5)

Execute o arquivo.

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/c6643e1c-9edb-42a1-a73b-ab3e0b8042ed) Clique em "Next"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/f15c55ff-1ed0-49ea-8fe5-1c341f5def57) Marque para aceitar os termos e clique em "Next"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/8da5bf84-4f2b-49cd-885b-8ae82c9b012c) Marque para adicionar o CMake ao PATH (segunda ou terceira opção) e clique em "Next"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/98d18045-5d52-4423-9689-7e47b1545b5e) Clique em "Next"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/ab3fd7f4-f31d-452b-8c33-60cf584830c5) Clique em "Install" e aguarde

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/02f70bba-f913-4034-8e34-fad4473a57e3) Clique em "Finish"


### 1.3. Instalando o toolchain da arm:
Acesse o link: https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads

Baixe o .exe do "arm-gnu-toolchain-13.2.rel1-mingw-w64-i686-arm-none-eabi"

![image](https://github.com/ThiTeiSan/CLI2-Mbed/assets/167451264/005714d3-b23d-40ea-a9bf-2d97d0cd3228)

Execute o arquivo.

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/2c3be5ec-1523-4302-a75c-6c06155d534c) Selecione a linguagem do instalador e clique em "OK"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/374f9a0b-89ea-4e95-a7de-e74cbcf100c1) Clique em "Próximo"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/60e8050c-21cc-43cd-9022-a43c401c256c) Clique em "Eu concordo"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/86bf542c-64b9-4a23-9892-5ca87ca59674) Clique em "Instalar"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/ba767c21-e2c0-4430-8420-9446df29e6c7) Certifique-se que a terceira opção está ativada (Add path to environment variable) e clique em "Concluir".



## 2. Instalando o CLI 2 do Mbed

1. Abra a prompt de comando (repita os passos de 1.1) e digite e rode o código:
````python -m pip install mbed-tools````
2. Para saber se funcionou, rode o comando:
````mbed-tools --help````

Resultado esperado:

![image](https://github.com/ThiTeiSan/CLI2-Mbed/assets/167451264/d34c4986-bf77-4f00-a0b6-6e802a3a7cbe)

Caso apareça um erro igual ao da imagem a seguir:
![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/44e113dd-9954-4641-86f6-dcfe08bad25f)

Insira o comando ````pip install setuptools```` no cmd e tente novamente.

Caso o erro mude para:
![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/3b1a86ac-e45e-4707-804e-8d51f9cd486f)

Será necessário **Instalar o Git**

### 2.1. Instalando o Git, se necessário

Acesse o site https://git-scm.com/download/win e instale o Standalone Installer para 64 bits. Execute o arquivo.

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/ac5f1dc6-0cc2-437c-93e1-f9403fbc363d) Vá clicando em "Next"

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/6e338068-19db-4cd5-a9f5-61a162d65692) Ao chegar nessa tela, abra as opções e selecione o Visual Studio Code (ou qualquer editor que tenha) como editor padrão. Caso não tenha nenhum instalado, utilize o "Notepad". Continue clicando em "Next"s

![image](https://github.com/Insper-Mecat-LSM/CLI-2-Mbed/assets/167451264/5ea45e2c-e887-482d-b504-bc936da0e239) Quando chegar nessa página, clique em "Install" e aguarde instalar.


## 3. Utilizando o CLI 2
Agora que tudo está intalado, aqui segue alguns comandos úteis para a utilização do CLI 2

### 3.1. Detectando uma placa
Conecte alguma placa no computador e rode o comando:
````
mbed-tools detect
````

Resultado esperado (para placa Nucleo F303RE):

![image](https://github.com/ThiTeiSan/CLI2-Mbed/assets/167451264/f754a589-7b29-4d21-9cb3-43a089ac2ef4)

### 3.2. Criando um novo projeto

O comando
````
mbed-tools new <PATH>
````

Cria um novo projeto, importando uma versão do Mbed OS 6. "\<PATH>" é o diretório onde o projeto será configurado. Por exemplo "mbed-tools new .\aps_4" cria uma pasta "aps_4" e baixa os arquivos para dentro dela.

> [!WARNING]
> O comando ````mbed-tools new <PATH>```` baixa uma nova versão do Mbed OS toda vez que ele é rodado (+- 1GB). Você pode rodar ````mbed-tools new -c <PATH>```` onde o ````-c```` previne o download de uma nova versão, e você pode copiar de um outro projeto.

Adicionalmente, é possível importar projetos de exemplo da Mbed através do comando

````
mbed-tools import <example> <PATH>
````

Por exemplo, o comando ````mbed-tools import mbed-os-example-blinky```` irá baixar o exemplo blinky em uma pasta.



### 3.3 Compilando um projeto

O comando 
````
mbed-tools compile -m <target> -t <toolchain>
````
Irá compilar o projeto. O ````<target>```` é a placa que está conectada. Caso esteja em dúvida, você pode adquirir o código que precisa colocar aqui através do ````mbed-tools detect````, na coluna "Build targets(s)". O ````<toolchain>```` será sempre ````GCC_ARM````, a menos que você baixe um toolchain diferente do indicado no tutorial.

O arquivo ````.bin```` fica salvo dentro do diretório ".\cmake_build\<target>\develop\GCC_ARM" e você pode mandá-lo para a placa.

Caso você queira compilar o código e já carregar para a placa em um único comando, basta adicionar o parâmetro ````-f````, resultando em:
````
mbed-tools compile -m <target> -t <toolchain> -f
````

## 4. Exemplo de uso com VSCode

(Caso não tenha, link de instalação: https://code.visualstudio.com/download)

- Abra o VSCode abra uma nova pasta vazia.
- Aperte ````Ctrl````+````'```` Para abrir a prompt de comando do VSCode.
- Insira e rode o comando ````mbed-tools new .```` (já que o terminal já abre no diretório da pasta)
![image](https://github.com/ThiTeiSan/CLI2-Mbed/assets/167451264/2f761ccd-1ffd-4a16-aa4b-406f9e6b7b02)

- Após o programa: (novos arquivos apareceram)
![image](https://github.com/ThiTeiSan/CLI2-Mbed/assets/167451264/ef8d592e-4396-4935-95b8-4d6e2641aa6f)

- Vá no ````main.cpp```` e edite o código. Abaixo segue o código para um blinky:
````
#include "mbed.h"

// Blinking rate in milliseconds
#define BLINKING_RATE     300ms
DigitalOut led(LED1);

int main()
{
    // Initialise the digital pin LED1 as an output
    while (true) {
        led = 1;
        ThisThread::sleep_for(BLINKING_RATE);
        led = 0;
        ThisThread::sleep_for(BLINKING_RATE);
    }
}
````
- Salve o programa (````Ctrl````+````S````).
- No terminal, digite o código ````mbed-tools compile -m <target> -t GCC_ARM -f```` substituindo o ````<target>```` com a sua placa. Nesse exemplo, está sendo usada a Nucleo F303RE. Rodar o código pela primeira vez demora um pouco (+- 1min30s)
  
![image](https://github.com/ThiTeiSan/CLI2-Mbed/assets/167451264/a30a17af-54c3-420b-90d6-530a754c93d7)

- O projeto deve ter sido compilado para a placa!
  
![image](https://github.com/ThiTeiSan/CLI2-Mbed/assets/167451264/a1b56869-7f8c-48ff-9443-db176f1a7639)
