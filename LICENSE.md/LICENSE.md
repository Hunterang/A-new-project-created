<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title></title>
    <style type="text/css">
    *{margin: 0;padding: 0;float: left;}
    #content{width: 100%;height:142px;}
    #section_head{width:1200px;height:142px;margin: 0 78px 0 78px;}
    #img1{width: 170px;height: 46px;margin:25px 29px;margin-left:0;}
    #section_head ul {display: block;list-style: none;text-align: center;}
       #section_head ul li{ font-family: Verdana,Arial,Helvetica,sans-serif;cursor: pointer;
     float: left;}
     #section_head ul li:hover{color:#00aa88}
     .head_input{position: absolute;top: 0;right:280px;height: 64px;width: 220px;}
     .head_in_put{height: 35px;width: 220px;margin-top: 29px;font-size: 30px;}
     .head_li{ display:block; font-size: 20px; padding: 35px 18px;}
     .oul2{padding-left: 207px;height:50px;width:993px;margin-top: 0px;border-top: 1px solid lightgrey;}
     .oul2 li{display:inline;font-size: 15px; padding: 15px 23px;}
     #Keywords{display: none;width: 169px;border:2px solid lightgrey;margin-top: 4px;border-top: none;background: white;}
     #Keywords p{padding-left: 10px;font-size: 15px;line-height: 30px ;clear: both;width: 159px; text-align: left;}
     #Keywords p:hover{background: lightgrey;color:#00aa88}
    </style>;
  </head>
  <body>
    <div id="content">
      <div id="section_head">
        <h1 id="head">
          <a href="">
            <img src="logo@2x.png" alt="" / id="img1"width="170px" height="46px"  >
          </a>
        </h1>
        <ul class="head_ul">
          <li class="head_li"title="音乐馆"style="background:#00bb56">音乐馆</li>
          <li class="head_li">我的音乐</li>
          <li class="head_li">客户端</li>
          <li class="head_li">音乐号</li>
          <li class="head_li">vip</li>
        </ul>
        <ul class="oul2">
          <li class="oul2_li">首页</li>
          <li class="oul2_li">专辑</li>
          <li class="oul2_li">歌手</li>
          <li class="oul2_li">排行榜</li>
          <li class="oul2_li">分类歌单</li>
          <li class="oul2_li">电台</li>
          <li class="oul2_li">MV</li>
          <li class="oul2_li">数字专辑</li>
        </ul>
        <div class="head_input">
          <div class="head_in_put">
           <input type="text" id="nav_inout" style="height:100%" width="180px"name="searchi" value="" placeholder=" 搜索音乐、 MV 、歌手" />

        </div>
        <div id="Keywords">
          <ul >
            <!-- <li>1&nbsp;&nbsp;  nihao</li> -->
            <!-- <li>2 &nbsp;&nbsp; nihao </li> -->
            <!-- <li></li> -->
          </ul>
          </div>
        </div>



      </div>

    </div>
<script type="text/javascript">
//获得input 发生事件
var oInput=document.getElementById("nav_inout");
oInput.onkeyup=function(){
  var val=this.value;
  var oscript=document.createElement("script");
  oscript.src="https://c.y.qq.com/splcloud/fcgi-bin/smartbox_new.fcg?key="+val+"&jsonpCallback=xiao";
  document.body.appendChild(oscript);
}
var keyword=document.getElementById("Keywords");
    // oul=document.querySelector("#Keywords ul");


// arr.forEach(function(val){
//   var oli=document.createElement("li");
//   oli.innerText=val.name;
//   oul.appendChild(oli);
//   })
function xiao(data){
  keyword.innerText=""
  // console.log(data);

  // console.log(albumArr);
  var albumArr=data.data.album.itemlist;
  var MVArr=data.data.mv.itemlist;
  var singerArr=data.data.singer.itemlist;
  var songArr=data.data.song.itemlist;

  if (!MVArr.length&!MVArr.length&!singerArr.length&!songArr.length) {
    return keyword.style.display=none;
  }

  keyword.style.display="block";

  if (albumArr.length>0) {
    var alb=document.createElement("h3")
    alb.innerText="专辑";
    keyword.appendChild(alb);
    albumArr.forEach(function(val){
      var oli=document.createElement("p");
          oli.innerText=val.name;
      oli.onclick=function(){
        window.location.href="https://www.baidu.com/s?wd="+val.name;
      }
      keyword.appendChild(oli);  })
  }

if (MVArr.length>0) {
  var mv=document.createElement("h3")
  mv.innerText="视频";
  keyword.appendChild(mv);
  MVArr.forEach(function(val){
      var oli=document.createElement("p");
      oli.innerText=val.name;
      oli.onclick=function(){
        window.location.href="https://www.baidu.com/s?wd="+val.name;
      }
      keyword.appendChild(oli);
      })
}
if (singerArr.length>0) {
  var singer=document.createElement("h3")
  singer.innerText="歌手";
  keyword.appendChild(singer);
  singerArr.forEach(function(val){
        var oli=document.createElement("p");
        oli.innerText=val.name;
        oli.onclick=function(){
          window.location.href="https://www.baidu.com/s?wd="+val.name;
        }
        keyword.appendChild(oli);
        })
}

if (songArr.length>0) {
  var song=document.createElement("h3")
      song.innerText="歌曲";
      keyword.appendChild(song);
  songArr.forEach(function(val){
          var oli=document.createElement("p");
          oli.innerText=val.name;
          oli.onclick=function(){
            window.location.href="https://www.baidu.com/s?wd="+val.name;
          keyword.appendChild(oli);
        }
          })
}


  // console.log(songArr);


  }
</script>

</body>
</html>
