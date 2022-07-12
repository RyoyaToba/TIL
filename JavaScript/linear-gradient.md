## CASE: backgroundのliner-gradient属性をJSで設定したい
## ANS:　.style.background = 'linear-gradientによって指定する


```JavaScript
`use strict`

window.addEventListener('load', function(){
	let reviewCount = document.getElementById('reviewCount').value;
	
	if (reviewCount == 0){
		document.querySelector('.bar-graph-wrap').style.display = 'none';
	}
	
	let parcent1 = document.getElementById('graph_par1').dataset.score;
	let parcent2 = document.getElementById('graph_par2').dataset.score;
	let parcent3 = document.getElementById('graph_par3').dataset.score;
	let parcent4 = document.getElementById('graph_par4').dataset.score;
	let parcent5 = document.getElementById('graph_par5').dataset.score;

	document.getElementById('graph_star5').style.background = 'linear-gradient(to right, #ffcf32 0% ' + Math.round(parcent5) + '%,' + ' lightgray ' + Math.round(parcent5) + '% ' + '100%)'
	document.getElementById('graph_star4').style.background = 'linear-gradient(to right, #ffcf32 0% ' + Math.round(parcent4) + '%,' + ' lightgray ' + Math.round(parcent4) + '% ' + '100%)'
	document.getElementById('graph_star3').style.background = 'linear-gradient(to right, #ffcf32 0% ' + Math.round(parcent3) + '%,' + ' lightgray ' + Math.round(parcent3) + '% ' + '100%)'
	document.getElementById('graph_star2').style.background = 'linear-gradient(to right, #ffcf32 0% ' + Math.round(parcent2) + '%,' + ' lightgray ' + Math.round(parcent2) + '% ' + '100%)'
	document.getElementById('graph_star1').style.background = 'linear-gradient(to right, #ffcf32 0% ' + Math.round(parcent1) + '%,' + ' lightgray ' + Math.round(parcent1) + '% ' + '100%)'

})
```

* CSSはstyleによって指定する
* Math.roundは小数点を四捨五入する
* [グラフの作成はここを参考にした](https://b-risk.jp/blog/2022/06/infographics/)
* [liner-gradientはここを参考にした](https://developer.mozilla.org/ja/docs/Web/CSS/gradient/linear-gradient)

