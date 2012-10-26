---
title: kendo.ui.AutoComplete
meta_title: Configuration, methods and events of Kendo UI AutoComplete widget
meta_description: How to configure and control methods in Autocomplete UI widget, which events to use to open, close, change, select.
slug: web-kendo.ui.autocomplete
tags: api,web
publish: true
---

# kendo.ui.AutoComplete

## Configuration

### animation `Object`

 Animations to be used for opening/closing the popup. Setting to false will turn of the animation.

### animation.close `Object`

 Animation to be used for closing of the popup.

#### Example

    //autocomplete initialization
     <script>
         $("#autocomplete").kendoAutoComplete({
             dataSource: dataSource,
             animation: {
                close: {
                    effects: "fadeOut",
                    duration: 300,
                    hide: true
                    show: false
                }
             }
         });
     </script>

### animation.open `Object`

 Animation to be used for opening of the popup.

#### Example

    //autocomplete initialization
     <script>
         $("#autocomplete").kendoAutoComplete({
             dataSource: dataSource,
             animation: {
                open: {
                    effects: "fadeIn",
                    duration: 300,
                    show: true
                }
             }
         });
     </script>

### dataSource `Object | kendo.data.DataSource`

The set of data that the AutoComplete will be bound to.
 Either a local JavaScript object, or an instance of the Kendo UI DataSource.

#### Example

    var items = [ { Name: "Item 1" }, { Name: "Item 2"} ];
    $("#autoComplete").kendoAutoComplete({ dataSource: items });

#### Example

    $("#autocomplete").kendoAutoComplete({
        dataSource: new kendo.data.DataSource({
            transport: {
                read: "Items/GetData" // url to server method which returns data
            }
        });
    });

### dataTextField `String`*(default: null)*

 Sets the field of the data item that provides the text content of the list items.

#### Example

    var items = [ { ID: 1, Name: "Item 1" }, { ID: 2, Name: "Item 2"} ];
    $("#autoComplete").kendoAutoComplete({
        dataSource: items,
        dataTextField: "Name"
    });

### delay `Number`*(default: 200)*

 Specifies the delay in ms after which the AutoComplete will start filtering the dataSource.

#### Example

    // set the delay to 500 milliseconds
    $("#autoComplete").kendoAutoComplete({
        delay: 500
    });

### enable `Boolean`*(default: true)*

 Controls whether the AutoComplete should be initially enabled.

#### Example

    // disable the autocomplete when it is created (enabled by default)
    $("#autoComplete").kendoAutoComplete({
        enable: false
    });

### filter `String`*(default: "startswith")*

 Defines the type of filtration. This value is handled by the remote data source.

#### Example

    // send a filter value of 'contains' to the server
    $("#autoComplete").kendoAutoComplete({
        filter: 'contains'
    });

### height `Number`*(default: 200)*

 Sets the height of the drop-down list in pixels.

#### Example

    // set the height of the drop-down list that appears when the autocomplete is activated to 500px
    $("#autoComplete").kendoAutoComplete({
        height: 500
    });

### highlightFirst `Boolean`*(default: true)*

 Controls whether the first item will be automatically highlighted.

#### Example

    $("#autocomplete").kendoAutoComplete({
        highlightFirst: false //no of the suggested items will be highlighted
    });

### ignoreCase `Boolean`*(default: true)*

 Defines whether the filtration should be case sensitive.

#### Example

    $("#autoComplete").kendoAutoComplete({
        filter: 'contains',
        ignoreCase: false //now filtration will be case sensitive
    });

### minLength `Number`*(default: 1)*

 Specifies the minimum number of characters that should be typed before the AutoComplete queries
the dataSource.

#### Example

    // wait until the user types 3 characters before querying the server
    $("#autoComplete").kendoAutoComplete({
        minLength: 3
    });

### placeholder `String`*(default: "")*

 A string that appears in the textbox when it has no value.


#### Example

    //autocomplete initialization
     <script>
         $("#autocomplete").kendoAutoComplete({
             dataSource: dataSource,
             placeholder: "Enter value..."
         });
     </script>

#### Example

    <input id="autocomplete" placeholder="Enter value..." />

     //combobox initialization
     <script>
         $("#autocomplete").kendoAutoComplete({
             dataSource: dataSource
         });
     </script>

### separator `String`*(default: "")*

 Sets the separator for completion. Empty by default, allowing for only one completion.

#### Example

    // set completion separator to ,
    $("#autoComplete").kendoAutoComplete({
        separator: ", "
    });

### suggest `Boolean`*(default: false)*

 Controls whether the AutoComplete should automatically auto-type the rest of text.

#### Example

    // turn on auto-typing (off by default)
    $("#autoComplete").kendoAutoComplete({
        suggest: true
    });

### template `String`

Template to be used for rendering the items in the list.

#### Example

    //template

    <script id="template" type="text/x-kendo-tmpl">
          # if (data.BoxArt.SmallUrl) { #
              <img src="${ data.BoxArt.SmallUrl }" alt="${ data.Name }" />Title:${ data.Name }, Year: ${ data.Name }
          # } else { #
              <img alt="${ data.Name }" />Title:${ data.Name }, Year: ${ data.Name }
          # } #
     </script>

     //autocomplete initialization
     <script>
         $("#autocomplete").kendoAutoComplete({
             dataSource: dataSource,
             dataTextField: "Name",
             template: kendo.template($("#template").html())
         });
     </script>

