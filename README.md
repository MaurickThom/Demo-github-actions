# Demo-github-actions

## Configuration

```sh
 
 > git clone my-repo.git
 > cd my-repo/
 > mkdir -p .github/workflows
 > vim .github/workflows/checker.yml 
```

```yml

name: Check critical files

on: [pull_request]

jobs:
  check-critical-files:
    runs-on: ubuntu-latest
    name: Check for critical files
    steps:
      - uses: codelytv/check-critical-files@v1
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          critical_message: ¡Alerta! Recuerda modificar el vault 
          critical_files: |
            .env
      - uses: codelytv/check-critical-files@v1
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          critical_message: ¡Alerta! Recuerda commitear el .lock 
          critical_files: |
            package.json
	    composer.json
```

```sh

 > git commit -m "Add workflow"
 > git push origin master
 > git switch -c demo
 > touch my-file
 > git add . && git commit -m "Add my-file"
 > git push origin demo

```

> Recommendation for branches that are not marked -> pull request : draft pull request

```sh

 > vim .env # something
 > git add . && git commit -m "Add .env" && git push origin demo
```

## References

- https://github.com/CodelyTV/check-critical-files
- https://pro.codely.tv/library/github-actions-de-0-a-integracion-continua/109857/about/
- https://www.youtube.com/watch?v=iJxrf9lkoJc
- https://elabismodenull.wordpress.com/2017/07/07/el-fichero-package-lock-json-tengo-que-versionarlo/

