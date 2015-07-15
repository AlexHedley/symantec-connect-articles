---
title: Workflow - Grid View Column Cell Colouring
# tags:
#     - 
author: AlexHedley
# description: 
published: 2015-07-15
---

In this article I will show you how to change the colour of a cell (in a given column) in a ![Grid](images\Grid.png) Grid Component in the ![Forms (Web).png](images\Forms%2520%2528Web%2529.png) Forms (Web) Project Type.
  
This can be handy for a RAG Status or Traffic light system.

*Linked Article*
  
[https://www-secure.symantec.com/connect/articles/workflow-multistatecolor-component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0f43883e-d4dd-4c00-8da0-ccfffeb3a12c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Add a ![Grid](images\Grid.png) Grid to your ![Form Builder.png](images\FormBuilder.png) Web Form.
  
Give the Grid a name
  
<u>Functionality tab</u>  
Control ID: ProdTable
  
This assumes the data set you are returning includes a column that lists the colour you want to show.

| Data | Colour |
| --- | --- |
| John | Red |
| Fred | Amber |
| Lucy | Green |

Make this the LAST column of your Table.
  
You want it to change to
  
![Table Colour.png](images\TableColour.png)
  
Add the following to the **onload** event of the Form.
  
Double click on the Form, go to the **Behavior** Tab.
  
In the 'Body Custom Events' click on **Add** -&gt; **AttributesKeyValuePair**.

| Event | onload |
| --- | --- |
| Event Handler | *#below code#* |

    $(function () {
        $('#ProdTable tr').each(function (index, value) {
            var lastTr = $('td', value).last();
            var colour = lastTr.text();
            if( colour == 'Amber' )
                colour = 'Orange';
                lastTr.text('');
                lastTr.css("background-color", colour);
        });
    });

\*There are certain colours in CSS instead of using the HEX code, Amber is not one of them so we need to change it to Orange.
  
[https://css-tricks.com/snippets/css/named-colors-and-hex-equivalents/](https://css-tricks.com/snippets/css/named-colors-and-hex-equivalents/)
  
There's an interesting [read](http://stackoverflow.com/questions/8318911/why-does-html-think-chucknorris-is-a-color) on why "ChuckNorris" is a colour.

If you wish to have it update a different column you will need to change the following line

    var lastTr = $('td', value).last();

and get the column you need instead.

This works fine for the first page of a Grid but the Paging is performed using AJAX so if you change to Page 2 the colours aren't updated.
  
To combat this

    $(function() {
        var previous = $("#ProdTable").text();
        $check = function() {
            if ($("#ProdTable").text() != previous) { 
              updateColor();
            }
            previous = $("#ProdTable").text();        
        }
        updateColor();
        setInterval(function() { $check(); }, 1000);
    });
    
    function updateColor() {
        $('#ProdTable tr').each(function (index, value) {
          var colour =  $(':nth-child(11)', $(this)).text();      
          var lastTr = $('td', value).last();   
        
          if( colour == 'Amber' )
              colour = 'Orange';
       
          lastTr.text('');
          lastTr.css("background-color", colour);
        });
    }

This uses a Timer to keep checking the Grid so it's the best performance wise solution but it works.

In Workflow 7.5 you could just map a value into a Column of

    <span style="background-color:blue"></span>

You could map across the colour from the DataType using the Merge component.

This is now encoded in the Grid in 7.6, the "&lt;" is converted to "&lt;" etc so therefore doesn't work anymore.

* * *

[![Protirus](images\Protirus.png)](http://www.protirus.com/)
