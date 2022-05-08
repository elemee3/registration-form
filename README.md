## About

The Pet Owner Registration page is a simple form that collects data in this front end application, and sends it to an API for consumption. Here we have a Vue.js project that utilizes form inputs and conditional rendering to collection pertinent information about a pet.

This repo is intended to be used in conjunction with the back end application, [registration-form-back](https://github.com/elemee3/registration-form-back).

## Requirements

This project requires the following:
  - node 16.13
  - npm 8.3
  - vuejs 3
  - axios 0.27

This project was developed on Ubuntu 20.04. Instructions will support Linux/Unix/MacOS environments. Windows support is not guaranteed at this time.

## Installation

1. Ensure proper installation of all required software listed above
2. Clone this repository via HTTPS
3. `cd` into the repository in the terminal
4. Run `npm install`
5. Run `npm run dev`
6. See that the development server has started
7. Assuming the back end application is ready to accept them, the front end is now ready to send requests from the UI at http://localhost:3000

## Design & Architectural Decisions

Due to the nature of this project including time constraints and unknown future states of the app, there were multiple opportunities to make design and architectural decisions. In addition there are of course many options for improving this app.

- My first draft of wire framing this project went fairly quickly, as it is a relatively simple page to style. I started with bare bones elements and flex box for quick arrangements and simple responsive capacity. As I added in CSS styling, it occurred to me that a few components could be enhanced, simplified, standardized by using Bootstrap. I did not end up making the switch for the sake of time, but if I had, I would have liked to use it on the navigation bar, and on the buttons.

- Another practice I would have customarily included is requesting official assets. For example the logos, images, breed options, etc. I did not consider those details to be particularly relevant to the purpose of this assignment, though in a client facing setting I realize that the consistency of branding and styling holds great weight.

- There were some elements displayed on the mock ups that were not mentioned in the requirements, notably the Help and Save and Finish Later options in the header. I opted to include these visually in the layout, but leave them without functionality. I could see the Help button opening a modal with support contact information, or even a live chat. Save and Finish Later could send an alert much like the 'Save Pet' button does, though it would be just as ineffectual at this time.

- I would have loved to make the paw print image dynamic, if I had the time. I think it would look really great to have them all start gray, then turn green as the user progresses through the form. To accomplish this I would find or request a paw print .svg, then conditionally add the color styling based on how many of the form element models are populated.
