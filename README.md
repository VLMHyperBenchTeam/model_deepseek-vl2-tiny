# Модель DeepSeek-VL2-tiny

 `DeepSeek-VL2-tiny` — усовершенствованная модель из серии больших Mixture-of-Experts (MoE) Vision-Language Models.
 Построена на базе `DeepSeekMoE-3B` (общее количество активных параметров - 1 млрд.)`.

Материалы:
* [ссылка на GitHub](https://github.com/deepseek-ai/DeepSeek-VL2) 
* [ссылка на научную статью](https://arxiv.org/abs/2412.10302)

Под лицензией [DeepSeek Model License](https://github.com/deepseek-ai/DeepSeek-VL2/blob/main/LICENSE-MODEL).
Модели серии DeepSeek-VL2 могут использоваться в коммерческих целях.

# Docker контейнер модели

## Build Docker image

Сборка `Docker image`

```
docker build -t ghcr.io/vlmhyperbenchteam/deepseek-vl2-tiny:latest -f docker/Dockerfile .
```

## Run Docker Container

Запуск `Docker Container`

```
docker run -it -v ./src:/workspace ghcr.io/vlmhyperbenchteam/deepseek-vl2-tiny:latest
```

Доустановка зависимостей в активированном окружении Python

```
source /opt/venv/bin/activate && pip install -e . && pip install wheel flash_attn xformers
```

Запуск скрипта с примером запуска модели

```
python /workspace/deepseek_simple_test.py
```

# Рекомендации от создателей

1. Использовать температуру T <= 0.7.
2. Чтобы сохранить управляемость числа токенов в окне контекста, применяют стратегию динамического разбиения (`dynamic tiling strategy`) для 1-го или 2-х изображений. Когда изображений больше 3-х, напрямую дополняют изображения до 384х384 в качестве входных данных без разбиения.
3. Основное различие между DeepSeek-VL2-Tiny, DeepSeek-VL2-Small и DeepSeek-VL2 заключается в базовом LLM.
