FROM ubuntu:latest
WORKDIR /root/repos
RUN apt-get update -y; \
  apt-get install -qy vim curl git ripgrep universal-ctags \
fzf ninja-build gettext cmake unzip curl build-essential tmux; \
  git clone https://github.com/dburian/dotfiles;
WORKDIR /opt
RUN git clone https://github.com/neovim/neovim.git;\
    cd neovim;\
    CMAKE_BUILD_TYPE=RelWithDebInfo make;\
    make install;
WORKDIR /root/.config
RUN ln -s /root/repos/dotfiles/.config/nvim;\
    ln -s /root/repos/dotfiles/.config/git;\
    ln -s /root/repos/dotfiles/.config/tmux;
RUN <<EOF cat >> ~/.bashrc
export XDG_CONFIG_HOME="\$HOME"/.config
export XDG_CACHE_HOME="\$HOME"/.cache
export XDG_DATA_HOME="\$HOME"/.local

export PATH="\$PATH":"\$HOME"/.local/bin
export EDITOR="nvim"

#Aliases
alias l="ls -lah --color=always"
alias v="nvim"
EOF

WORKDIR /root
CMD bash
