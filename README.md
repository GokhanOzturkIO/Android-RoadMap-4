# Android-RoadMap-4 `v1.0.0-alpha01`

**Androidv14 - Level34**

## UI GUIDE - COMPOSE

### 1. Introduction

#### 1.1 Documentation

- Foundation
- Development environment
- Design
- Adopting Compose
- Additional resources

#### 1.2 Why Compose

- Less code
- Intuitive
- Accelerate development
- Powerful

#### 1.3 Quick start

- Create a new app with support for Compose
- Set up Compose for an existing app
- Try Jetpack Compose sample apps

#### 1.4 Thinking in Compose

- The declarative programming paradigm
- A simple composable function
- The declarative programming paradigm
- Dynamic content
- Recomposition
    - Composable functions can execute in any order
    - Composable functions can run in parallel
    - Recomposition skips as much as possible
    - Recomposition is optimistic
    - Composable functions might run quite frequently

#### 1.5 Bill of Materials

##### 1.5.1 Using the Bill of Materials

- Why isn't the Compose Compiler library included in the BOM?
- How do I use a different library version than what's designated in the BOM?
- Does the BOM automatically add all the Compose libraries to my app?
- Why is the BOM the recommended way to manage Compose library versions?
- Am I forced to use the BOM?
- Does the BOM work with version catalogs?

##### 1.5.2 BOM to library version mapping

---

### 2. UI Architecture

#### 2.1 Lifecycle of composables

- Lifecycle overview
- Anatomy of a composable in Composition
    - Add extra information to help smart recompositions
    - Skipping if the inputs haven't changed

#### 2.2 Side-effects in Compose

- State and effect use cases
    - `LaunchedEffect`: run suspend functions in the scope of a composable
    - `rememberCoroutineScope`: obtain a composition-aware scope to launch a coroutine outside a composable
    - `rememberUpdatedState`: reference a value in an effect that shouldn't restart if the value changes
    - `DisposableEffect`: effects that require cleanup
    - `SideEffect`: publish Compose state to non-Compose code
    - `produceState`: convert non-Compose state into Compose state
    - `derivedStateOf`: convert one or multiple state objects into another state
    - `snapshotFlow`: convert Compose's State into Flows
- Restarting effects
    - Constants as keys

#### 2.3 Jetpack Compose phases

- The three phases of a frame
    - Understand the phases
- State reads
- Phased state reads
    - Phase 1: Composition
    - Phase 2: Layout
    - Phase 3: Drawing
- Optimizing state reads
- Recomposition loop (cyclic phase dependency)

#### 2.4 Managing State

##### 2.4.1 Overview

- State and composition
- State in composables
- Other supported types of state
    - Stateful versus stateless
- State hoisting
- Restoring state in Compose
    - Ways to store state
- State holders in Compose
- Retrigger remember calculations when keys change
    - Store state with keys beyond recomposition

##### 2.4.2 Where to hoist state

- Best practice
- Types of UI state and UI logic
    - UI state
    - Logic
- UI logic
    - Composables as state owner
    - No state hoisting needed
    - Hoisting within composables
    - Plain state holder class as state owner
- Business logic
    - ViewModels as state owner
    - Screen UI state
    - UI element state

##### 2.4.3 Save UI state in Compose

- UI logic
    - Best practice
    - Verify state restoration
- Business logic
    - Best practice
    - `SavedStateHandle` APIs
    - Summary

#### 2.5 Architecting your Compose UI

- Unidirectional data flow
    - Unidirectional data flow in Jetpack Compose
    - Define composable parameters
- Events in Compose
    - ViewModels, states, and events: an example

#### 2.6 Jetpack Compose architectural layering

- Layers
- Design principles
    - Control
    - Customization
    - Picking the right abstraction

#### 2.7 Locally scoped data with CompositionLocal

- Introducing `CompositionLocal`****
- Creating your own `CompositionLocal`****
    - Deciding whether to use `CompositionLocal`****
    - Creating a `CompositionLocal`****
    - Providing values to a `CompositionLocal`****
    - Consuming the `CompositionLocal`****
- Alternatives to consider
    - Pass explicit parameters
    - Inversion of control

#### 2.8 Navigation with Compose

