[stage](https://gitlab-docs.creationline.com/ee/ci/yaml/#stage)

```yml
stages:
  - build
  - test
  - deploy

job 0:
  stage: .pre
  script: make something useful before build stage

job 1:
  stage: build
  script: make build dependencies

job 2:
  stage: build
  script: make build artifacts

job 3:
  stage: test
  script: make test

job 4:
  stage: deploy
  script: make deploy

job 5:
  stage: .post
  script: make something useful at the end of pipeline
```

[extends](https://gitlab-docs.creationline.com/ee/ci/yaml/#extends)

```yml
.tests:
  script: rake test
  stage: test
  only:
    refs:
      - branches

rspec:
  extends: .tests
  script: rake rspec
  only:
    variables:
      - $RSPEC
```

[Predefined environment variables reference](https://gitlab-docs.creationline.com/ee/ci/variables/predefined_variables.html)

[CIサービスの自動ビルドをスキップする方法まとめ](https://qiita.com/vmmhypervisor/items/f10c77a375c2a663b300)

