---
title: Grid
slug: grid
publish: true
---

# Server-Side API
 
## DataKeys 

**DataKeys** are moved to the DataSource Model configuration:

### Old

    Html.Telerik().Grid<Order>()
        .Name("Grid")       
        .DataKeys(dataKeys => dataKeys.Add(o => o.OrderID))

### New

    Html.Kendo().Grid<Order>()
        .Name("Grid")
        .DataSource(dataSource => dataSource
            .Ajax()
            .Model(model => model.Id(o => o.OrderID))
        )
 
## DataBinding

**DataBinding** configuration is moved to DataSource:
 
### Old
    
    Html.Telerik().Grid<Order>()
        .Name("Grid")      
        .DataBinding(dataBinding => dataBinding.Ajax().Select("_AjaxBinding", "Grid"))
    
### New    

    Html.Kendo().Grid<Order>()   
        .Name("Grid")  
        .DataSource(dataSource => dataSource
            .Ajax()
            .Read(read => read.Action("AjaxBinding ", "Grid"))
        )
 
**DataBinding** “URL” methods are renamed to match the KendoUI DataSource client configuration:

### Old -> New
                
##### Select 

Read

##### Update

Update

##### Delete

Destroy

##### Insert

Create
 
**OperationMode** is change to **ServerOperation**:

### Old

    Html.Telerik().Grid<Order>()
        .Name("Grid")      
        .DataBinding(dataBinding => dataBinding.Ajax().OperationMode(GridOperationMode.Client))

### New

    Html.Kendo().Grid<Order>()
        .Name("Grid")
        .DataSource(dataSource => dataSource
            .Ajax()
            .ServerOperation(false)
        )

**DataBinding.WebService** is removed.
 
## DetailView

**DetailView.ClientTemplate** changed to **ClientDetailTemplateId**:

### Old

    Html.Telerik().Grid<Order>()
        .Name("Grid")
        .DetailView(details => details.ClientTemplate(
            Html.Telerik().TabStrip()
            .Name("TabStrip_<#= EmployeeID #>")                                                                                                           
            .ToHtmlString()
        ))

### New

    Html.Kendo().Grid<Order>()
        .Name("Grid")
        .ClientDetailTemplateId("employeesTemplate")

    <script id="employeesTemplate" type="text/kendo-tmpl">
        @(Html.Kendo().TabStrip()
            .Name("TabStrip_#=EmployeeID#")           
            .ToClientTemplate())
    </script>
 
**DetailView.Template** changed to **DetailTemplate**:
 
### Old
      
    Html.Telerik().Grid(Model)
        .Name("Employees")  
        .DetailView(detailView => detailView.Template(e =>
        {           
                Html.Telerik().TabStrip()
                    .Name("TabStrip_" + e.EmployeeID)
                    .Render();
        }))

### New

    Html.Kendo().Grid(Model)
        .Name("Employees")   
        .DetailTemplate(e =>
        {            
            Html.Kendo().TabStrip()
            .Name("TabStrip_" + e.EmployeeID) 
            .Render();
        })
       
## Editable 

**InForms** mode is removed.

**InsertRowPosition** is renamed to **CreateAt**.

**BeginEdit** and **HtmlFormAttributes** options are not available.

**DefaultDataItem** is moved to DataSource Model configuration:
 
### Old

    Html.Telerik().Grid<Order>()
        .Name("Grid")                           
        .Editable(editable => editable.DefaultDataItem(new Order {
            OrderDate = DateTime.Today
        }))

### New

    Html.Kendo().Grid<Order>()    
        .Name("Grid")     
        .DataSource(dataSource => dataSource
            .Ajax()
            .Model(model => model.Field(o => o.OrderDate).DefaultValue(DateTime.Today)) 
        )

## Groupable 

Groups configuration is moved to DataSource:
 
### Old

    Html.Telerik().Grid<Order>()
        .Name("Grid")                        
        .Groupable(groupable => groupable
            .Groups(groups => groups.Add(o => o.OrderDate))
        )    

### New

    Html.Kendo().Grid<Order>()   
        .Name("Grid")    
        .DataSource(dataSource => dataSource
            .Ajax()                       
            .Group(group => group.Add(o => o.OrderDate))
        )     

**Visible** option is removed. Same functionality can be achieved by setting **Groupable.Enabled** to false and Group descriptors through the DataSource.
 
## Sortable

**OrderBy** is moved to the DataSource configuration:
 
### Old

    Html.Telerik().Grid<Order>()
        .Name("Grid")   
        .Sortable(sortable => sortable.OrderBy(order => order.Add(o => o.OrderDate).Ascending()))

### New

    Html.Kendo().Grid<Order>()   
        .Name("Grid")    
        .DataSource(dataSource => dataSource
            .Ajax()                       
            .Sort(sort => sort.Add(o => o.OrderDate).Ascending())
        )

## Filterable

**Filters** is moved to the DataSource configuration:
 
