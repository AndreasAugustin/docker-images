FROM debian:buster-slim

ARG GID=1000
ARG UID=1000
ARG USER=git-crypt
ARG GITHUB_URL="https://github.com/AndreasAugustin/docker-images/tree/main/images/git-crypt"

# https://github.com/opencontainers/image-spec/blob/main/annotations.md#pre-defined-annotation-keys
LABEL org.opencontainers.image.url="${GITHUB_URL}"
LABEL org.opencontainers.image.documentation="${GITHUB_URL}/README.md"
LABEL org.opencontainers.image.licenses="MIT"
LABEL org.opencontainers.image.authors="andyAugustin"
LABEL org.opencontainers.image.title="git-crypt image"
LABEL org.opencontainers.image.description="contains git-crypt"

RUN apt-get update && \
    # Install basic requirements
    apt-get install -y git git-crypt zsh curl tmux make && \
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

CMD [ "/bin/zsh" ]
