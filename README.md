# -Sieve-of-Eratosthenes-algorithm
This algorithm find all the prime numbers upto given integer

#include <iostream>
using namespace std;
#include <vector>
int countPrimes(int n)
{
    /******Time complexity is (n root n) whis is not optimise solution*****/

    /* if(n<=2) return 0;
     int  count=0;
     for(int i=2;i<n;i++){
         int flag=1;
         for(int j=2;j<=sqrt(i);j++){
             if(i%j==0){
                 flag=0;
                 break;
             }
         }
         if(flag==1) count++;
     }
     return count;
     */

    /***** time complexity is n log log n.....******/
    if (n <= 2)
        return 0;
    int count = 0;
    vector<bool> prime(n, true);
    prime[0] = prime[1] = false;
    for (int i = 2; i * i < n; i++)
    {
        if (prime[i])
        {
            for (int j = i * i; j < n; j += i)
            {
                prime[j] = false;
            }
        }
    }
    for (int i = 2; i < n; i++)
    {
        if (prime[i])
            count++;
    }
    return count;
}

int main()
{
    int num;
    cout << "Enter the number to count prime numbers less than:  ";
    cin >> num;
    cout << countPrimes(num);
}
