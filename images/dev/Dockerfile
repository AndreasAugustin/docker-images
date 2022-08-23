#######################################
# image for dev build environment
######################################
FROM alpine:3.16.2 as DEV

ARG USER=dev
ARG GROUP=dev

# install packages
RUN apk add --update --no-cache bash make git zsh curl tmux

# add user group
RUN addgroup -S ${GROUP} && adduser -G ${GROUP} -S ${USER}

USER ${USER}
WORKDIR /home/${USER}

# Make zsh your default shell for tmux
RUN echo "set-option -g default-shell /bin/zsh" >> /home/${USER}/.tmux.conf

# install oh-my-zsh
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

ENTRYPOINT [ "/bin/zsh" ]


#######################################
# image for creating the documentation
######################################

FROM node:18.7.0-alpine as DOCS

ARG USER=docs
ARG GROUP=docs

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

ENTRYPOINT [ "/bin/zsh" ]

