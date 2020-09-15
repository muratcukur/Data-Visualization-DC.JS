# Data-Visualization-With-DC.JS
Retail sales visualization , analyse data  on web with DC.JS , CSS, HTML

For making data visualization you don't need fancy , expensive tools like Tableau , Power BI or any other software.

You can do even better web based visualization without these tools. : ) . 

BUT YOU SHOULD LEARN SOME CODING and should know how to handle database, HTML, CSS , BOOTSTRAP , MYSQL  .... : (

So let's start how to do beautiful visualization.

First we import our csv file and convert string to integer :

d3.csv("perakende.csv", function (data) {
        data.forEach(function(d) {
        d["yil"] = +d["yil"];
        d["ay"] = +d["ay"];
        d["gun"] = +d["gun"];
        d["magaza_sayisi"] = +d["magaza_sayisi"];
        d["kar"] = +d["kar"];
        d["toplam_musteri_sayisi"] = +d["toplam_musteri_sayisi"];
    });


Then we describe graphs and attach them to html id we described in out html.

                       var totalProfit = dc.numberDisplay("#totalprofit");	
                       var totalStore = dc.numberDisplay("#totalstore");
                       var totalCustomer = dc.numberDisplay("#totalcustomer");	
                       var profitChart = dc.barChart('#profitmontly');
                       var categoryPie = dc.pieChart('#categorypie');
                       var trChart = dc.geoChoroplethChart("#tr-chart"); 
                       var cityCategoryProfitChart= dc.barChart('#citycategoryprofit')


Then our magic functions comes. We use crossfilter multi-dimensional dataset.

After that we define our dimensions. 

var categoryDim=ndx.dimension(function(d) { return d.kategori;})
var categoryGroup=categoryDim.group();

Finally we use these dimensions to make our graph

                  profitChart
                    .width(1000)
                    .height(400)
                    .margins({ top: 5, right: 40, left: 50, bottom: 20 })
                    .yAxisPadding('20%')  
                    .brushOn(false)                      
                    //.renderLabel(true)                 
                    .title(function(d) { return d3.format(',.0f')(d.value)+" ₺"})                    
                    .dimension(monthDim)                    
                    .group(filtered_group)                                                   
                    .x(d3.scale.ordinal()) //x axis
                    .xUnits(dc.units.ordinal)
                    .elasticY(true)
                    .elasticX(true)
                    .renderHorizontalGridLines(true)
                    .barPadding(0.3)                       
                    .outerPadding(0.1)
                    .label(d => d3.format('.3s')(d.y)+" ₺")                                                                                             
                    .renderLabel(true) 
                    .yAxis().tickFormat(d3.format('.3s'));
                    
  
There are many graph on this work. So feel free to contact me if you have any questions.  
