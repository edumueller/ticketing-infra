# Environment setup

## Skaffold config:

- install [skaffold](https://skaffold.dev/)
- verify the paths referenced on file [skaffold.yml](./skaffold.yml) file on the project directory (sibling of infra dir).
- create a jwt-secret - see file [auth-depl.yml](./k8s/auth-depl.yml), line 22
- navigate to this project's dir
- run `skaffold dev`

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
