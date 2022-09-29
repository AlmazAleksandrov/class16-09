### Task 7kyu:

You've just moved into a perfectly straight street with exactly n identical houses on either side of the road. 
Naturally, you would like to find out the house number of the people on the other side of the street. 

[Task link](https://www.codewars.com/kata/5f0ed36164f2bc00283aed07)

#### Solution:
```
class CodeWars {
  public static long overTheRoad(long address, long n) {

        if (address%2 == 0){
            long x = (n*2) - address;
            return 1+x;
        }
        else {
            long x = (n*2) - address;
            return x+1;
        }
        
    }
}
```

#### Fav solution:
```
class CodeWars {
  public static long overTheRoad(long address, long n) {
    return n*2+1-address;
  }
}
```

#### Comment:
They did without conditions, which greatly simplified the code.

### Task 7kyu:

Not considering number 1, the integer 153 is the first integer having this property: the sum of the third-power of each of its digits is equal to 153. 
Take a look: 153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = 153
The next number that experiments this particular behaviour is 370 with the same power.
Write the function eq_sum_powdig(), that finds the numbers below a given upper limit hMax (inclusive) that fulfills this property 
but with different exponents as the power for the digits.
eq_sum_powdig(hMax, exp): ----> sequence of numbers (sorted list) (Number one should not be considered).

[Task link](https://www.codewars.com/kata/560a4962c0cc5c2a16000068)

#### Solution:
```
import java.util.ArrayList;

class Sumpowdig {
    public static Integer[] eqSumPowDig(long Hmax, long exp)
    {
        ArrayList<Integer> ans = new ArrayList<Integer>();
        for (int i = 2; i <= Hmax; i++)
        {
            int num = i;
            int sum = 0;
            int digit = 0;
            while (num != 0)
            {
                digit = num % 10;
                for (int j = 1; j < exp; j++)
                {
                    digit = digit * (num % 10);
                }
                sum = sum + digit;
                num = num / 10;
            }
            if (sum == i) ans.add(sum);
        }
        Integer[] objects = ans.toArray(new Integer[0]);
        return objects;
    }
```

#### Fav solution:
```
import java.util.stream.LongStream;

class Sumpowdig {
    
    public static long[] eqSumPowDig(long hmax, int exp) {
        return LongStream.rangeClosed(2, hmax).filter(i -> i == String.valueOf(i).chars().asLongStream().map(j -> (long)Math.pow(Character.getNumericValue((char)j), exp)).sum()).toArray();
    }
}
```

#### Comment:
It is interesting to look at such people who decide in one line.
