## 이삼이 Yeesamee V2  
  
### [이삼이 V1을 개발하며](https://velog.io/@huise0ng/232)

### [이삼이 V2를 개발하며](https://velog.io/@huise0ng/232-V2)

### 개발을 시작하며

저는 디스코드를 사용 중 **노래하는하리보**라는 봇을 처음으로 접하게 되었습니다. 친구의 도움으 로 사용하게 되었는데 명령어 한 줄로 봇을 제어할 수 있음에 놀라 개발을 시작하게 되었습니다. 그러고 디스코드 봇 제작에 대해 관심이 많아졌고, 개발에 자신있는 Javascript로 디스코드 봇을 개발하기 시작하였습니다.

이삼이는 사용자의 벨로그 최신 글을 알려주는 봇입니다. 친구들과 디스코드에서 서로 벨로그에 글을 쓰면 함께 공유를 했습니다. 하지만 매번 링크를 보내주어야 했습니다. 

> 만약 봇이 내가 벨로그를 쓰면 자동으로 디스코드에 보내준다면?
> 
 
이라는 생각으로 개발에 들어갔습니다.  

### 개발 중

저는 일차적으로 @huise0ng의 벨로그 (제 벨로그)의 새 글을 가져 오는 것에 성공하였습니다. VS Code에서 node index.js 명령어로 실행하면 10분 후 채널에 저의 최신글이 가져와졌습니다. 

하지만 문제점이 발생했습니다. 

10분마다 조회만 된다면 계속 최신 글을 가져오는 것 이였습니다. 저는 이 문제를 if 함수로 전에 끌어왔던 최신글과 같지 않다면 10분 후라도 가져오지 않도록 해결을 완료 하였습니다. 

이 문제를 해결하고, 글을 쓴 후 인스타그램에 올렸는데 지인의 조언으로 기능을 더 추가하게 되었습니다.

그 기능은 

1. 이삼이를 쓸 때 명령어를 쓴다.
2. 저뿐만이 아닌 서버 사용자 모두가 쓸 수 있도록 해라. 

라는 두 가지 였습니다.  

저도 1차 개발 이 후 혼자만 쓸 수 있다는 한계점에서 불편함을 느꼈습니다. 

조언을 듣고 바로 2차 개발에 들어갔습니다. 

2차 개발에서는 

1. Database 활용
2. 명령어 사용

이 두가지에 가장 큰 초점을 두었습니다. 

데이터베이스 활용은 json으로 가능하다는 것을 새로 알게 되었습니다. 

json 파일을 사용해 봇을 실행시켰을 때 feed.json파일이 없다면 생성 → 사용자가 디스코드에 명령어로 쳐 피드를 등록시키면 

```json
{
    "디스코드 사용자": {
        "채널 ID": {
            "rssUrl": "벨로그 RSS URL",
            "lastLink": "RSS URL을 넣은 사용자의 최신 글"
        }
    }
}
```

이렇게 feeds.json에 등록되었다. 여기서 lastlink를 넣은 이유는 10분 후 전에 확인했던 글과 똑같은지 다른지를 비교해서 똑같다면 이삼이는 아무 반응이 없고, 다르다면 글을 올려줍니다.

![Untitled (6)](https://github.com/huise0ng/Discord-Bot-YeeSamee/assets/128358820/1b223ffe-7abb-43e4-afa3-adbf55b7b031)

[여기서 테스트 1은 벨로그 글 제목입니다.]

명령어도 추가하는데 성공하였습니다

제가 선택한 이삼이의 명령어는

> !yeesamee Velog RSS URL 채널 ID
> 

입니다.

```jsx
if (message.content.startsWith('!yeesamee')) {
        const args = message.content.split(' ').slice(1);
        if (args.length < 2) {
            return message.reply('사용법: !yeesamee Velog RSS_URL Channel_ID');
        }. 
```

이삼이를 처음 사용하는 사용자를 위해서 !yeesamee라고만 채팅에 쳤을 경우

![Untitled (2)](https://github.com/huise0ng/Discord-Bot-YeeSamee/assets/128358820/74ff576b-e1c1-45ae-8f11-cb9e4a15c9a0)


사용법에 대해서 소개합니다.




### 개발 기술
``` Javascirpt``` ``` JSON```
