# 058 Huffman Compression

Huffman compression is a very simple lossless compression aglorithm. How does it work?

Well first let's take a basic look of how compression works. Take a look at the following sentence:

```
Silly Sally sells seashells.
```

Let's also take a look at what this sentence looks like stored in binary using 8 bits per character:

```
01010011 01101001 01101100 01101100 01111001 00100000 01010011 01100001 01101100
01101100 01111001 00100000 01110011 01100101 01101100 01101100 01110011 00100000
01110011 01100101 01100001 01110011 01101000 01100101 01101100 01101100 01110011
00101110
```

We can now create a dictionary of the most frequently occuring characters and assigning them smaller binary values. Let's take a look at what the frequency table for the original sentence is:

<table><thead><tr><th width="120">Character</th><th width="131">Frequency</th></tr></thead><tbody><tr><td>l</td><td>8</td></tr><tr><td>s</td><td>5</td></tr><tr><td>space</td><td>3</td></tr><tr><td>e</td><td>3</td></tr><tr><td>S</td><td>2</td></tr><tr><td>y</td><td>2</td></tr><tr><td>a</td><td>2</td></tr><tr><td>i</td><td>1</td></tr><tr><td>h</td><td>1</td></tr><tr><td>.</td><td>1</td></tr></tbody></table>

Now instead of repeating the 8 bit value for every character in our data, we can assign the most frequently occurring characters smaller binary values:

<table><thead><tr><th width="116">Character</th><th width="139">Binary Value</th></tr></thead><tbody><tr><td>l</td><td>0</td></tr><tr><td>s</td><td>1</td></tr><tr><td>space</td><td>10</td></tr><tr><td>e</td><td>11</td></tr><tr><td>S</td><td>100</td></tr><tr><td>y</td><td>101</td></tr><tr><td>a</td><td>110</td></tr><tr><td>i</td><td>111</td></tr><tr><td>h</td><td>1000</td></tr><tr><td>.</td><td>1001</td></tr></tbody></table>

Take a look at what the resulting data is now:

```
100 111 0 0 101 10 100 110 0 0 101 10 1 11 0 0 1 10 1 11 110 1 1000 11 0 0 1 1001
```

What a reduction! If you want to know how much of one you do the math yourself.

(Just kidding, I did it. A reduction of 167 bits, or 67%)

Huffman coding using a binary tree to assign fewer bits to more frequently occuring items.
