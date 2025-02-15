# GSoC 2021 Ideas

## Project Ideas

   * [Port Sugar and core activities to Python 3](#port-sugar-and-core-activities-to-python-3)
   * [Improve and maintain 15 Sugar activities](#improve-and-maintain-15-sugar-activities)
   * [Music Blocks Block Graphics Refactoring](#music-blocks-block-graphics-refactoring)
   * [Music Blocks Menus and Palettes](#music-blocks-menus-and-palettes)
   * [Music Blocks Project Blocks Reorganization](#music-blocks-project-blocks-reorganization)
   * [Music Blocks Debugging Aids](#music-blocks-debugging-aids)
   * [Sugarizer Measure activity](#sugarizer-measure-activity)
   * [Sugarizer Story activity](#sugarizer-story-activity)
   * [Sugarizer Security and Availability](#sugarizer-security-and-availability)
   * [Port ASLOv1 to PHP8](#port-aslov1-to-php8)
   * [Human Interface Guidelines Redesign for Sugar](#human-interface-guidelines-redesign-for-sugar)

[Administrative notes](#administrative-notes)

------------

## Port Sugar and core activities to Python 3

**Prerequisites**<br>
 - Experience with Python
 - Experience with porting telepathy bindings
 - Strong experience with
   [Sugar Desktop](https://github.com/sugarlabs/sugar) and activities

**Description**<br> Support for Python 2 was withdrawn by the Python
Foundation, so we need to finish the move to Python 3.  The move was
started in GSoC 2018, and continued in GSoC 2020, but there is still
work to be done.  Sugar 0.116 runs on Python 2 or Python 3.  Core
activities run on Python 3.  Many other activities run on Python 2.
Many regressions have been seen as a result of code not being tested.

We have a [Python 3 Porting
Guide](https://github.com/sugarlabs/sugar-docs/blob/master/src/python-porting-guide.md)
which describes the process for activities.

**Project Task Checklist**<br>
 - Review the Sugar source code changes since 0.112 that were made for porting to Python 3,
 - Design tests and iterate until the tests have sufficient [coverage](https://github.com/sugarlabs/sugar-docs/blob/master/src/python-coverage-guide.md) for the code changes identified about,
 - Fix regressions in Sugar, the Toolkit, and the Datastore,
 - For affected activities, port Telepathy bindings to TelepathyGLib, see [Port to TelepathyGLib](https://github.com/orgs/sugarlabs/projects/4).
 - For affected activities, port to the latest Sugargame or CollabWrapper library,
 - Port activities to Python 3, fixing any problems that prevent them from being ported or used,

See GitHub Project [Port to Python 3 via
six](https://github.com/orgs/sugarlabs/projects/1) for some open
issues and pull requests.  Most activities do not have issues.  Some
activities have problems that prevent them from being ported.

The Telepathy library is used by some activities for network
collaboration between Sugar users.  The library does not have static
bindings for Python 3, so porting Telepathy to the PyGObject binding
is a prerequisite, see GitHub Project [Port to
TelepathyGLib](https://github.com/orgs/sugarlabs/projects/4).

**Coding Mentors**<br>
[Jui Pradhan](https://github.com/JuiP), [Srevin Saju](https://github.com/srevinsaju), [Saumya Mishra](https://github.com/Saumya-Mishra9129), [Ibiam Chihurumnaya](https://github.com/chimosky/)

**Assisting Mentors**<br>
To be added.

------------

## Improve and maintain 15 Sugar activities

**Prerequisites**<br>
 - Experience with Python
 - Strong experience with Sugar activities
 - Experience with maintaining activities on ASLO and ASLO-v4

**Description**<br>
Sugar has a lot of activities, with 250+ on GitHub, and more
elsewhere. These have scope for improvement; bugs,
features, updated human translations, and release.  This project will involve
working on **at least 15** activities to improve them. Students can choose
activities on their own, and are encouraged to select activities which
are either a part of Fructose or have a strong pedagogical value. To
understand how to locate and work on activities, see our guide to
[Modifying
Activities](https://github.com/sugarlabs/sugar-docs/blob/master/src/contributing.md#modifying-activities)

In their proposal, students may mention _some_ of the issues they will
work on.  Any new feature suggestion should be discussed on GitHub
Issues or on the mailing list before being added to a proposal.

Since there are a lot of activities to work on, **more than one instance
of this project may be selected**.

**Suggested Issues to work on:**<br>
 - jukebox-activity: [#22 Add collaboration for sharing playlist items](https://github.com/sugarlabs/jukebox-activity/issues/22)

Other issues will have been raised since.

Suggesting or adding features, fixing bugs, or releasing activities
will help you to gain experience

**Coding Mentors**<br>
[Jui Pradhan](https://github.com/JuiP), [Srevin Saju](https://github.com/srevinsaju), [Saumya Mishra](https://github.com/Saumya-Mishra9129), [Ibiam Chihurumnaya](https://github.com/chimosky/)

**Assisting Mentors**<br>
To be added.

--------------

## Human Interface Guidelines Redesign for Sugar
**Prerequisites**<br>
- Experience with UX design
- Extensive experience with Python and GTK3
- Experience with Sugar activities/toolkit
- Experience with user interface and graphics design (and SVG)

**Description**<br>
Sugar’s use of color and icons (described in detail here [HIG
color](https://wiki.sugarlabs.org/go/Human_Interface_Guidelines/The_Sugar_Interface/Colors)
and [HIG icons](https://wiki.sugarlabs.org/go/Human_Interface_Guidelines/The_Sugar_Interface/Icons))
is functional but a bit tired when compared to modern desktops and
mobile systems. Sugar uses monochrome icons. The reason for monochrome icons
and high contrasting colour choices was to support reflective displays that
cannot show colour. In turn that was because backlights could not be made
bright enough for use in high ambient light, without risking large amounts
of incidental heat. Since then backlights are more efficient (less heat) and
much brighter (in nits). Now that the reflective display technology has all
but been abandoned, the requirement is removed, and so Sugar can go for a
UI design that is more colourful.

This project is about redesigning the use of color in Sugar in order
to enable full-color icons for both the desktop itself and activities.
This would require rewriting the [Human Interface Guidelines](https://wiki.sugarlabs.org/go/Human_Interface_Guidelines).

The primary role of color in the current icon design is to;
 - Indicate whether or not an activity has been used
 - Indicate whether or not an activity is being shared with another
   Sugar user (the colors of the person who launches the activity show
   up on the desktops of the people who join the activity.)

Fortunately, Sugar also support a mechanism for putting badges on
icons. An example is in the neighborhood view, where badges are used
to indicate which access points are active (See
[networkviews.py](https://github.com/sugarlabs/sugar/blob/master/src/jarabe/desktop/networkviews.py)).

We could use badges (See
[icon.py](https://github.com/sugarlabs/sugar-toolkit-gtk3/blob/master/src/sugar3/graphics/icon.py#L49))
to replace the functionality of color described above: for example, an
XO badge to indicate an activity has been used. And the color of that
badge could indicate collaboration. This would free up the icon itself
to take on any colors deemed suitable by the activity designer.

**Project Task:**<br>
 - [ ] Improve icons, assets for [sugar-artwork](https://github.com/sugarlabs/sugar-artwork)
       as well as the [Fructose Set Activities](https://wiki.sugarlabs.org/go/Taxonomy). 
 - [ ] Rewrite the Human Interface Guidelines. Design a new idea for
       the Sugar UX and UI.
 - [ ] Add color functionality to the badges;
 - [ ] Add badges in every instance where we currently use color: the
       desktop, the journal, the neighborhood view and the activity
       toolbar;
 - [ ] Work with the design team to come up with new color icons for
       all of the core Sugar toolbars, activities and activity toolbars

**Optional Tasks:**<br>
 - [ ] Improve the Sugar Shell desktop UI, such as adding Animations 
 - [ ] Port Sugar Toolkit to GTK4 (GTK4 has extensive support for animations)
 - [ ] Complete the [Corner Layout Feature](https://github.com/sugarlabs/sugar/pull/740)
       which is an open pull request, not finished yet.
 - [ ] Complete adding the [Screenshot Popup](https://github.com/sugarlabs/sugar/pull/675)
       feature, which also remains as an open pull request.

**Suggested issues to work on:**<br>
 - There are not any issues specific to this project, but working on
   some open bugs would be a good place to start in understanding the
   code base.

**Coding Mentors**<br>
[Ibiam Chihurumnaya](https://github.com/chimosky)

**Assisting Mentors**<br>
[Peace Ojemeh](https://github.com/perriefidelis)


------------

## Music Blocks Block Graphics Refactoring

**Prerequisites**<br>
 - Experience with React (TypeScript)
 - Experience with graphic design
 - Strong experience with SVG

**Description**<br> We are refactoring Music Blocks. This gives us an opportunity to revisit a number of UX issues, including the design and implementation of the block graphics. One thing that will not change is that we will use SVG for the block graphics, but other than that, we have the opportunity to rethink bot how blocks look (in particular, how they interlock and how they expand/resize) as well as the corresponding code we use to generate the block artwork SVG. Finally, it would be great to use CSS to define many of the block attributes, e.g., color and other styling features, rather than having everything hardcoded in the SVG. (Modern SVG supports this.)

**Project Task Checklist**<br>
 - Familiarize yourself with the current implementation [blockfactory](https://github.com/sugarlabs/musicblocks/blob/master/js/blockfactory.js)
 - Come up with a framework for how the block interconnections will work -- we'd like to make it more obvious how blocks interlock and also use the interlocking to help define the schemas associated with some block logic.
 - Design the class structure for the new block rendering approach.
 - Implement all of the above in React (TypeScript).

**Coding Mentors**<br>
[Walter Bender](https://github.com/walterbender),
[Anindya Kundu](https://github.com/meganindya).

**Assisting Mentors**<br>
[Peace Ojemeh](https://github.com/perriefidelis)

------------

## Music Blocks Menus and Palettes

**Prerequisites**<br>
 - Experience with React (TypeScript).
 - Experience with user interface design
 - Experience with Materials

**Description**<br> We are refactoring Music Blocks. This gives us an opportunity to revisit a number of UX issues, including the design and implementation of the menu bars and block palettes. We have some sketches as to what it might look like, but your ideas are most welcome.

**Project Task Checklist**<br>
 - Familiarize yourself with the current implementations [toolbars](https://github.com/sugarlabs/musicblocks/blob/master/js/toolbar.js) [palettes](https://github.com/sugarlabs/musicblocks/blob/master/js/palette.js)
 - Familiarize yourself with the Music Blocks v4 sketches [wireframe](https://github.com/sugarlabs/musicblocks-v4/discussions/5)
 - Come up with a framework for the new toolbars and palettes
 - Design the class structure for the toolbars
 - Design the class structure for the palettes
 - Implement all of the above in React (TypeScript).

**Coding Mentors**<br>
[Anindya Kundu](https://github.com/meganindya),
[Walter Bender](https://github.com/walterbender).

**Assisting Mentors**<br>
[Peace Ojemeh](https://github.com/perriefidelis)

------------

## Music Blocks Project Blocks Reorganization

**Prerequisites**
 - Experience with React (TypeScript).
 - Experience with user interface design
 - Experience with HTML Canvas element, SVG

**Description**<br> We are refactoring Music Blocks. This gives us an opportunity to revisit a number of UX issues, including the design and implementation of the how we present the blocks of a Music Blocks project on the canvas. In the current implementation, users can place blocks (and block stacks) at any arbitrary position on the canvas. Very quickly, it can get overwhelming when there are quite a few blocks lying around. Also, those can overlap each other, resulting in a poor experience.

The goal of this project is to come up with design ideas to handle this issue, and implement them. 'Clamp' blocks have a collapse button which metaphorically folds the nested content, sort of like a feature modern code editors provide. Perhaps, only a fixed number of top-level 'clamp' blocks should be allowed to remain expanded. In addition, columns (like swim lanes) could be created side by side; blocks would go like a list in each lane whose order can be rearranged.

We would want the design to encourage the user towards making clean projects. However, enforcing contraints might not be a good idea; perhaps, these could be guides. This could exist as a 'high-shelf' feature for experienced users. The aforementioned are just hints &mdash; your ideas are most welcome.

**Project Task Checklist**<br>
 - Familiarize yourself with the current implementation
 - Come up with a framework for better project structuring
 - Design a flexible guidance layer on top of the canvas
 - Implement the above in React (TypeScript).

**Coding Mentors**<br>
[Anindya Kundu](https://github.com/meganindya),
[Walter Bender](https://github.com/walterbender).

**Assisting Mentors**<br>
[Peace Ojemeh](https://github.com/perriefidelis)

------------

## Music Blocks Debugging Aids

**Prerequisites**<br>
 - Experience with React (TypeScript).
 - Experience with user interface design

**Description**<br> We are refactoring Music Blocks. This gives us an opportunity to revisit a number of UX issues, including the design and implementation of the various tools we provide for debugging. We have some ideas, such as changing the appearing of a block that is throwing an error, better handling of break points, visualizing program status, etc., but your ideas are most welcome.

**Project Task Checklist**<br>
 - Familiarize yourself with the current debugging features [Debugging](https://github.com/sugarlabs/musicblocks/blob/master/Debugging.md)
 - Come up with a framework for how debugging might work in Music Blocks v4
 - Implement your ideas -- some coordination will be needed both with the [Music Blocks Block Graphics Refactoring](#music-blocks-block-graphics-refactoring) project and the language interpreter.

**Coding Mentors**<br>
[Walter Bender](https://github.com/walterbender).
[Anindya Kundu](https://github.com/meganindya),

**Assisting Mentors**<br>
None.

------------

## Port ASLOv1 to PHP8

**Prerequisites**<br>
 - Experience with PHP
 - Ability to test aslo-v1 against multiple versions of PHP
 - Experience with CakePHP (not required, but preferred)

**Description**<br> ASLO, which is expanded to Activities (dot) Sugar Labs (dot) org is 
[Sugar's Activity Library](https://wiki.sugarlabs.org/go/Activities) created primarily for Python 2 Activities.
ASLOv1, written in PHP 5, is accessible at [activities.sugarlabs.org](http://activities.sugarlabs.org). 
PHP 5 has reached [its 'end-of-life'](https://www.php.net/supported-versions.php) on January 1st 2019. ASLO v1 uses 
[Remora](https://wiki.mozilla.org/Update:Remora). This is however, no longer maintained. 
It is important to migrate to a newer version, such as PHP 8 (preferred)
or PHP7. 

The source code for ASLO-v1 is available here: [sugarlabs/aslo](https://github.com/sugarlabs/aslo).
Along with the source code, the [Sugar Labs Wiki page for ASLO](https://wiki.sugarlabs.org/go/Service/activities)
is also an inexhaustible resource to help developers get started to ASLO-v1


**Project Task Checklist**<br>
 - [ ] Port ASLO v1 and its dependencies to PHP 8
 - [ ] Make sure that ASLO v1 works as intended even after the port to PHP 8
 
**Suggested Issues**<br>
- [ ] Automatically redirect to [v4.activities.sugarlabs.org](https://v4.activities.sugarlabs.org)
      based on the User Agent [#21](https://github.com/sugarlabs/aslo/issues/21).
- [ ] Fix insecure login [#5](https://github.com/sugarlabs/aslo/issues/5)
- [ ] Fix incorrect mimetype on downloads [#13](https://github.com/sugarlabs/aslo/issues/13)
- [ ] Show supported versions [#4](https://github.com/sugarlabs/aslo/issues/4)
 
**Coding Mentors**<br>
[Srevin Saju](https://github.com/srevinsaju)
[Ibiam Chihurumnaya](https://github.com/chimosky)

**Assisting Mentors**<br>
To be added.

------------

## Sugarizer Measure activity
Mentor: [Lionel Laské](https://github.com/llaske),
Backup mentor: [Ashish Aggarwal](https://github.com/ashish0910)

**Prerequisites**<br>

 * Experience with JavaScript/HTML5 development
 * Experience with Vue.js framework development
 * Experience with Android and/or iOS development using  Cordova
* Basic knowledge of audio concepts

**Description**<br>Measure activity is an activity written for Sugar and available [here](https://activities.sugarlabs.org/en/sugar/addon/4197).The Measure activity draws a picture of the sound heard by the internal microphone or of the signal present on the microphone socket. More specifically it draws a graph of this input versus time, the input is on the vertical axis and time is on the horizontal axis. That is, the activity functions like a machine called an oscilloscope.
<br>The objective of this project is to develop a new Sugarizer Measure activity equivalent to the Sugar Measure activity.

![](assets/measure_sugar.png)

<br>A major complexity to implement this activity is to support Android/iOS platform. On these platforms, direct HTML5 audio capture is not possible so audio input should be captured using a Cordova Plugin that have to be identify.

<br>The detailed activity feature and implementation will be discussed with the project mentor but here is a non-exhaustive list of inspiration:

- [Sugar Measure activity](https://help.sugarlabs.org/measure.html)
- [Oscilloscope.js](https://sambego.github.io/oscilloscope.js/)
- [Audio oscilloscope](https://github.com/mathiasvr/audio-oscilloscope)
- [Virtual oscilloscope](https://academo.org/demos/virtual-oscilloscope/)
- [Cordova Plugin AudioInput](https://github.com/edimuj/cordova-plugin-audioinput)
- [An incomplete PR with a Measure activity for Sugarizer](https://github.com/llaske/sugarizer/pull/708 )


**Project Tasks**

These new activity should provide unique Sugarizer features:

- Sugarizer look & feel: use of Sugar toolbar and palette
- Sugarizer storage: load/save context into the Journal
- Network integration: integrate Sugarizer presence to share the activity on the network so that multiple users could play together
- Responsive: content should adapt to any screen size, a fullscreen button should allow to mask the toolbar for smaller screens
- Multi-device support: should work on any browser (Chrome, Firefox, Safari) and any platform (Android, iOS, Windows, Linux, MacOS) supported by Sugarizer
- Tutorial: an integrated documentation should be integrated to explain each feature of the activity

As with other Sugarizer activities, the new activity should be written using JavaScript and Sugar-Web library. The activity should be written using the Vue.js framework.

**First steps to start:**

- Complete the [Sugarizer Vue.js activity development tutorial](https://github.com/llaske/sugarizer/blob/dev/docs/tutorial/VueJS/tutorial.md)
- Create a Sugarizer environment to be able to generate Sugarizer for Android/iOS, for example by using [Sugarizer APK Builder](https://github.com/llaske/sugarizer-apkbuilder)
- Test and suggest Cordova Plugin that could be use for the development
- Explore the list of inspiration provided above
- Propose UI and features for this activity

**Coding Mentors**<br>
[Lionel Laské](https://github.com/llaske), [Ashish Aggarwal](https://github.com/ashish0910)

**Assisting Mentors**<br>
None.

------------


## Sugarizer Story activity
Mentor: [Ashish Aggarwal](https://github.com/ashish0910),
Backup mentor: [Lionel Laské](https://github.com/llaske)

**Prerequisites**<br>

 * Experience with JavaScript/HTML5 development
 * Experience with Vue.js framework development
 * Experience with Android and/or iOS development using  Cordova

**Description**<br>Story is an activity written for Sugar and available [here](https://activities.sugarlabs.org/en/sugar/addon/4565). The Story Activity uses images to prompt a learner to tell a story. The learner should try to tell a story that ties the images together into a comprehensive narrative.
<br>The objective of this project is to develop a new Sugarizer Story activity equivalent to the Sugar Story activity.

![](assets/story_sugar.png)

<br>One complexity to implement this activity is to handle sound recording. Sound capture is possible using HTML5 feature but is not compatible with Android/iOS where a Cordova Plugin should be use. Once captured the sound should also be able to be played by the activity.

<br>The detailed activity feature and implementation will be discussed with the project mentor but here is a non-exhaustive list of inspiration:

- [Sugar Story activity](https://help.sugarlabs.org/story.html)
- [Record activity](https://github.com/llaske/sugarizer/tree/dev/activities/Record.activity) to learn how to handle sound recording for each platform
- [Abecedarium journal integration](https://github.com/llaske/sugarizer/blob/master/lib/sugar-web/graphics/journalchooser.js#L342) to learn how to get images coming from Abecedarium database


**Project Tasks**

These new activity should provide unique Sugarizer features:

- Sugarizer look & feel: use of Sugar toolbar and palette
- Sugarizer storage: load/save context into the Journal
- Network integration: integrate Sugarizer presence to share the activity on the network so that multiple users could play together
- Responsive: content should adapt to any screen size, a fullscreen button should allow to mask the toolbar for smaller screens
- Multi-device support: should work on any browser (Chrome, Firefox, Safari) and any platform (Android, iOS, Windows, Linux, MacOS) supported by Sugarizer
- Tutorial: an integrated documentation should be integrated to explain each feature of the activity

As with other Sugarizer activities, the new activity should be written using JavaScript and Sugar-Web library. The activity should be written using the Vue.js framework.

**First steps to start:**

- Complete the [Sugarizer Vue.js activity development tutorial](https://github.com/llaske/sugarizer/blob/dev/docs/tutorial/VueJS/tutorial.md)
- Create a Sugarizer environment to be able to generate Sugarizer for Android/iOS, for example by using [Sugarizer APK Builder](https://github.com/llaske/sugarizer-apkbuilder)
- Explore the code of Record activity to understand how sound recording could be done
- Explore the list of inspiration provided above
- Propose UI and features for this activity

**Coding Mentors**<br>
[Lionel Laské](https://github.com/llaske), [Ashish Aggarwal](https://github.com/ashish0910)

**Assisting Mentors**<br>
None.

------------

## Sugarizer Security and Availability

**Prerequisites**<br>
 * Experience with JavaScript/HTML5 development
 * Experience with Node.js development
 * Knowlegde of good security practices
 * Knowlegde of high availability concepts

**Description**<br>Thanks to former GSoC Projects, Sugarizer can easily be deployed on Kubernetes clusters to meet some users deployment expectations.
<br>The objective of this project is to keep Sugarizer growing by enhancing two core concepts for our deployments: **Security** and **Availability**.

**Project Tasks**

- Learn about 2FA and TOTP code generation
- Familiarize yourself with Sugarizer, the Sugarizer School Portal, the Sugarizer Dashboard.
- Fix current issues/features request https://github.com/NikhilM98/sugarizer-school-portal-server/issues (and other to come)
- Update package/chart versions for Sugarizer School Portal.
- Add an TOTP registration feature to Sugarizer School Portal to enhance user's security.
- Add an TOTP registration feature to the Sugarizer Dashboard to enhance user's security.
- Familiarize yourself with Sugarizer collaborative features.
- Move "Presence" our Websocket based communication channel to High Availability by switching ram storage to Redis cache. 
- Bonus: Allow Hardware keys to be used to replace TOTP (example: Yubikey 5)

**First steps to start:**

- Follow the tutorial to deploy [Sugarizer Server](https://github.com/llaske/sugarizer-server)
- Learn about [2FA](https://authy.com/what-is-2fa/), try to generate some codes using [Sample library](https://www.npmjs.com/package/totp-generator) and try to validate them using Authy, Google Authenticator or any Auth app you like.
- Explore how users are managed in **Sugarizer Server** and try to add fields to manage 2FA.
- Implement the actual 2FA!

**Coding Mentors**<br>
[Michaël Ohayon](https://github.com/mikklfr), [Nikhil Mehra](https://github.com/NikhilM98)

**Assisting Mentors**<br>
None.

------------

# Administrative notes

Above are a list of ideas we've planned for GSoC 2021 projects.
If you have any ideas which can be useful to us, but are not in the
list, we'd love to hear from you.  You need not be a potential
student or a mentor to suggest ideas.

   * [Criteria for Ideas](#criteria-for-ideas)
   * [Coding Mentors](#coding-mentors)
   * [Assisting Mentors](#assisting-mentors)
   * [Everyone Else](#everyone-else)
   * [Suggested Issues](#suggested-issues)

## Criteria for Ideas
1. Does it fill an empty pedagogy niche in the activity set for Sugar
   or Sugarizer,
2. Does it increase quality of our software products (Sugar, activities,
   Music Blocks, or Sugarizer),
3. Does it _not_ involve any project infrastructure, e.g. not another
   app store, web site, or developer landing page,
4. Do we have a developer _now_ who would be willing and able to do it
   if a student was not available, and who can _promise_ to do it if a
   student is not selected; these are shown as a _coding mentor_,

## Coding Mentors
For each idea, we must have offers from one or more _coding mentors_
willing and able to assist students with coding questions.

Requirements for a _coding mentor_ are a demonstrated coding ability
in the form of contributions of code to Sugar Labs.

Mentors for a project will be assigned after proposals are received.

## Assisting Mentors
For each idea, we may have offers from mentors _who do not code_
willing to assist students in various other ways, such as gathering
requirements, visual design, testing, and deployment; these are shown
as an _assisting mentor_.

The only requirement for an _assisting mentor_ is _knowledge of the
project_.

Mentors for a project will be assigned after proposals are received.

## Everyone Else
Everyone else in Sugar Labs may also be involved with these projects, through mailing lists, Wiki, and GitHub.

The difference between a _mentor_ and _everyone else_, is that a
_mentor_ is obliged to respond when a student has a question, even if
the answer is "I don't know."

When a _mentor_ receives a question for which the best forum is
_everyone else_, then they are to respectively redirect the student to
ask _everyone else_.  See
[Be flexible](https://github.com/sugarlabs/sugar-docs/blob/master/src/CODE_OF_CONDUCT.md#be-flexible)
and
[When you are unsure, ask for help](https://github.com/sugarlabs/sugar-docs/blob/master/src/CODE_OF_CONDUCT.md#when-you-are-unsure-ask-for-help)
in our Code of Conduct.

## Suggested Issues

For some ideas, there is a list of 'Suggested issues to work on'.
These may help you to get familiar with the project.  The more you
work on these issues, the more experienced you will be for the
project.  However, this is not a strict list.  You _should_ try and
explore other issues as well.
