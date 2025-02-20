---
title: "Neovim"
date: 2020-12-16T17:04:43-03:00
summary: "How to install, use and configure Neovim"
description: "Neovim Guide"
tags:
- cli
- step-by-step
- plugins
- editor
- programming
- code
categories: Neovim
ShowToc: true
draft: false
---

## Oque é?

[Neovim](https://neovim.io/) é um editor de texto baseado no Vim que roda via CLI (Linha de comando), com a possibilidade de instala plugins.

## Instalar neovim
Executei o comando
```bash
$ sudo apt install python3-neovim
```
no Parrot Sec 4.10 e ele instalou o neovim e os módulos python para ele automaticamente.

A forma mais direta de instalar usando uma disctribuição debain-based é com 
```bash
$ sudo apt install neovim
```
Para abrir o neovim basta executar o comando `nvim` no terminal.

Arquivo de configurações do neovim:
`~/.config/nvim/init.vim`

## Uso

O padrão do neovim é baseado no vim, etão todos os comandos do vim funcionam no neovim.

O vim possui 2 modos, modo de edição e modo de comando, o modo de edição é o modo onde podemos editar o arquivo, pode ser ativado com a tecla `INSERT`, e o modo de comando é o modo onde podemos rodar comandos do vim, para ativar o modo comando pressione a tecla `ESC`.

Todos os comandos do neovim devem ser adicionados após `:` no buffer do neovim.

### Comandos

descrição | comando
---|---
Sair | `:q`
Sair sem salvar | `:q!`
Salvar um arquivo | `:w`
Salvar e sair | `:wq`
Deletar um caractere | `x`
Desfazer uma ação | `u`
Procurar uma letra ou palavra | `/palavra`

### Atalhos

Alguns atalhos do modo de edição

Ir para o início da linha - `home`

Ir para o final da linha - `end`

Navegar para cima e para baixo - `Page Up` e `Page Down`

Apagar uma linha - `CTRL+U`

## Instalar Plugins
### step-by-step
O gerenciador de plugins que vou usar é o [VimPlug](https://github.com/junegunn/vim-plug).

#### Configurar nvim para instalar pluggins:

Instale o gerenciador VimPlug:
```bash
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
Adicione essas linhas no `~/.config/nvim/init.vim`
```vim
call plug#begin()
" Your plugins...
call plug#end()
```
_ex:_
```vim
call plug#begin()
Plug 'roxma/nvim-completion-manager'
Plug 'SirVer/ultisnips'
Plug 'honza/vim-snippets'
call plug#end()
```

#### Instalar plugins

Você pode encontrar muitos plugins no site [VimAwesome](https://vimawesome.com/). Escolha um e adicione as linhas do plugins entre a função `call plug#begin()` e `call plug#end()` no arquivo `~/.config/nvim/init.vim`.
```vim
call plug#begin()                                                                                                                                                                                                                                
Plug 'valloric/youcompleteme'                                                                                                         
call plug#end()
 ```
segundo o padrão `Plug 'nomedodesenvolvedor/nomedoplugin'`.

depois execute os comandos a seguir no nvim
```
:PlugInstall
:UpdateRemotePlugins
```

### Meus Plugins

#### **emmet-vim**

_Download_: https://vimawesome.com/plugin/emmet-vim

_Plugin Label_: `'mattn/emmet-vim'`

_Usage_:

Escreva a abreviação do código, depois aperte `CTRL+Y+,`. 

ex1:

```html
html:5
```
> `CTRL+Y+,`
```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
	</body>
</html>
```
ex2:
```html
div>ul>li*5
```
> `CTRL+Y+,`
```html
<div>
	<ul>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
	</ul>
</div>
```

_Additional Config_
```vim
let g:user_emmet_leader_key='<C-Z>' " remap keybind to CTRL+Z+,
```

#### **jedi-vim**

_Downlaod_: https://vimawesome.com/plugin/jedi-vim

_Plugin Label_: 'davidhalter/jedi-vim'

_Usage_:
Autocomplete de padrões de código

#### **AutoClose**

_Download_: https://vimawesome.com/plugin/autoclose

_Plugin Label_: 'townk/vim-autoclose'

_Usage_:
Fecha alguns caracteres de escopo automaticamente, como (), [], {}, '', ""...

#### **vim-closetag**

_Download_: https://vimawesome.com/plugin/vim-closetag

_Plugin Label_: 'alvan/vim-closetag'

_Usage_: Auto completa tags HTML

#### **tabnine-vim**

_Download_: https://www.tabnine.com/install

_Plugin Label_: 'zxqfl/tabnine-vim'

_Usage_: IA para prever textos e oferecer um autocomplete inteligente

#### **vim-workspace**

_Download_: https://vimawesome.com/plugin/vim-workspace

_Plugin Label_: 'thaerkh/vim-workspace'

_Usage_: Disponibilisa funcionalidades interessantes, mas eu uso so o autosave, porque é  o único que sei usar

_Additional Config_:
```vim
let g:workspace_autosave_always = 1
```

#### **vim-airline**

_Download_: https://vimawesome.com/plugin/vim-airline-superman

_Plugin Label_: 'vim-airline/vim-airline'

_Usage_: Exibe uma barra de status com informações sobre a branch atual, tipo de arquivo, modo de edição, êtc... brabo demais.

#### **vim-wakatime**

_Download_: https://wakatime.com/vim

_Plugin Label_: 'wakatime/vim-wakatime'

_Usage_: Disponibiliza uma dashboard com statísticas de tempo em uma determinada linguage, projeto, editor...
Tudo isso no site da Wakatime

#### **editorconfig-vim**

_Download_: https://github.com/editorconfig/editorconfig-vim

_Plugin Label_: 'editorconfig/editorconfig-vim'

_Usage_: Padroniza configuração de editores atraves do arquivo `.editorconfig`


---

referencias:

Installing Neovim: [_https://github.com/neovim/neovim/wiki/Installing-Neovim_](https://github.com/neovim/neovim/wiki/Installing-Neovim)

How to find a Word in Vim or vi text editor: [_https://www.cyberciti.biz/faq/find-a-word-in-vim-or-vi-text-editor/_](https://www.cyberciti.biz/faq/find-a-word-in-vim-or-vi-text-editor/)

How to Install NeoVim and Plugins with vim-plug: [_https://www.linode.com/docs/guides/how-to-install-neovim-and-plugins-with-vim-plug/_](https://www.linode.com/docs/guides/how-to-install-neovim-and-plugins-with-vim-plug/)

