# 糖果大战

Problem Description

生日Party结束的那天晚上，剩下了一些糖果，Gandon想把所有的都统统拿走，Speakless于是说：“可以是可以，不过我们来玩24点，你不是已经拿到了一些糖果了吗？这样，如果谁赢一局，就拿走对方一颗糖，直到拿完对方所有的糖为止。”如果谁能算出来而对方算不出来，谁就赢，但是如果双方都能算出或者都不能，就算平局，不会有任何糖果的得失。

Speakless是个喜欢提前想问题的人，既然他发起了这场糖果大战，就自然很想赢啦（不然可就要精光了-_-）。现在他需要你的帮忙，给你他每局赢的概率和Gardon每局赢的概率，请你给出他可能获得这场大战胜利的概率。


Input

每行有四个数，Speakless手上的糖果数N、Gardon手上的糖果数M(0<=N,M<=50)、一局Speakless能解答出来的概率p、一个问题Gardon能解答出来的概率q(0<=p,q<=1)。


Output

每行一个数，表示Speakless能赢的概率（用百分比计算，保留到小数点后2位）。


Sample Input

50 50 0.5 0.5 10 10 0.51 0.5 50 50 0.51 0.5

Sample Output

0.50 0.60 0.88


代码：

#include <stdio.h>

#include <math.h>

const double EPS = 1e-12;

inline void solve(int n, int m, double p, double q)

{

   if(n==0)             printf("0.00\n");
   
   else if(m==0)         printf("1.00\n");
   
   else if(p==0.0||q==1.0)  printf("0.00\n");
   
   else 
   
{
        double lamda = q*(1-p)/(p*(1-q));
        
        if(fabs(lamda-1.0)<EPS)           
        printf("%.2lf\n", double(n)/(m+n));
        
        else
        
 {
            double res = (1-pow(lamda, n))/(1-pow(lamda, m+n));
            
            printf("%.2lf\n", res);
            
        }
        
    }
}

int main()

{
    int n, m;
    
    double p, q;
    
    while(scanf("%d%d%lf%lf", &n, &m, &p, &q)!=EOF) {
    
        solve(n, m, p, q);
        
    }
    
    return 0;
    
}
