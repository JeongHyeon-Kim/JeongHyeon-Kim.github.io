1. YouTube에서 생성한 사진을 비디오의 미리보기로 사용하여 Github Pages에 동영상 넣기

다음 형식의 YouTube URL의 경우 :  
<pre>
  <code>
https://www.youtube.com/watch?v=[VIDEO ID]
https://youtu.be/[VIDEO ID]
  </code>
</pre>

미리보기 URL의 형식
<pre>
  <code>
https://img.youtube.com/vi/[VIDEO ID]/maxresdefault.jpg
https://img.youtube.com/vi/[VIDEO ID]/hqdefault.jpg
  </code>
</pre>

예:  

[![Watch the video](https://img.youtube.com/vi/gtqctgfywn4/hqdefault.jpg)](https://youtu.be/gtqctgfywn4)

2. URL 넣기

예:

[RedHat 계열 리눅스+톰캣(tomcat) 설치](https://heeestorys.tistory.com/559)

3. ATOM Editor와 GitHub 연동

- [Git 설치](https://git-scm.com/download/win)이후 git user 설정
- ATOM GitHub 탭(ctrl+shift+8)의 로그인

참고

[아톰(Atom) 개발 환경과 깃허브(GitHub) 연동하는 방법](https://ndb796.tistory.com/51)

[pull 방법](https://m.blog.naver.com/wlgh325/221443819508)

4. tomcat 루트 디렉토리 변경

- {톰캣 설치 폴더}/conf/server.xml를 편집기로 열기
- Host 태그 내부에 Context 태그 추가(<Context path="" reloadable="true" docBase="{바꾸고자 하는 루트 디렉토리 경로}"/>)
- {톰캣 설치 폴더}/shutdown.sh와 {톰캣 설치 폴더}/start.sh 실행

반영

http://13.125.90.22:8080/foo.jsp

참고

[JSP 간단하게 시작하기...](https://ospace.tistory.com/132)
