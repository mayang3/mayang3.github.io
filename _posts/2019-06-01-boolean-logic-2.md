---
title: "Boolean Logic (불 논리)-2"
tag:
- boolean logic
- hardware
- computer science
- nand2tetris
- MIT
categories:
- computer science
---
## Continue...
[boolean-logic-1](https://mayang3.github.io/computer%20science/boolean-logic/) 에 이어 
나머지 Multi-Bit Version 과 Multi-Way Version 을 구현해 보자.

기존과 마찬가지로, 각각의 명세와 내가 구현한 hdl 코드, 그리고 하드웨어 시뮬레이터의 테스트 성공 화면을 넣었다.

## Multi-Bit Version
컴퓨터 하드웨어는 일반적으로 bus 라고 불리는 multi-bit 배열에 대해 연산을 수행한다.
예를 들면, 32bit 컴퓨터는 기본적으로 두 개의 32bit bus 에 대해 and 함수를 bit 단위로 계산할 수 있다.

### Multi-Bit Not
``` text
// Specification
Chip name: Not16
Inputs: in[16] // a 16-bit pin
Outputs: out[16]
Function: For i=0..15 out[i]=Not(in[i]).
```

``` text
// implementation
CHIP Not16 {
    IN in[16];
    OUT out[16];

    PARTS:
    Not (in=in[0], out=out[0]);
    Not (in=in[1], out=out[1]);
    Not (in=in[2], out=out[2]);
    Not (in=in[3], out=out[3]);
    Not (in=in[4], out=out[4]);
    Not (in=in[5], out=out[5]);
    Not (in=in[6], out=out[6]);
    Not (in=in[7], out=out[7]);
    Not (in=in[8], out=out[8]);
    Not (in=in[9], out=out[9]);
    Not (in=in[10], out=out[10]);
    Not (in=in[11], out=out[11]);
    Not (in=in[12], out=out[12]);
    Not (in=in[13], out=out[13]);
    Not (in=in[14], out=out[14]);
    Not (in=in[15], out=out[15]);
}
``` 

![IMAGE]({{ site.url }}{{ site.baseurl }}/assets/images/nand_to_tetris/C3E6DD47921E42CCB9BFA8F5A6887FFD.jpg)


### Multi-Bit And
``` text
// Specification
Chip name: And16
Inputs: a[16], b[16]
Outputs: out[16]
Function: For i=0..15 out[i]=And(a[i],b[i]).
```

``` text
// implementation
CHIP And16 {
    IN a[16], b[16];
    OUT out[16];

    PARTS:
    And (a=a[0], b=b[0], out=out[0]);
    And (a=a[1], b=b[1], out=out[1]);
    And (a=a[2], b=b[2], out=out[2]);
    And (a=a[3], b=b[3], out=out[3]);
    And (a=a[4], b=b[4], out=out[4]);
    And (a=a[5], b=b[5], out=out[5]);
    And (a=a[6], b=b[6], out=out[6]);
    And (a=a[7], b=b[7], out=out[7]);
    And (a=a[8], b=b[8], out=out[8]);
    And (a=a[9], b=b[9], out=out[9]);
    And (a=a[10], b=b[10], out=out[10]);
    And (a=a[11], b=b[11], out=out[11]);
    And (a=a[12], b=b[12], out=out[12]);
    And (a=a[13], b=b[13], out=out[13]);
    And (a=a[14], b=b[14], out=out[14]);
    And (a=a[15], b=b[15], out=out[15]);
}
``` 

![IMAGE]({{ site.url }}{{ site.baseurl }}/assets/images/nand_to_tetris/85EEF45E8968BF4A1158D3FDBAA34C0E.jpg)

### Multi-Bit Or
``` text
// Specification
Chip name: Or16
Inputs: a[16], b[16]
Outputs: out[16]
Function: For i=0..15 out[i]=Or(a[i],b[i]).
```

``` text
// implementation
CHIP Or16 {
    IN a[16], b[16];
    OUT out[16];

    PARTS:
    Or(a=a[0], b=b[0], out=out[0]);
    Or(a=a[1], b=b[1], out=out[1]);
    Or(a=a[2], b=b[2], out=out[2]);
    Or(a=a[3], b=b[3], out=out[3]);
    Or(a=a[4], b=b[4], out=out[4]);
    Or(a=a[5], b=b[5], out=out[5]);
    Or(a=a[6], b=b[6], out=out[6]);
    Or(a=a[7], b=b[7], out=out[7]);
    Or(a=a[8], b=b[8], out=out[8]);
    Or(a=a[9], b=b[9], out=out[9]);
    Or(a=a[10], b=b[10], out=out[10]);
    Or(a=a[11], b=b[11], out=out[11]);
    Or(a=a[12], b=b[12], out=out[12]);
    Or(a=a[13], b=b[13], out=out[13]);
    Or(a=a[14], b=b[14], out=out[14]);
    Or(a=a[15], b=b[15], out=out[15]);
}
```

![IMAGE]({{ site.url }}{{ site.baseurl }}/assets/images/nand_to_tetris/7FF6785420394C3BCC42522D48F6A0B4.jpg)
 
### Multi-Bit Multiplexor
``` text
// Specification
Chip name: Mux16
Inputs: a[16], b[16], sel
Outputs: out[16]
Function: If sel=0 then for i=0..15 out[i]=a[i]
else for i=0..15 out[i]=b[i].
```

``` text
// implementation
CHIP Mux16 {
    IN a[16], b[16], sel;
    OUT out[16];

    PARTS:
    Mux(a=a[0], b=b[0], sel=sel, out=out[0]);
    Mux(a=a[1], b=b[1], sel=sel, out=out[1]);
    Mux(a=a[2], b=b[2], sel=sel, out=out[2]);
    Mux(a=a[3], b=b[3], sel=sel, out=out[3]);
    Mux(a=a[4], b=b[4], sel=sel, out=out[4]);
    Mux(a=a[5], b=b[5], sel=sel, out=out[5]);
    Mux(a=a[6], b=b[6], sel=sel, out=out[6]);
    Mux(a=a[7], b=b[7], sel=sel, out=out[7]);
    Mux(a=a[8], b=b[8], sel=sel, out=out[8]);
    Mux(a=a[9], b=b[9], sel=sel, out=out[9]);
    Mux(a=a[10], b=b[10], sel=sel, out=out[10]);
    Mux(a=a[11], b=b[11], sel=sel, out=out[11]);
    Mux(a=a[12], b=b[12], sel=sel, out=out[12]);
    Mux(a=a[13], b=b[13], sel=sel, out=out[13]);
    Mux(a=a[14], b=b[14], sel=sel, out=out[14]);
    Mux(a=a[15], b=b[15], sel=sel, out=out[15]);
}
``` 

![IMAGE]({{ site.url }}{{ site.baseurl }}/assets/images/nand_to_tetris/B8787A5B68DE54F6B35E5B769DFF7006.jpg)

## Multi-Way Version
2-way 논리 게이트들은 입력이 여러개인 multi-way gate 들로 일반화 할 수 있다.

### Multi-Way Or
``` text
// Specification
Chip name: Or8Way
Inputs: in[8]
Outputs: out
Function: out=Or(in[0],in[1],...,in[7]).
```

``` text
// implementation
CHIP Or8Way {
    IN in[8];
    OUT out;

    PARTS:
    Or (a=in[0], b=in[1], out=o1);
    Or (a=o1, b=in[2], out=o2);
    Or (a=o2, b=in[3], out=o3);
    Or (a=o3, b=in[4], out=o4);
    Or (a=o4, b=in[5], out=o5);
    Or (a=o5, b=in[6], out=o6);
    Or (a=o6, b=in[7], out=out);
}
```

![IMAGE]({{ site.url }}{{ site.baseurl }}/assets/images/nand_to_tetris/9F2FCFB14A6BA93FED5A466814270BB9.jpg)

### Multi-Way/Multi-Bit Multiplexor
m입력 n비트 멀티플렉서는 m개의 n비트 입력 버스 중에 하나를 골라서 n비트 출력 버스에 출력한다.
선택 입력은 k개의 제어 비트로 디어 있으며, $k=\log_2 m$ 이다.

``` text
// Specification
Chip name: Mux4Way16
Inputs: a[16], b[16], c[16], d[16], sel[2]
Outputs: out[16]
Function: If sel=00 then out=a else if sel=01 then out=b
else if sel=10 then out=c else if sel=11 then out=d
Comment: The assignment operations mentioned above are all
16-bit. For example, "out=a" means "for i=0..15
out[i]=a[i]".
```

``` text
// implementation
CHIP Mux4Way16 {
    IN a[16], b[16], c[16], d[16], sel[2];
    OUT out[16];

    PARTS:
    Mux16 (a=a, b=b, sel=sel[0], out=o1);
    Mux16 (a=c, b=d, sel=sel[0], out=o2);
    Mux16 (a=o1, b=o2, sel=sel[1], out=out);
}
```
![IMAGE]({{ site.url }}{{ site.baseurl }}/assets/images/nand_to_tetris/90B1867D0A45BF1CEC28F6A19C1F3E85.jpg)

``` text
// Specification
Chip name: Mux8Way16
Inputs: a[16],b[16],c[16],d[16],e[16],f[16],g[16],h[16],
sel[3]
Outputs: out[16]
Function: If sel=000 then out=a else if sel=001 then out=b
else if sel=010 out=c ... else if sel=111 then out=h
Comment: The assignment operations mentioned above are all
16-bit. For example, "out=a" means "for i=0..15
out[i]=a[i]".
```

``` text
// implementation
CHIP Mux8Way16 {
    IN a[16], b[16], c[16], d[16],
       e[16], f[16], g[16], h[16],
       sel[3];
    OUT out[16];

    PARTS:
    Mux4Way16 (a=a, b=b, c=c, d=d, sel=sel[0..1], out=o1);
    Mux4Way16 (a=e, b=f, c=g, d=h, sel=sel[0..1], out=o2);
    Mux16 (a=o1, b=o2, sel=sel[2], out=out);
}
```
![IMAGE]({{ site.url }}{{ site.baseurl }}/assets/images/nand_to_tetris/082C52B02A24E80068A8DD1EAD587CAA.jpg)


### Multi-Way/Multi-Bit Demultiplexor
m 입력 n 비트 디멀티플렉서는 n 비트의 입력을 받아 m 개의 n비트 출력 중 하나로 내보낸다. 선택 입력은 k개의 제어 비트로 되어 있고, $k=log_2 m$ 이다.

``` text
// Specification
Chip name: DMux4Way
Inputs: in, sel[2]
Outputs: a, b, c, d
Function: If sel=00 then {a=in, b=c=d=0}
else if sel=01 then {b=in, a=c=d=0}
else if sel=10 then {c=in, a=b=d=0}
else if sel=11 then {d=in, a=b=c=0}.
```

``` text
// implementation
CHIP DMux4Way {
    IN in, sel[2];
    OUT a, b, c, d;

    PARTS:
    DMux (in=in, sel=sel[1], a=a1, b=b1);
    DMux (in=a1, sel=sel[0], a=a, b=b);
    DMux (in=b1, sel=sel[0], a=c, b=d);
}
```

![IMAGE]({{ site.url }}{{ site.baseurl }}/assets/images/nand_to_tetris/D6D4D264875594EAA276BA222B8702E1.jpg)

``` text
// Specification
Chip name: DMux8Way
Inputs: in, sel[3]
Outputs: a, b, c, d, e, f, g, h
Function: If sel=000 then {a=in, b=c=d=e=f=g=h=0}
else if sel=001 then {b=in, a=c=d=e=f=g=h=0}
else if sel=010 ...
...
else if sel=111 then {h=in, a=b=c=d=e=f=g=0}.
```

``` text
// implementation
CHIP DMux8Way {
    IN in, sel[3];
    OUT a, b, c, d, e, f, g, h;

    PARTS:
    DMux (in=in, sel=sel[2], a=o1, b=o2);
    DMux4Way(in=o1, sel=sel[0..1], a=a, b=b, c=c, d=d);
    DMux4Way(in=o2, sel=sel[0..1], a=e, b=f, c=g, d=h);
}
```

![IMAGE]({{ site.url }}{{ site.baseurl }}/assets/images/nand_to_tetris/0A95F7CC9F3BE7A1FB23A84BA0CA5BE0.jpg)

## References
* [https://www.nand2tetris.org](https://www.nand2tetris.org/)
* [https://www.coursera.org/learn/build-a-computer?](https://www.coursera.org/learn/build-a-computer?)
* [http://www.yes24.com/Product/Goods/71129079?Acode=101](http://www.yes24.com/Product/Goods/71129079?Acode=101)