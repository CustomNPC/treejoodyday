# tree.joody.day
숨겨진 메세지를 보는 취약점

# 취약점
내부 API가 본인이 아닌 사용자에게 표시될 때, 모자이크된 이미지가 아닌 암호화된 컨텐츠를 사용해 리턴해 클라이언트에서 내용을 모자이크하기에, 원본 내용을 가져올 수 있음.

# 방법
개발자 도구로 Sources 탭의 index js 파일을 열고,
```js
 return decodeURIComponent(escape(ht.stringify(ft)))
```
줄에 BP를 걸고, 아무 게시글 클릭 뒤 BP가 트리거되면 콘솔에
```js
decodeURIComponent(escape(ht.stringify(ft)))
```
를 입력해 원본 메세지를 취득.

# 방법 2
```js
const og = decodeURIComponent;
decodeURIComponent = (arg) => {
    console.log(og(arg));
    return og(arg);
}
```
위 코드를 콘솔에 입력해, 더욱 더 쉽게 원본 메세지를 취득

# 영상 튜토리얼
Soon
