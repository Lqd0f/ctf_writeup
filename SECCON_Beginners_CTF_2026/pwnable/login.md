## pwnable
#### login
> まずは手始めにadminを目指しましょう


接続先で動いているCプログラムが与えられます．
```c:main.c
#include <stdio.h>

struct user {
    char username[0x10];
    int is_admin;
};

void win() {
    system("/bin/sh");
}

static void setup(void) {
    setvbuf(stdin, NULL, _IONBF, 0);
    setvbuf(stdout, NULL, _IONBF, 0);
    setvbuf(stderr, NULL, _IONBF, 0);
}

int main() {
    setup();

    struct user normal_user = {0};
    printf("Input username: ");
    fgets(normal_user.username, sizeof(struct user), stdin);
    normal_user.username[strcspn(normal_user.username, "\n")] = '\0';
    if (normal_user.is_admin) {
        printf("Welcome, admin %s!\n", normal_user.username);
        win();
    } else {
        printf("Welcome, %s!\n", normal_user.username);
    }
    return 0;
}
```

名前を入力すると挨拶してくれるようです．管理者であると判断された場合，`win()`関数が呼び出され，bashを奪取することができます．判定には`User`構造体内のメンバ変数`is_admin`をそのまま使用しているので，これをtrueにすれば(int型なので非0ならtrue)よいです．

`User`構造体のもう１つのメンバ変数である`username`は，長さ`0x10`で宣言されています．しかし，名前の入力処理は以下のようになっています．
```c
fgets(normal_user.username, sizeof(struct user), stdin);
```
`username`への入力として`user`構造体のサイズ分を受け付けてしまっていますね．つまり，ここで`username`変数の許容以上の大きさのデータを入力することで，BOFが発生し，`is_admin`の値に干渉することができるということです．

`0x10`は１６進数表記なので，１０文字ではなく１６文字を超えるような入力をしなければいけないことに注意してください．

:::details flag
`ctf4b{l0g1n_r00t_us4r!}`
:::