- Setup
- Get started
- Create a NavController
- Create a NavHost
- Navigate to a composable
- Navigate with arguments
    - Retrieve complex data when navigating
    - Add optional arguments
- Deep links
- Nested Navigation
- Integration with the bottom nav bar
- Type safety in Navigation Compose
- Interoperability
    - Navigate from Compose with Navigation for fragments
- Testing
    - Testing the `NavHost`****
    - Testing navigation actions

---

### 3. Develop Your App’s Layout

#### 3.1 Layouts in Compose

#### 3.2 Compose layout basics

- Goals of layouts in Compose
- Basics of composable functions
- Standard layout components
- The layout model
- Performance
- Using modifiers in your layouts
- Scrollable layouts
- Responsive layouts
    - Constraints
- Slot-based layouts

#### 3.3 Compose modifiers

- Order of modifiers matters
- Built-in modifiers
    - `padding` and `size`****
    - Offset
- Scope safety in Compose
    - `matchParentSize` in `Box`****
    - `weight` in `Row` and `Column`****
- Extracting and reusing modifiers
    - Best practices for reusing modifiers

#### 3.4 Constraints and modifier order

- Modifiers in the UI tree
- Constraints in the layout phase
    - Types of constraints
    - How constraints are passed from parent to child
- Modifiers that affect constraints
    - `size` modifier
    - `requiredSize` modifier
    - `width` and `height` modifiers
    - `sizeIn` modifier
- Examples

#### 3.5 Create custom modifiers

- Chain existing modifiers together
- Create a custom modifier using a composable modifier factory
- Implement custom modifier behavior using `Modifier.Node`****
    - Implement a custom modifier using `Modifier.Node`****
- Common situations using `Modifier.Node`****
    - Zero parameters
    - Referencing composition locals
    - Animating modifier
    - Sharing state between modifiers using delegation
    - Opting out of node auto-invalidation

#### 3.6 List of Compose modifiers

- Actions, Alignment, Animation, Border, Drawing, Focus, Graphics, Keyboard, Layout, Padding, Pointer, Position, Semantics, Scroll, Size, Testing, Transformations, Other

#### 3.7 Pager in Compose

- `HorizontalPager`****
- `VerticalPager`****
- Lazy creation
    - Load more pages offscreen
- Scroll to an item in the pager
- Get notified about page state changes
- Add a page indicator
- Apply item scroll effects to content
- Custom page sizes
- Content padding
- Customize scroll behavior
    - Snap distance

#### 3.8 Flow layouts in Compose

- Basic usage
- Features of flow layout
    - Main axis arrangement: horizontal or vertical arrangement
    - Cross axis arrangement
    - Individual item alignment
    - Max items in row or column
    - Item weights
    - Fractional sizing

#### 3.9 Custom layouts

- Use the layout modifier
- Create custom layouts
- Layout direction
- Custom layouts in action

#### 3.10 Adaptive layouts

##### 3.10.1 Build adaptive layouts

- Make large layout changes for screen-level composables explicit
- Flexible nested composables are reusable
- Ensure all data is available for different sizes

##### 3.10.2 Build a list-detail layout

- Implement UI pattern with `ListDetailPaneScaffold`****
    - Declare dependencies
    - Basic usage

#### 3.11 Alignment lines in Jetpack Compose

- Create custom alignment lines

#### 3.12 Intrinsic measurements in Compose layouts

- Intrinsics in action
    - Intrinsics in your custom layouts

#### 3.13 ConstraintLayout in Compose

- Get started with `ConstraintLayout`****
- Decoupled API
- `ConstraintLayout` concepts
    - Guidelines
    - Barriers
    - Chains

---

### 4. Components

- Material components in Compose

#### 4.1 Scaffold

- Example

#### 4.2 App bars

- Top app bars
    - API surface
    - Scroll behavior
- Examples
    - Small
    - Center aligned
    - Medium
    - Large
- Bottom app bar

#### 4.3 Button

- API surface
- Filled button
- Filled tonal button
- Outlined button
- Elevated button
- Text button

#### 4.4 Floating action button

- API surface
- Floating action button
- Small button
- Large button
- Extended button

#### 4.5 Card

- Basic implementation
- Advanced implementations
    - Filled card
    - Elevated Card
    - Outlined Card
- Limitations

#### 4.6 Chip

