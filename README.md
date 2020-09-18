# OH-MY-ZSH + PowerLevel10k + LSD

This is my Linux Terminal configuration.

# Install Oh-My-Bash

sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"

# Install Powerlevel10k

git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
nano .zshrc
Cambiar ZSH_THEME="robbyrussell" a 
ZSH_THEME="powerlevel10k/powerlevel10k"

Configurar entorno con el comando: zsh
Prompt Style:
Rainbow
Current Time - yes
Prompt Separators = Angled
Blurred
Blurred
One Line
Separed
Many Icons
Fluent
Transient Prompt = No
Instant Prompt Mode = Off
Apply Changes = yes

# Configurar .p10k.zsh

typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
	os_icon
	dir
	vcs
	status
	command_execution_time
	context
)

typeset -g POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
#COMENTAR TODO
	#dir
	#vcs
	#status
	#command_execution_time
)

NOTA: Para root buscar la linea "typeset -g POWERLEVEL9K_CONTEXT_ROOT_TEMPLATE="..."
cambiar por POWERLEVEL9K_CONTEXT_ROOT_TEMPLATE="# " y comentar la linea #typeset -g POWERLEVEL9K_CONTEXT_PREFIX='with'


# Instalar Neofetch

>> Debian (Apt)
sudo apt-get install neofetch

>> Red Hat
sudo dnf-plugins-core
sudo dnf copr enable konimex/neofetch
sudo dnf install neofetch

>> Arch
sudo pacman -S neofetch

# Ejecutar neofetch al iniciar la consola

nano .bashrc
**Ir al final del archivo y escribir neofetcch

#Definir ZSH como la consola por default ========

which zsh
sudo userdmod --shell /usr/bin/zsh mrrob0t
**Reiniciar**

# Configurar el archivo .zshrc con neofetch
ir al final y escribir neofetch


NOTA: Hacer esto tanto para el usuario normal como para el usuario root

# Themes for zhs
https://github.com/ohmyzsh/ohmyzsh/wiki/Themes


# Otras configuraciones para .zshrc
Ejecutar bash para obtener el path
	echo $PATH
Copiar y pegar en .zshrc

# Manual configuration
PATH="pegar_sin_parentesis"

# Manual aliases
alias ll='lsd -lh --group-dirs=first'
alias la='lsd -a --group-dirs=first'
alias l='lsd --group-dirs=first'
alias lla='lsd -lha --group-dirs=first'
alias ls='lsd --group-dirs=first'


# Function
SAVEHIST=1000 
HISTFILE=~/.zsh_history

# Descargar e instalar LSD

https://github.com/Peltoche/lsd/releases/tag/0.14.0
descargar: lsd_0.14.0_amd64.deb
dpkg -i lsd_0.14.0_amd64.deb



# !!!!WARNING!!!!!
Se pueden aplicar los cambios solo a un archivo borrando la .zshrc de root y solo aplicar cambios en el usuario normal con un link (I haven't tested yet).
ln -s -f /home/mrrob0t/.zshrc .zshrc
