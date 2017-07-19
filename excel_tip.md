#### 문자열 추출

```
     A                                 B      C         D
1    num   type   calories  soduim
2    19    Beef   135       298
3    21    Meat   173       458
4    38 Poultry   129       430

# 1. 스페이스 제거 (B2)
= =TRIM(A2)

# 2. num 분리 (C2)
=LEFT(B2, FIND(" ",B2,1))

# 3. type 분리 (D2)
=MID(B2,FIND(" ",B2,1)+1,FIND(" ",B2,FIND(" ",B2,1)+1)-FIND(" ",B2,1))

# 4. calories 분리 (D2)
=MID(B2,FIND(" ",B2,FIND(" ",B2)+1),FIND(" ",B2,FIND(" ",B2,FIND(" ",B2)+1)+1)-FIND(" ",B2,FIND(" ",B2)+1))

# 5. soduim 분리 (E2)
=RIGHT(I2,LEN(B2)- FIND(" ",B2,FIND(" ",B2,FIND(" ",B2)+1)+1))

############################################################
# Use "Text to Columns" menu instead of above fomula !!!!!!
############################################################


# substring num
=LEFT(A2, FIND(" ", A2, 1)-1)

# substitute (모든 스페이스 제거)
=SUBSTITUTE(A2, " ", "")

# check b, m, p
=IF(OR(ISERROR(FIND("B",A22)), ISERROR(FIND("M",A22)), ISERROR(FIND("P",A22))),"A","B")
```

[예제파일](https://www.dropbox.com/s/9758tg38ekjxu7c/hotdogs_manupilate_data.xlsx?dl=0)

참고 사이트
- [How to split text string in Excel by comma, space, specified characters](https://www.ablebits.com/office-addins-blog/2016/06/01/split-text-string-excel)
- [Find The Position Of First Letter From String](https://www.extendoffice.com/documents/excel/3790-excel-find-position-of-first-letter-in-string.html)
- [Find & Iserror](http://www.officetutor.co.kr/board/faq_lib/frm_vba_content.asp?page=1&idx=396)
- [Find Position Of Nth Space](https://www.extendoffice.com/documents/excel/3786-excel-find-position-of-first-space.html)
