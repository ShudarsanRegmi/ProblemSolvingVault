- Range is to be known in prior
- It is an efficient sorting algorithm that works for integers or strings with fixed sized keys
- It can be performed using different variations: Least Significant Digit(LSD) Radix sort  or Most Significant Digit (MSD) Radix sort




- Find the no. of digits in largest element. 

$$No.\ of \ iteraitons = No.\ of \ digits \ in \ largest \ element$$

```
 for (int place = 1; max / place > 0; place *= 10)
    countingSort(array, size, place);
```

eg. max = 5525
5525/1 = 5525 => place = 1
5525/10 = 552 => place = 10
5525/100 = 55 => place = 100
5525/1000 = 5 => place = 1000
5525 / 1000 = 0 => loop won't execute

=> Loop is made for CountSort of all the places

