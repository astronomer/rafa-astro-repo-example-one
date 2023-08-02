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

# CI/CD Process - Trunk Based
* Each deployment contains the code in the `main` branch

```mermaid
graph LR;
    subgraph updates
    updates.hotfix
    updates.feature
    end
    subgraph git
    git.main
    end
    subgraph astro
    dev
    qa
    prod
    end
    
    updates.hotfix-->git.main;
    updates.feature-->git.main;
    git.main-|ci cd handles dev update|->dev;
    git.main-|ci cd handles qa update|->qa;
    git.main-|ci cd handles prod update|->prod;
```

# CI/CD Process -  Branch Development
* Each deployment has a relationship to a specific branch

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