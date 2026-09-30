# Django Blog

**Django Girls 튜토리얼을 따라 구현한 개인 블로그 웹 애플리케이션입니다.**

글 목록·상세 화면과 작성·수정 폼을 만들며 Django의 모델, 뷰, URL, 템플릿이 연결되는 과정을 학습했습니다.

`Python` · `Django 6.0.4` · `SQLite` · `Django Templates` · `Bootstrap`

[전체 튜토리얼 기록](docs/tutorial-notes.md) · [이어서 만든 REST API](https://github.com/unknownamed/Simplifying-code-with-Django-REST-Framework)

## 동작 미리보기

![Django 블로그의 실제 웹 동작 녹화](images/웹동작영상.gif)

> 기존에 촬영한 데스크톱 웹 동작 GIF입니다. 구현 단계별 화면은 전체 튜토리얼 기록에서 확인할 수 있습니다.

## 주요 기능

| 화면 | 경로 | 내용 |
| --- | --- | --- |
| 글 목록 | `/` | 글 목록과 게시 시각 표시 |
| 글 상세 | `/post/<pk>/` | 제목과 본문 확인 |
| 새 글 | `/post/new/` | ModelForm으로 입력·저장 |
| 글 수정 | `/post/<pk>/edit/` | 기존 글을 불러와 수정 |
| 관리자 | `/admin/` | 사용자·게시글 관리 |

## 로컬 실행

[Django 6.0은 Python 3.12 이상을 지원합니다](https://docs.djangoproject.com/en/6.0/faq/install/).

```bash
git clone https://github.com/unknownamed/Django-Girls-tutorial-follow.git
cd Django-Girls-tutorial-follow
python -m venv .venv
```

가상환경을 활성화합니다.

```powershell
# Windows PowerShell
.\.venv\Scripts\Activate.ps1
```

```bash
# macOS / Linux
source .venv/bin/activate
```

```bash
python -m pip install "Django==6.0.4"
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver 127.0.0.1:8000
```

`http://127.0.0.1:8000/admin/`에서 로그인한 뒤 글을 작성할 수 있습니다. 저장소에 포함된 DB 대신 새 DB로 시작하려면 기존 `db.sqlite3`를 따로 보관하고 마이그레이션합니다.

## 구현에서 확인할 부분

- [Post 모델](blog/models.py): 작성자, 제목, 본문, 생성·게시 시각
- [뷰](blog/views.py): 조회, 폼 검증, 저장, 상세 화면으로 이동
- [URL](blog/urls.py): 화면과 뷰 연결
- [템플릿](blog/templates/blog): 공통 레이아웃과 글 목록·상세·편집 화면
- [스타일](blog/static/css/blog.css): 블로그 화면 스타일

현재 글 목록은 모든 글을 조회하고 게시 시각 역순으로 정렬합니다. 작성·수정 뷰의 로그인 및 작성자 권한 검사는 추가 보완이 필요한 학습용 구현입니다.

## 학습 자료

- [Django Girls 튜토리얼](https://tutorial.djangogirls.org/ko/)
- [환경 설정부터 배포까지의 기존 기록](docs/tutorial-notes.md)
