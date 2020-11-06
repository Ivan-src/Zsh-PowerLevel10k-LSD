# OH-MY-ZSH + PowerLevel10k + LSD

This is my Linux Terminal configuration, tested on Kali Linux, ParrotOS, RedHat and Manjaro.

![Kali_Linux](https://user-images.githubusercontent.com/55292448/98312716-e9533800-1f97-11eb-9855-7a9e4cee6baa.png)

### Install Hack Font
-------------
We need to use a patched font so the terminal will be able to recognize all the icons, I like to use the font "HACK".

https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/Hack/Regular/complete/Hack%20Regular%20Nerd%20Font%20Complete.ttf

### Install Oh-My-ZSH
-------------
`$ sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"`

### Install Powerlevel10k
-------------
`$ git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k`

`$ nano .zshrc`

- In the document .zshrc change 

`ZSH_THEME="robbyrussell" `

- to

`ZSH_THEME="powerlevel10k/powerlevel10k"`

### Use the zsh command to configure the terminal.
-------------
- This are the options that I use:

Prompt Style= Rainbow
Current Time= yes
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

**If the terminal ask you to define zsh terminal as the default, click yes, otherwise you can do it manually after.**

### Configure .p10k.zsh
-------------
Search the following line

```bash
typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
	os_icon
	dir
	vcs
)
```

I add the following plugins:

```bash
typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
	os_icon
	dir
	vcs
	status
	command_execution_time
	context
)
```
And I comment (with #) all the elements in RIGHT_PROMPT because I don't like them.
```bash
typeset -g POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
	#dir
	#vcs
	#status
	#command_execution_time
	#etc
)
```
### Install Neofetch.
-------------
- Debian (Kaali Linux, ParrotOS, Ubuntu, etc.)
`$ sudo apt-get install neofetch`

- Red Hat
`$ sudo dnf-plugins-core`
`$ sudo dnf copr enable konimex/neofetch`
`$ sudo dnf install neofetch`

- Arch
`$ sudo pacman -S neofetch`

### Configure neofetch with the terminal.
-------------
Edit the bashrc and the zshrc file with nano to write the command neofetch.
`$ nano .bashrc`
Go to the bottom and write neofetch, then save it and exit.
`$ nano .zshrc`
We do the same with .zshrc.
We need to do this so the terminal will start with this command and will show us a banner.

### Define ZSH as your default terminal 
-------------
With this command we see where zsh is.
`$ which zsh`
Then we define zsh a default.
`$ sudo userdmod --shell /usr/bin/zsh your_user`
Reboot System to apply changes.
`$ sudo reboot now`

### Another Configuration.
-------------
Execute bash to see the path and export to the zsh terminal.
`$ bash`
`$ echo $PATH`
We copy and paste it at the bottom of the .zshrc file.
`$ nano .zshrc`

It should be something like this, (I added another function for history command and the configuration for LSD).

```bash
# Manual configuration
PATH=paste_PATH

# Manual aliases
alias ll='lsd -lh --group-dirs=first'
alias la='lsd -a --group-dirs=first'
alias l='lsd --group-dirs=first'
alias lla='lsd -lha --group-dirs=first'
alias ls='lsd --group-dirs=first'

# Function
SAVEHIST=1000 
HISTFILE=~/.zsh_history
```

### Descargar e instalar LSD
-------------
Download LSD (I use 0.14.0 version, if you use a newer version could give you issues).
- Doanload: ***lsd_0.14.0_amd64.deb***
https://github.com/Peltoche/lsd/releases/tag/0.14.0

And install it with:
`$ dpkg -i lsd_0.14.0_amd64.deb`

#### NOTE: We need to do all this process with normal user and the root user.
-------------
We could apply all the changes deleting .zshrc from root and just applying changes in .zshrc from normal user a symbolic link (but I haven't tested it yet).

`# ln -s -f /home/your_user/.zshrc .zshrc`

### End
