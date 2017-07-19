#### 문자열 추출

```
     A                                 B      C         D
1    num   type   calories  soduim
2    19    Beef   135       298
3    21    Meat   173       458
4    38 Poultry   129       430

# 1. 스페이스 제거 (B1)
= =TRIM(A2)


# substring num
=LEFT(A2, FIND(" ", A2, 1)-1)

# check b, m, p
=IF(OR(ISERROR(FIND("B",A22)), ISERROR(FIND("M",A22)), ISERROR(FIND("P",A22))),"A","B")
```

참고 사이트
- [How to split text string in Excel by comma, space, specified character(s) or mask] (https://www.ablebits.com/office-addins-blog/2016/06/01/split-text-string-excel/)
- [Find The Position Of First Letter From String](https://www.extendoffice.com/documents/excel/3790-excel-find-position-of-first-letter-in-string.html)
- [Find & Iserror](http://www.officetutor.co.kr/board/faq_lib/frm_vba_content.asp?page=1&idx=396)
