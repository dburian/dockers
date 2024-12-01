FROM dburian/dotfiles
WORKDIR /root
RUN apt install -y python3 python3-pip python3-venv;\
    python3 -m venv ml_venv;\
    . ml_venv/bin/activate;\
    pip install pandas numpy jupyterlab jupytext seaborn matplotlib tqdm ipywidgets ruff pyright;
RUN <<EOT cat >> ~/.bashrc
alias python="python3"

# Activating default python virtual environment
. /root/ml_venv/bin/activate
EOT
CMD bash
