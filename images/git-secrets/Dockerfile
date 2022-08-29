FROM debian:buster-slim

ARG GID=1000
ARG UID=1000
ARG USER=git-secrets
ARG GITHUB_URL="https://github.com/AndreasAugustin/docker-images/tree/main/images/git-secrets"

# # https://github.com/opencontainers/image-spec/blob/main/annotations.md#pre-defined-annotation-keys
LABEL org.opencontainers.image.url="${GITHUB_URL}"
LABEL org.opencontainers.image.documentation="${GITHUB_URL}/README.md"
LABEL org.opencontainers.image.licenses="MIT"
LABEL org.opencontainers.image.authors="andyAugustin"
LABEL org.opencontainers.image.title="git-secrets image"
LABEL org.opencontainers.image.description="contains git-secrets"

RUN apt-get update && \
    # Install basic requirements
    apt-get install -y git zsh curl tmux make && \
    # Tidy up apt
    apt-get clean

# add user group
RUN groupadd -g ${GID} ${USER} && useradd -u ${UID} -g ${GID} -m ${USER}

# install git-crypt
RUN mkdir /git/  && \
    git clone https://github.com/awslabs/git-secrets.git /git/git-secrets/ && \
    cd /git/git-secrets && \
    make install

USER ${USER}
WORKDIR /home/${USER}

# Make zsh your default shell for tmux
RUN echo "set-option -g default-shell /bin/zsh" >> /home/${USER}/.tmux.conf

# install oh-my-zsh
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# ENTRYPOINT [ "/bin/zsh" ]
CMD [ "/bin/zsh" ]
