---
title: kendo.ui.ComboBox
meta_title: ComboBox UI widget configuration, methods and events documentation
meta_description: Learn to configure Kendo UI ComboBox widget, use the documentation guide to operate different types of methods and get familiar with all events, used in ComboBox UI widget.
slug: web-kendo.ui.combobox
tags: api,web
publish: true
---

# kendo.ui.ComboBox

## Configuration

### animation `Object`

 Animations to be used for opening/closing the popup. Setting to false will turn off the animation.

#### Example

    $("#comboBox").kendoComboBox({
        animation: false
    });

### animation.close `Object`

 Animation to be used for closing of the popup.

#### Example

    //combobox initialization
     <script>
         $("#combobox").kendoComboBox({
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

    //combobox initialization

    <script>
         $("#combobox").kendoComboBox({
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

### autoBind `Boolean`*(default: true)*

 Controls whether to bind the widget to the DataSource on initialization.

#### Example

    $("#comboBox").kendoComboBox({
        autoBind: false
    });

### cascadeFrom `String`

Use it to set the Id of the parent DropDownList.

#### Example
    $("#dropdownlist1").kendoDropDownList();

    $("#dropdownlist2").kendoDropDownList({
        cascadeFrom: "dropdownlist1"
    });

### dataSource `Object | kendo.data.DataSource`

A local JavaScript object or instance of DataSource or the data that the ComboBox will be bound to.

#### Example

    var items = [{ text: "Item 1", value: "1" }, { text: "Item 2", value: "2" }];
    $("#comboBox").kendoComboBox({
        dataTextField: "text",
        dataValueField: "value",
        dataSource: items
    });

#### Example

    $("#comboBox").kendoComboBox({
        dataSource: new kendo.data.DataSource({
            transport: {
                read: {
                    url: "Get/Items" // url to remote data source (simple list of strings)
                }
            }
        });
    });

### dataTextField `String`*(default: "")*

 Sets the field of the data item that provides the text content of the list items.

#### Example

    $("#comboBox").kendoComboBox({
        dataTextField: "Name",
        dataValueField: "ID"
    });

### dataValueField `String`*(default: "")*

 Sets the field of the data item that provides the value content of the list items.

#### Example

    $("#comboBox").kendoComboBox({
        dataTextField: "Name",
        dataValueField: "ID"
    });

### delay `Number`*(default: 200)*

 Specifies the delay in ms after which the ComboBox will start filtering dataSource.

#### Example

    $("#comboBox").kendoComboBox({
        delay: 500
    });

### enable `Boolean`*(default: true)*

 Controls whether the ComboBox should be initially enabled.

#### Example

    $("#comboBox").kendoComboBox({
        enable: false
    });

#### Example

    // get a reference to the ComboBox widget
    var comboBox = $("#comboBox").data("kendoComboBox");
    comboBox.enable(false);

### filter `String`*(default: "none")*

 Defines the type of filtration. If "none" the ComboBox will not filter the items.

#### Example

    $("#comboBox").kendoComboBox({
        filter: "startswith"
    });

### height `Number`*(default: 200)*

 Define the height of the drop-down list in pixels.

#### Example

    $("#comboBox").kendoComboBox({
        height: 500
    });

### highlightFirst `Boolean`*(default: true)*

 Controls whether the first item will be automatically highlighted.

#### Example

    $("#comboBox").kendoComboBox({
        highLightFirst: true
    });

### ignoreCase `String`*(default: true)*

 Defines whether the filtration should be case sensitive.

#### Example

    $("#combobox").kendoComboBox({
        filter: 'contains',
        ignoreCase: false //now filtration will be case sensitive
    });

### index `Number`*(default: -1)*

 Defines the initial selected item.

#### Example

    var items = [{ text: "Item 1", value: "1" }, { text: "Item 2", value: "2" }];
    $("#comboBox").kendoComboBox({
        dataSource: items,
        index: 1 // 0 based from the start of the collection of objects. this selects "Item 2".
    });

### minLength `Number`*(default: 1)*

 Specifies the minimum characters that should be typed before the ComboBox activates

#### Example

    $("#comboBox").kendoComboBox({
        minLength: 3
    });

### placeholder `String`*(default: "")*

 A string that appears in the textbox when the combobox has no value.


#### Example

    //combobox initialization
     <script>
         $("#combobox").kendoComboBox({
             dataSource: dataSource,
             placeholder: "Select..."
         });
     </script>

#### Example

    <input id="combobox" placeholder="Select..." />

     //combobox initialization
     <script>
         $("#combobox").kendoComboBox({
             dataSource: dataSource
         });
     </script>

### suggest `Boolean`*(default: false)*

 Controls whether the ComboBox should automatically auto-type the rest of text.

#### Example

    $("#comboBox").kendoComboBox({
        suggest: false
    });

### template `string`

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

     //combobox initialization
     <script>
         $("#combobox").kendoComboBox({
             dataSource: dataSource,
             dataTextField: "Name",
             dataValueField: "Id",
             template: kendo.template($("#template").html())
         });
     </script>

### text `String`*(default: "")*

 Define the text of the widget, when the autoBind is set to false.

#### Example

    $("#combobox").kendoComboBox({
         autoBind: false,
         text: "Chai"
    });

### value `String`*(default: "")*

 Define the value of the widget

#### Example

    $("#combobox").kendoComboBox({
         dataSource: ["Item1", "Item2"],
         value: "Item1"
    });

## Methods

### close

Closes the drop-down list.

#### Example

    // get a reference to instance of the Kendo UI ComboBox
    var combobox = $("#comboBox").data("kendoComboBox");
    combobox.close();

### dataItem

Returns the raw data record at the specified index. If the index is not specified, the selected index will be used.

#### Example

    var combobox = $("#combobox").data("kendoComboBox");

    // get the dataItem corresponding to the selectedIndex.
    var dataItem = combobox.dataItem();

    // get the dataItem corresponding to the passed index.
    var dataItem = combobox.dataItem(1);

#### Parameters

##### index `Number`

The zero-based index of the data record

#### Returns

`Object` The raw data record. Returns <i>undefined</i> if no data.

### destroy
Prepares the **ComboBox** for safe removal from DOM. Detaches all event handlers and removes jQuery.data attributes to avoid memory leaks. Calls destroy method of any child Kendo widgets.

> **Important:** This method does not remove the ComboBox element from DOM.

#### Example

    var combobox = $("#combobox").data("kendoComboBox");
    
    // detach events
    combobox.destroy();

### enable

Enables/disables the combobox widget

#### Example

    // get a reference to instance of the Kendo UI ComboBox
    var combobox = $("#comboBox").data("kendoComboBox");
    // disables the combobox
    combobox.enable(false);

#### Parameters

##### enable `Boolean`

Desired state

### open

Opens the drop-down list.

#### Example

    // get a reference to instance of the Kendo UI ComboBox
    var combobox = $("#comboBox").data("kendoComboBox");
    combobox.open();

### refresh

Re-render the items of the drop-down list.

#### Example

    // get a referenence to the Kendo UI ComboBox
    var combobox = $("#combobox").data("kendoComboBox");
    // re-render the items of the drop-down list.
    combobox.refresh();

### search

Filters dataSource using the provided parameter and rebinds drop-down list.

#### Example

    var combobox = $("#combobox").data("kendoComboBox");

    // Searches for item which has "In" in the name.
    combobox.search("In");

#### Parameters

##### word `string`

The filter value.

### select

Selects drop-down list item and sets the value and the text of the combobox.

#### Example

    var combobox = $("#combobox").data("kendoComboBox");

    // selects by jQuery object
    combobox.select(combobox.ul.children().eq(0));

    // selects by index
    combobox.select(1);

    // selects item if its text is equal to "test" using predicate function
    combobox.select(function(dataItem) {
        return dataItem.text === "test";
    });

#### Parameters

##### li `jQuery | Number | Function`

LI element or index of the item or predicate function, which defines the item that should be selected.

#### Returns

`Number` The index of the selected LI element.

### suggest

Forces a suggestion onto the text of the ComboBox.

#### Example

    // note that this suggest is not the same as the configuration method
    // suggest which enables/disables auto suggesting for the ComboBox
    //
    // get a referenence to the Kendo UI ComboBox
    var combobox = $("#combobox").data("kendoComboBox");
    // force a suggestion to the item with the name "Inception"
    combobox.suggest("Inception");

#### Parameters

##### value `string`

Characters to force a suggestion.

### text

Gets/Sets the text of the ComboBox.

#### Example

    var combobox = $("#combobox").data("kendoComboBox");

    // get the text of the combobox.
    var text = combobox.text();

#### Parameters

##### text `String`

The text to set.

#### Returns

`String` The text of the combobox.

### toggle

Toggles the drop-down list between opened and closed state.

#### Example

    var combobox = $("#combobox").data("kendoComboBox");

    // toggles the open state of the drop-down list.
    combobox.toggle();

#### Parameters

##### toggle `Boolean`

Defines the whether to open/close the drop-down list.

### value

Gets/Sets the value of the combobox. If the value is undefined, text of the data item will be used.

#### Example

    var combobox = $("#combobox").data("kendoComboBox");

    // get the value of the combobox.
    var value = combobox.value();

    // set the value of the combobox.
    combobox.value("1"); //looks for item which has value "1"

#### Parameters

##### value `String`

The value to set.

#### Returns

`String` The value of the combobox.

## Events

### change

Fires when the value has been changed.

#### Example

    $("#comboBox").kendoComboBox({
        change: function(e) {
            // handle event
        }
    });

#### To set after initialization

    // get a reference to instance of the Kendo UI ComboBox
    var combobox = $("#comboBox").data("kendoComboBox");
    // bind to the change event
    combobox.bind("change", function(e) {
        // handle event
    });

### close

Fires when the drop-down list is closed

#### Example

    $("#comboBox").kendoComboBox({
        close: function(e) {
            // handle event
        }
    });

#### To set after initialization

    // get a reference to instance of the Kendo UI ComboBox
    var combobox = $("#comboBox").data("kendoComboBox");
    // bind to the close event
    combobox.bind("close", function(e) {
        // handle event
    });

### dataBound

Fires when the ComboBox has received data from the data source.

#### Example

    $("#comboBox").kendoComboBox({
        dataBound: function(e) {
            // handle event
        }
    });

#### To set after initialization

    // get a reference to instance of the Kendo UI ComboBox
    var combobox = $("#comboBox").data("kendoComboBox");
    // bind to the close event
    combobox.bind("dataBound", function(e) {
        // handle event
    });

### open

Fires when the drop-down list is opened

#### Example

    $("#comboBox").kendoComboBox({
        open: function(e) {
                // handle event
            }
    });

#### To set after initialization

    // get a reference to instance of the Kendo UI ComboBox
    var combobox = $("#comboBox").data("kendoComboBox");
    // bind to the open event
    combobox.bind("open", function(e) {
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
    var combobox = $("#combobox").kendoComboBox({
        select: onSelect
    });

    // detach select event handler via unbind()
    combobox.data("kendoComboBox").unbind("select", onSelect);

#### Attach select event handler via bind(); detach via unbind()

    // event handler for select
    var onSelect = function(e) {
        // access the selected item via e.item (jQuery object)
    };

    // attach select event handler via bind()
    $("#combobox").data("kendoComboBox").bind("select", onSelect);

    // detach select event handler via unbind()
    $("#combobox").data("kendoComboBox").unbind("select", onSelect);

#### Event Data

##### e.item `jQuery`

The selected item chosen by a user.
