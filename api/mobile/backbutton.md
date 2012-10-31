---
title: kendo.mobile.ui.BackButton
meta_title: Kendo UI Mobile BackButton API reference
meta_description: Examples how to initialize Kendo UI mobile BackButton based on role data attribute and using jQuery plugin syntax.
slug: mobile-kendo.mobile.ui.backbutton
tags: api,mobile
publish: true
---

# kendo.mobile.ui.BackButton

## BackButton

The mobile BackButton widget navigates to the previously visited mobile View when pressed. A view can be explicitly set using the `href` attribute.

#### Initialize Kendo mobile BackButton based on role data attribute

    <a data-role="backbutton">Foo</a>

#### Initialize Kendo mobile BackButton using jQuery plugin syntax

    var button = $("#button").kendoMobileBackButton();

## Events

### click

Fires when the user taps the button.

#### Event Data

##### e.target `jQuery`

The clicked DOM element

##### e.button `jQuery`

The button DOM element
