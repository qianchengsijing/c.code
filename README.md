# c.code
#include <stdio.h>

int main()
{
	int a = 0;
	printf("%d\n",~a);
	int a = 11;
	printf("%d\n",++a);
	printf("%d\n",a++);
	printf("%d\n",a);
	a = a | (1<<2);
	printf("%d\n",a);
	a = a & (~(1<<2));
	printf("%d\n",a);
	int i = 0,a = 0,b = 2,c = 3,d = 4;
	i = a++ && ++b && d++;//1,2,3,4
	i = a++ || ++b || d++;//1,3,3,4
	int i = 0,a = 1,b = 2,c = 3,d = 4;
	//i = a++ && ++b && d++;//2,3,3,5
	i = a++ || ++b || d++;//2,2,3,4
	printf("a = %d\n b = %d\n c = %d\n d = %d\n",a,b,c,d);
	return 0;
}
int main()
{
	int a = 0;
	int b = 0;
	int max = 0;
	if(a > b)
		max = a;
	else
		max = b;
	max = (a > b ? a : b);
	printf("%d\n",max);
	/*int a = 0;
	int b = 0;
	if(a>5)
		b = 3;
	else
		b = -3;
	b = (a > 5 ? 3 : -3);
	printf("%d\n",b);*/
	return 0;
}
int main()
{
	/*int a = 1;
	int b = 2;
	int c = (a>b,a=b+10,a,b=a+1);
	printf("%d\n",c);*/
	int a = 0;
	a=get_val();
	count_val(a);
	while(a>0)
	{
		a=get_val();
	    count_val(a);
	}//等价于while(a=get_val(),count_val(a),a>0);
	return 0;

}
int main()
{
	char a = 3;
	//00000000000000000000000000000011
	//00000011
	char b = 127;
	//00000000000000000000000001111111
	//01111111
	//计算相加
	//00000000000000000000000000000011
	//00000000000000000000000001111111//1+1余0进1，1+1+1=3，3余1进1，逢2进1
	//00000000000000000000000010000010//整形提升高位补充符号位1
	//11111111111111111111111110000010-补码
	//11111111111111111111111110000001-反码
	//10000000000000000000000001111110-原码
	char c = a + b;
	printf("%d\n",c);//结果为-126
	return 0;

}

//创建结构体变量
struct stu
{
	char name[20];
	int age;
	char id[20];
};
int main()
{
	struct stu s1={"张三",20,"20201456"};
	struct stu* ps = &s1;
	printf("%s\n",(*ps).name);
	printf("%s\n",(*ps).age);
	printf("%s\n",(*ps).id);
	printf("%s\n",ps->name);
	printf("%s\n",ps->age);
	printf("%s\n",ps->id);
	printf("%s\n",s1.name);
	printf("%s\n",s1.age);
	printf("%s\n",s1.id);

	return 0;
}
int main()
{
	char a = 0xb6;//b为16进制，6为16进制，10110110整形提升后超过一个字节（char为一个字节放不下）
	short b = 0xb600;//同理
	int c = 0xb60000;//已经为整形
	if(a == 0xb6)
		printf("a");
	if(b == 0xb600)
		printf("b");
	if(c == 0xb60000)
		printf("c");
	return 0;//输出为c
}
int main()
{
	char c =1;
	printf("%u\n",sizeof(c));
	printf("%u\n",sizeof(+c));//只要c进行表达式运算，就会发生整形提升为int为4个字节
	printf("%u\n",sizeof(!c));
	return 0;
}
int fun()
{
	static int count = 1;//static修饰
	return ++count;
}
int main()
{
	int answer;
	answer = fun()-fun()*fun();//不确定运算的顺序，结果不同
	printf("%d\n",answer);
	return 0;
}
int main()
{
	int a = -1;
	int b = a>>1;;
	printf("%d\n",b);
	return 0;
}
