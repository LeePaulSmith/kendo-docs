---
title:Kendo.Mvc.UI.Fluent.DropDownListBuilderBase
slug:aspnetmvc-kendo.mvc.ui.fluent.dropdownlistbuilderbase
publish:true
---

# Kendo.Mvc.UI.Fluent.DropDownListBuilderBase

## Methods

### Enable(System.Boolean)
Enables or disables the combobox.

### IgnoreCase(System.Boolean)
Use it to enable case insensitive bahavior of the combobox. If true the combobox will select the first matching item ignoring its casing.

#### Example
    <%= Html.Kendo().ComboBox()
        .Name("ComboBox")
        .IgnoreCase(true)
        %>