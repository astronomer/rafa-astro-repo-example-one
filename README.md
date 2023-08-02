# rafa-repo-example
An example of a repo for an Astro deployment

# This is used for a set of deployments
It contains the following branches
* `dev`
* `qa`
* `prod`

# Folder structure

```
├── Dockerfile
├── LICENSE
├── README.md
├── airflow_settings.yaml
├── dags
│   ├── example_dag_advanced.py
│   └── example_dag_basic.py
├── include
├── packages.txt
├── plugins
├── requirements.txt
└── tests
    └── dags
        └── test_dag_integrity.py
```

# CI/CD Process

```mermaid
graph LR;
    subgraph git
    git.dev
    git.qa
    git.prod
    end
    subgraph astro
    dev
    qa
    prod
    end
    
    git.dev-->dev;
    git.qa-->qa;
    git.prod-->prod;
```

# Mermaid Example
```mermaid
flowchart TD
    A-->B;
    B-->C;
```