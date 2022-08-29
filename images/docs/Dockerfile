#######################################
# image for creating the documentation
######################################

FROM node:18.7.0-alpine as DOCS

ARG USER=docs
ARG GROUP=docs
ARG GITHUB_URL="https://github.com/AndreasAugustin/docker-images/tree/main/images/docs"

# https://github.com/opencontainers/image-spec/blob/main/annotations.md#pre-defined-annotation-keys
LABEL org.opencontainers.image.url="${GITHUB_URL}"
LABEL org.opencontainers.image.documentation="${GITHUB_URL}/README.md"
LABEL org.opencontainers.image.licenses="MIT"
LABEL org.opencontainers.image.authors="andyAugustin"
LABEL org.opencontainers.image.title="docs image"
LABEL org.opencontainers.image.description="base image used for documentation purposes"

# install packages
RUN apk add --update --no-cache bash make git zsh curl tmux

# install quality gate
RUN npm install -g markdownlint-cli

# add user group
RUN addgroup -S ${GROUP} && adduser -G ${GROUP} -S ${USER}

USER ${USER}
WORKDIR /home/${USER}

# Make zsh your default shell for tmux
RUN echo "set-option -g default-shell /bin/zsh" >> /home/${USER}/.tmux.conf

# install oh-my-zsh
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

CMD [ "/bin/zsh" ]
