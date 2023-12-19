---
title: HR-Solution 제작기 03
tags: [react, Portfolio]
style: strok
color: primary
description: 포트폴리오, 리액트, hr-solution
toc: true
toc_sticky: true
date: 2023-12-12
last_modified_at: 2023-12-12
published: true
---
<br>

https://joylee-developer.tistory.com/171
지난번 문제에서 위의 블로그 글을 참고하여 수정했다.
displayName

```jsx
const { user } = userCradit.user;
        //const photoURL = await uploadImage(photo); //프로필사진을 firebase storage에 업로드
        await updateProfile(auth.currentUser, {displayName : name});
```

updateProfile(auth.currentUser, {displayName : name}) 이 구문에서 위의 user을 {}로 감싸서 해결!!
이메일 회원가입 할 때 유저 이름이 들어가게 됐당!!!

```jsx
const clockInRef = ref(db, `user/${user.displayName}/workTime/${dateKey}/clockIn`);
    set(clockInRef, time);
```
이 구문으로 이제 파이어베이스에 user/유저이름/workTime/날짜/clockIn의 경로로 출,퇴근 시간이 찍히게 됐다..
이제 출퇴근시간, 회원가입 해결됐는데 다른건,,언제... 갈길이막막...

<br>
