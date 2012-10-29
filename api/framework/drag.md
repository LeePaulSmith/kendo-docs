---
title: kendo.Drag
meta_title: API Reference for kendo.Drag in Kendo UI framework
meta_description: How to set the value of kendo.Drag, find configuration examples, methods and types of events which are triggered upon specific state of the drag.
slug: fw-kendo.drag
tags: api,framework
publish: true
---

# kendo.Drag

## Configuration

### allowSelection `Boolean`*(default: false)*

 If set to true, the mousedown and selectstart events will not be prevented.

### filter `Selector`

If passed, the filter limits the child elements that will trigger the event sequence.

### global `Boolean`*(default: false)*

 If set to true, the drag event will be tracked beyond the element boundaries.

### stopPropagation `Boolean`*(default: false)*

 If set to true, the mousedown event propagation will stopped, disabling
drag capturing at parent elements.
If set to false, dragging outside of the element boundaries will trigger the `end` event.

### surface `Element`

If set, the drag event will be tracked for the surface boundaries. By default, leaving the element boundaries will end the drag.

### threshold `Number`*(default: 0)*

 The minimum distance the mouse/touch should move before the event is triggered.

## Methods

### cancel

Discard the current drag. Calling the `cancel` method will trigger the `cancel` event.
The correct moment to call this method would be in the `start` event handler.

#### Cancel the drag event sequence

    new kendo.Drag($("#foo"), {
     start: function(e) {
         e.cancel();
     }
    });

### capture

Capture the current drag, so that Drag listeners bound to parent elements will not trigger.
This method will not have any effect if the current drag instance is instantiated with the `global` option set to true.

## Events

### cancel

Fires when the drag is canceled. This  when the `cancel` method is called.

#### Event Data

##### e.x `DragAxis`

Reference to the horizontal drag axis instance.

##### e.y `DragAxis`

Reference to the vertical drag axis instance.

##### e.event `jQueryEvent`

Reference to the jQuery event object.

##### e.target `Element`

Reference to the DOM element from which the Drag started.
It is different from the element only if `filter` option is specified.

### end

Fires when the drag ends.

#### Event Data

##### e.x `DragAxis`

Reference to the horizontal drag axis instance.

##### e.y `DragAxis`

Reference to the vertical drag axis instance.

##### e.event `jQueryEvent`

Reference to the jQuery event object.

##### e.target `Element`

Reference to the DOM element from which the Drag started.
It is different from the element only if `filter` option is specified.

### move

Fires while dragging.

#### Event Data

##### e.x `DragAxis`

Reference to the horizontal drag axis instance.

##### e.y `DragAxis`

Reference to the vertical drag axis instance.

##### e.event `jQueryEvent`

Reference to the jQuery event object.

##### e.target `Element`

Reference to the DOM element from which the Drag started.
It is different from the element only if `filter` option is specified.

### start

Fires when the user starts dragging the element.

#### Event Data

##### e.x `DragAxis`

Reference to the horizontal drag axis instance.

##### e.y `DragAxis`

Reference to the vertical drag axis instance.

##### e.event `jQueryEvent`

Reference to the jQuery event object.

##### e.target `Element`

Reference to the DOM element from which the Drag started.
It is different from the element only if `filter` option is specified.

### tap

Fires when the user presses and releases the element without any movement or with a movement below the `threshold` specified.

#### Event Data

##### e.x `DragAxis`

Reference to the horizontal drag axis instance.

##### e.y `DragAxis`

Reference to the vertical drag axis instance.

##### e.event `jQueryEvent`

Reference to the jQuery event object.

##### e.target `Element`

Reference to the DOM element from which the Drag started.
It is different from the element only if `filter` option is specified.
