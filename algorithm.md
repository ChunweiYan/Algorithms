<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#org67e10b5">1. binary operations</a>
<ul>
<li><a href="#org0397809">1.1. set some bit</a></li>
<li><a href="#org3e70d09">1.2. reset some bit</a></li>
<li><a href="#orgc1547c5">1.3. check some bit</a></li>
<li><a href="#org7289001">1.4. bitset</a>
<ul>
<li><a href="#org5c4258a">1.4.1. operators</a></li>
</ul>
</li>
<li><a href="#orgf74f69f">1.5. storeage of negative numbers</a></li>
<li><a href="#org6d2c7cf">1.6. classicial problems</a>
<ul>
<li><a href="#org007e927">1.6.1. XOR</a></li>
<li><a href="#org19b5f97">1.6.2. bits as tiny hashmap (which has less than 32 or 64 entries)</a></li>
</ul>
</li>
</ul>
</li>
<li><a href="#org3ebafa5">2. trees</a></li>
<li><a href="#org3345ec8">3. Dynamic Programming</a></li>
</ul>
</div>
</div>
This post is my notes for preparing a coding interview, 
including some thoughts about classic problems, 
and some terminologies that might be necessary for an interview.


<a id="org67e10b5"></a>

# binary operations

The basic binary operations are as follows

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">`<<`</td>
<td class="org-left">left shift</td>
<td class="org-left">`1<<2` gets 2</td>
</tr>


<tr>
<td class="org-left">`>>`</td>
<td class="org-left">right shift</td>
<td class="org-left">`4>>2` gets 1</td>
</tr>


<tr>
<td class="org-left">`&`</td>
<td class="org-left">bitwise and</td>
<td class="org-left">`0 & 1 = 0`</td>
</tr>


<tr>
<td class="org-left">`\vert`</td>
<td class="org-left">bitwise or</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">`\~`</td>
<td class="org-left">bitwise complement</td>
<td class="org-left">`unsigned int max=\~0`</td>
</tr>


<tr>
<td class="org-left">`^`</td>
<td class="org-left">bitwise Exclusive-Or (XOR)</td>
<td class="org-left">`10^11=01`</td>
</tr>
</tbody>
</table>


<a id="org0397809"></a>

## set some bit

    x |= 1 << n;


<a id="org3e70d09"></a>

## reset some bit

    x &= (~0 ^ (1<<n))


<a id="orgc1547c5"></a>

## check some bit

    x & (1<<n)


<a id="org7289001"></a>

## bitset

Bitset is a c++ container for bits.


<a id="org5c4258a"></a>

### operators

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">`test`</td>
<td class="org-left">access the specific bit</td>
</tr>


<tr>
<td class="org-left">`all`</td>
<td class="org-left">check if all bits are set to `true`</td>
</tr>


<tr>
<td class="org-left">`any`</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">`none`</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">`count`</td>
<td class="org-left">returns the number of bits set to `true`</td>
</tr>


<tr>
<td class="org-left">`size`</td>
<td class="org-left">return the size number of bits that bitset can hold</td>
</tr>


<tr>
<td class="org-left">`set`</td>
<td class="org-left">sets bits to `true` or gien value</td>
</tr>


<tr>
<td class="org-left">`reset`</td>
<td class="org-left">sets bits to `false`</td>
</tr>


<tr>
<td class="org-left">`flip`</td>
<td class="org-left">toggles the values of bits</td>
</tr>


<tr>
<td class="org-left">`to_string`</td>
<td class="org-left">returns a string representation of the data</td>
</tr>


<tr>
<td class="org-left">`to_ulong`</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">`to_ullong`</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">`&`</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">`\vert`</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">`^`</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">`<<`</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">`>>`</td>
<td class="org-left">&#xa0;</td>
</tr>
</tbody>
</table>

    using namespace std;
    
    bitset<16> bits;
    bits.set(1);
    bits.set(3);
    bits.set(5);
    
    cout << bits.to_string() << endl;
    cout << "~ " << bits.flip().to_string() << endl;


<a id="orgf74f69f"></a>

## storeage of negative numbers

A positive number is representated as itself while a negative number 
is representated as the two's complement of its absolute value.

In other words, the binary representation of -K as a N-bit number is concat(1, 2<sup>(N-1)</sup>-K).


<a id="org6d2c7cf"></a>

## classicial problems


<a id="org007e927"></a>

### XOR

-   Single Number
-   Single Number II
-   Single Number III


<a id="org19b5f97"></a>

### bits as tiny hashmap (which has less than 32 or 64 entries)

By using an `unsigned int` or `unsigned long long`, one can get a hashmap with constant memroy.

The bitset can be used too, but its size is fixed.


<a id="org3ebafa5"></a>

# trees


<a id="org3345ec8"></a>

# Dynamic Programming

