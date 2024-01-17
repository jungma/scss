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
	> '$'로 시작 
	> '$'로 시작하는데 $다음 바로 숫자 시작은 안된다. $123 = 사용x
	

- css 속성을 변수로 사용시
	> css 속성을 변수로 사용할 때는 #{} - 사용



# Partial

부분적인 part 부분 
소스에 반복되는 부분들을 분리 분산시켜서 모듈화 시키는 기능

파셜의 파일명은 _로시작 
Sass는 _로 시작하는 파일은 컴파일 하지 않는다.
불러들일 때는 @import '파일명' (_, 확장자 없이) 선언


- @use 
	> @use './partial/var2';
	> use 사용이 보편적이다
	> 중복된 변수 네이밍 사용 시 var.$color-primary / var2.$color-primary 사용으로 필요한 변수로 사용 가능
	> @use './partial/var' as v2; // as 는 변수 명을 변경 가능하게 해줌

- @forward
> _index.scss 파일 생성 
> _index.scss 파일 내 선언 : @forward './var' ; @forward './var2'; 
> style.scss 파일 내 선언 : @use './partial/index';


- 지역변수 / 전역변수
	> 
	<code>
		$spacer : 5px; // 전역변수
		class{
    		$spacer10px : vars.$spacer * 2; // 중괄호 안에서 만든 변수는 중괄호 내에서만 사용 가능하다 = 지역변수!!
    		margin-top:$spacer10px ;
		}
	</code>


- 변수 이름 Tip
	> '$color-primary' : 주요한 컬러
	> '$color-secondary' : 두번쨰 중요한 컬러

- 변수 연산
	> $s = 10;
	> width:#{$s * $s}px; // 100px

- 클래스명 또한 변수로 활용 가능
	> $class-name : '.sss';
	> #{$class-name}{border:1px solid #ddd}
	> #{$class-name}--text{border:1px solid #ddd}
	> #{$class-name}__title--btn{border:1px solid #ddd}


- Nesting : 품다, 내포하다(안쪽으로 포함한다)
	> 
	<code>
	#box > .box{
		& > .box{
			font-size:24px;
			@media screen and (max-width:400px){
				font-size:60px;
			}
		}
	}
	</code>

- CSS - BEM 구조
B : Block - 특정 독립적인 요소
E : Element - 하위 요소들
M : Modifier - 수정자

CSS id class 등의 이름을 구조적으로 붙여주는 방법
.text-box
.text-box__title
.text-box__content
.text-box__content__desc

__ 두개는 하위 포함
- 글자띄어쓰기 의미
