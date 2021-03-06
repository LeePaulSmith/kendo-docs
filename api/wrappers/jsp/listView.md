---
title: listView
slug: jsp-listView
tags: api, java
publish: true
---

# \<kendo:listView\>
A JSP tag representing Kendo ListView.


## Configuration Attributes


### autoBind `boolean`

Indicates whether the list view will call read on the DataSource initially.

#### Example
    <kendo:listView autoBind="autoBind">
    </kendo:listView>



### navigatable `boolean`

Indicates whether keyboard navigation is enabled/disabled.

#### Example
    <kendo:listView navigatable="navigatable">
    </kendo:listView>



### selectable `String`

Indicates whether selection is enabled/disabled. Possible values:

#### Example
    <kendo:listView selectable="selectable">
    </kendo:listView>



### template `String`

The id of the template used for rendering the items in the listview.

#### Example
    <kendo:listView template="template">
    </kendo:listView>



### pageable `boolean`

Indicates whether paging is enabled/disabled.

#### Example
    <kendo:listView pageable="pageable">
    </kendo:listView>



### editTemplate `String`

Specifies ListView item template in edit mode.

#### Example
    <kendo:listView editTemplate="editTemplate">
    </kendo:listView>



### altTemplate `String`

Template to be used for rendering the alternate items in the listview.

#### Example
    <kendo:listView altTemplate="altTemplate">
    </kendo:listView>



### tagName `String`

Specifies ListView wrapper element tag name.

#### Example
    <kendo:listView tagName="tagName">
    </kendo:listView>



### change `String`

Fires when the list view selection has changed.

#### Example
    <kendo:listView change="handle_change">
    </kendo:listView>
    <script>
        function handle_change(e) {
            // Code to handle the change event.
        }
    </script>



### dataBound `String`

Fires when the list view has received data from the data source.
and is about to render it.

#### Example
    <kendo:listView dataBound="handle_dataBound">
    </kendo:listView>
    <script>
        function handle_dataBound(e) {
            // Code to handle the dataBound event.
        }
    </script>



### edit `String`

Fires when the list view enters edit mode.

#### Example
    <kendo:listView edit="handle_edit">
    </kendo:listView>
    <script>
        function handle_edit(e) {
            // Code to handle the edit event.
        }
    </script>



### remove `String`

Fires before the list view item is removed.

#### Example
    <kendo:listView remove="handle_remove">
    </kendo:listView>
    <script>
        function handle_remove(e) {
            // Code to handle the remove event.
        }
    </script>



### Event Attributes


### change `String`

Fires when the list view selection has changed.

#### Example
    <kendo:listView change="handle_change">
    </kendo:listView>
    <script>
        function handle_change(e) {
            // Code to handle the change event.
        }
    </script>



### dataBound `String`

Fires when the list view has received data from the data source.
and is about to render it.

#### Example
    <kendo:listView dataBound="handle_dataBound">
    </kendo:listView>
    <script>
        function handle_dataBound(e) {
            // Code to handle the dataBound event.
        }
    </script>



### edit `String`

Fires when the list view enters edit mode.

#### Example
    <kendo:listView edit="handle_edit">
    </kendo:listView>
    <script>
        function handle_edit(e) {
            // Code to handle the edit event.
        }
    </script>



### remove `String`

Fires before the list view item is removed.

#### Example
    <kendo:listView remove="handle_remove">
    </kendo:listView>
    <script>
        function handle_remove(e) {
            // Code to handle the remove event.
        }
    </script>


## Event Tags


### kendo:listView-change

Fires when the list view selection has changed.

#### Example
    <kendo:listView>
        <kendo:listView-change>
            <script>
                function(e) {
                    // Code to handle the change event.
                }
            </script>
        </kendo:listView-change>
    </kendo:listView>

 

### kendo:listView-dataBound

Fires when the list view has received data from the data source.
and is about to render it.

#### Example
    <kendo:listView>
        <kendo:listView-dataBound>
            <script>
                function(e) {
                    // Code to handle the dataBound event.
                }
            </script>
        </kendo:listView-dataBound>
    </kendo:listView>

 

### kendo:listView-edit

Fires when the list view enters edit mode.

#### Example
    <kendo:listView>
        <kendo:listView-edit>
            <script>
                function(e) {
                    // Code to handle the edit event.
                }
            </script>
        </kendo:listView-edit>
    </kendo:listView>

 

### kendo:listView-remove

Fires before the list view item is removed.

#### Example
    <kendo:listView>
        <kendo:listView-remove>
            <script>
                function(e) {
                    // Code to handle the remove event.
                }
            </script>
        </kendo:listView-remove>
    </kendo:listView>

 

## Child JSP Tags
    
