Django는 Python으로 만들어진 백엔드 프레임워크 입니다.

첫 Django 프로젝트를 만들면 여러 폴더와 파일이 생겨 뭔가 거대해 보이지만, 생각보다 간단하고 사용하기 쉽습니다.

이번 글에서는 Virtualenv와 Django를 사용해 장고 프로젝트를 생성하고 실행시켜봅니다.

## pip

`pip`은 node.js의 `npm`과 비슷한 역할을 합니다. `npm`처럼 프로젝트의 명령어를 실행하는 기능(`npm run ...`)은 없지만 패키지 설치와 관리를 도와줍니다. 일반적으로 Python을 설치하면 같이 설치됩니다.

## Poetry
 
하지만 pip은 패키지 관리가 불편합니다.

이전에 진행했던 React 프로젝트는 각 프로젝트마다 `node_modules` 폴더가 존재했습니다. 즉 같은 한 프로젝트에서 설치한 패키지를 다른 프로젝트에서 사용할 수 없는 구조로 되어 있어 패키지 버전이 충돌날 일이 없었습니다.

하지만 Python은 Node.js처럼 프로젝트별 패키지 관리가 아닌 환경 버전별 패키지 관리 방식이기 때문에 한 번 A 프로젝트에서 설치한 패키지를 B에서도 사용할 수 있습니다.

이런 문제를 해결하기 위해 `pipenv`나 `virtualenv` 등의 해결책이 나왔지만, 가장 깔끔하고 패키지 관리를 잘 해주는 것은 Poetry입니다.

Poetry는 `pip`을 통해 설치할 수 있습니다.

```sh
pip install poetry
```

### 프로젝트 초기화 및 환경 만들기

먼저 프로젝트에 사용할 폴더를 하나 만듭니다. 원하는 이름으로 만들어주세요.

저는 `first-django-app`이라는 이름으로 진행하겠습니다.

```sh
mkdir first-django-app
```

이후 폴더 안으로 들어가 `poetry init` 명령어로 프로젝트를 초기화 해줍니다. (`npm init`과 비슷한 일을 하는 과정입니다)

`poetry init`을 하면서 아래와 같은 물음에는 일단 `no`를 입력하고 넘어가주세요.
```
Would you like to define your (main/development) dependencies interactively?
```

이후 프로젝트 폴더에 `pyproject.toml` 이라는 파일이 생성되면 프로젝트 초기화가 성공적으로 끝난 것입니다.

그 다음 `poetry shell` 명령어로 프로젝트에서 사용할 가상 파이썬 환경을 실행시켜주세요. `poetry shell`을 하면 해당 프로젝트에서만 쓰는 파이썬 환경을 따로 만들고, 패키지도 따로 관리됩니다.

### Django 설치 하기

`poetry add 패키지_이름` 명령어로 원하는 패키지를 설치할 수 있습니다. 먼저 Django를 설치해봅시다.

```sh
poetry add django
```

설치가 완료되었으면 이제 장고 프로젝트를 만들어봅시다. 아래 명령어로 `firstapp` 이라는 장고 프로젝트를 생성할 수 있습니다.

```sh
# django-admin startproject 프로젝트_이름 .
django-admin startproject firstapp .
```

여기까지 진행한 `first-django-app` 프로젝트의 구조는 아래와 같습니다!
```
first-django-app/
├─ firstapp/
├─ manage.py
├─ poetry.lock
└─ pyproject.toml
```

### Django 프로젝트 실행하기

프로젝트를 실행시키거나, 데이터베이스를 동기화 시키는 등 프로젝트에 관련한 여러가지 작업은 `manage.py` 파일을 통해 합니다.

방금 우리가 만들었던 Django 프로젝트는 `runserver`라는 명령어로 실행할 수 있습니다. 아래 명령어로 프로젝트를 실행시켜보세요.

```sh
python manage.py runserver
```

서버가 잘 실행되었다면 여러 문구들이 나타날텐데 그 중 아래와 같이 서버가 실행된 호스트와 포트 번호가 적혀있습니다. 해당 주소로 접속해보세요.

```
...
Starting development server at http://127.0.0.1:8000/
...
```