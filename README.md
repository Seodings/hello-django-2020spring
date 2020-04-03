# hello-django-2020spring

#project Setting
 1) 가상환경을 anaconda 폴더의 python.exe로 잡으니 manage.py로 서버 돌릴때 sqlite가 import안된다는 오류가 있었다.
 2) 바보같이 첫 노트북 사고부터 user이름을 한국어로 해서 프로젝트만들때마다 오류파티다 ㅎㅎㅎ
 3) 영어로된 user에 python 새로 깔고 이걸로 가상환경 다시 만들었다.
 4) sqlite 오류는 안뜨는데 window hostname이 한국어라 utf-8 변환안된다고 오류..
 5) 이미 가상환경 5개 만들어서 슬펐다 ..
 6) wmic ComputerSystem Where Name="%COMPUTERNAME%" Call Rename Name="NEW-HOSTNAME"
    wmic 커맨드로 hostname 영어로 바꿔주니 드디어 성.공!
 7) 느낀점-> 무 족  권. 폴더명과 호스트네임은 영어로 ..