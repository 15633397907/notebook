# Section.1 转动的线

```C++
#include<Windows.h>
while (1)
{
  for (int i = 0; i < 12; i++)
  {
    printf("\b%c", "\\|/-\\|/-\\|/-"[i]);
    Sleep(150);
  }
}

//sleep首字母大写,数字应该是以毫秒为单位
//\b=backspace 退格键

```

>16是4的3倍 \
对应的，下面要写三组“\\|/-” \
注意：不能使用中文符号 会发生错误