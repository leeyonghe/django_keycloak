# Django Notes Application with Keycloak Integration
# Django 노트 애플리케이션 (Keycloak 통합)

A secure notes application built with Django and Keycloak authentication. This application allows users to create, read, update, and delete their personal notes with a modern, responsive interface.

Django와 Keycloak 인증을 사용하여 구축된 안전한 노트 애플리케이션입니다. 사용자는 현대적이고 반응형 인터페이스를 통해 개인 노트를 생성, 읽기, 수정, 삭제할 수 있습니다.

## Features / 기능

- **User Authentication / 사용자 인증**
  - Secure login/logout functionality / 안전한 로그인/로그아웃 기능
  - User-specific note management / 사용자별 노트 관리
  - Admin interface for user management / 사용자 관리를 위한 관리자 인터페이스

- **Notes Management / 노트 관리**
  - Create, read, update, and delete notes / 노트 생성, 읽기, 수정, 삭제
  - Responsive card-based interface / 반응형 카드 기반 인터페이스
  - Rich text content support / 서식 있는 텍스트 지원
  - Automatic timestamp tracking / 자동 타임스탬프 추적

- **Modern UI / 현대적인 UI**
  - Bootstrap 5 for responsive design / 반응형 디자인을 위한 Bootstrap 5
  - Clean and intuitive interface / 깔끔하고 직관적인 인터페이스
  - Mobile-friendly layout / 모바일 친화적 레이아웃
  - Alert messages for user feedback / 사용자 피드백을 위한 알림 메시지

## Project Structure / 프로젝트 구조

```
django_keycloak/
├── django_keycloak/          # Main project configuration / 메인 프로젝트 설정
│   ├── settings.py           # Django settings / Django 설정
│   ├── urls.py              # URL routing / URL 라우팅
│   └── wsgi.py              # WSGI configuration / WSGI 설정
├── notes/                    # Notes application / 노트 애플리케이션
│   ├── models.py            # Note model definition / 노트 모델 정의
│   ├── views.py             # View functions / 뷰 함수
│   ├── forms.py             # Form definitions / 폼 정의
│   └── templates/           # HTML templates / HTML 템플릿
│       └── notes/
│           ├── base.html    # Base template / 기본 템플릿
│           ├── note_list.html
│           ├── note_form.html
│           ├── note_confirm_delete.html
│           └── login.html
├── manage.py                # Django management script / Django 관리 스크립트
├── requirements.txt         # Python dependencies / Python 의존성
├── Dockerfile              # Docker configuration / Docker 설정
└── docker-compose.yml      # Docker services configuration / Docker 서비스 설정
```

## Prerequisites / 필수 요구사항

- Python 3.10 or higher / Python 3.10 이상
- Docker and Docker Compose (for containerized deployment) / Docker와 Docker Compose (컨테이너화된 배포용)
- PostgreSQL (for production) / PostgreSQL (프로덕션용)
- Keycloak server (for authentication) / Keycloak 서버 (인증용)

## Installation / 설치 방법

1. Clone the repository / 저장소 복제:
   ```bash
   git clone <repository-url>
   cd django_keycloak
   ```

2. Create and activate a virtual environment / 가상환경 생성 및 활성화:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies / 의존성 설치:
   ```bash
   pip install -r requirements.txt
   ```

4. Run migrations / 마이그레이션 실행:
   ```bash
   python manage.py migrate
   ```

5. Create a superuser / 슈퍼유저 생성:
   ```bash
   python manage.py createsuperuser
   ```

## Running the Application / 애플리케이션 실행

### Development Mode / 개발 모드

1. Start the development server / 개발 서버 시작:
   ```bash
   python manage.py runserver
   ```

2. Access the application / 애플리케이션 접속:
   - Main application: http://localhost:8000 / 메인 애플리케이션
   - Admin interface: http://localhost:8000/admin / 관리자 인터페이스

### Docker Deployment / Docker 배포

1. Build and start the containers / 컨테이너 빌드 및 시작:
   ```bash
   docker-compose up --build
   ```

2. Access the services / 서비스 접속:
   - Django application: http://localhost:8000 / Django 애플리케이션
   - Keycloak: http://localhost:8080 / Keycloak
   - PostgreSQL: localhost:5432 / PostgreSQL

## Keycloak Configuration / Keycloak 설정

1. Access Keycloak admin console at http://localhost:8080 / Keycloak 관리 콘솔 접속
2. Create a new realm named "django-realm" / "django-realm"이라는 새 영역 생성
3. Create a new client named "django-client" / "django-client"라는 새 클라이언트 생성
4. Configure client settings / 클라이언트 설정 구성:
   - Access Type: confidential / 접근 유형: 기밀
   - Valid Redirect URIs: http://localhost:8000/* / 유효한 리다이렉트 URI
   - Web Origins: http://localhost:8000 / 웹 출처

## Security Features / 보안 기능

- User authentication and authorization / 사용자 인증 및 권한 부여
- CSRF protection / CSRF 보호
- SQL injection prevention / SQL 주입 방지
- XSS protection / XSS 보호
- Secure password handling / 안전한 비밀번호 처리
- Session management / 세션 관리
