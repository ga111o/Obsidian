### 원인

리눅스 계열 DJango 가상환경 디렉토리 구조
`venv\{이름}\bin\activate`

윈도우 DJango 가상환경 디렉토리 구조
`venv\{이름}\Scripts\activate`

각 os별 디렉토리가 다르다.

리눅스에서 만든 가상환경을 윈도우즈에서 그대로 git clone해서 발생한 오류

![](https://velog.velcdn.com/images/ga111o/post/78330716-3a9d-4d9a-bc37-86e447e1f7e0/image.png)

<br>
<hr>

### 해결 방법

윈도우즈 상에서 새로 가상환경을 만들고 실행시키는 방법으로 해결
`python -m venv mysite`

or

wsl 켜고 ubuntu22.04 설치해서
해당 환경 위에서 git clone 하고 서버 실행