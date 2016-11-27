--- 
layout: post 
title: Jsxgraphs 
author: Guillaume Rabault
categories: [Tests] 
tags: [] 
fullview: false 
--- 

*This is just a test of javascript interactive graphs*

* * * * *

## Some HTML

<p>
<form>
Number of random walks: <select id="number">
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
<option value="5">5</option>
<option value="6">6</option>
<option value="7">7</option>
<option value="8">8</option>
<option value="9">9</option>
<option value="10">10</option>
<option value="15">15</option>
<option value="20" selected>20</option>
<option value="30">30</option>
<option value="50">50</option>
<option value="100">100</option>
<option value="200">200</option>
</select> <br />
<input type="button" value="run simulation" onClick="run()">
<input type="button" value="clear screen" onClick="clearturtle()">
<br />
</form>
Fixed values in this simulation are:
</p>

## Function in JSXGraph

<input type="text" id="input" value="sin(x)*x">
<input type="button" value="plot" onClick="plotter()">
<input type="button" value="clear all" onClick="clearAll()"> 
<input type="button" value="add tangent" onClick="addTangent()">
<input type="button" value="add Derivative" onClick="addDerivative()">

<div id="box" class="box" style="width:500px; height:500px;"></div>

<script type="text/javascript">
var board = JXG.JSXGraph.initBoard('box', {boundingbox:[-5,8,8,-5], axis:true});
var f, curve; // global objects

function plotter() {
  var txtraw = document.getElementById('input').value;
  f = board.jc.snippet(txtraw, true, 'x', true);
  curve = board.create('functiongraph',[f,
                function(){ 
                  var c = new JXG.Coords(JXG.COORDS_BY_SCREEN,[0,0],board);
                  return c.usrCoords[1];
                },
                function(){ 
                  var c = new JXG.Coords(JXG.COORDS_BY_SCREEN,[board.canvasWidth,0],board);
                  return c.usrCoords[1];
                }
              ],{name:txtraw, withLabel:true});
  var q = board.create('glider', [2, 1, curve], {withLabel:false});
  var t = board.create('text', [
          function(){ return q.X()+0.1; },
          function(){ return q.Y()+0.1; },
          function(){ return "The slope of the function f(x)=" + txtraw + "<br>at x=" + q.X().toFixed(2) + " is equal to " + (JXG.Math.Numerics.D(f))(q.X()).toFixed(2); }
      ], 
      {fontSize:15});
}
 
function clearAll() {
    JXG.JSXGraph.freeBoard(board);
    board = JXG.JSXGraph.initBoard('box', {boundingbox:[-5,8,8,-5], axis:true});
    f = null;
    curve = null;
}
 
function addTangent() {
    if (JXG.isFunction(f)) {
        board.suspendUpdate();
        var p = board.create('glider',[1,0,curve], {name:'drag me'});
        board.create('tangent',[p], {name:'drag me'});
        board.unsuspendUpdate();
    }
}
 
function addDerivative() {
    if (JXG.isFunction(f)) {
        board.create('functiongraph',[JXG.Math.Numerics.D(f),
                function(){ 
                  var c = new JXG.Coords(JXG.COORDS_BY_SCREEN,[0,0],board);
                  return c.usrCoords[1];
                },
                function(){ 
                  var c = new JXG.Coords(JXG.COORDS_BY_SCREEN,[board.canvasWidth,0],board);
                  return c.usrCoords[1];
                }], {dash:2});
    }
}
</script>

## Load csv

<div id="jxgbox" class="jxgbox" style="width:500px; height:200px;"></div>
</script>

<script type="text/javascript">

var board1 = JXG.JSXGraph.initBoard("jxgbox", {boundingbox:[-5,8,8,-5], axis:true});

function loadCSV(file) {
    var request;
    if (window.XMLHttpRequest) {
        // IE7+, Firefox, Chrome, Opera, Safari
        request = new XMLHttpRequest();
    } else {
        // code for IE6, IE5
        request = new ActiveXObject('Microsoft.XMLHTTP');
    }
    // load
    request.open('GET', file, false);
    request.send();
    parseCSV(request.responseText);
}

function parseCSV(data){
    
    var x=[];
    var y=[];

    //replace UNIX new lines
    data = data.replace (/\r\n/g, "\n");
    //replace MAC new lines
    data = data.replace (/\r/g, "\n");
    //split into rows
    var rows = data.split("\n");


    // loop through all rows
    for (var i = 0; i < rows.length; i++) {
        // this line helps to skip empty rows
        if (rows[i]) {
            // our columns are separated by comma
            var column = rows[i].split(",");

            // column is array now 
            // first item is date
            x[i] = column[0];
            // second item is value of the second column
            y[i] = column[1];
            board1.create('point',[x[i],y[i]]);
        }

    }

}

loadCSV("{{ site.BASE_PATH }}/assets/data/data.csv");

</script>

<!--
## Load data from url

<div id="graphbox" class="jxgbox" style="width:500px; height:200px;"></div>

<script type="text/javascript">

var strbox="graphbox"

function loadURL(url,strbox) {


    var handleResponse = function (status, response) {

        var json = JSON.parse(response);
        graphdata(json["data"],strbox);
    }

    var handleStateChange = function () {
       switch (request.readyState) {
          case 0 : // UNINITIALIZED
          case 1 : // LOADING
          case 2 : // LOADED
          case 3 : // INTERACTIVE
          break;
          case 4 : // COMPLETED
          handleResponse(request.status, request.responseText);
          break;
          default: alert("error");
       }
    }

    var request = new XMLHttpRequest();

    request.onreadystatechange=handleStateChange;
    request.open('GET',url, true);
    request.send(null);

}


function graphdata(data,strbox) {

    var brd = JXG.JSXGraph.initBoard(strbox,{boundingbox:[-1,5000,25,-400],axis:true});

    var plotData = function(data) {
        var i,x=[],y=[],lab=[]; 

        var minY = data[0][1]*1.0;
        var maxY = data[0][1]*1.0;
        var minX = 0.0;
        var maxX = 0.0;

        var l=data.length-1;

        for (i=0;i<l;i++) {

           y[i] = data[l-i][1]*1.0;
           x[i]=i;
           lab[i] = data[l-i][0];
                
            if (y[i]>maxY) maxY = y[i];
            if (y[i]<minY) minY = y[i];
        }
    maxX=x[l-1];
    minX=x[0];
    minY=-20.0;
    minX=-100;
    
    brd.setBoundingBox([minX,maxY,maxX,minY]);
    var c = brd.create('curve',[x,y],{strokeColor:'blue'});
    brd.update();
    };
    plotData(data);

};


var url0="https://www.quandl.com/api/v1/datasets/CBOE/VIX.json?trim_start=2004-01-02&trim_end=2014-11-21&auth_token=9q1Zxtr15FmJxz1yKCyH";
loadURL(url0,strbox);


</script>
-->

