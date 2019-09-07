Code Review
===============

1. tab = 4 sapces (in RapidSQL, extend tab)
2. function name UPPERcase
3. align '='
4. one statement per line
5. case 
       when
6. check error for each statement
7. @@error/@@rowcount is only the impact of the last statement, so sometimes we use a variable to store the values for logging
8. don't need order by in insert in req proc, put it in response -> data in table are not necessarily the insert order
9. for optional input parameters, instead of checking them in where clause, check them beforehand and set them to some impossible values -> performance gain
10. if
    begin
        select
    end
    else
11. check parameter constraints, not only madatory or not
12. read though code again after finish
13. space for paratthes for large complex logic block