- API surface
- Assist chip
- Filter chip
- Input chip
- Suggestion chip
- Elevated chip

#### 4.7 Dialog

- Alert dialog
- Dialog composable
    - Basic example
    - Advanced example

#### 4.8 Progress indicators

- API Surface
- Determinate indicators
- Indeterminate indicators

#### 4.9 Slider

- Basic implementation
- Advanced implementation
- Range slider

#### 4.10 Switch

- Basic implementation
- Advanced implementation
    - Custom thumb
    - Custom colors

#### 4.11 Bottom sheets

#### 4.12 Navigation drawer

- Example

#### 4.13 Snackbar

- Basic example
- Snackbar with action

#### 4.14 Lists and grids

- Lazy lists
- `LazyListScope` DSL
- Lazy grids
- Lazy staggered grid
- Content padding
- Content spacing
- Item keys
- Item animations
- Sticky headers (experimental)
- Reacting to scroll position
- Controlling the scroll position
- Large data-sets (paging)
- Tips on using Lazy layouts
    - Avoid using 0-pixel sized items
    - Avoid nesting components scrollable in the same direction
    - Beware of putting multiple elements in one item
    - Consider using custom arrangements
    - Consider adding `contentType`****
    - Measuring performance

#### 4.15 Resources in Compose

- Strings
    - String plurals (experimental)
- Dimensions
- Colors
- Vector assets and image resources
- Animated Vector Drawables
- Icons
- Fonts

---

### 5. Theming

#### 5.1 Design systems in Compose

#### 5.2 Material Design 3 in Compose

- Dependency
    - Experimental APIs
- Material theming
    - Color scheme
    - Typography
    - Shapes
    - Emphasis
- Elevation
- Material components
    - Navigation components
    - Customize a component's theming
- System UI
    - Ripple
    - Overscroll
- Accessibility
    - Color accessibility
    - Typography accessibility
- Large screens

#### 5.3 Migrate from Material 2 to Material 3 in Compose

- Approaches
    - When to migrate
    - Phased approach
- Dependencies
- Experimental APIs
- Theming
    - Color
    - Typography
    - Shape
- Components and layouts
    - Scaffold, snackbars and navigation drawer
    - Top app bar
    - Bottom navigation / Navigation bar
    - Buttons, icon buttons and FABs
    - Switch
- Surfaces and elevation
- Emphasis and content alpha
- Backgrounds and containers
- Views interoperability

#### 5.4 Material Design 2 in Compose

- Color
    - Using theme colors
    - Surface and content color
    - Content alpha
    - Dark theme
- Typography
    - Using text styles
- Shape
    - Using shapes
- Default styles
- Theme overlays
- Component states
- Ripples

#### 5.5 Custom design systems in Compose

- Extending Material Theming
    - Using Material components
- Replacing Material systems
    - Using Material components
- Implementing a fully-custom design system
    - Using Material components

#### 5.6 Anatomy of a theme in Compose

- Theme system classes
- Theme system composition locals
- Theme function
- Theme object

#### 5.7 Migrate XML themes to Compose

---

### 6. Text and Typography

#### 6.1 Text in Compose

#### 6.2 Display and style text

##### 6.2.1 Display text

- Display text from resource

##### 6.2.2 Style text

- Common text stylings
    - Change text color
    - Change text size
    - Make text italic
    - Make text bold
    - Add shadow
- Add multiple styles in text
- Enable advanced styling with `Brush`****
    - Use a brush for text styling
    - Integrations

##### 6.2.3 Style paragraph

- Set text alignment
- Add multiple styles in a paragraph
- Adjust line height and padding

##### 6.2.4 Configure text layout

- Limit visible lines
- Indicate text overflow

#### 6.3 Handle user input

- Choose `TextField` implementation
- Style `TextField`****
- Style input with Brush API
    - Implement colored gradients using `TextStyle`****
- Set keyboard options
- Format input
- Clean input
- Best practices with state

#### 6.4 Enable user interactions

- Select text
- Get position of a click on text
    - Click with annotation

#### 6.5 Work with fonts

- Set font
- Downloadable fonts
    - Use downloadable fonts programmatically
    - Add fallback fonts
    - Debug your implementation
    - Caveats
- Use variable fonts
    - Load a variable font
    - Use custom axes

