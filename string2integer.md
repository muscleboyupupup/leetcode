# leetcode
# string2integer
class Solution {
public:
    int myAtoi(string str) {
        int number=0;
        int i=0;
        int flag=0;
        while (str[i]==' ' or str[i]=='  ') 
            i++;
        if (str[i]=='-')
        {
            i++;
            flag=1;
        }
        else if(str[i]=='+')
            i++;
        while (isdigit(str[i]))  //最初觉得只考虑数值（绝对值）是否溢出不对，因为负数（32位signed integer）的数值部分最大为2147483648，而正数最大为2147483647，所以在while函数里-2147483648会被判定为溢出（但实际并未溢出），但输出并未受影响，输出-2147483648，结果正确，所以只用考虑绝对值的溢出。
       {
            int Newnumber=number*10+str[i]-'0';
            if((Newnumber/10)!=number)
            {
                if (flag==0) 
                    return INT_MAX;
                else return INT_MIN; 
            }
            number=Newnumber;
            i++;
        }
        if (flag==1) return -number;
        return number;
    }
};
