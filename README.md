Activity 4 - Data Pipelines
================

It is assumed that you have read Sections 5.1 - 5.4 from R4DS and
completed the Isolating Data with dplyr Primer.

In this activity, you will:

-   Isolate variables and observations of a dataset using `{dplyr}`.
-   Rearrange a dataset by variables using `{dplyr}`.
-   Use the pipe `%>%` from `{magrittr}` to build data pipelines.
-   Name R code chunks in an `.Rmd` report.

## ☑️ Task 1: The Workflow

Remember to take these steps slowly, help each other out, and get a hold
of your instructor when you have questions or issues.

**You may need your PAT that you created in Preparation 2**. If you
misplaced this token, you will need to create a new one prior to
beginning these steps.

1.  In this GitHub repo, click on the ![fork](README-img/fork-icon.png)
    **Fork** icon near the upper-right-hand corner. You should be taken
    a copy of this repo that is in your GitHub account - your page title
    should be `{username}/activity03-r-intro`, where `{username}` is
    replaced with your GitHub username.
2.  Click on the green **Code** button.

-   Verify that the drop-down identifies that you are using the
    **HTTPS** method (this is *probably* the default view; otherwise,
    select “HTTPS”).
-   Click on the ![clipboard](README-img/clipboard-icon.png) icon to
    copy the repo HTTPS information.

3.  Log in to the [RStudio Server](https://rstudio.gvsu.edu/).

-   Verify that you are in an RStudio session (it doesn’t matter if it
    is a previous Project session or a “vanilla” RStudio session).

4.  Create a new Project. You can do this by clicking on the
    <img src="README-img/new-project-icon.png" alt="new project" width = "20"/>
    icon or through the menus (File > New Project…).

-   In the *New Project Wizard* pop-up, select **Version Control** on
    the *Create Project* screen, then select **Git** on the *Create
    Project from Version Control* screen.
-   On the *Clone Git Repository* screen, paste the HTTPS information
    from (2) into the *Repository URL* dialog box. It should look like:
    `https://github.com/<username>/activity03-r-intro.git`
-   The *Project directory name* dialog box should automatically
    populate with your repository name, but sometimes Macs have an issue
    with this (if so, click into this box and press the ![command
    key](README-img/command-key-icon.png) command key on your keyboard).
    It should look something like: `activity03-r-intro`
-   In the *Create project as subdirectory of* dialog box, click on
    **Browse**.
-   In the *Choose Directory* pop-up, navigate to your class-level
    folder (i.e., you were encouraged to create a folder named either
    `STA418` or `STA518`) You were also encouraged to create
    an`activities` folder within your class-level folder to help
    organize our materials. Once you have navigated to the folder you
    wish this repo to be located, click **Choose**.
-   Verify that the *Create project as a directory of* dialog box
    contains the folder location that you previously specified, then
    click on **Create Project**.
-   You may be asked to login with your GitHub credentials on a *Clone
    Repository* pop-up window. Provide your GitHub username and PAT (not
    your GitHub password) if prompted.

6.  After a few seconds, your RStudio session will refresh and you
    should be in your newly created RStudio Project!

Starting with Activity 5, I will be no longer provide these full steps
and will instead be saying, “![fork](README-img/fork-icon.png) **Fork**
this repo and clone it to a new [RStudio
Project](https://rstudio.gvsu.edu/)”.Remember that more detailed
directions are provided in this Activity.

<img src="README-img/noun_pause.png" alt="pause" width = "20"/>
<b>Planned Pause Point</b>: If you have any questions, contact your
instructor or another group.

## The Pipe `%>%`

I strongly encourage you to use pipes `%>%` when working throughout this
semester. Pipes are from `{magrittr}` and are a way to take nested
functions and make them more informative to read and write. Consider the
[following lyrics](https://youtu.be/wZv62ShoStY?t=50) from Bradford’s
college days:

> To the left  
> Take it back now y’all  
> One hop this time  
> Right foot let’s stomp  
> Left foot let’s stomp  
> Cha cha real smooth  

One way to write this out is with nested functions:

    cha_cha(lets_stomp(lets_stomp(hops(take_it(to_the(direction = "left"), direction = "back", when = "now", who = "y'all"), this_time = 1), foot = "right"), foot = "left"), style = "real smooth")

If we start in the inner-most function, we can then work our way out to
see what we are trying to do. Pipes, however, clean this up:

    to_the(direction = "left") %>% 
      take_it(direction = "back", when = "now", who = "y'all") %>% 
      hops(this_time = 1) %>% 
      lets_stomp(foot = "right") %>% 
      lets_stomp(foot = "left") %>% 
      cha_cha(style = "real smooth")

Writing this using pipes give the statement a more natural structure. I
will refer to this process of piping functions a “pipeline”.

![Mario on a pipe](https://i.ytimg.com/vi/uMCCxuGIGtw/hqdefault.jpg)

Starting with [R version
4.1.0](https://stat.ethz.ch/pipermail/r-announce/2021/000670.html),
there is now a native pipe `|>` in R! However, this pipe does not have
one of the key features that the `{magrittr}` pipe does which is that
you do not necessarily need the previous step to be the first argument
in the next step. Therefore, I encourage you to stick with the
`{magrittr}` pipe.

## ☑️ Task 2: Complete the RMarkdown File

The `activity04-data-pipelines.Rmd` file contains the directions for
this activity. For the rest of this class period, you will complete the
RMarkdown document with your neighbor(s). Your instructor will be
circling and be available to help when needed.

Note that each person is working in their own repo. We are not worrying
about collaborating for the time being and instead will be working on
being more comfortable with the workflow for working between RStudio and
GitHub.

However, do not continue in this README document until you and your
neighbor(s) have completed your `.Rmd` files.

![Cat at work](https://media.giphy.com/media/E6jscXfv3AkWQ/giphy.gif)

## ☑️ Task 3: Reflection

Take 5 minutes to write a reflection on what you feel confident in and
what you need to spend some time better understanding. What is one thing
you can do to help clarify your current misunderstandings?

**Next**: Activity 5 will focus on isolating rows and columns of
datasets.
