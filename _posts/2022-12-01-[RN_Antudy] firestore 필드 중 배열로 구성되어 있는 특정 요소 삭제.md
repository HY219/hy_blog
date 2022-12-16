---
title: [RN_Antudy] firestore 필드 중 배열로 구성되어 있는 특정 요소 삭제
categories: [RN_Antudy]
tags: [js, rn, project] # TAG는 반드시 소문자로 이루어져야함!
---

### 스터디 생성 및 관리 어플리케이션 (RN 프로젝트)


* 관리중인 스터디 삭제기능 완료
* joinUid 필드 중 사용자의 uid 삭제 완료
  * updateDoc 사용
  * firebase.firestore.arrayRemove 사용
    ```
    const pressDeleteJoinButton = () => {
      console.log("참여중인 스터디 삭제하기")
      const ANTUDYJoinDelete = doc(db, "ANTUDY", uid+adminTitle);
        updateDoc(ANTUDYJoinDelete, {
          joinUid: arrayRemove(uid) //deleteField()
        });
      }
      ```