## Methods

### close

Closes the drop-down list.

#### Example

    // get a reference to the autocomplete widget
    var autocomplete = $("autocomplete").data("kendoAutoComplete");

    autocomplete.close();

### dataItem

Returns the raw data record at the specified index

#### Example

    var autocomplete = $("#autocomplete").data("kendoAutoComplete");

    // get the dataItem corresponding to the passed index.
    var dataItem = autocomplete.dataItem(1);

#### Parameters

##### index `Number`

The zero-based index of the data record

#### Returns

`Object` The raw data record. Returns <i>undefined</i> if no data.

### destroy
Prepares the **AutoComplete** for safe removal from DOM. Detaches all event handlers and removes jQuery.data attributes to avoid memory leaks. Calls destroy method of any child Kendo widgets.

> **Important:** This method does not remove the AutoComplete element from DOM.

#### Example

    var autocomplete = $("#autocomplete").data("kendoAutoComplete");
    
    // detach events
    autocomplete.destroy();

### enable

Enable/Disable the autocomplete widget.

#### Example

    // get a reference to the autocomplete widget
    var autocomplete = $("autocomplete").data("kendoAutoComplete");

    // disables the autocomplete
    autocomplete.enable(false);

    // enables the autocomplete
    autocomplete.enable(true);

#### Parameters

##### enable `Boolean`

The argument, which defines whether to enable/disable the autocomplete.

### refresh

Re-render the items in drop-down list.

#### Example

    // get a referenence to the Kendo UI AutoComplete
    var autocomplete = $("autocomplete").data("kendoAutoComplete");
    // re-render the items in drop-down list.
    autocomplete.refresh();

### search

Filters dataSource using the provided parameter and rebinds drop-down list.

#### Example

    // get a reference to the autocomplete widget
    var autocomplete = $("autocomplete").data("kendoAutoComplete");

    // Searches for item which has "Inception" in the name.
    autocomplete.search("Inception");

#### Parameters

##### word `string`

The filter value.

### select

Selects drop-down list item and sets the text of the autocomplete.

#### Example

    // get a reference to the autocomplete widget
    var autocomplete = $("autocomplete").data("kendoAutoComplete");

    // selects by jQuery object
    autocomplete.select(autocomplete.ul.children().eq(0));

#### Parameters

##### li `jQuery Object`

The LI element.

### suggest

Forces a suggestion onto the text of the AutoComplete.

#### Example

    // note that this suggest is not the same as the configuration method
    // suggest which enables/disables auto suggesting for the AutoComplete
    //
    // get a referenence to the Kendo UI AutoComplete
    var autoComplete = $("#autoComplete").data("kendoAutoComplete");

    // force a suggestion to the item with the name "Inception"
    autoComplete.suggest("Inception");

#### Parameters

##### value `string`

Characters to force a suggestion.

### value

Gets/Sets the value of the autocomplete.

#### Example

    // get a reference to the autocomplete widget
    var autocomplete = $("autocomplete").data("kendoAutoComplete");

    // get the text of the autocomplete.
    var value = autocomplete.value();

#### Parameters

##### value `String`

The value to set.

#### Returns

`String` The value of the autocomplete.

## Events

### change

Fires when the value has been changed.

#### To set after initialization

    var autoComplete = $("#autoComplete").data("kendoAutoComplete");
    $("#autoComplete").data("kendoAutoComplete").bind("change", function(e) {
        // handle event
    });

### close

Fires when the drop-down list is closed

#### Example

    $("#autoComplete").kendoAutoComplete({
        close: function(e) {
            // handle event
        }
    });

#### To set after initialization

    var autoComplete = $("#autoComplete").data("kendoAutoComplete");
    autoComplete.bind("close", function(e) {
        // handle event
    });

### dataBound

Fires when the AutoComplete has received data from the data source.

#### Example

    $("#autoComplete").kendoAutoComplete({
        dataBound: function(e) {
            // handle event
        }
    });

#### To set after initialization

    var autoComplete = $("#autoComplete").data("kendoAutoComplete");
    autoComplete.bind("dataBound", function(e) {
        // handle event
    });

### open

Fires when the drop-down list is opened

#### Example

    $("#autoComplete").kendoAutoComplete({
        open: function(e) {
            // handle event
        }
    });

#### Example

    var autoComplete = $("#autoComplete").data("kendoAutoComplete");
    autoComplete.bind("open", function(e) {
        // handle event
    });

### select

Triggered when a Li element is selected.

#### Attach select event handler during initialization; detach via unbind()

    // event handler for select
    var onSelect = function(e) {
        // access the selected item via e.item (jQuery object)
    };

    // attach select event handler during initialization
    var autocomplete = $("#autocomplete").kendoAutoComplete({
        select: onSelect
    });

    // detach select event handler via unbind()
    autocomplete.data("kendoAutoComplete").unbind("select", onSelect);

#### Attach select event handler via bind(); detach via unbind()

    // event handler for select
    var onSelect = function(e) {
        // access the selected item via e.item (jQuery object)
    };

    // attach select event handler via bind()
    $("#autocomplete").data("kendoAutoComplete").bind("select", onSelect);

    // detach select event handler via unbind()
    $("#autocomplete").data("kendoAutoComplete").unbind("select", onSelect);

#### Event Data

##### e.item `jQuery`

The selected item chosen by a user.
