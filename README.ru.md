# grafanalib

[![Documentation Status](https://readthedocs.org/projects/grafanalib/badge/?version=main)](https://grafanalib.readthedocs.io/en/main)

**Python-библиотека для описания дашбордов Grafana в коде.**

Это форк репозитория [weaveworks/grafanalib](https://github.com/weaveworks/grafanalib), поддерживаемый [Ranas Mukminov](https://github.com/ranas-mukminov) для использования сообществом.

[Русский] | [English](README.md)

---

## Обзор

Вам нравится [Grafana](http://grafana.org/), но вы хотите версионировать конфигурацию дашбордов? Вам надоело повторять одни и те же паттерны? Тогда grafanalib — для вас.

grafanalib позволяет генерировать дашборды Grafana из простых Python-скриптов, делая ваши дашборды:
- **Версионируемыми** – отслеживайте изменения в Git
- **Переиспользуемыми** – выносите общие паттерны в функции
- **Тестируемыми** – проверяйте конфигурацию в CI/CD

## Быстрый старт

Установите grafanalib:

```bash
pip install grafanalib
```

Скачайте пример дашборда:

```bash
curl -o example.dashboard.py \
  https://raw.githubusercontent.com/weaveworks/grafanalib/main/grafanalib/tests/examples/example.dashboard.py
```

Сгенерируйте JSON-дашборд:

```bash
generate-dashboard -o frontend.json example.dashboard.py
```

Полученный файл `frontend.json` можно загрузить в Grafana через веб-интерфейс или развернуть через систему провизионинга дашбордов Grafana.

## Пример

Пример простого дашборда на Python:

```python
from grafanalib.core import (
    Dashboard,
    Graph,
    Row,
    Target,
)

dashboard = Dashboard(
    title="Дашборд моего сервиса",
    rows=[
        Row(panels=[
            Graph(
                title="Запросов в секунду",
                targets=[
                    Target(expr='rate(http_requests_total[5m])'),
                ],
            ),
        ]),
    ],
).auto_panel_ids()
```

## Документация

- **Полная документация**: [grafanalib.readthedocs.io](https://grafanalib.readthedocs.io/)
- **Оригинальный README** (reStructuredText): [README.rst](README.rst)
- **Примеры**: [grafanalib/tests/examples](https://github.com/weaveworks/grafanalib/tree/main/grafanalib/tests/examples)
- **Основной репозиторий**: [weaveworks/grafanalib](https://github.com/weaveworks/grafanalib)

## Возможности

- Поддержка Grafana 8.x, 9.x и 10.x
- Различные типы панелей: Graph, Timeseries, Table, Heatmap и другие
- Поддержка источников данных: Prometheus, Elasticsearch, CloudWatch, InfluxDB и другие
- Правила алертов и каналы уведомлений (Grafana 8.x+)
- Шаблонизация дашбордов и переменные
- Аннотации и ссылки между дашбордами

## Требования

- Python 3.8, 3.9, 3.10 или 3.11
- Grafana 8.x или новее (для большинства функций)

## Поддержка

- **Документация**: https://grafanalib.readthedocs.io
- **Проблемы**: [Создать issue](https://github.com/weaveworks/grafanalib/issues/new)
- **Сообщество**: [#grafanalib в Weave Community Slack](https://weave-community.slack.com/messages/grafanalib/)

## Лицензия

Лицензировано под Apache License, Version 2.0. Подробности в файле [LICENSE](LICENSE).

---

**Поддерживается**: [Ranas Mukminov](https://github.com/ranas-mukminov) | **Оригинальные авторы**: [Weaveworks](https://github.com/weaveworks)
