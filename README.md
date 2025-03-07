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

사용자가 값을 입력했는데 그것이 start라면 valid를 나타내는 함수

str2영역에는 글자 8개 까지 담을 수 있다 (char str2[8] 이기 때문)

만약 str2 영역에 글자 8개 이상을 담으면 버퍼오버플로우 발생.

c가 제공하는 함수 gets에서 복사할 문자열의 길이를 검사하는 과정을 생략.

버퍼오버플로우 발생
