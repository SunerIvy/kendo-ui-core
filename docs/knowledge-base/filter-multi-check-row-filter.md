---
title: Add Multi-Check Filter to Grid in Row Mode
description: An example on how to enable the multi-check filter in a Kendo UI Grid
type: how-to
page_title: Implement Multi-Checkbox Filter in Row-Filterable Grid | Kendo UI Grid
slug: filter-multi-check-row-filter
tags: checkbox, filter, row, multi, kendo, grid
ticketid: 1123045
res_type: kb
component: grid
---

## Environment

<table>
 <tr>
  <td>Product</td>
  <td>Progress Kendo UI Grid</td>
 </tr>
</table>


## Description

My Grid uses row mode for filtering. I need the `FilterMultiCheck` to appear in the filter row and not in the header.

    filterable: {  
        mode: 'row'  
    },

How can I implement a multi-selection filter in a column Grid which is in a row-filterable mode?

## Suggested Workarounds

The Kendo UI Grid does not provide a built-in solution for achieving this behavior. However, you can still work around the issue.

Move the built-in menu to the filter row and, if not needed, hide the rest of the filter menus from the headers:

1. Set `filterable` to mode `"menu, row"`by using use `column.filterable.multi`.
1. Add an event handler to the `dataBound` event of the Grid.  
1. Look for the `MultiFilterCheck` in the header.
1. Find the desired filter row cell and replace its content with `MultiFilterCheck`.
1. To give it the same look and feel as the neighboring cells, wrap it in a span through `"class='k-button k-button-icon k-dropdown-wrap"`.   
1. Copy the following code:

    ```
    dataBound: function(e){

      var multifilter = e.sender.thead.find("th[data-field='name']>a");
      var ageFilter = e.sender.thead.find("th[data-field='age']>a").hide();

      if(multifilter){
        $("span[data-field='name']").first().replaceWith(multifilter);
        multifilter.wrap("<span class='k-button k-button-icon k-dropdown-wrap'></span>");
      }
    }
    ```

For the complete implementation, refer to [this Dojo example](http://dojo.telerik.com/eVOjE).  
