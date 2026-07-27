---
tags:
  - AppDev/Design
---
## Patterns and Anti-Patterns

A **pattern** is a generally accepted and reusable implementation applicable to not just design but programming and more.

An **anti-pattern** is a implementation that contradicts a common pattern. Anti-patterns should be avoided and often result in cumbersome solutions.

## Primary and Secondary Navigation

Various navigation patterns fall under a primary pattern category, this pattern is core to their behavior.

- **Persistent** - simple menu structures that persist in the UI 
- **Transient** - hidden until gesture/action is performed by the user.
- **Card** - UI elements are contained in a stacked card format. Gesture based navigation to interact with the underlying application/components.

	I would argue that the Card pattern is a subset of the Transient pattern.
	The term primary is meant to denote top-level navigation.

A secondary pattern, in this context, is the design pattern used for navigation within the exposed UI reached by navigating through the primary pattern. 

Design patterns are interchangeable, meaning they are not pinned to primary or secondary categories and as a result the patterns are used interchangeably.

## Navigation Pattern Examples

I've attempted to categorize these patterns under the previously mentioned primary patterns. This is largely used in the event the class tests on this information.

Many different patterns are seemingly combined to make up a cohesive navigation experience. As such, many patterns I find cannot be pinned to a single primary pattern. Categorization can largely be ignored in my opinion, what matters are the patterns themselves.

*Again, the text used for this data is very, very old so this confusion could be a byproduct of material age.*

### Persistent

| Pattern | Description |
| ---- | ---- |
| List Menu | Similar to the transient springboard pattern. Static list of hierarchical items that can be drilled into to reach the designed sub-component. |
| Dashboard | Also similar to the list menu and springboard patterns. UI displays periodically updated state. The user can interact with UI elements to drill into the associated data. |
| Gallery | Think the media within Instagram. Content are displayed as cards and you can doom-scroll through the content. The user can interact with the cards to expand the content and reveal more options. |
| Tab Menu | Similar to the Discord app. A persistent tab used for navigation within the app. Often will take up the bottom section of the app from edge to edge, with minimal vertical height. Tabs can also be scroll-able. |
| Accordian | Very similar to sideboard. The UI takes up the string and is hierarchical. Drilling into an element expands out all sub categories contained within, **without** hiding top-level categories. |

### Transient

| Pattern | Description |
| ---- | ---- |
| Panorama | UI is a wide virtual landscape. The mobile device screen acts as a window to a slice of the the virtual landscape. |
| Springboard | also known as Launchpad, contains a landing screen of typically 3x3 icons that *spring* the user into the selected application or application component. Commonly used in the home screen of phone based OSs. |
| Side Drawer | a side fly-out menu container a hierarchy of menu categories. This can be docked in many cases. *I would argue this is the same as the Navigation Drawer pattern* |

Transient patterns will either *overlay* or *inlay*.
- **Overlay** - the underlying UI **is not** affected. The nav will fly-out or sit on top of the content.
- **Inlay** - the underlying UI **is** affected. The nav will fly-out and merge with the content, result in the content resizing/repositioning to accommodate the nav.

### Calls to Action

In some patterns, namely the transient tab pattern, a call to action may be put in place. A call to action is simply a UI a design used to draw attention to an action. 

For example, the icon to take a photo within Instagram. This icon is centered, and colored/highlighted to differentiate it. This enables users to quickly identity this commonly used component and intuitively engage with the app.

## Emerging Patterns

The text highlights these as emerging patterns, but these patterns are simply common place today. Again, the text is very old.

| Pattern | Description |
| ---- | ---- |
| Hiding Navigation | A pattern that hides navigation components while the user is engaged with the content, such as scrolling through a Gallery or expanding a single element. |
| Configurable Tabs | Similar to tab navigation, the user can rearrange and decide what tab items are listed. |
| Sidebars | Identical to the Sidebar except it is *not* hierarchical and the bard is permanently docked. Additionally, the sidebar is very narrow and relies on icons to communicate purpose. |
| Skeuomorpic | UI resembles real life objects. Think a music mixing app with a digital turntable to you can "scratch" to manipulate the sound. |
| Gesture | User gestures are used to navigate throughout the UI. UI relying on gestures should be designed in a way to enable to user to infer the way to reach content is via gesture. |