### Old
       
    Html.Telerik().Grid<Order>()
        .Name("Grid")   
        .Filterable(filtarable => filtarable.Filters(filters => filters.Add(o => o.OrderDate).IsEqualTo(DateTime.Today))

### New

    Html.Kendo().Grid<Order>()   
        .Name("Grid")        
        .DataSource(dataSource => dataSource
            .Ajax()                        
            .Filter(filter => filter.Add(o => o.OrderDate).IsEqualTo(DateTime.Today))
        ) 

## Pageable

**Position** is not available.

**PageSize** and Total is moved to the DataSource configuration:
 
### Old
    Html.Telerik().Grid<Order>()
        .Name("Grid")   
        .Pageable(pageable => pageable.PageSize(42).Total(100))

### New
     
    Html.Kendo().Grid<Order>()   
    .Name("Grid")        
    .DataSource(dataSource => dataSource
        .Ajax()                       
        .PageSize(42)
        .Total(100)
    ) 

**PageOnScroll** is removed (use **Scrollable.Virtual** option to enabled virtual scrolling instead).

**Style** is removed. Pager style can be configured by setting individual properties such as **Input**, **PageSizes**, **Info
**, **Numeric**, **PreviousNext**.

## Columns 

**Aggregates** are moved to the DataSource configuration:
 
### Old

    Html.Telerik().Grid<Order>()
        .Name("Grid")   
        .Columns(columns =>
        {
            columns.Bound(o => o.OrderID)
            .Aggregate(agg => agg.Count());          
        })

### New

    Html.Kendo().Grid<Order>()   
        .Name("Grid"
        .Columns(columns =>
        {
            columns.Bound(o => o.OrderID);
        })
        .DataSource(dataSource => dataSource
            .Ajax()                       
            .Aggregates(agg => agg.Add(o => o.OrderID).Count())
        )
        
**ReadOnly** in moved to DataSource Model configuration:
 
### Old

    Html.Telerik().Grid<Order>()
        .Name("Grid")   
        .Columns(columns =>
        {
            columns.Bound(o => o.OrderID).ReadOnly(true);          
        })

### New

    Html.Kendo().Grid<Order>()   
        .Name("Grid")
        .Columns(columns =>
        {
            columns.Bound(o => o.OrderID);
        })
        .DataSource(dataSource => dataSource
            .Ajax()
            .Model(model => model.Field(o => o.OrderID).Editable(false))
        )

## KeyboardNavigation

**KeyboardNavigation** is renamed to **Navigatable**.

**KeyboardNavigation.EditOnTab** is not available. This is enabled by default.

## NoRecordsTemplate

**NoRecordsTemplate** is not available. There will be a no NoRecords item but text will be shown within the pager. This text is configurable through **Pageable.Messages** configuration.

# Client-side API Changes

## Client-side API

#### insertRow

Removed. Use **grid.dataSource.insert(index, model)**

#### updateRow

Renamed. Use **saveRow** instead.

#### hasChanges

Removed.

#### submitChanges

Renamed. Use **saveChanges** instead.

#### cancelCell

Renamed. Use **closeCell** instead.

#### saveCell

Renamed. use **closeCell* instead.

#### insertedDataItems

Removed. Use the following code snippet instead:

    var inserted = $.grep(grid.DataSource.data(), function(model) {
        return model.isNew();
    });

#### updatedDataitems

Removed. Use the following code snippet instead:

    var inserted = $.grep(grid.dataSource.data(), function(model) {
        return model.dirty;
    });

#### deletedDataItems

Removed. Use the following code snippet instead (utilizing private API):

    var destroyed = grid.dataSource._destroyed

#### ajaxRequest

Removed. Use **grid.dataSource.read()** instead.

#### dataBind(data)

Removed. Use **grid.dataSource.data(data)** instead.

#### filter("Name~eq~'foo'");

Removed. Use the following code snippet instead:

    grid.dataSource.filter( { field: “Name”, operator: “eq”, value: “foo” } )

#### pageTo

Removed. Use **grid.dataSource.page** instead.

#### grid.rebind(params)

Removed. Use **grid.dataSource.read(params)** instead.

#### sort("Name-desc")

Removed. Use **grid.dataSource.sort( { field: “Name”, dir: “desc” } );** instead.

#### serializeData

Removed.

## Client-side Events

All events have removed the "On" prefix.

OnLoad no longer exists, please utilize $(document).ready() instead.

#### OnCommand

Removed. Utilize click event instead:

    command.custom("ViewDetails").Click("showDetails")

#### OnComplete

Removed.

#### OnDetailViewCollapse

Renamed to **DetailCollapse**

#### OnDetailViewExpand

Renamed to **DetailInit**

#### OnDelete

Renamed to **Remove**.

#### OnDataBinding

Removed.

If you want to be notified when an ajax request is being made use the following snippet:

    dataSource => dataSource.Ajax().Events(e => e.RequestStart(“onRequestStart”))

If you need to send custom data to the action method use .Data() on the DataSource:

    dataSource => dataSource.Ajax().Data(“sendData”)
    
    function sendData() {
        return { foo: “bar” };
    }

#### OnError

Removed. Use the Error event on the DataSource instead:

    dataSource => dataSource.Ajax().Events(e => e.Error(“onError”))

#### OnRowDataBound

Removed. Utilize **DataBound** instead and utilize the following code snippet:

    function onDataBound() {
        var data = this.view();

        for (var i=0; i< data.length; i++) {
            var dataItem = data[i];
            var tr = $(“#grid”).find(“[data-uid=’” + dataItem.uid + “’]”);
            // use the table row (tr) and data item (dataItem)
     }
}

#### OnRowSelect

Renamed to **Change**

#### OnSubmitChanges

Renamed to **SaveChanges**