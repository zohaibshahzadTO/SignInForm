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