#### 6.6 Display emoji

- Interoperatibility
    - Extending from `ComponentActivity`****
    - Extending from `AppCompatActivity`****
- Troubleshooting

---

### 7. Images and Graphics

#### 7.1 Images and graphics in Compose

#### 7.2 Images

##### 7.2.1 Working with images

##### 7.2.2 Loading images

- Load an image from the disk
    - Drawable support
- Load an image from the internet
    - `Coil`
    - `Glide`

##### 7.2.3 ImageBitmap vs ImageVector

- `ImageBitmap`
- `ImageVector`

##### 7.2.4 Material icons

##### 7.2.5 Customize an image

- Content scale
- Clip an `Image` composable to a shape
- Add a border to an `Image` composable
- Set a custom aspect ratio
- Color filter - Transform pixel colors of image
    - Tinting an image
    - Applying an `Image` filter with color matrix
- Blur an `Image` composable

##### 7.2.6 Custom painter

##### 7.2.7 Optimizing performance for images

- Only load the size of the bitmap you need
- Don’t store a bitmap in memory longer than you need it
- Don’t package large images with your AAB/APK file

#### 7.3 Graphics

##### 7.2.1 Graphics in Compose

- Basic drawing with modifiers and `DrawScope`
- Coordinate system
- Basic transformations
    - Scale
    - Translate
    - Rotate
    - Inset
    - Multiple transformations
- Common drawing operations
    - Draw text
    - Draw image
    - Draw basic shapes
    - Draw path
- Accessing `Canvas` object

##### 7.3.2 Graphics modifiers

- Drawing modifiers
    - `Modifier.drawWithContent`: Choose drawing order
    - `Modifier.drawBehind`: Drawing behind a composable
    - `Modifier.drawWithCache`: Drawing and caching draw objects
- Graphics modifiers
    - `Modifier.graphicsLayer`: Apply transformations to composables
- Write contents of a composable to a bitmap
- Custom drawing modifier

##### 7.3.3 Brush: gradients and shaders

- Gradient brushes
    - Change distribution of colors with `colorStops`****
    - Repeat a pattern with `TileMode`****
    - Change brush Size
- Use an image as a brush
- Advanced example: Custom brush
    - AGSL `RuntimeShader` brush

---

### 8. Animation

#### 8.1 Animations in Compose

#### 8.2 Choose an animation API

#### 8.3 Quick guide to Animations in Compose

- Animate common composable properties
    - Animate appearing / disappearing
    - Animate background color
    - Animate the size of a composable
    - Animate position of composable
    - Animate padding of a composable
    - Animate elevation of a composable
    - Animate text scale, translation or rotation
    - Animate text color
- Switch between different types of content
- Animate whilst navigating to different destinations
- Repeat an animation
- Start an animation on launch of a composable
- Create sequential animations
- Create concurrent animations
- Optimize animation performance
- Change animation timing

#### 8.4 Animation modifiers and composables

- Built-in animated composables
    - Animate appearance and disappearance with `AnimatedVisibility`****
    - Animate based on target state with `AnimatedContent`****
    - Animate between two layouts with `Crossfade`****
- Built-in animation modifiers
    - Animate composable size changes with `animateContentSize`****
- List item animations

#### 8.5 Value-based animations

- Animate a single value with `animate*AsState`****
- Animate multiple properties simultaneously with a transition
    - Use transition with `AnimatedVisibility` and `AnimatedContent`****
    - Encapsulate a transition and make it reusable
- Create an infinitely repeating animation with `rememberInfiniteTransition`
- Low-level animation APIs
    - `Animatable`: Coroutine-based single value animation
    - `Animation`: Manually controlled animation

#### 8.6 Animated vector images in Compose

- Animated vector drawables (experimental)

#### 8.7 Advanced animation example: Gestures

#### 8.8 Customize animations

- Customize animations with the `AnimationSpec` parameter
    - Create physics-based animation with `spring`****
    - Animate between start and end values with easing curve with `tween`****
    - Animate to specific values at certain timings with `keyframes`****
    - Repeat an animation with `repeatable`
    - Repeat an animation infinitely with `infiniteRepeatable`****
    - Immediately snap to end value with `snap`****
- Set a custom easing function
- Animate custom data types by converting to and from `AnimationVector`****

