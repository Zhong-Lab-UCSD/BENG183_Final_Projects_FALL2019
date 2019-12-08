# Final Report

![k-means demo](http://shabal.in/visuals/kmeans/random.gif)

```html
<img src="http://shabal.in/visuals/kmeans/random.gif" width=500 height=300>
```

* $N$ = the number of data points
* $~c~$ = the number of cluster centers
* $d_{ij}$ = Euclidean distance between $i^{th}$ data point and $j^{th}$ cluster center
* $~v_i$ = the $i^{th}$ cluster center
* $~m$ = weighting component, *aka* fuzziness index; $m \in (1,\infty)$
* $\mu_{ij}$ = membership of $i^{th}$ data point to $j^{th}$ cluster center
* $~y_k$ = the $k^{th}$ data point

$$ \mu_{ij} = \Big( \sum_{k=1}^c (d_{ij}/d_{ik})^{\frac{2}{m-1}} \Big)^{-1} $$

$$ v_i = \sum_{k=1}^N (u_{ik})^my_k \Big/ \sum_{k=1}^k (u_{ik})^m $$

![just a link](https://github.com/insanebruce/BENG183_Final_Projects_FALL2019/images/)

![K-Means](https://github.com/insanebruce/BENG183_Final_Projects_FALL2019/images/kmeans.png "K-Means") ![MOG]()
![K-Means](https://github.com/insanebruce/BENG183_Final_Projects_FALL2019/images/mog.png "MOG")
