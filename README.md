# grafanalib

[![Documentation Status](https://readthedocs.org/projects/grafanalib/badge/?version=main)](https://grafanalib.readthedocs.io/en/main)

**Python library for building Grafana dashboards as code.**

This is a fork of [weaveworks/grafanalib](https://github.com/weaveworks/grafanalib), maintained by [Ranas Mukminov](https://github.com/ranas-mukminov) for community use.

[English] | [Русский](README.ru.md)

---

## Overview

Do you like [Grafana](http://grafana.org/) but wish you could version your dashboard configuration? Do you find yourself repeating common patterns? If so, grafanalib is for you.

grafanalib lets you generate Grafana dashboards from simple Python scripts, making your dashboards:
- **Version controlled** – track changes in Git
- **Reusable** – factor out common patterns into functions
- **Testable** – validate dashboard configuration in CI/CD

## Quick Start

Install grafanalib:

```bash
pip install grafanalib
```

Download an example dashboard:

```bash
curl -o example.dashboard.py \
  https://raw.githubusercontent.com/weaveworks/grafanalib/main/grafanalib/tests/examples/example.dashboard.py
```

Generate the JSON dashboard:

```bash
generate-dashboard -o frontend.json example.dashboard.py
```

The resulting `frontend.json` file can be uploaded directly to Grafana or provisioned via Grafana's dashboard provisioning system.

## Example

Here's a simple example of a dashboard defined in Python:

```python
from grafanalib.core import (
    Dashboard,
    Graph,
    Row,
    Target,
)

dashboard = Dashboard(
    title="My Service Dashboard",
    rows=[
        Row(panels=[
            Graph(
                title="Requests per second",
                targets=[
                    Target(expr='rate(http_requests_total[5m])'),
                ],
            ),
        ]),
    ],
).auto_panel_ids()
```

## Documentation

- **Full documentation**: [grafanalib.readthedocs.io](https://grafanalib.readthedocs.io/)
- **Original README** (reStructuredText): [README.rst](README.rst)
- **Examples**: [grafanalib/tests/examples](https://github.com/weaveworks/grafanalib/tree/main/grafanalib/tests/examples)
- **Upstream repository**: [weaveworks/grafanalib](https://github.com/weaveworks/grafanalib)

## Features

- Support for Grafana 8.x, 9.x, and 10.x
- Comprehensive panel types: Graph, Timeseries, Table, Heatmap, and more
- Data source support: Prometheus, Elasticsearch, CloudWatch, InfluxDB, and others
- Alert rules and notification channels (Grafana 8.x+)
- Dashboard templating and variables
- Annotations and dashboard links

## Requirements

- Python 3.8, 3.9, 3.10, or 3.11
- Grafana 8.x or later (for most features)

## Support

- **Documentation**: https://grafanalib.readthedocs.io
- **Issues**: [File an issue](https://github.com/weaveworks/grafanalib/issues/new)
- **Community**: [#grafanalib on Weave Community Slack](https://weave-community.slack.com/messages/grafanalib/)

## License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.

---

**Maintained by**: [Ranas Mukminov](https://github.com/ranas-mukminov) | **Original authors**: [Weaveworks](https://github.com/weaveworks)
