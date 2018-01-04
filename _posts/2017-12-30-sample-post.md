---
layout: post
title: Segundo teste - jupyter notebook
tags: [test, sample]
---

Aqui haverá uma pequena explicação sobre algum tópico importante para o correto entendimento de um determinado assunto. E, como referência adicional, há, também, um link para futuras pesquisas - para tal, clique [aqui](http://www.google.com).

Em adição, podem existir também, equações **importantes**, ***médio importantes*** e *pouco importantes*, como essa *inline*: $$\displaystyle \int_0^\infty e^{-x^2} dx$$, ou essa aqui que aparece em uma nova linha:

$$
\frac{1}{\displaystyle 1+
\frac{1}{\displaystyle 2+
\frac{1}{\displaystyle 3+x}}} +
\frac{1}{1+\frac{1}{2+\frac{1}{3+x}}}
$$


```python
import numpy  as np
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
```

## Seção dois
Aqui vai outro texto para preencher esse espaço, possibilitando, portanto, que o leitor consiga identificar elementos importantes no código, e compreender o que está, de fato, acontecendo


```python
my_array = np.array(np.arange(0, 25)).reshape(5, 5)
my_array
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22, 23, 24]])




```python
my_array.flatten()
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19, 20, 21, 22, 23, 24])




```python
data = {'1st column': pd.Series([1, 2, 3], index = ['A', 'B', 'C']),
        '2nd column': pd.Series([4, 5, 6], index = ['A', 'B', 'D'])}
```


```python
my_df = pd.DataFrame(data)
my_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1">
  <thead>
    <tr>
      <th></th>
      <th>1st column</th>
      <th>2nd column</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>1.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>B</th>
      <td>2.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>C</th>
      <td>3.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>D</th>
      <td>NaN</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
print("Hello, world!")
```

    Hello, world!


### Seção três

Aqui vai alguma coisa do **matplotlib.pyplot**:

* Bullet 1
* Bullet 2
  * Bullet 2a
  * Bullet 2b
* Bullet 3

> One thing was certain, that the white kitten had had nothing
> to do with it -- it was the black kitten's fault entirely. For
> the white kitten had been having its face washed by the old cat,
> for the last quarter of an hour (and bearing it pretty well,
> considering) so you see that it couldn't have had any hand in
> the mischief. <cite>Lewis Carroll, Through the Looking
> Glass</cite>


```python
import numpy as np

import matplotlib.pyplot as plt
import matplotlib.patches as patches
import matplotlib.path as path
import matplotlib.animation as animation

fig, ax = plt.subplots()

# histogram our data with numpy
data = np.random.randn(1000)
n, bins = np.histogram(data, 100)

# get the corners of the rectangles for the histogram
left = np.array(bins[:-1])
right = np.array(bins[1:])
bottom = np.zeros(len(left))
top = bottom + n
nrects = len(left)

# here comes the tricky part -- we have to set up the vertex and path
# codes arrays using moveto, lineto and closepoly

# for each rect: 1 for the MOVETO, 3 for the LINETO, 1 for the
# CLOSEPOLY; the vert for the closepoly is ignored but we still need
# it to keep the codes aligned with the vertices
nverts = nrects*(1 + 3 + 1)
verts = np.zeros((nverts, 2))
codes = np.ones(nverts, int) * path.Path.LINETO
codes[0::5] = path.Path.MOVETO
codes[4::5] = path.Path.CLOSEPOLY
verts[0::5, 0] = left
verts[0::5, 1] = bottom
verts[1::5, 0] = left
verts[1::5, 1] = top
verts[2::5, 0] = right
verts[2::5, 1] = top
verts[3::5, 0] = right
verts[3::5, 1] = bottom

barpath = path.Path(verts, codes)
patch = patches.PathPatch(
    barpath, facecolor='green', edgecolor='yellow', alpha=0.5)
ax.add_patch(patch)

ax.set_xlim(left[0], right[-1])
ax.set_ylim(bottom.min(), top.max())


def animate(i):
    # simulate new data coming in
    data = np.random.randn(1000)
    n, bins = np.histogram(data, 100)
    top = bottom + n
    verts[1::5, 1] = top
    verts[2::5, 1] = top
    return [patch, ]

ani = animation.FuncAnimation(fig, animate, 100, repeat=False, blit=True)
plt.show()
```


![png]({{ site.baseurl }}/assets/img/myDocument_11_0.png)
