# SignInForm

I’d like to break down the things we’re going to have in the component. This will help as it will make the code we write much clearer.

We have 4 smaller screens/boxes inside the main component (the .container):

- The Sign In form
- The Sign Up form
- The Sign In overlay
- The Sign Up overlay

Also, at one moment in time you can see either:

- The Sign In form alongside the Sign Up overlay
- The Sign Up form alongside the Sign In overlay

In the overlay panels, we have some text and a button. By clicking it you will bring up the other combination of screens and vice-versa

# Overlay Animation

We have the following layers for the overlay component:

**The overlay-container** — this will display the visible area (more on this below) at a certain moment in time. It has a width of 50% of the total container's width.

**The overlay** — this div has a double width size (200%) so it's taking the full width of the main container. (200% * 50%= 100%. The 50% is from the .overlay-container above).

**The overlay-panels** — are the divs which are holding the actual content (the text and the button) we see on the screen. They both have a position of absolute. We can position them wherever we want in the .overlay component. One of the panels is positioned to the left and the other one is positioned to the right. Both having a width of 50% of the .overlay component.

“Why do we need 3 layers?” you might ask… Well, let’s see how it would look like without the first layer:

In the picture above you can see that both of the panels are “visible”, which is not what we want. This is why we’re adding the .overlay-container to act like a “focus area”. This allows us to hide the panel which is overflowing, or which is out of its boundaries. This is why we needed the .overlay to be twice as big as the .overlay-container. By moving around the .overlay-container, which also has a position of absolute, we can hide or show which panel we want.


# Forms Animations

These aren’t difficult to understand at all. Basically, we have again two containers — the .form-containers. Each has a width of 50% and a position - absolute. We move both of them at the same time from left to right. When they get behind the .overlay-container from above (while these are moving) we quickly change the z-index value. The Sign Up form (for example) will move on top of the Sign In form, and vice-versa.

# HTML 

For the basic skeleton, the main div has a class of **.container** and also an id of **.container** because we want to target this element in the Javascript.

# Sign Up Form and Sign In Form

We also have a few classes on each div:

- The .form-container class will contain the CSS which is duplicated for both the .sign-in-container and .sign-up-container classes

- The 2 different classes (mentioned above) will contain the CSS which is different.

This way we avoid having to write the same CSS code twice and we use the power of being able to add multiple classes.

You might have also noticed that the i tags have some classes. These are because we are using FontAwesome for the icons. Read more about them on their website.

# The Overlay Container

Same as above, we have a common class .overlay-panel and two different classes: .overlay-left and .overlay-right. Also, we have ids for the buttons as we're going to add an onClick eventListener for both of them in the JavaScript.

# Javascript

As explained above, we add the event listeners. When the buttons are clicked we add or remove the .right-panel-active class. This class will be used to style the subcomponents differently as we have two screens.

# CSS

Few things to note here:

- We are styling the elements directly (h1, p, a). Usually, you wouldn’t do that as it might get mixed up with other styles, so it’s good to add a class to each of them. But for this example it’s working ok because we only have these elements on the page.

- We have a little transition on the button. When it's clicked, the active state is triggered so we make it a little smaller. Nice and simple clicking effect. 

- The form is a flex container as we want to center everything within it, and it's easy to do that with flexbox. You'll see below that it's used a few more times.

# CSS Container

- Relative positioned because we'll have absolute positioned children elements (explained why, above).

- Overflow is set to hidden because we have set a border-radius and we don't want the child elements to break this radius and be displayed outside of the .container.

# CSS Form Container

- The animation (show) which is responsible for changing the z-index of the .form-containers as discussed above. We go by having the z-index 1 from 0-49.99% and having it at 5 from 50-100%. These ranges are used because we want them to change fast.

- We use the .right-panel-active class to move around the .form-containers when the buttons are clicked.

# The Overlay

- The .overlay has a gradient background, I used UI Gradients to get it;

- .overlay-left and .container.right-panel-active .overlay-right have a -20% and 20% translation on the X-axis. This is because I wanted to add a little effect to the text when it's displayed as if it's coming from outside 