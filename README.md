# waSans-BulletinBoard
<img width="321" alt="스크린샷 2023-01-25 오후 4 42 04" src="https://user-images.githubusercontent.com/58936172/214508617-04c3c50b-4731-4916-a505-6a995a526536.png">
<img width="318" alt="스크린샷 2023-01-25 오후 4 42 18" src="https://user-images.githubusercontent.com/58936172/214508732-dfbb193a-ba87-4e17-9874-486a85d27a95.png">
<img width="262" alt="스크린샷 2023-01-25 오후 4 42 45" src="https://user-images.githubusercontent.com/58936172/214508756-16578218-c565-4e32-bb9b-46f3c74eee5a.png">


### WHSP 요약
***
- **What**: 동기 용민이가 멘토로 있느 노드 스터디에서 한 처 게시판 과제. 샌즈는 용민이가 매우 좋아하는 캐릭터라 그냥 붙여봤음.
- **Why**: Node.js 로 서버를 구축하는 도중, 문득 사람들에게 보여지는 프론트에서는 서버로부터 어떻게 정보를 받아와 표시하는 지, 연동 과정에서 발생하는 문제점이나 힘든 점들은 무엇이 있을 지 손수 경험하기 위해 앱 형태로 구현하고자 했음.
- **How**: 
  - Figma로 게시판 UI를 디자인해보았음.
  - Firebase로 게시판 구축에 필요한 데이터베이스를 구축
  - Node.js로 기본적인 Router를 만들어 Firebase에서 데이터를 받아온 다음 클라이언트에 정보를 주는 간단한 서버 구축
  - Swift로 서버로부터 정보를 받아오고, 이를 실시간으로 반영하는 앱 구축
- **Problems**:
  - Router마다 firebase를 init하는 식으로 했더니 서버 속도가 현저하게 느려졌음.
  - 화면전환 전에 정보를 완전히 받아와야 하는데, 그 전에 화면 전환이 이루어져 데이터가 표시되지 않았음.
  - 그럴려면 프론트에서도 비동기 방식으로 정보를 처리해야 했는데, 그 과정을 해본 적이 없어서 매우 힘들었음. 
  - Async, await식의 비동기 구문들을 어디다가 사용할 지 감이 안 잡혀 처리가 잘 되지 않았음. 대부분의 시간을 이를 해결하는 데에 쏟아부었음.
- **Solution**:
  - FIrebase 관련 함수들과, 데이터 인터페이스 부분 등을 독립적으로 분리시켜 서버 속도를 개선시킴.
  - Firebase 함수 Parameter을 확장시켜 여러 라우터에서 공동으로 함수를 사용할 수 있게 함.
  - 화면 전환 전에 정보를 모두 받은 다음에야 이루어지도록 Task 블록을 사용했음.
  - Async, await를 밑에 코드를 잠시 일시정지 시킨다는 것으로 생각하고, 구문을 코드의 적절한 부분에 사용하여 비동기 처리가 단계적으로 이루어지도록 했음
