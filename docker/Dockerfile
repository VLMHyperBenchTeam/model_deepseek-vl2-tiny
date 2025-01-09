# Образы для контейнера
FROM nvidia/cuda:12.5.1-cudnn-devel-ubuntu22.04

# Установка инструментов для сборки
RUN apt-get update -y && apt upgrade -y && apt install -y --no-install-recommends \
    git \
    python3 \
    python3-pip \
    python3-dev \
    python3-venv \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Создание ссылки для python
RUN ln -s /usr/bin/python3 /usr/bin/python

# Создание рабочей директории
WORKDIR /workspace

# Создание дополнительной директории для репозитория с моделью
WORKDIR /model

# Клонирование репозитория с моделью
RUN git clone https://github.com/deepseek-ai/DeepSeek-VL2.git /model

# Создание виртуального окружения
RUN python -m venv /opt/venv

# Запуск терминала
CMD ["/bin/bash"]
