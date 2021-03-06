---
title: Make Page Number Responsive for SASS Themes
description: An example on how to make the page numbers responsive in SASS themes.
type: how-to
page_title: Responsive Pager for SASS Themes | Kendo UI Pager
slug: pager-responsive-numbers-sass-themes
tags: kendo, pager, responsive, dropdown, numbers, bootstrap, default
res_type: kb
component: grid
---

## Environment

<table>
 <tr>
  <td>Product</td>
  <td>Progress Kendo UI Pager</td>
 </tr>
</table>

## Description

I would like to make the Kendo Pager show dropdown with the pages when the Grid is shown in smaller screens. This does not happen for the 

## Solution

The pager in the SASS themes does not change to dropdown automatically like in the LESS themes. To change the behavior we suggest using one of the following workarounds. Note that you may need to adjust the CSS in order to fit in your specific scenario:

If you are using **Default-v2** theme: 

```
<style>
    @media only screen and (max-width: 1024px) {
    .k-pager-numbers {
        border: 1px solid rgba(0,0,0,.08);
        position: absolute;
        left: 4.8em;
        flex-direction: column-reverse;
        overflow: visible;
        height: auto;
    }

    .k-pager-numbers:first-child {
        left: .2em;
    }

    .k-pager-numbers.k-state-expanded {
        transform: translatey(-60%);
    }


    .k-pager-numbers .k-current-page {
        display: block;
        border-left: 0;
    }

    .k-pager-numbers.k-state-expanded .k-current-page {
        transform: translatey(100%);
        -webkit-transform: translatey(100%);
    }

    .k-pager-numbers li:not(.k-current-page) {
        display: none;
    }

    .k-pager-numbers + .k-link {
        margin-left: 4.8em;
    }

    .k-pager-numbers .k-state-selected,
    .k-pager-numbers .k-link {
        display: block;
        margin-right: 0;
        padding: 3px 20px;
        text-align: left;
    }

    .k-pager-numbers.k-state-expanded .k-current-page {
        margin: -2em 0 0;
        padding: 0;
        border: 1px solid rgba(0,0,0,.08);
        border-top-width: 0;
    }

    .k-pager-numbers.k-state-expanded li {
        display: inline-block;
    }
    .k-pager-wrap .k-pager-numbers .k-current-page {
        display: block;
    }
    
    .k-pager-numbers.k-reset.k-state-expanded {
        border-width: 0;
        flex-direction: column-reverse;
        background-color: #f9f9f9;
    }
}
</style>
```

To see this code in action check out [this runnable example](https://dojo.telerik.com/ewoFoxaB/2).


If you are using **Bootstrap-v4** theme: 

```
<style>
    @media only screen and (max-width: 1024px) {
    .k-pager-numbers {

        position: absolute;
        left: 5.85em;
        flex-direction: column-reverse;
        overflow: visible;
        height: auto;
    }

    .k-pager-numbers:first-child {
        left: .2em;

    }

    .k-pager-numbers.k-state-expanded {
        transform: translatey(-60%);
    }


    .k-pager-numbers .k-current-page {
        display: block;
        border-left: 0;
    }

    .k-pager-numbers.k-state-expanded .k-current-page {
        transform: translatey(100%);
        -webkit-transform: translatey(100%);
    }

    .k-pager-numbers li:not(.k-current-page) {
        display: none;
    }

    .k-pager-numbers + .k-link {
        margin-left: 4.8em;
    }

    .k-pager-numbers .k-state-selected,
    .k-pager-numbers .k-link {
        display: block;
        margin-right: 0;
        padding: 3px 20px;
        text-align: left;

        width: calc(2em );
        height: calc(2.1em + 2px);
        line-height: calc(2em + 2px);
    }

    .k-state-expanded li:not(.k-current-page) .k-link {
        border: none;  
    }
    
    .k-pager-numbers.k-state-expanded .k-current-page {
        margin: -2em 0 0;
        padding: 0;
        border-top-width: 0;
        width: calc(2em );
        height: calc(2.1em + 3px);
        line-height: calc(2em + 2px);
    }

    .k-pager-numbers.k-state-expanded li {
        display: inline-block;
    }
    .k-pager-wrap .k-pager-numbers .k-current-page {
        display: block;
    }

    .k-pager-numbers.k-reset.k-state-expanded {
        border-width: 0;
        flex-direction: column-reverse;
        background-color: #f9f9f9;
    }
    }
</style>
```

To see this code in action check out [this runnable example](https://dojo.telerik.com/UkovECEy/3).

