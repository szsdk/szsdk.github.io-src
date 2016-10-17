Title: C Idiom
Date: Mon Oct 17 07:34:39 CST 2016
Modified: Mon Oct 17 07:34:47 CST 2016
Category: C
Tags: C
Slug: my-super-post
Authors: sz
Summary: <++>

## offsetof

```c
#include <stdio.h>
#include <stdlib.h>
#define offsetof(TYPE, MEMBER) ((size_t) &((TYPE *)0)->MEMBER)
 
struct abc {
    int a;
    int b[4];
    int c;
} abc_inst;
 
int main()
{
    printf ("%lu %lu %lu\n", offsetof(struct abc, a), 
                        offsetof(struct abc, b), 
                        offsetof(struct abc, c));
    return 0;
}
```

This prints
```
0 4 20
```

## Array size macro

```c
#define ARRAY_SIZE(x) (sizeof(x) / sizeof((x)[0]))

// Can be used like this:
int a[] = {0, 4, 5, 6};
int n = ARRAY_SIZE(a); // n = 4

// Warning: does not work with array arguments to functions:
int func(int a[]) {
    int nb = ARRAY_SIZE(a); // Would not work!
}
```

## Size of variables

```c
Sometype *a = malloc(sizeof *a);
```
