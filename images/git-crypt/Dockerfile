FROM debian:buster-slim

ARG GID=1000
ARG UID=1000
ARG GIT_CRYPT_VERSION=nightly
ARG USER=git-crypt

RUN apt-get update && \
    # Install basic requirements
    apt-get install -y git git-crypt zsh curl tmux && \
    # Tidy up apt
    apt-get clean

# add user group
RUN groupadd -g ${GID} ${USER} && useradd -u ${UID} -g ${GID} -m ${USER}

USER ${USER}
WORKDIR /home/${USER}

# Make zsh your default shell for tmux
RUN echo "set-option -g default-shell /bin/zsh" >> /home/${USER}/.tmux.conf

# install oh-my-zsh
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
