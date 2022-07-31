# html-tables-styling
How to apply rounded corners and dropshadow to a table element

Styling tables is always a pain for the frontend developer, since table elements do have limited customization options or techniques you can apply using CSS. However, designers will often propose layout and designs and you need to deal with them to please the client.

First thing to make this clear, it is not possible to apply round edges to table elements, TR or TD or any of them, BUT, if you are able and do have the flexibility in the code to introduce a helper element, you can use this element to apply the custom styling.

So this would go as below:

* Add a emtpy first column where we will place our helper
* Empty column should exist in thead, tbody and tfooter if you are using them

```html

<table>
  <thead>
    <tr>
      <th class="first"></th>  <!-- empty first column-->
      ...
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="first">
        <div class="table-helper"></div>
      <td> <!-- empty first column -->
      ...
    </tr>
  </tbody>
</table>

```

Style the first column with CSS with a 0 width and 0 height and then you can use the added div element in the first column and use it as a background for the entire row, apply a background color and the desired rounded edges and including a dropshadow if you wish. TR will have to hold this helper element, then if we use this as the container we can use position: absolute; to manipulate the helper div element.

```css
.table .first {
  width: 0;
  padding: 0;
}

table tr {
  position: relative;
  z-index: 1;
}

table td {  
  vertical-align: middle;
  height: 75px;
}

.table .table-helper {
  width: 100%;
  height: 85%;
  position: absolute;
  background-color: #fff;
  z-index: -1;
  border-radius: 10px;
  top: 10px;
  box-shadow: 0px 5px 7px -3px rgba(0,0,0,0.37);
  -webkit-box-shadow: 0px 5px 7px -3px rgba(0,0,0,0.37);
  -moz-box-shadow: 0px 5px 7px -3px rgba(0,0,0,0.37);
}

```
Note the table-helper class styling the div we left in the first column. With this simple technique you can end in getting a beatiful styled table like this one.
