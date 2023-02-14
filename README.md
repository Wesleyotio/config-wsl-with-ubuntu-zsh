# Configurando o WSL com o Ubuntu 22.04 + ZSH

O WSL é uma excelente alternativa para desenvolvedores que querem possuir todas as vantagens do Windows e ainda manter toda a produtividade que o ambiente Linux pode oferecer.

Esta postagem é uma versão customizada do artigo da [Fullcycle](https://fullcycle.com.br) que está nesse link: [Guia rápido do WSL2 + Docker](https://github.com/codeedu/wsl2-docker-quickstart).

Também vou deixar o aqui os videos do youtube que me ajudaram a fazer esta configuração.
 - [A forma mais produtiva para utilizar Docker no Windows e WSL2](https://www.youtube.com/watch?v=g4HKttouVxA&list=LL&index=113&t=4402s)     
 - [Ambiente perfeito de Docker com VSCode e WSL2](https://www.youtube.com/watch?v=a49gYcBwITc&list=LL&index=112&t=7661s)
 - [O Melhor Setup Dev com Arch e WSL2](https://www.youtube.com/watch?v=sjrW74Hx5Po)

# Índice

- [Configurando o WSL com o Ubuntu 22.04 + ZSH](#configurando-o-wsl-com-o-ubuntu-2204--zsh)
- [Índice](#índice)
- [Instalando o WSL2](#instalando-o-wsl2)
  - [Para Windows 11](#para-windows-11)
  - [Para Windows 10](#para-windows-10)
  - [Configuração de recursos de maquina no WSL](#configuração-de-recursos-de-maquina-no-wsl)
- [Escolhendo uma distro Linux](#escolhendo-uma-distro-linux)
- [Usando docker nativo](#usando-docker-nativo)
- [Habilitando o VScode](#habilitando-o-vscode)
- [ZSH e OhMyZsh](#zsh-e-ohmyzsh)
- [Nerds Fonts](#nerds-fonts)

# Instalando o WSL2
Antes de iniciar a instalação do WSL2 propriamente dita acredito que valha muito a pena instalar antes o [windows terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=pt-br&gl=br) por ser um emulador de terminal melhorar muito nossa produtividade alem de ser altamente customizável. Pode ser encontrado diretamente na Microsoft Store procurando por **windows terminal**, também será mostrado o windows terminal preview que é a versão beta que recebe as atualizações mais recentes.

![Image description](config-wsl2-wt-fig1.png)

Agora que temos o windows terminal instalado podemos executa-lo em modo **administrador**, de acordo com a documentação mais atualizada, você deve rodar o  comando.
## Para Windows 11
```sh
wsl --install
```
O processo pode ser um pouco demorado e por padrão no windows 11 a distro Ubuntu é instalada, para especificar qual distro você deseja instalar primeiro precisa listar as disponíveis usando o comando: 
 ```sh
wsl --list --online
```
E o **resultado** apresentado no terminal será este:
 ```sh
 NAME               FRIENDLY NAME
Ubuntu             Ubuntu
Debian             Debian GNU/Linux
kali-linux         Kali Linux Rolling
SLES-12            SUSE Linux Enterprise Server v12
SLES-15            SUSE Linux Enterprise Server v15
Ubuntu-18.04       Ubuntu 18.04 LTS
Ubuntu-20.04       Ubuntu 20.04 LTS
Ubuntu-22.04       Ubuntu 22.04 LTS
OracleLinux_8_5    Oracle Linux 8.5
OracleLinux_7_9    Oracle Linux 7.9
```

Escolhida a distro executamos o comando com o nome igual ao apresentado na lista acima.

 ```sh
 wsl --install -d Ubuntu-22.04 
 ```
## Para Windows 10

Aqui as etapas mudam um pouco, inicialmente vamos rodar o seguinte comando para habilitar o WSL, sempre em modo **administrador**  

```sh
 dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
 ```
Em seguida habilitamos a virtualização
```sh
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
Em seguida **reiniciamos** o sistema.

Agora precisamos baixar o [pacote de atualização](https://learn.microsoft.com/pt-br/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package) do kernel do linux e executa-lo. Com a instalação concluída com sucesso vamos tornar a versão do WSL2 como a padrão.
```sh
wsl --set-default-version 2
```
## Configuração de recursos de maquina no WSL

Em termos de recurso o WSL é um lobo feroz, podendo consumir por padrão os seguintes números.
 - Quase totalmente o processamento disponível
 - 80% da memória RAM
 - 25% do SWAP

Para limitar esse consumo basta criar o arquivo **.wslconfig** em sua pasta raiz do usuário **C:\Users\nameuser** como demostrado a seguir.
```sh
[wsl2]
memory=3GB
processors=4
swap=4GB
```
# Escolhendo uma distro Linux
Abra a [Microsoft store](https://aka.ms/wslstore) e escolha sua distro.

![Image description](config-wsl2-wt-fig2.png)

Selecione a que mais te agradar clique em instalar, nesse caso selecionaremos a 22.04 LTS

![Image description](config-wsl2-wt-fig3.png)

Terminada a instalação da distro ao inicia-la teremos a seguinte imagem solicitando a criação de um usuário para o sistema. Com isso temos certeza que nosso WSL2 está funcionando plenamente.

![Image description](config-wsl2-wt-fig4.png)

Com sua conta criada com sucesso está será sua visualização, agora oficialmente você é um usuário do Linux no Windows. Parabéns!!!

![Image description](config-wsl2-wt-fig5.png)


**PS:** Caso nenhuma das distro apresentadas seja do seu agrado é possível instalar qualquer distro, mas como o foco aqui é no Ubuntu deixo somente o link para quem quiser se aventurar. [Importar qualquer distribuição do Linux a ser usada com o WSL](https://learn.microsoft.com/pt-br/windows/wsl/use-custom-distro)   


# Usando docker nativo
Além de reduzir o consumo de recursos drasticamente em relação ao docker desktop temos o controle total dentro do Linux não dependendo de um terceiro. Neste [link](https://docs.docker.com/engine/install/) é explicado como fazer a instalação em outras distros Linux fora o Ubuntu.
 
# Habilitando o VScode

# ZSH e OhMyZsh

# Nerds Fonts
