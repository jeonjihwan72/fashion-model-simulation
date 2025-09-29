# 미니 쇼핑몰 프로젝트 기술 지침 (Instruction)

## 1. 핵심 아키텍처 (Core Architecture)

- **Architecture**: **모놀리식 아키텍처 (Monolithic Architecture)**
    - **사유**: 프로젝트 초기 단계이며 1개월 내 빠른 프로토타입 개발을 목표로 하므로, 단일 애플리케이션 구조가 가장 효율적입니다. 모든 기능(상품, 장바구니, 주문)을 하나의 프로젝트 내에서 개발합니다.
    - **향후 확장**: 프로젝트가 성공적으로 성장하면, 각 기능을 **마이크로서비스 아키텍처(MSA)**로 전환하는 것을 고려할 수 있습니다. (예: 상품 서비스, 주문 서비스 분리)

## 2. 개발 언어 및 프레임워크 (Language & Framework)

- **Programming Language**: **Java** (Version 17 LTS 이상 권장)
- **Core Framework**: **Spring Boot**
    - **사유**: 내장 웹 서버(Tomcat)를 포함하고 있어 독립 실행이 가능하며, 방대한 라이브러리와 커뮤니티 지원을 통해 웹 애플리케이션을 빠르고 안정적으로 구축할 수 있습니다.

## 3. 데이터 관리 (Data Management)

- **Initial Data Store**: **JSON 파일**
    - **사유**: 초기 단계에서 데이터베이스 설정의 복잡성을 피하고 핵심 비즈니스 로직 개발에 집중하기 위함입니다. `resources` 폴더 내에 `products.json` 파일을 두고, 애플리케이션 시작 시 데이터를 메모리에 로드하여 사용합니다.
- **Future Data Store**: 향후 H2 Database (개발용) 또는 MySQL/PostgreSQL (운영용) 같은 RDBMS로 전환할 계획입니다.

## 4. 개발 환경 (Development Environment)

- **IDE**: IntelliJ IDEA Ultimate 또는 VS Code with Java Extension Pack
- **Build Tool**: **Gradle** (또는 Maven)
- **Version Control**: **Git** & GitHub

## 5. 주요 의존성 (Key Dependencies - build.gradle)

- `spring-boot-starter-web`: 웹 애플리케이션 및 RESTful API 개발
- `lombok`: 반복적인 코드(Getter, Setter 등) 자동 생성을 통한 생산성 향상
- `jackson-databind`: Java 객체와 JSON 데이터 간의 변환 처리