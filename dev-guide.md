# DEV GUIDE - BROOKLYN COLLEGE CIS CONNECT

This is a guide to help any future developers (or anybody) contributing to the maintenance or updating of the CIS Connect website.

draft details to elaborate further on:
    -css in customize section not applying to custom written html until converted to block-form
    -custom properties, particularly the color palette, and the sites it is based on and comes from
    -wordpress file structure
    -google calendar api key info, calendar management

    -CSS issues, Academic Commons-specific. Academic Commons has several limitations, one primary relevant one being the themes. WordPress has thousands, and Academic Commons is alotted a small subset of those themes for use. To use any external/alternative themes, you would have to contact them directly, as per their documentation, and get the theme approved. Child themes fall under this same umbrella, meaning they cannot be created directly through Academic Commons. For the current theme being used (selected due to it's similarity to the example website chosen by my project supervisor), Academica, a child theme cannot be created, and, unfortunately, there are not a lot of things the custom CSS added can actually alter, due to it not being able to override the way the theme is set. -note JS block format -screenshots --annotated screenshots