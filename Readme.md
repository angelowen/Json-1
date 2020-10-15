# 儲存所有json資料用於讀取

## EX
```
var xhr = new XMLHttpRequest();
xhr.open("get","https://raw.githubusercontent.com/kiang/pharmacies/master/json/points.json");
xhr.send();
xhr.onload = function(){
 var data = JSON.parse(xhr.responseText).features
 for(let i =0;data.length>i;i++){
  var mask;
 if(data[i].properties.mask_adult == 0){
   mask = redIcon;
 }else{
   mask = greenIcon;
 } markers.addLayer(L.marker([data[i].geometry.coordinates[1],data[i].geometry.coordinates[0]], {icon: mask}).bindPopup('<h1>'+data[i].properties.name+'</h1>'+'<p>成人口罩數量'+data[i].properties.mask_adult+'</p>'));
// add more markers here...
  // L.marker().addTo(map)
  //   )
 }
 map.addLayer(markers);
}

```