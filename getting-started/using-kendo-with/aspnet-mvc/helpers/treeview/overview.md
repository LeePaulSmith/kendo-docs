---
title: Overview
meta_title: User Guide for TreeView HtmlHelper extension for Kendo UI TreeView widget
meta_description: Instructions and examples for TreeView HtmlHelper extension for Kendo UI TreeView for ASP.NET MVC.
slug: mvc-treeview-overview
publish: true
---

# TreeView

The TreeView HtmlHelper extension is a server-side wrapper for the [Kendo UI TreeView](http://docs.kendoui.com/api/web/treeview) widget.

## Getting Started

Here is how to configure a simple Kendo TreeView:

1.  Make sure you have followed all the steps from the [Introduction](http://docs.kendoui.com/getting-started/using-kendo-with/aspnet-mvc/introduction) help topic.

2.  Create a new action method which renders the view:

        public ActionResult Index()
        {
            return View();
        }
3.  Add a simple treeview:
    - WebForms

            <%: Html.Kendo().TreeView()
                    .Name("treeview") //The name of the treeview is mandatory. It specifies the "id" attribute of the widget.
                    .Items(items =>
                    {
                        items.Add().Text("Item 1"); //Add item with text "Item1")
                        items.Add().Text("Item 2"); //Add item with text "Item2")
                    })
            %>
    - Razor

            @(Html.Kendo().TreeView()
                  .Name("treeview") //The name of the treeview is mandatory. It specifies the "id" attribute of the widget.
                  .Items(items =>
                  {
                      items.Add().Text("Item 1"); //Add item with text "Item1")
                      items.Add().Text("Item 2"); //Add item with text "Item2")
                  })
            )

## Accessing an Existing TreeView

You can reference an existing TreeView instance via [jQuery.data()](http://api.jquery.com/jQuery.data/).
Once a reference has been established, you can use the [API](http://docs.kendoui.com/api/web/treeview#methods) to control its behavior.

### Accessing an existing TreeView instance

    //Put this after your Kendo TreeView for ASP.NET MVC declaration
    <script>
    $(function() {
        // Notice that the Name() of the treeview is used to get its client-side instance
        var treeview = $("#treeview").data("kendoTreeView");
    });
    </script>


## Handling Kendo UI TreeView events

You can subscribe to all [events](http://docs.kendoui.com/api/web/treeview#events) exposed by Kendo UI TreeView:

### WebForms - subscribe by handler name

    <%: Html.Kendo().TreeView()
            .Name("treeview")
            .Events(e => e
                .Expand("treeview_expand")
                .Collapse("treeview_collapse")
            )
    %>
    <script>
    function treeview_collapse() {
        //Handle the collapse event
    }

    function treeview_expand() {
        //Handle the expand event
    }
    </script>


### Razor - subscribe by handler name

    @(Html.Kendo().TreeView()
          .Name("treeview")
          .Events(e => e
                .Expand("treeview_expand")
                .Collapse("treeview_collapse")
          )
    )
    <script>
    function treeview_collapse() {
        //Handle the collapse event
    }

    function treeview_expand() {
        //Handle the expand event
    }
    </script>


### Razor - subscribe by template delegate

    @(Html.Kendo().TreeView()
          .Name("treeview")
          .Events(e => e
              .Expand(@<text>
                function() {
                    //Handle the expand event inline
                }
              </text>)
              .Collapse(@<text>
                function() {
                    //Handle the collapse event inline
                }
                </text>)
          )
    )