#### 8.9 Test animations

#### 8.10 Animation tooling support

#### 8.11 Animations additional resources

- Animation cheat sheet

---

### 9. Accessibility

#### 9.1 Semantics in Compose

- Semantics properties
- Merged and unmerged Semantics tree
    - Inspecting the trees
    - Merging behavior
- Adapting the Semantics tree

#### 9.2 Accessibility in Compose

- Semantics
- Common use cases
    - Consider minimum touch target sizes
    - Add click labels
    - Describe visual elements
    - Merge elements
    - Add custom actions
    - Describe an element’s state
    - Define headings
- Automated testing of accessibility properties
- Creating custom low-level composables
- Modify traversal order with `isTraversalGroup` and `traversalIndex`****
    - Group elements with `isTraversalGroup`****
    - Further customize traversal order with traversalIndex

---

### 10. Touch and Input

#### 10.1 Touch and input in Compose

#### 10.2 Pointer input

##### 10.2.1 Pointer input in Compose

##### 10.2.2 Understand gestures

- Definitions
- Different levels of abstraction
    - Component support
    - Add specific gestures to arbitrary composables with modifiers
    - Add custom gesture to arbitrary composables with `pointerInput` modifier
- Event dispatching and hit-testing
- Event consumption
- Event propagation
- Test gestures

##### 10.2.3 Tap and press

- Respond to tap or click
- Long-press to show a contextual context menu
- Dismiss a composable by tapping a scrim
- Double tap to zoom

##### 10.2.4 Scroll

- Scroll modifiers
- Scrollable modifier
- Nested scrolling
    - Automatic nested scrolling
    - Using the `nestedScroll` modifier
- Nested scrolling interop (Starting with Compose 1.2.0)
    - A cooperating parent `View` containing a child `ComposeView`****
    - A parent composable containing a child `AndroidView`****
    - A non-cooperating parent `View` containing a child `ComposeView`****

##### 10.2.5 Drag, swipe, and fling

- Swiping

##### 10.2.6 Migrate from Swipeable to AnchoredDraggable

- Migrate `SwipeableState` to `AnchoredDraggableState`****
    - Update your state holder
    - Access the offset
- Migrate `Modifier.swipeable` to `Modifier.anchoredDraggable`****
    - Define anchors
    - Define positional thresholds
    - Define velocity thresholds
- Changes to the API surface
    - `AnchoredDraggableState`****
    - `Modifier.anchoredDraggable`****

##### 10.2.7 Multitouch: Panning, zooming, rotating

#### 10.3 Focus

##### 10.3.1 Focus in Compose

- Default focus traversal order

##### 10.3.2 Change focus traversal order

- Override one-dimensional traversal order
- Override two-dimensional traversal order

##### 10.3.3 Change focus behavior

- Provide coherent navigation with focus groups
- Making a composable focusable
- Making a composable unfocusable
- Request keyboard focus with `FocusRequester`****
- Capture and release focus
- Precedence of focus modifiers
- Redirect focus upon entry or exit
- Change focus advancing direction

##### 10.3.4 React to focus

- Provide visual cues for easier focus visualization
    - Implement advanced visual cues
- Understand the state of the focus

#### 10.4 User interactions

##### 10.4.1 Handling user interactions

- Interactions
- Interaction state
- Consume and emit `Interaction`****
    - Consuming modifier example
    - Producing modifier example
    - Build components that consume and produce
- Work with `InteractionSource`****
- Example: Build component with custom interaction handling
- Create and apply a reusable custom effect with `Indication`****
    - Replace effect with an `Indication`
    - Build an advanced `Indication` with animated border

##### 10.4.2 Migrate to Indication and Ripple APIs

- Behavior change
- Upgrade Material library version without migrating
- Migrate from `rememberRipple` to `ripple`****
    - Using a Material library
    - Implementing custom design system
- Migrate from `RippleTheme`****
    - Temporarily opt out of behavior change
    - Using `RippleTheme` to disable a ripple for a given component
    - Using `RippleTheme` to change the color/alpha of a ripple for a given component
    - Using `RippleTheme` to globally change all ripples in an application
- Migrate from `Indication` to `IndicationNodeFactory`****
    - Passing around `Indication`****
    - Creating `Indication`****
    - Using `Indication` to create an `IndicationInstance`****

