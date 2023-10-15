FROM mcr.microsoft.com/devcontainers/rust:1-1-bookworm

RUN apt-get update && apt-get -y install \
    zsh \
    sed \
    git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN zsh

ENV SHELL /usr/bin/zsh

RUN git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"

# TODO: forceフラグを利用せずに設定を完了させる
RUN ln -s $HOME/.zprezto/runcoms/zlogin       $HOME/.zlogin \
    && ln -s $HOME/.zprezto/runcoms/zlogout   $HOME/.zlogout \
    && ln -s $HOME/.zprezto/runcoms/zpreztorc $HOME/.zpreztorc \
    && ln -s $HOME/.zprezto/runcoms/zprofile  $HOME/.zprofile \
    && ln -s $HOME/.zprezto/runcoms/zshenv    $HOME/.zshenv \
    && ln -s --force $HOME/.zprezto/runcoms/zshrc     $HOME/.zshrc

RUN chsh -s /bin/zsh
RUN sed -ri "s/theme 'sorin'/theme 'skwp'/g" ~/.zpreztorc
RUN sed -ri "s/'prompt'/'prompt' 'archive' 'syntax-highlighting' 'autosuggestions' 'git'/g" ~/.zpreztorc

CMD [ "zsh" ]
