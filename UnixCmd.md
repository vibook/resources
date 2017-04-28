## Unix/Linux Commands
### 압축
```
$> tar cvf filename.tar [file1] [file2] ...
$> gzip filename.tar
$> tar cvzf filename.tar.gz [file1] [file2] ...
$> tar jcvf filename.tar.bz2 [filename]
```

### 압축 풀기
```
$> gunzip filename.tar.gz
$> tar xvf filename.tar
$> tar xvzf filename.tar.gz
$> tar jxvf filename.tar.gz2
```

### 파일
```
$> mv test1.txt test2.txt  # 파일 이름 바꾸기
$> rm test01.txt # 파일 삭제
```

### 디렉토리
```
$> cp /home/test1/ /home/test2 # 디렉토리 복사
$> cp -r /home/test1 /home/test2 # 디렉토리 복사(하위 디렉토리 포함)
$> rmdir test01 # 디렉토리 삭제
$> mvdir test1 test2 # 디렉토리 이름 변경 또는 이동
```

### 와일드카드 문자 및 메타문자
```
*log : log로 끝나는 모든 파일
*file* : file이 들어가는 모든 파일
file? : file 뒤에 한 문자
file?? : file 뒤에 두 문자
file[12] : file1과 file2 선택 가능
file[0-5] : file 뒤에 숫자 0~5까지 가능
[!a]* : a로 시작하지 않는 모든 파일
```