---

### 11. Performance

#### 11.1 Jetpack Compose performance

#### 11.2 Tooling

- Layout Inspector
- Composition tracing

#### 11.3 Follow best practices

- Use `remember` to minimize expensive calculations
- Use Lazy layout keys
- Use `derivedStateOf` to limit recompositions
- Defer reads as long as possible
- Avoid backwards writes

#### 11.4 Stability

##### 11.4.1 Stability in Compose

- Immutable objects
    - Mutable objects
- Implementation in Compose
    - Functions
    - Types
- Debug stability
- Fix stability issues
- Summary

##### 11.4.2 Diagnose stability issues

- Layout Inspector
- Compose compiler reports
    - Setup
    - Run the task

##### 11.4.3 Fix stability issues

- Make the class immutable
- Immutable collections
- Annotate with `Stable` or `Immutable`****
    - Annotated classes in collections
- Stability configuration file
- Multiple modules
    - Solution
- Not every composable should be skippable

---

### 12. Style guidelines

#### 12.1 Style guidelines for Jetpack Compose APIs

- Audience

#### 12.2 Kotlin for Jetpack Compose

- Default arguments
- Higher-order functions and lambda expressions
    - Trailing lambdas
- Scopes and receivers
- Delegated properties
- Destructuring data classes
- Singleton objects
- Type-safe builders and DSLs
- Kotlin coroutines

---

### 13. UI testing

#### 13.1 Testing your Compose layout

- Semantics
- Setup
- Testing APIs
    - Finders
    - Assertions
    - Actions
    - Matchers
- Synchronization
    - Disabling automatic synchronization
    - Idling resources
    - Manual synchronization
    - Waiting for conditions
- Common patterns
    - Test in isolation
    - Access the activity and resources after setting your own content
    - Custom semantics properties
    - Verify state restoration
- Debugging
- Interoperability with Espresso
- Interoperability with UiAutomator

#### 13.2 Testing cheatsheet

---

### 14. Migrate to Compose

#### 14.1 Migrate existing View-based apps

#### 14.2 Migration strategy

- Build new screens with Compose
    - Add new features in existing screens
- Build a library of common UI components
- Replace existing features with Compose
    - Simple screens
    - Mixed view and Compose screens
- Removing Fragments and Navigation component

#### 14.3 Interoperability APIs

##### 14.3.1 Overview Interoperability APIs

##### 14.3.2 Using Compose in Views

- `ViewCompositionStrategy` for `ComposeView`****
- `ComposeView` in Fragments
- Multiple `ComposeView` instances in the same layout
- Preview composables in Layout Editor

##### 14.3.3 Using Views in Compose

- `AndroidView` with view binding
- `AndroidView` in Lazy lists
- Fragments in Compose
- Calling the Android framework from Compose
    - Composition Locals
- Other interactions
- Case study: Broadcast receivers

#### 14.4 Common migration scenarios

##### 14.4.1 Migrate RecyclerView to Lazy list

- Migration steps
- Common use cases
    - Item decorations
    - Item animations

##### 14.4.2 Migrate CoordinatorLayout to Compose

- Migration steps
- Common use cases
    - Collapse and expand toolbars
    - Drawers
    - Snackbars

##### 14.4.3 Migrate Jetpack Navigation to Navigation Compose

- Migration prerequisites
- Migration steps
- Common use cases
    - Safe Args
    - Retrieve complex data when navigating
- Limitations
    - Incremental migration to Navigation Compose
    - Transition animations

#### 14.5 Other considerations

- Migrating your app's theme
- Navigation
- Test your mixed Compose/Views UI
- Integrating Compose with your existing app architecture
    - Using a `ViewModel` in Compose
    - State source of truth
    - Compose as the source of truth
    - View system as the source of truth
- Migrating shared UI
- Prioritize splitting state from presentation
- Promote encapsulated and reusable components
- Handling screen size changes
- Nested scrolling with Views
- Compose in `RecyclerView`****
- `WindowInsets` interop with Views

#### 14.6 Technical decision makers: Adopt Compose for your teams

#### 14.7 Compose and other libraries

- Activity
    - Activity Result
    - Requesting runtime permissions
    - Handling the system back button
