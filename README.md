## 👨‍🦳 Mono Repo

MonoRepo 는 Monolithic Repositories 의 약자로, 하나의 리포지토리에서 여러개의 프로젝트가 구성된 것을 의미합니다.

# 📁 Folder Structure

A quick look at the directories you'll see in this project.

### Root driectory layout

    .
    ├── packages            # 프로젝트A, B, C
    │   ├── components      # 공통으로 사용할 components
    │   └── web-app         # (next.js) 프로젝트A 
    └── ...
    └── package.json        # 공통으로 관리할 패키지 

### ⭐️ 장점

MonoRepo 를 사용하는 이유는 여러가지가 있습니다. 물론 장점만 있는것은 아니기에 프로젝트의 목적 및 환경 등 여러가지 조건을 고려해서 결정하면 좋을것 같습니다.

- **장점 1.** 하나의 리포지토리로 여러개의 프로젝트 관리
하나의 리포지토리가 여러개의 프로젝트를 포함하고 있는것은 큰 편의성을 가집니다. 코드를 짜는 입장에서도 IDE를 열거나, IDE에서 프로젝트를 스위치해가며 개발할 필요없이 하나의 IDE에서 하위폴더로 구분된 여러 패키지들이 코드를 작성할 수 있습니다.

- **장점 2.** 중첩되는 코드의 공통화
A, B, C, D 패키지로 구성된 MonoRepo 가 있고, 여러 프로젝트들이 공통으로 사용해야 하는 로직이 있을때, 이를 쉽게 추가적인 E 패키지로 분리하고, A~D 패키지에서 import 하여 사용할 수 있습니다.

- **장점 3.** 중첩되는 모듈은 하나만 설치해서 사용
A, B, C, D 패키지 모두 node 16.1.0 버전을 사용한다고 가정하면, 각각의 패키지에서 node를 설치할 필요 없이, root path에만 node 를 설치하고 A~D 에서 끌어다 쓸 수 있습니다.


### 단점

- **단점 1.** Dependency 충돌 문제
특정 패키지가 특정 버전의 모듈을 필요로 하는 경우, 다른 버전의 모듈을 사용하는 패키지와 Dependency 충돌이 발생할 수 있습니다.

- **단점 2.** 단일 리포지토리 문제
여러 프로젝트를 하나의 리포지토리에서 관리하기 때문에 오히려 관리가 어려워 질 수 있습니다.
MonoRepo 로 관리하는 패키지가 많지 않을 경우에는 해당되지 않지만, 관리하는 패키지가 증가함에 따라 오히려 가독성이나 여러가지 측면에서 비효율적이게 될 수 있습니다.

- **단점 3.** 긴 초기 프로젝트 설정시간
MonoRepo 로 포함되는 모든 프로젝트를 사용한다면 상관없지만, 그 중 일부만 필요한 경우에도 node_module 설치가 이루어 져야 합니다.

### 🛠️ Installation Steps

1. 저장소 복사

```bash
git clone https://github.com/deanlim8961/monorepo.git
```

2. working directory로 이동

```bash
cd monorepo
```

3. Install dependencies

```bash
yarn install
```

4. app 실행

```bash
yarn workspace @project/web-app dev
```
