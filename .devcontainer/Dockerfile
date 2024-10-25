FROM mcr.microsoft.com/devcontainers/base:jammy as Config

COPY .zshrc home/vscode/.zshrc

# Install zsh-autosuggestions plugin
ENV ZSH_CUSTOM=/home/vscode/.oh-my-zsh/custom

RUN git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
RUN git clone https://github.com/spaceship-prompt/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
RUN ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"

FROM mcr.microsoft.com/devcontainers/jekyll:3.3-bookworm
COPY --from=Config /home/vscode/.zshrc /home/vscode/.zshrc
COPY --from=Config /home/vscode/.oh-my-zsh /home/vscode/.oh-my-zsh