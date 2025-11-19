# 📊 grafanalib

[![Documentation Status](https://readthedocs.org/projects/grafanalib/badge/?version=main)](https://grafanalib.readthedocs.io/en/main)
[![Security Audit](https://github.com/ranas-mukminov/grafanalib/workflows/Security%20Audit/badge.svg)](https://github.com/ranas-mukminov/grafanalib/actions/workflows/security.yml)
[![Code Quality](https://github.com/ranas-mukminov/grafanalib/workflows/Code%20Quality/badge.svg)](https://github.com/ranas-mukminov/grafanalib/actions/workflows/code-quality.yml)

Python library for building Grafana dashboards as code.

**Version-controlled** | **Reusable** | **Testable** | **Infrastructure-as-Code**

> This is a fork of [weaveworks/grafanalib](https://github.com/weaveworks/grafanalib), maintained by [Ranas Mukminov](https://github.com/ranas-mukminov) for community use.

[English] | [Русский](README.ru.md)

---

## English

### 💡 Overview

Do you like [Grafana](http://grafana.org/) but wish you could version your dashboard configuration? Do you find yourself repeating common patterns? If so, grafanalib is for you.

grafanalib lets you generate Grafana dashboards from simple Python scripts, making your dashboards:

- 🔄 **Version controlled** – track changes in Git
- ♻️ **Reusable** – factor out common patterns into functions
- ✅ **Testable** – validate dashboard configuration in CI/CD
- 🚀 **Deployable** – integrate with GitOps workflows
- 🛠️ **Maintainable** – refactor dashboards like any other code

### ✨ Features

- �� **Grafana Support**: Works with Grafana 8.x, 9.x, and 10.x
- 📊 **Panel Types**: Graph, Timeseries, Table, Heatmap, Stat, Gauge, and more
- 🔌 **Data Sources**: Prometheus, Elasticsearch, CloudWatch, InfluxDB, Loki, and others
- 🚨 **Alerting**: Alert rules and notification channels (Grafana 8.x+)
- 🔧 **Templating**: Dashboard variables and templating support
- 📝 **Annotations**: Dashboard annotations and links
- 🎨 **Customization**: Full control over dashboard appearance and behavior

### 🚀 Quick Start

**Prerequisites:** Python 3.8, 3.9, 3.10, or 3.11

**1. Install grafanalib:**
```bash
pip install grafanalib
```

**2. Download an example dashboard:**
```bash
curl -o example.dashboard.py \
  https://raw.githubusercontent.com/weaveworks/grafanalib/main/grafanalib/tests/examples/example.dashboard.py
```

**3. Generate the JSON dashboard:**
```bash
generate-dashboard -o frontend.json example.dashboard.py
```

**4. Upload to Grafana:**
The resulting `frontend.json` file can be uploaded directly to Grafana or provisioned via Grafana's dashboard provisioning system.

### 📝 Example

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

### 🎯 Use Cases

#### 🏢 Enterprise Monitoring
- Standardize dashboards across teams
- Enforce naming conventions and best practices
- Generate hundreds of similar dashboards programmatically

#### 🔄 GitOps Workflows
- Store dashboards in Git alongside application code
- Review dashboard changes via pull requests
- Automated deployment with CI/CD pipelines

#### 🧪 Testing & Validation
- Unit test dashboard configuration
- Validate panel queries before deployment
- Catch configuration errors early

#### 📚 Dashboard Templates
- Create reusable dashboard templates
- Share common patterns across projects
- Build dashboard libraries for your organization

### 📚 Documentation

- 📖 **Full documentation**: [grafanalib.readthedocs.io](https://grafanalib.readthedocs.io/)
- 📄 **Original README** (reStructuredText): [README.rst](README.rst)
- 💡 **Examples**: [grafanalib/tests/examples](https://github.com/weaveworks/grafanalib/tree/main/grafanalib/tests/examples)
- 🔗 **Upstream repository**: [weaveworks/grafanalib](https://github.com/weaveworks/grafanalib)

### 🔧 Requirements

- Python 3.8, 3.9, 3.10, or 3.11
- Grafana 8.x or later (for most features)

### 👨‍💻 Professional services – run-as-daemon.ru

**Professional monitoring & observability services by [run-as-daemon.ru](https://run-as-daemon.ru)**

This project is maintained by the DevSecOps / SRE engineer behind run-as-daemon.ru.

#### 💼 Services Offered:

- 📊 **Grafana Consulting**: Dashboard design, optimization, and best practices
- 🔧 **Monitoring Setup**: Complete observability stack implementation
- 🎓 **Training**: Grafana, Prometheus, and monitoring workshops
- 🚀 **Dashboard as Code**: Implementing grafanalib in your organization
- 🔄 **GitOps Integration**: CI/CD pipelines for dashboard deployment
- 📈 **Custom Solutions**: Tailored monitoring solutions for your needs

#### 📞 Contact for Consulting:

**Website:** [run-as-daemon.ru](https://run-as-daemon.ru)

*"Defense by design. Speed by default"* — Security-first architecture with performance optimization

---

### 🤝 Contributing

We welcome contributions! Please follow these guidelines:

1. **Fork and branch** per feature; keep changes focused
2. **Follow code style**: Use black, isort, and flake8
3. **Add tests**: Ensure new features have test coverage
4. **Update docs**: Keep documentation in sync with code changes
5. **Test locally**: Run the test suite before submitting PRs

#### Development Guidelines:

- Write clear commit messages
- Keep PRs focused on a single concern
- Add examples for new panel types or features
- Follow the existing code structure

### 📄 License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.

---

## 📮 Support

**Community Support:**
- 📖 **Documentation**: https://grafanalib.readthedocs.io
- 🐛 **Issues**: [File an issue](https://github.com/weaveworks/grafanalib/issues/new)
- 💬 **Community**: [#grafanalib on Weave Community Slack](https://weave-community.slack.com/messages/grafanalib/)

**Professional Support:**
- Grafana dashboard consulting and optimization
- Enterprise monitoring architecture design
- Custom dashboard development
- Training and workshops
- 24/7 support packages

**Contact:** [run-as-daemon.ru](https://run-as-daemon.ru)

---

**Maintained by**: [Ranas Mukminov](https://github.com/ranas-mukminov) | **Original authors**: [Weaveworks](https://github.com/weaveworks)

**Made with ❤️ for the monitoring community**

**Professional Monitoring & Observability Support:** [run-as-daemon.ru](https://run-as-daemon.ru)
