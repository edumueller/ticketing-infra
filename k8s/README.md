# Environment setup

## Skaffold config:

- install [skaffold](https://skaffold.dev/)
- create a `skaffold.yml` file on the project directory (sibling of infra dir).
- copy the content below
- run skaffold dev

```
apiVersion: skaffold/v2alpha3
kind: Config
deploy:
  kubectl:
    manifests:
      - ./infra/k8s/*
build:
  local:
    push: false
  artifacts:
    - image: edunicastro/auth
      context: auth
      docker:
        dockerfile: Dockerfile
      sync:
        manual:
          - src: 'src/**/*.ts'
            dest: .
```
