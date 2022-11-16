## 特定の数字にBackgroundColorを設定する

複数の場合、querySelectorAllで要素を取得し、for文で回す

**やりたいことのイメージ**

![レース検索](https://user-images.githubusercontent.com/105257856/185064786-eb3761d7-f2a5-427c-8d83-cb09ebd45bf9.png)

枠順において、特定の数字に色を表示したい。枠順は同じ数字が複数存在するため、getElementByIdでは最初のものしかとれない。（querySelectorでも同様。複数取ってくる場合はquerySelectorAllとする）


```JavaScript
window.addEventListener('load', function() {

	let ranking1 = document.getElementById('rank1');
	let ranking2 = document.getElementById('rank2');
	let ranking3 = document.getElementById('rank3');
	
	let waku1 = document.querySelectorAll('.waku1');
	let waku2 = document.querySelectorAll('.waku2');
	let waku3 = document.querySelectorAll('.waku3');
	let waku4 = document.querySelectorAll('.waku4');
	let waku5 = document.querySelectorAll('.waku5');
	let waku6 = document.querySelectorAll('.waku6');
	let waku7 = document.querySelectorAll('.waku7');
	let waku8 = document.querySelectorAll('.waku8');

	ranking1.bgColor = '#FFFF66';
	ranking2.bgColor = '#CCCCCC';
	ranking3.bgColor = '#BDB76B';

	for(let i = 0; i < waku1.length; i++){
		waku1.item(i).bgColor = 'white';
	}
	for(let i = 0; i < waku2.length; i++){
		waku2.item(i).bgColor = '#000000';
		waku2.item(i).style.color = 'white';
	}
	for(let i = 0; i < waku3.length; i++){
		waku3.item(i).bgColor = '#FF0000';
	}
	for(let i = 0; i < waku4.length; i++){
		waku4.item(i).bgColor = '#0000FF';
		waku4.item(i).style.color = 'white';
	}
	for(let i = 0; i < waku5.length; i++){
		waku5.item(i).bgColor = '#FFFF00';
	}
	for(let i = 0; i < waku6.length; i++){
		waku6.item(i).bgColor = '#006600';
		waku6.item(i).style.color = 'white';
	}
	for(let i = 0; i < waku7.length; i++){
		waku7.item(i).bgColor = '#FF6928';
	}
	for(let i = 0; i < waku8.length; i++){
		waku8.item(i).bgColor = '#FF55FF';
	}	
})
```