- `ViewModel`****
- Streams of data
- Asynchronous operations in Compose
- Navigation
- Hilt
    - Hilt and Navigation
- Paging
- Maps

#### 14.8 Compare Compose and View metrics

- APK size and build times
    - APK size
    - Build time
    - Summary
- Runtime performance
    - Smart recompositions
    - Baseline Profiles
    - Comparison with the View system
    - Benchmark Compose
    - Compose profile installation

---

### 15. Tools

#### 15.1 Tools for Compose

#### 15.2 Design

##### 15.2.1 Preview your UI with composable previews

- Define your `@Preview`****
    - Dimensions
    - Dynamic color preview
    - Use with different devices
    - Locale
    - Set background color
    - System UI
    - UI mode
    - `LocalInspectionMode`
- Interact with your `@Preview`****
    - Interactive mode
    - Code navigation and composable outlines
    - Run preview
    - Copy `@Preview` render
- Multiple previews of the same `@Preview` annotation
    - Multipreview templates
    - Create custom multipreview annotations
    - `@Preview` and large data sets
- Limitations and best practices
    - Previews limitations
    - Previews and `ViewModels`****
- Annotation class `@Preview`****

##### 15.2.2 Animation Preview

#### 15.3 Develop

##### 15.3.1 Iterative code development

- Live Edit
    - Get started with Live Edit
    - Troubleshoot Live Edit
    - Limitations of Live Edit
    - Frequently asked questions about Live Edit
- Live Edit of literals (deprecated)
- Apply Changes

##### 15.3.2 Editor actions

- Live templates
- Gutter icons
    - Deploy preview
    - Color picker
    - Image resource picker

#### 15.4 Debug

##### 15.4.1 Layout Inspector

- Get recomposition counts
- Compose semantics

##### 15.4.2 Composition tracing

- Set up for composition tracing
- Take a system trace
- Caveats
    - APK size overhead
    - Accurate timing
- Capture a trace from terminal
    - Add dependencies
    - Generate a record command
    - Capture a trace
    - Open the trace
- Capture a trace with Jetpack Macrobenchmark

#### 15.5 Relay designer and developer tooling

##### 15.5.1 Overview

##### 15.5.2 Install Relay

- Prerequisites
- Install the Relay for Figma plugin
- Install the Relay for Android Studio plugin
- Install the Relay Gradle plugin
- Setup Figma access
- Download and setup the pre-configured project
    - Running the pre-configured project

##### 15.5.3 Set up your Android project

- Create a new Compose project
- Edit module-level Gradle build file

##### 15.5.4 Basic tutorial

###### **15.5.4.1 Overview**

###### **15.5.4.2 Create UI Package in Figma**

- Download pre-configured Figma file
- Create a component
- Create a UI Package
- Share with developer flow

###### **15.5.4.3 Convert the designs to code in Android Studio**

- Import design from Figma
- Build & generate code
- Integrate component & run app

###### **15.5.4.4 Make and propagate design updates**

- Changes in Figma
- Save named version
- Update the component code

###### **15.5.4.5 Content parameters**

- Add a content parameter
- Save named version
- Update the component in Android Studio

##### 15.5.5 Advanced tutorial

###### **15.5.5.1 Overview**

###### **15.5.5.2 Handling design variants**

- Starting point
- Copy Figma example
- Create a UI package
- Save named version
- Download Android Studio project
- Import into Android Studio
- Preview app & component

###### **15.5.5.3 Content parameters**

- Introduction
- Add parameters in Figma
- Save named version
- Update component in Android Studio
- Integrate into app

###### **15.5.5.4 Add interaction handlers to designs**

- Add handlers
- Save named version
- Update component in Android Studio
- Integrate into app

##### 15.5.6 Relay workflow

###### **15.5.6.1 Overview**

- Figma workflow
- Android Studio workflow
- UI Package & Generated Code

###### **15.5.6.2 Create UI Packages**

- UI Packages in Figma
- Create UI Package
- Add a summary
- Remove UI Packaging

###### **15.5.6.3 Add parameters**

- Parameter properties
    - All layers
    - Frame or group layer
    - Text layer
    - Image layer
- Adding parameters
- Rename parameters
- Remove parameters

###### **15.5.6.4 Check errors**

- Example
- Checking error from "Share with developer" screen

