Hashing
=======
Make directory with URL and hash URL with C.


## 과정
1. 표준 입력으로 URL을 사용자가 입력한다.
2. 입력한 URL을 SHA-1 알고리즘을 이용하여 hashed URL로 바꾼다.
3. hashed URL의 앞 3글자로 Directory를 만들고 나머지로 text file을 만든다.



## Hash function
1. hash function은 임의의 길이의 데이터를 고정된 길이의 데이터
로 변환하는 함수이며 해시 함수에 의해 얻어지는 값은 해시 값, 해시 코드,
해시 체크섬 또는 해시라고 한다.
2. 해쉬함수의 종류로는 CRC32, MD5, SHA 등이 있다.
### SHA-1
1993년에 미국 국가 안보국(NSA)에 의해 전자 서명 알고리즘의 일부분으로 개발되었다. SHA-1 에 대한 공격 발견되었
음에도 불구하고 아직 여러 보안 프로토콜이나 프로그램에서 많이 사용된다. 입력 한 text data(최대 2 64 bits)를 
160 bits의 hashed data로 반환
한다.



## Make Directory
### mkdir()
**사용법**
> #include <sys/types.h>
> #include <sys/stat.h>
> int mkdir(const char* 경로이름, 모드)
#### 모드
>  S_IRUSR : user-read

>S_IWUSR : user-write

>S_IXUSR : user-execute

>S_IRGRP : group-read

>S_IWGR : group-write

>S_IXGRP : group-execute

>S_IROTH : other-read

>S_IWOTH : other-write

>S_IXOTH : other-execute

> 심화 : IRWXU는 S_IRUSR | S_IWUSR | S_IXUSR와 같다.

> 예시 : mkdir("C:\Users\GrapCandy", S_IRWXU | S_IRWXG | S_IRWXO)



## Reading a Directory
### DIR 구조체
> 디렉토리 스트림(DIR *)
> 접근 가능한 디렉토리에 접근할 때 필요한 구조체
> FILE 구조체와 비슷한 역할을 한다.
> #include <dirent.h>를 이용하여 사용가능하다.
### opendir()
> 경로 이름에 상응하는 디렉토리 스트림을 열고 해당 스트림에 대한 pointer를 반환한다.
> pointer는 디렉토리의 첫번째 entry를 가리킨다.
**사용법**
> #include <sys/types.h>
> #nclude <dirent.h>
> DIR* opendir(경로이름)
### readdir()
**사용법**
>#include <sys/types.h>
>#include <dirent.h>
>struct dirent* readdir(DIR* dp)
#### DIR* dp
> dp가 가리키고 있는 디렉토리 entry에서 다음 디렉토리 entry에 대한 pointer를 반환한다.
> 마지막 entry라면 null을 반환한다.
### closedir()
> 해당 디렉토리 스트림을 닫는다.
