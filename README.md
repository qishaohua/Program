0 个类型结构大小 sizeof
3. 语法：

sizeof有三种语法形式，如下：
1) sizeof( object );    // sizeof( 对象 );
2) sizeof( type_name ); // sizeof( 类型 );
3) sizeof object;       // sizeof 对象; 

2. 指针变量的sizeof 4/8

 与计算机类型有关，32为计算机，地址长度为4字节
 64位的计算机，地长度为 8字节
 这里的指针包括所有类型的指针:
    字符指针、整形指针、字符串指针、指针的指针、函数指针、数组指针等。

3.数组的sizeof

数组的sizeof值等于数组所占用的内存字节数，如：
char a1[] = "abc";
int a2[3];
sizeof( a1 ); // 结果为4，字符串末尾还存在一个NULL终止符
sizeof( a2 ); // 结果为3*4=12（依赖于int,这里int为4字节） 
// 这里注意 &a2和a2的值是相等的,都是a2[0]的地址
// 但是 &a2 的类型为 int *[10]
// 而a2的类型为 int* p

//数组元素数量求取
int c1 = sizeof( a1 ) / sizeof( char ); // 总长度/单个元素的长度(知道元素类型)
int c2 = sizeof( a1 ) / sizeof( a1[0] ); // 总长度/第一个元素的长度(不知道元素类型)

4. sizeof进行结构体大小的判断

    需要看编译器是几个字节对齐 的，一般为4字节对齐
typedef struct
{
    int a;  // 占据第一个4字节
    char b; // 占据第二个4字节
}A_t;
typedef struct
{
    int a; // 占据第一个4字节
    char b;// 占据第二个4字节中的第一个字节
    char c;// 占据第二个4字节中的第二个字节
}B_t;
typedef struct
{
    char a;// 占据第一个4字节的第一个字节
    int b; // 占据第二个4字节
    char c;// 占据第三个4字节的第一个字节
}C_t;
