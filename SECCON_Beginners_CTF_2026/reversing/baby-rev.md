## reversing
#### baby-rev
>Welcome to the world of Reversing! I hope you find it interesting :)


以下のCプログラムが与えられる問題です．
```c:baby-rev.c
#include <stdio.h>

int main()
{
    const unsigned char xorFlag[] = {0xeb,0xfc,0xee,0xbc,0xea,0xf3,0xe4,0xb8,0xb8,0xe3,0xd7,0xe5,0xb8,0xe5,0xd7,0xe6,0xb8,0xd7,0xe0,0xbc,0xe6,0xec,0xfb,0xd7,0xe2,0xfd,0xfb,0xfc,0xd7,0xf0,0xb8,0xfa,0xa9,0xf5};
    const int xorKey = 0x88;
    const int len = 34;

    unsigned char inp[64] = {0};
    printf("INPUT > ");


    if (scanf("%63s", inp) != 1) {
        printf("Wrong:(\n");
        return -1;
    }

    int inputLen = 0;
    while (inp[inputLen] != '\0') inputLen++;
    if (inputLen != len) {
        printf("Wrong:(\n");
        return -1;
    }

    for (int i = 0; i < len; i++) {
        if ((inp[i] ^ xorKey) != xorFlag[i]) {
            printf("Wrong:(\n");
            return -1;
        }
    }

    printf("Correct:)\n");
    return 0;
}
```

実際にコンパイルして実行してみるとわかりやすいですが，文字列を入力するとそれがflagと一致するか教えてくれます．入力が正常に行われたか，文字列長がflag長と一致するかなども見ているようですが，問題を解く(少なくとも私が解いた)うえでは関係ありませんでした．

重要なのは
```c
for (int i = 0; i < len; i++) {
    if ((inp[i] ^ xorKey) != xorFlag[i]) {
        printf("Wrong:(\n");
        return -1;
    }
}
```
の部分です．(１番下のfor文)

入力文字列を１文字ずつ見ていき，`xorKey`とのXORをとったものが`xorFlag`の該当箇所と一致するか確認しているようです．

この判定方法が成り立つということは，`xorFlag`はflagの各文字に対して`xorKey`とのXORをとったものであると推測できます．２回XORをすると元の値に戻るというのは有名な性質です．これを利用すると，与えられたプログラムに以下の処理を追加することでflagを表示させることができます！

```c
for(int i = 0;i < len;i++){
    printf("%c", xorFlag[i]^xorKey); // ∵ P XOR K = C ⇒ C XOR K = P
}
printf("\n");
```

これを置く位置には注意が必要です．`return -1`等が呼び出される前に実行されるようにしてください．いちいち入力するのも面倒なので，定数が宣言されているすぐ後に置くのが無難かなと思います．

:::details flag
`ctf4b{l00k_m0m_n0_h4nds_just_x0r!}`
:::
