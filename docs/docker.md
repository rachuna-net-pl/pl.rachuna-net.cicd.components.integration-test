
## 📑 Template: docker

---
### Wejściowe zmienne (`inputs`):

- **docker_image**  
  _Opis_: Obraz Docker, na którym zostanie uruchomiony job.  
  _Domyślnie_: `""` (należy podać własny obraz)

- **docker_test_script_path**  
  _Opis_: Ścieżka do skryptu testowego, który zostanie uruchomiony w kontenerze.  
  _Domyślnie_: `container_test.sh`

---
### Przykład użycia
```yaml
include:
  - local: 'templates/docker.yml'

test_my_image:
  extends: ['🧪 test docker image']
  variables:
    CONTAINER_IMAGE_DOCKER: 'registry.gitlab.com/moj-projekt/moj-obraz:latest'
    DOCKER_TEST_SCRIPT_PATH: 'test/integration.sh'
  rules:
    - if: '$CI_COMMIT_BRANCH == "main"'
```
---
### Co robi template?

- Wyświetla logo projektu oraz ustawione zmienne wejściowe.
- Uruchamia wskazany skrypt testowy w podanym obrazie Docker.
- Umożliwia łatwą integrację testów kontenerowych w pipeline CI/CD.