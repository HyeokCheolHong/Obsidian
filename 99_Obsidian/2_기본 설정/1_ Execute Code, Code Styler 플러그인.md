
# 편집 모드에서 코드 실행 (Execute Code)
백틱 뒤에 run-javascript를 추가해주면 됨, 단점은 편집모드에서 행번호가 보이질 않음..;;
  
```run-javascript
const classifyResponses = (responses) => {
	let scores = { "yes": 0, "no": 0, "maybe": 0 };
	responses.forEach((response) => {
		if(response.toLowerCase() === "yes") scores.yes += 1;
		else if(response.toLowerCase() === "no") scores.no += 1;
		else if(response.toLowerCase() === "maybe") scores.maybe += 1;
	});

	return scores;
}

let responses = [ "Yes", "no", "Maybe", "yes", "YES", "no", "maybe", "Yes" ];
let scores = classifyResponses(responses);

console.log("설문 결과: ");
console.log(`Yes: ${scores.yes}`);
console.log(`No: ${scores.no}`);
console.log(`Maybe: ${scores.maybe}`);
```


# 하이라이팅 (code styler 플러그인 설치해야함)
백틱 뒤 javascript 에서 한 칸 띄고 hl:5 하게 되면 5번째 라인에 하이라이트 효과
```javascript hl:5

let a = 5;
let b = 2;

console.log(a + b);

```

여러 줄 하이라이팅 => hl:3-5
```javascript hl:3-5

let a = 5;
let b = 2;

console.log(a + b);

```

키워드 검색해서 하이라이팅 => hl:let
```javascript hl:let

let a = 5;
let b = 2;

console.log(a + b);

```

에러 하이라이팅과 기본 하이라이팅 => error:5 hl:let
(error 키워드는 code styler 설정에서 추가 해줘야 함)
```javascript error:5 hl:let

let a = 5;
let b = 2;

console.log(a + b);

```


![[codeStyler 하이라이트 추가한 설정.png]]






