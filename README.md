# 설치 및 실행 (Installation & Execution Guide)
[!https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdna%2Fb7owax%2FdJMcacO223l%2FAAAAAAAAAAAAAAAAAAAAAEebaf3WytqW2IsgIgr_mwzzau4CKrgKFhr1OqouX6s-%2Fimg.jpg%3Fcredential%3DyqXZFxpELC7KVnFOS48ylbz2pIh7yKj8%26expires%3D1764514799%26allow_ip%3D%26allow_referer%3D%26signature%3DFY3GU2my0kqzyqm6jVIC5eRlwdA%253D]

(1) PC 사전 준비 사항
  ① Docker 엔진
  ② Docker Compose(v2) (docker compose 명령 지원)
  ③ 웹 브라우저(Chrome 등)
  ④ (옵션) HeidiSQL과 같은 MySQL GUI 툴
  ⑤ 배포 파일: exchange-diary.zip
    - 구성: docker-compose.yml, .env
    - GitHub: https://github.com/HyeonSeoyeon/cloud-native .zip 파일 다운
    - Docker Hub(이미지 정보 참고용):
        https://hub.docker.com/repositories/hyunseoyeon

(2) 설치 방법 및 컨테이너 기동
  ① Github에서 exchange-diary.zip 다운 후 압축 풀기 및 해당 폴더로 이동
    unzip exchange-diary.zip
    cd exchange-diary
  ② 이미지 내려받기 (Docker Hub → 로컬)
    docker compose pull
● proxy, frontend, api-auth, api-rooms, api-entries, redis, diary-mysql 이미지가 자동으로 내려받아짐.
● DB는 컨테이너 최초 기동 시 자동 초기화되도록 설계함.
  ③ 컨테이너 실행
    docker compose up –d
  ④ 상태 확인
    docker ps
  ⑤ 예상되는 컨테이너 상태 (예시)
    CONTAINER ID   NAME           PORTS
    b41234f23aa      proxy           0.0.0.0:8080->80/tcp
    a2d8e21b3f44     frontend       
    ce8a933f2123     api-auth       
    f1b9234d899a     api-rooms      
    aa3d9bcb3423    api-entries    
    b2c1234c22bc    redis            6379/tcp
    d4e12b3c56de    diary-mysql     0.0.0.0:33307->3306/tcp