###### **15.5.6.5 Share UI Packages**

- Best practices
    - Check for errors and create named versions before sharing
- Sharing Figma Link
    - Sharing all UI Packages in a page
    - Sharing a specific UI package
    - Sharing all UI Packages in a file
    - Share all UI packages in a page with a specific version
- Advanced usage

###### **15.5.6.6 Android Studio workflow**

- Import a UI Package
- UI Package import screen
- UI Package tool window
- Build your Android Project
- Update a UI Package

###### **15.5.6.7 Understand UI Package & Generated Code**

- UI Package
- Removing UI Packages
- Generated code folder structure
- Generated code structure
    - Composables
    - Translated Figma variants and parameters

###### **15.5.6.8 Figma DevMode**

- Read-only limitations

##### 15.5.7 Design-to-code translation details

###### **15.5.7.1 Figma component properties**

- Boolean properties
- Text properties
- Instance swap properties
- Variant properties

###### **15.5.7.2 Children Parameters**

###### **15.5.7.3 Nested package instances**

- Add nested instances and expose nested parameters
- Override properties of nested package instance
- Limitations

###### **15.5.7.4 Vector Graphics**

- Limitations

###### **15.5.7.5 Multiple Styles in Text**

- Limitations

###### **15.5.7.6 Absolute Positioning Within Auto Layout**

- Limitations

###### **15.5.7.7 Fill Color**

- Limitations

###### **15.5.7.8 Effects**

- Limitations

##### 15.5.8 Limitations and troubleshooting

- Figma and translation limitations
    - Supported Figma layer types
    - Unsupported Figma layers and features
    - Unsupported Figma properties
    - Partially supported Figma layers and properties
    - Multiple styles are dropped if passed into text parameter with one style
    - Nested components with same variant properties as parent component fails to compile
    - Font support
- Android Studio troubleshooting
    - I received an error about converting SVG resources on Windows
    - Updates are not imported into Android Studio
    - I receive an error about SVG and Java Runtime when building
    - I receive an error about fonts when building
    - Updating resources outside ui-packages do not force a new build
    - In Android Studio, undoing a deleted UI Package folder may fail
    - Generated code or `ui-packages` folders are missing in Android project browser
    - App themes for child components are not updated
    - UI Package name must start with letter
    - Font padding in Compose does not match Figma

##### 15.5.9 Experimental features

###### **15.5.9.1 Mapping Styles to Compose theme**

- Configuration files for custom translations
- Limitations

###### **15.5.9.2 Map components to existing code**

- Mapping file
- Generate a mapping file
    - Mapping file name
    - Mapping file contents
- Mapped variants

---

### 16. Leverage System Capabilities

#### 16.1 Design Window insets in Compose

- Inset fundamentals
- Insets setup
- Compose APIs
    - Padding modifiers
    - Inset size modifiers
    - Inset consumption
    - Insets and Jetpack Compose phases
- Keyboard IME animations with `WindowInsets`****
- Inset support for Material 3 Components
    - Inset handling composables
    - Override default insets
 
#### 16.2 Cutouts in Compose

- Default case
- Handle cutout information manually
- Best practices
- Test how your content renders with cutouts
---

### 17. Create Widgets

#### 17.1 Jetpack Glance

#### 17.2 Glance setup

- Add Glance dependencies

#### 17.3 Create an app widget with Glance

- Declare the `AppWidget` in the Manifest
- Add the `AppWidgetProviderInfo` metadata
- Define `GlanceAppWidget`****
- Create UI

#### 17.4 Handle user interaction

- Launch an activity
- Launch a service
- Send a broadcast event
- Perform custom actions
    - Run lambda actions
    - Run ActionCallback
- Provide parameters to actions

#### 17.5 Manage and update GlanceAppWidget

- Manage `GlanceAppWidget` state
    - Use application state
- Update `GlanceAppWidget`****

#### 17.6 Build UI with Glance

- Use `Box`, `Column`, and `Row`****
- Use scrollable layouts
- Define the `SizeMode`****
    - `SizeMode.Single`****
    - `SizeMode.Responsive`****
    - `SizeMode.Exact`
- Access resources
- Add compound buttons

#### 17.7 Implement a Glance theme

- Add colors
- Add shapes

#### 17.8 Glance interoperability
