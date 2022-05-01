# progress-bar-page-is-loading

JS 
```
document.onreadystatechange = function(e) {
  if (document.readyState == "interactive") {
    var all = document.getElementsByTagName("*");
    for (var i = 0, max = all.length; i < max; i++) {
      set_ele(all[i]);
    }
  }
}

function check_element(ele) {
  var all = document.getElementsByTagName("*");
  var totalele = all.length;
  var per_inc = 100 / all.length;

  if ($(ele).on()) {
    var prog_width = per_inc + Number(document.getElementById("progress_width").value);
    document.getElementById("progress_width").value = prog_width;
    $("#bar1").animate({
      width: prog_width + "%"
    }, 10, function() {
      if (document.getElementById("bar1").style.width == "100%") {
        $(".progress").fadeOut("slow");
      }
    });
  } else {
    set_ele(ele);
  }
}

function set_ele(set_element) {
  check_element(set_element);
}
```

CSS
```
body
{
  margin:0px; auto;
  padding:0px;
  font-family:helvetica;
}
.progress 
{
  position: fixed;
  left: 0px;
  top: 0px;
  width: 100%;
  height: 100%;
  z-index: 9999;
  background-color: #F2F2F2;
}
.bar 
{ 
  background-color: #819FF7; 
  width:0%; 
  height:5px; 
  border-radius: 3px;
}
.percent 
{ 
  position:absolute; 
  display:inline-block; 
  top:3px; 
  left:48%; 
}
#wrapper
{
  width:995px;
  padding:0px;
  margin:0px auto;
  font-family:helvetica;
  text-align:center;
}
h1
{
  text-align:center;
  font-size:35px;
  margin-top:60px;
  color:#A9BCF5;
}
h1 p
{
  text-align:center;
  margin:0px;
  font-size:18px;
  text-decoration:underline;
  color:grey;
}
```

HTML

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<div class='progress' id="progress_div">
   <div class='bar' id='bar1'></div>
   <div class='percent' id='percent1'></div>
</div>

<div id="wrapper">
   <div id="content">
     <h1>Display Progress Bar While Page Loads Using jQuery<p>TalkersCode.com</p></h1>
   </div>
</div>

<input type="hidden" id="progress_width" value="0">
```
