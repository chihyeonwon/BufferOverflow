# BufferOverflow
What is BufferOverflow igloo corporation wonchihyeon

헤더의 길이가 
말 그대로 버퍼의 공간에 담길 데이터가 흘러넘침을 뜻한다.

데이터가 흘러넘치면 어떻게 되는가? 버퍼에 할당된 구역을 넘어서 다른 데이터가 저장된 메모리 영역
까지 침범하여 데이터를 덮어쓰게 된다.

이로 인해 시스템은 정상적으로 동작하지 않게 된다.

버퍼 오버 플로우는 기본적인 해킹 스킬이다.

버퍼는 임시 저장 공간으로 메모리 영역에서 스택 혹은 히프 혹은 데이터 영역에 존재할 수 있는데 각 영역에 따라 스택 버퍼 오버 플로우, 힙 버퍼 오버 플로우, 데이터 버퍼 오버 플로우로 불릴 수 있다.

가드페이지 구현

```c
int main(int argc, char *argv[]) {
  int valid = FALSE;

char str1[8]; // str1 선언
char str2[8]; // str2 선언

next_tag(str1); // str1에 태그값붙이고
gets(str2); // 사용자가 값을 입력하면 str2에 담긴다.
if(strncmp(str1, str2, 8) == 0)
  valid = TRUE;
printf("buffer1: str1(%s), str2(%s), valid(%d)\n", str1, str2, valid);
}
```
사용자가 값을 입력했는데 그것이 start라면 valid를 나타내는 함수

str2영역에는 글자 8개 까지 담을 수 있다 (char str2[8] 이기 때문)

만약 str2 영역에 글자 8개 이상을 담으면 버퍼오버플로우 발생.

c가 제공하는 함수 gets에서 복사할 문자열의 길이를 검사하는 과정을 생략.

버퍼오버플로우 발생

이 도구를 이용하여 허용받지 않은 서비스 대상으로 해킹을 시도하는 행위는 범죄 행위입니다. 해킹을 시도할 때에 발생하는 법적인 책임은 그것을 행한 사용자에게 있다는 것을 명심하시기 바랍니다.
 
A9 - Buffer Overflow (Local)
 
버퍼 오버플로 오류는 의도적 또는 비의도적으로 수정되어서는 안 되는 프로세스의 메모리 조각을 덮어쓰는 것이 특징입니다.          
IP(Instruction Pointer), BP(Base Pointer) 및 기타 레지스터의 값을 덮어쓰면 예외, 분할 오류 및 기타 오류가 발생합니다.           
일반적으로 이러한 오류는 예기치 않은 방식으로 응용 프로그램 실행을 종료합니다. 버퍼 오버플로 오류는 char 유형의 버퍼에서 작업할 때 발생합니다.          

버퍼 오버플로는 스택 오버플로[스택 오버플로] 또는 힙 오버플로[힙 오버플로]로 구성될 수 있습니다. 이 문서에서는 혼동을 피하기 위해 이 두 가지를 구분하지 않습니다.    
## 스택 오버플로, 힙 오버플로

bof_1.php 메인 페이지와 소스코드를 살펴보면 메인 페이지에서는 힌트를 제공하고 소스 코드에서는 shell_exe를 통하여 쉘 명령을 실행한다는 것을 알 수 있습니다.
 
먼저 해당 문제를 풀기 위해서는 컴파일, 디버깅을 통한 메모리 분석, 쉘코드 작성을 통한 공격코드 삽입이 이루어져야 하며 여기서는 BOF(Buffer Overflow)가 무엇이고 어떻게 공격이 이루어지는지 참고에 있는 OWSAP 문서를 통하여 확인해 보시기 바랍니다.
 
해당 BOF에 관한 문제는 추후 어떻게 컴파일이 이루어 지고 디버깅을 어떻게 하는지 유닉스, 윈도를 나눠서 다룰 예정이며 쉘 코드 작성 방법과 어떤 툴들을 사용하는지 다룰 예정입니다.
              
## 참고     
https://owasp.org/www-community/attacks/Buffer_overflow_attack     
https://owasp.org/www-project-web-security-testing-guide/v41/4-Web_Application_Security_Testing/07-Input_Validation_Testing/13.2-Testing_for_Stack_Overflow     
https://owasp.org/www-community/vulnerabilities/Buffer_Overflow     
                    


