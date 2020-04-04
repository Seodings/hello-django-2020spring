##### hello-django-2020spring

#project Setting
 1) 가상환경을 anaconda 폴더의 python.exe로 잡으니 manage.py로 서버 돌릴때 sqlite가 import안된다는 오류가 있었다.
 3) 영어로된 user에 python 새로 깔고 이걸로 가상환경 다시 만들었다.
 4) sqlite 오류는 안뜨는데 window hostname이 한국어라 utf-8 변환안된다고 오류..
 5) 이미 가상환경 5개 만들어서 슬펐다 ..
 6) wmic ComputerSystem Where Name="%COMPUTERNAME%" Call Rename Name="NEW-HOSTNAME"
    wmic 커맨드로 hostname 영어로 바꿔주니 드디어 성.공!
 7) 느낀점-> 무 족  권. 폴더명과 호스트네임은 영어로 ..
 
 #part 1
 1. 뷰를 호출하려면 이와 연결된 URL필요 -> 이를 위해 URLconf가 사용된다.
 2. URLconf 생성하려면 urls.py파일 생성
 3. `path('polls/', include('polls.urls')),` 
   최상위 URLconf에서 polls.urls모듈 바라보게 설정
 4. path() 함수
 - **route**: URL패턴을 가진 문자열
 - **view**: HttpRequest 객체를 첫번째 인수로한 특정 view함수 호출
 
 #part2
 1) **모델**: 부가적인 메타데이터를 가진 데이터베이스의 구조
 - 데이터의 필수적인 필드들과 동작을 포함
 - 데이터베이스의 각 필드는 **Field** 클래스의 인스턴스로서 표현된다.
 2) 모델의 활성화: 앱을 현재의 프로젝트에 포함시키기 위해서는, 앱의 구성 클래스에 대한 탐조를 **INSTALLED_APPS**설정에 추가
 3) `sqlmigrate` : sql문장 보여준다, 기본키가 자동으로 추가
 4) `migrate` : 아직 적용되지 않은 마이그레이션을 모두 수집해 실행, 모델에서의 변경 사항들과 DB 스키마의 동기화가 이루어짐
 5) 마이그레이션: 동작 중인 DB 자료 손실 없이 업그레이드 하는 데 최적화
    1. (models.py 에서) 모델을 변경
    2. python manage.py makemigrations을 통해 이 변경사항에 대한 마이그레이션을 만들기
    3. python manage.py migrate 명령을 통해 변경사항을 데이터베이스에 적용
 6) shell-> Django에서 동작하는 모든 명령 시험 가능 
 7) 모델에 `__str__()` 추가: 객체표현 위해
 8) polls/admin.py에 Question import하고 `admin.site.register(Question)` 하면 관리사이트에서 poll app변경 가능
 
 #part3
 1) 뷰: 장고 어플리케이션이 일반적으로 특정 기능과 템플릿을 제공하는 웹페이지의 한 종류   
 -URLconf는 URL패턴을 뷰에 연결   
 -뷰에 기능 메소드 **detail, results, vote**를 추가             
 -path() 호출을 추가하여 새로운 뷰를 polls.urls모듈로 연결
 
 2) 뷰의기능                                                                                                
 -요청된 페이지의 내용이 담긴 HttpResponse객체를 반환                                                                                                       
 -Http404의 예외처리  
 -templates: 장고가 어떻게 템플릿을 불러오고 렌더링 할 것인지 기술
 3) **render()**:request, 템플릿이름, context 사전형 객체를 인수로 받는다.                   
 -> loader, HttpResponse 임포트 할 필요 없음
 4) `get_object_or_404()`: 객체가 존재하지 않을 경우 Http404 에러 발생   
 5) `{% url %}` template 태그를 사용하여 url설정에 정의된 특정한 URL 경로들의 의존성 제거 가능    
 6) polls/urls.py에 **app_name**을 추가하여 애플리케이션의 이름공간 설정가능
 
 #part4
 1) `request.POST`: 키로 전송된 자료에 접근할 수 있도록 한다. 항상 문자열로 반환
 2) HttpResponseRedirect 생성자 안의 `reverse()`: '/polls/3/results/'와 같은 문자열을 반환, 뷰 함수에서 URL을 하드코딩하지 않도록 도와준다.
 3) request는 HttpRequest 객체이다.
 4) 제너릭 뷰 사용하기: 적은 코드가 더 좋다.   
 -URLconf 수정   
 -views수정   
 -`ListView`: 객체 목록 표시   
 -`DetailView`: 특정 객체 유형에 대한 세부 정보 페이지 표시