# rafa-repo-example
An example of a repo for an Astro deployment

# Repo Branches
* `main`
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

# Development Approaches
## Trunk Based
* Each deployment contains the code in the `main` branch

```mermaid
graph LR;
    subgraph update branches
        updates.hotfix
        updates.feature
    end
    subgraph git
        git.main
    end
    subgraph ci-cd
        ci-cd.release-tag
    end
    subgraph astro
        dev
        qa
        prod
    end
    updates.hotfix-->git.main;
    updates.feature-->git.main;
    git.main-->ci-cd;
    ci-cd.release-tag-- dev tag -->dev;
    ci-cd.release-tag-- qa tag -->qa;
    ci-cd.release-tag-- prod tag -->prod;
```

# Branch Development
* Each deployment has a relationship to a specific branch

```mermaid
    subgraph branches
        git.hotfix
        git.feature
    end
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
    branches-- test in dev -->git.dev;
    branches-- test in qa -->git.qa;
    branches-- test in prod -->git.prod;
    git.dev-->dev;
    git.qa-->qa;
    git.prod-->prod;
```