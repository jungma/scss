# sass 란

빠르고 효율적으로 css를 만드는 작은 프로그래밍 언어
시간을 벌어 생산성을 높임
css의 미래 (2024년 현재 그 잡채! 라 생각됨)

sass - 초창기 방식 : 들여쓰기로 중괄호 처리
. box 
	font-size:32px
	.box-in 
		font-size:12px

scss - 요즘 방식 : 중괄호 처리
.box{
	font-size:32px;
	.box-in{
	font-size:12px
	}
}
# 컴파일방법

## visual stidio code 확장 live sass compiler를 쓰는 방법 (일단 이방법 사용)
setting.json 파일 수정
{
	"liveSassCompile.settings.formats": [
		{
			"format": "compressed", // 포맷 형태 지정 nested/expanded/compact/compressed
			"extensionName": ".css",
			"savePath": "~/css", // path 지정
			"savePathReplacementPairs": null
		}
	],
}

## 공식 컴파일러 사용 

참고 공식경로
https://sass-lang.com/documentation/cli/dart-sass/



# 변수

어떤 값을 담을 수가 있다.
값 종류 숫자 , 문자

- 변수 이름의 규칙
	> $로 시작 
	> $로 시작하는데 $다음 바로 숫자 시작은 안된다. $123 = 사용x
	

- css 속성을 변수로 사용시
	> css 속성을 변수로 사용할 때는 #{} - 사용
