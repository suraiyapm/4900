# DEV GUIDE - BROOKLYN COLLEGE CIS CONNECT

`This is a guide to help any future developers (or anybody) contributing to the maintenance or updating of the CIS Connect website.`

<!-- draft details to elaborate further on:
    -css in customize section not applying to custom written html until converted to block-form
    -custom properties, particularly the color palette, and the sites it is based on and comes from
    -wordpress file structure
    -google calendar api key info, calendar management
    -more regarding CSS overrides from Academic Commons/Restrictive Academica theme: Inspect element to see SPECIFIC class selectors, make stronger selector for CSS using several, some work (some still can't)
    -simple CSS doesn't show up (universal page one) for each page, empty

    -CSS issues, Academic Commons-specific. Academic Commons has several limitations, one primary relevant one being the themes. WordPress has thousands, and Academic Commons is alotted a small subset of those themes for use. To use any external/alternative themes, you would have to contact them directly, as per their documentation, and get the theme approved. Child themes fall under this same umbrella, meaning they cannot be created directly through Academic Commons. For the current theme being used (selected due to it's similarity to the example website chosen by my project supervisor), Academica, a child theme cannot be created, and, unfortunately, there are not a lot of things the custom CSS added can actually alter, due to it not being able to override the way the theme is set. -note JS block format -screenshots --annotated screenshots -->

## Random Specifics

## Getting Started
`This section is mostly the same as the one in the Faculty section, as the account creation process remains the same.`

Welcome to Brooklyn College CIS Connect!

[Click here for information regarding CUNY Academic Commons, straight from the BC Knowledge website.](https://employees.brooklyn.edu/base/cuny-academic-commons/)
>This link explains what CUNY Academic Commons is, along with key features and potential uses and practical application examples!

[Click here for the official getting-started guide!](https://help.commons.gc.cuny.edu/getting-started-with-the-commons/)
>This link covers all you need to know for your initial account activation. Having a campus email address is a requirement, but you can contact the email on the site to request a registration code if you don't have a CUNY email address.

These two links contain a plethora of information regarding these initial topics, along with several screenshots for clarity.

There's also some useful information regarding Commons available at [this](https://guides.cuny.edu/digital-toolkit/exhibits/cuny-academic-commons) CUNY link.

[Here](https://help.commons.gc.cuny.edu/our-tools/) are some features of Commons, with descriptions and additional information if you click the list item links. You can also click [here](https://help.commons.gc.cuny.edu/commons-basics/) for an overview of several topics, each linked with additional information! These include a section for the [Account Settings Tab](https://help.commons.gc.cuny.edu/personal-settings/), with information regarding things like changing your password/email/profile photo, profile visibility, email notifications, and more.


There's a lot of functionality in WordPress, and [this](https://help.commons.gc.cuny.edu/wp-basics/) link provides some great information on the actual WordPress side of things.

`The following portion of this section is not the same as that of the Faculty Guide.`

For future devs, you can click [here](https://help.commons.gc.cuny.edu/) for the CUNY Academic Commons `Help & Support` website.
It may also be worth briefly running through [this page](https://help.commons.gc.cuny.edu/overview/), and consulting it along the development or maintenance process, as it contains invaluable information about Academic Commons website management. It has incredibly useful sections including some about Accessibility, and general vital documentation. The secion `Themes` includes one very, very important piece of information, stating:
> Thousands of themes have been developed for WordPress, and the Commons provides a small subset of those to choose from.
The current theme for the website is set to Academica, a common Academia page theme, but there are others that you're able to preview (before switching), and you can also pretty easily clone a site if you'd like to experiment before making any big changes.
This also means that you can't just use any theme, or random external ones, and if you want to try something external then you have to contact WordPress through the email in the page, and it would have to be approved.
The thing about many of the themes is that they can be quite restrictive and limiting. It can be easy to use them with many presets and defaults, and you can likely go a long way by purely using **Patterns** and just altering the details or replacing images. The parts that get tricky with restrictive themes comes along when you need (or want) to think about CSS or customization. To a certain extent, these things are adjustable, but there are some complications that come up. These complications will be discussed further in the `CSS` section.


### Calendars

`This section of the guide starts out the same as the section in the Faculty Guide, but with the added API key details.`

`CIS Events` is the current calendar added for the website (which you can find from clicking Dashboard>Calendars). From clicking that, you can edit some settings, such as **Calendar Start**, **Earliest Event**, and **Latest Event**.

![alt text](<media/Guide Photos/Calendar1.png>)

It is currently set to:
- Start Day: Today
- Earliest Event: 2 Months before start date
- Latest Event: 1 Year after start date

If you click the **Appearance** tab on the left, you can alter some visual details, such as the default calendar span, colors, etc.

If you click the **Google Calendar** tab, you'll see the Calendar ID for the calendar you selected in the list from Dashboard>Calendars. `CIS Events` is based on a Google Calendar, and the ID ends in `@import.calendar.google.com`. For adding calendars, you'd want to find that ID from your own public Google calendar.

Under **Advanced**, you can find things such as time format, date format, timezone, and a few other similarly less frequently used details. It also includes the **Refresh Interval**, which is currently set to **2 hours**.

Back on the Dashboard menu, if you click `Calendars>Settings`, you can find the Google API Key. As these are not meant to be shared, it would be ideal for one specific faculty member or developer to obtain a new one for future use.

The **Simple Calendar** plugin documentation includes a useful guide for how to go about obtaining one of these API keys. Click [here](https://docs.simplecalendar.io/google-api-key/?utm_source=inside-plugin&utm_medium=link&utm_campaign=core-plugin&utm_content=settings-link) to view it!

### CSS

Theme restrictive-ness leads to a lot of complications with applying Custom CSS.

First, though, you can head to `Dashboard>Appearance>Simple CSS" to view, alter, and save the custom CSS for the website. I've been keeping track of it through GitHub (to also type it more comfortably from VS Code), but then I'd Copy/Paste into this Simple CSS section in the Dashboard (or site customization/editing screens, on the left). From the regular site editor, or from this screen from the dashboard if you click Customize, you can live preview the CSS.

Now, regarding the restrictive nature of some WordPress themes, and definitely Academica, it seems that writing up regular, more modular and clean CSS classes to apply to different elements (in the editor menu on the right, for Classes) doesn't usually work due to overrides. In order to combat this, you have to make more aggressive, specific `selectors`.

Please excuse the slightly less ideal state of the CSS, as I ended up having to change a lot in order to implement these aggressive selectors, and haven't removed some of the separate classes I have previously written out.

Custom properties/variables, luckily, work fine for the Simple CSS, so I've written up several custom properties for ease of altering, and for maintaining a somewhat consistent color palette. This color palette is primarily based on the [CUNY Official Colors](https://www.cuny.edu/about/administration/offices/communications-marketing/university-identity/colors/), and the Brooklyn College maroon and gold. These can be altered as you wish, or you can add as many custom properties as you'd like, that don't have to be based on these same things.

For writing the stronger selectors, I'd strongly recommend opening up your browser `Inspector` with F12 (or right-click>Inspect). That way, you can see what specific classes and IDs different elements have, so that you can more easily target them. You can also try typing in "page-id" to search, and you may be able to find the page ID class for whichever page you're actively editing. That way, you can include/exclude specific pages from CSS specifications as you see fit. Near the top of the CSS and under the custom properties sections, I tried to include the Page IDs for each page, in a comment. I've labeled the dot grid background sections and such, as well. If faculty or devs would prefer a more clean, classic WordPress Academica appearance for the site, simply remove all the CSS in the section and everything would appear as the theme intended, edited only from the actual page editors. Nothings major was written into the CSS, so nothing major would change, and all functionalities should remain exactly the same (except, certain elements would no longer have a hover effect for slightly enhanced emphasis and reading clarity).

### Misc. Details!

`Here are some quick, individual little notes for things that may not require their own section just yet.`

One cool little WordPress detail involves a specific plugin type. There are many plugins that you can select from, to apply to the website/activate, but two specific active plugins are the Accessibility Checker and WP Accessibility. These plugins will appear on the site during editing as little symbols indicating when something is unclear or could potentially be improved. For instance, if images are missing alt text, or if certain colors may be difficult to read, these plugins would pop up as a small round symbol with a question mark over that element, and it'll tell you what the issue might be (as well as how to potentially fix it). These plugins help to ensure readability across the site pages, and help us keep in mind how to keep the site as accessible as possible for as many people as possible (suggestions for visually impaired accessibility, etc.).

Another random detail is the outline view in the left menu of the site editor. This menu makes editing the site much, much easier, and makes it easy to work with element groups and move things around.

Random GitHub details: I've been naming the Guide photos as the Section they're for, and the number image they are from that section (the order they appear in). This can be changed, it's just how it's currently set up.

#### Some Possible Future Paths! (Or Things I'd Personally Try with More Time)

- `Alternate Platform Optimization:` The site is functional and alright on mobile platforms, but I haven't focused on those during editing, so they can probably be improved and optimized! The site editor has a button to shift views by platform, including showing the mobile view.
- `FSE:` Full Site Editing is available with [specific Commons themes](https://help.commons.gc.cuny.edu/full-site-editing/), and this could be fun to experiment with. It can be a less restrictive theme option!