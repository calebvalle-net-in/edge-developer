---
description: To inspect accessibility during all states of elements, such as text contrast during the hover state, in the Styles pane, use Toggle Element State.
title: Verify accessibility during all states of elements
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/13/2021
ms.topic: article
ms.prod: microsoft-edge
keywords: microsoft edge, web development, f12 tools, devtools
---
# Verify accessibility during all states of elements

<!-- 5. STYLES: TOGGLE STATE -->

Check the accessibility during all states of elements, such as text color contrast during the `hover` state.  To check other states of elements, in the **Styles** tab, select **\:hov** (**Toggle Element State**).  This button displays the **Force element state** checkboxes.  

First, we show why state simulation is necessary while using the **Inspect** tool.  Then we show how to use state simulation.


## Hovering when the Inspect tool is active doesn't show the text-color contrast for the hover state

The **Inspect** tool's information overlay only represents a single state.  But the elements on the page could have different states, and you need to test those states for accessibility, too.  For example, when you hover the mouse pointer over the menu of the accessibility-testing demo page, you get a rather involved animation that changes the colors:

1.  Open the [accessibility-testing demo webpage][DevToolsA11yErrorsDemopage] in a new tab.

1.  Hover over the blue buttons in the sidebar navigation menu.  The menu animations run.

    :::image type="complex" source="../media/a11y-testing-hover.msft.png" alt-text="The menu item showing different colors when the mouse pointer is over it" lightbox="../media/a11y-testing-hover.msft.png":::
        The menu item showing different colors when the mouse pointer is over it
    :::image-end:::
    
    But when you turn on the Inspect tool, you can't reach the `hover` state of the menu element to test the contrast ratio, because the `hover` state in your styles doesn't get triggered when the Inspect tool is active.  When the Inspect tool is active, animations of the demo menu items don't occur when you hover over them.  Confirm this lack of animation as follows:
    
1.  Select the **Inspect** \(![the Inspect button](../media/inspect-icon.msft.png)\) button in the top-left corner of DevTools so that the icon is highlighted (blue).

1.  Hover over the various buttons in the menu that begins with the blue **Cats** button.  The animations for the buttons don't run; instead, the buttons are color-highlighted in the way that is standard for the Inspect tool.

Checking for sufficient text contrast this way isn't enough, because the elements on the page could have different states.


<!-- Elements tool: Styles pane: Toggle Element State -->
## Using state simulation in the Styles pane to simulate the hover state of an animated menu item 

When the **Inspect** tool is active, instead of hovering over an animated element, you need to simulate the state of the menu item.  To simulate the state of a menu item, use the state simulation in the **Styles** pane.  The **Styles** pane has a **\:hov** (**Toggle Element State**) button, which displays a group of checkboxes labeled **Force element state**.

**To turn on the hover state while using the Inspect tool:**

1.  Open the [accessibility-testing demo webpage][DevToolsA11yErrorsDemopage] in a new tab.  Then select **F12** to open DevTools.

1.  Select the **Inspect** \(![Inspect tool button](../media/inspect-icon.msft.png)\) button in the top-left corner of DevTools so that the icon is highlighted (blue).

1.  In the rendered webpage, select the blue **Cats** button in the menu.  The **Elements** tool opens, with the element `<a href="#cats">Cats</a>` selected.

    :::image type="complex" source="../media/a11y-testing-inspecting-link-to-hover.msft.png" alt-text="Inspecting the element that has a hover state in the Elements tool" lightbox="../media/a11y-testing-inspecting-link-to-hover.msft.png":::
        Inspecting the element that has a hover state in the Elements tool
    :::image-end:::

1.  Select the **Styles** tab.  The selected `a` element has a `hover` state in the CSS that is applied to it, but that's not visible in the **Styles** pane, which doesn't show the `hover` CSS rule.

1.  In the **Styles** pane, to the right of the style rule `#sidebar nav li a`, select the `styles.css` link.  The **Sources** tool opens.  Then find the CSS pseudo-class rule `#sidebar nav li a:hover`.  This rule doesn't run when the **Inspect** tool is active.  We'll simulate this state-rule running, in the next steps.

1.  Select the **Elements** tool.  Then in the **Styles** pane, select the **:hov** (**Toggle Element State**) button.  The **Force element state** group of checkboxes appears.

    :::image type="complex" source="../media/a11y-testing-state-simulation.msft.png" alt-text="The state simulation tool showing all the options" lightbox="../media/a11y-testing-state-simulation.msft.png":::
        The state simulation tool showing all the options
    :::image-end:::

1.  Select the **:hover** checkbox.  In the DOM, to the left of the element `<a href="#cats">Cats</a>`, a yellow dot appears, indicating that the element has a simulated state.  The **Cats** menu item now appears in the webpage as if the pointer were hovering over it.  The animation might partly run.

    :::image type="complex" source="../media/a11y-testing-hover-simulated.msft.png" alt-text="DevTools simulating a hover state" lightbox="../media/a11y-testing-hover-simulated.msft.png":::
        DevTools simulating a hover state
    :::image-end:::

    After the simulated state is applied, you can use the **Inspect** tool again to check the contrast of the element when the user hovers over it, as follows.

1.  Select the **Inspect** \(![Inspector icon](../media/inspect-icon.msft.png)\) button in the top-left corner of DevTools so that the icon is highlighted (blue).

1.  Hover over the blue **Cats** button, which is now light blue, because of the simulated hover animation.  The **Inspect** tool's information overlay appears, showing an orange exclamation point in the **Contrast** row, indicating that the contrast isn't high enough.

    :::image type="complex" source="../media/a11y-testing-hover-contrast-testing.msft.png" alt-text="Testing the contrast of an element in a simulated hover state" lightbox="../media/a11y-testing-hover-contrast-testing.msft.png":::
        Testing the contrast of an element in a simulated hover state
    :::image-end:::

State simulation is also a good way to check whether you considered different user needs, such as for keyboard users.  By using the **Force element state** checkboxes, you can find out that simulating the `:focus` state makes no difference to the look and feel.  Lack of indication of focus is a problem, as is experienced when using the keyboard to navigate this demo page.


## See also

*  [Overview of accessibility testing using DevTools](accessibility-testing-in-devtools.md)


## Getting in touch with the Microsoft Edge DevTools team  

[!INCLUDE [contact DevTools team note](../includes/contact-devtools-team-note.md)]  


<!-- links -->
[DevToolsA11yErrorsDemopage]: https://microsoftedge.github.io/DevToolsSamples/a11y-testing/page-with-errors.html "Accessibility-testing demo webpage | GitHub"