# DSL Project

The main purpose of this repository is to hold instructions and notebook entries for the
CS 111 project.

## Repositories

_Create the repos no later than **Sunday, April 2**._

You will create two repositories for your project: one for reflecting on your progress and
sharing your work with your critique partners, and one for your project artifact itself.
Details for both repos are below.

### Reflection repo

The repository that contains this file is for reflecting on your progress and for sharing
your work with your critique group. You will contribute to a notebook entry each week (see
more details below).

To create the reflection repo, use our typical Github-Classroom-based workflow.

### Artifact repo

You should separately create a repository for your project artifact. This repository will
contain all the code for your project, along with any other files that are part of your
artifact (e.g., a README file, a Makefile, a test suite, etc.).

To do so, go to our [organization's
GitHub](https://github.com/orgs/hmc-cs111-spring2023/repositories)
and create a new repo. You can organize the repo any way you want, but it will need to be
visible by everyone in the organization. After the semester is over, you can transfer the
repo to your own account (and make it private), if you want.

Edit this document to add a link to your artifact repo, below:

[**Artifact repo**](<link-goes-here>)

## Notebooks

_Finish your entry no later than Sunday night of each week: **April 2, April 9, April 16,
and April 23**._

Each week, you should spend about 45-60 minutes writing a notebook entry. Ideally, the
contents of your entry will be a byproduct of the work you're doing on the project (e.g.,
you can include links to examples, pictures of markerboard sessions, etc.). A little bit
of time reflecting is also a good way to zoom out and check your own progress on the
project.

To write your notebook, respond to the prompts in the file from the [notebooks](./notebooks/)
folder for the appropriate week. Below are some suggested "themes" for each week of the
project. You are not required to write about these topics each week, but I include them to
help give you a sense of how to plan out the project and what you might reflect on each
week.

Regardless of the topics you choose to write about, be sure to write clearly and with
enough specificity that your critique group (and the course staff) will be able to read
and understand your entry.

### Week 1

The theme for this week is **"Getting started with design and implementation".** Here are
some things you can consider doing and reporting on in your notebook:

- Gather a few, specific **example programs** in your DSL. Each program should have an
  ideal syntax (how would you like the end-user to describe their program?) and an actual
  result (for example, an equivalent program in a general-purpose programming language and /
  or the output that results from running the program).
- Report any decisions you have made about **implementation techniques.** Have you decided
  whether your  language will be an internal DSL or external one? If so, how did you make
  this decision?
- Gather resources for deciding which **host language** you will use. How will you choose
  your host language? Are there libraries for your domain available for your chosen host
  language (or other languages)?

### Week 2

The theme for this week is **implementation choices**. Here are some things you can
consider doing and reporting on in your notebook:

- An overview of the structure of your implementation.
- Specific tools, techniques, and / or libraries you are using in your implementation.
- Any other significant implementation decisions you have made, and how those decisions
  might have affected your design.
- Anything you might currently be struggling to implement.

### Week 3

The theme for this week is **prototyping**.

Can you try to demo your language for someone (preferably someone who knows the domain but
nothing about your language)? Try giving them a brief overview of how to use the language
(possibly with some example programs). Then, give a task that is different from the
examples, and ask them to complete the task, while thinking out loud. Your goal is to
observe and make notes about their expectations and their struggles, so resist the urge to
help them complete the task.

Did you learn anything from this exercise? Is there anything you might want to change or
adjust about your design?

### Week 4

The theme for this week is **evaluation**. Here are some things you might consider
evaluating and writing about in your notebook:

- Describe what you've done to evaluate your design. Have you tried it out on potential
  users? If so, what did you ask the users to do?
- What about your language works well? What are you particularly pleased with?
- What could be improved? For example, how could the user's experience be better? How
  might your implementation be simpler or more cohesive?
- Where did you run into trouble and why? For example, did you come up with some syntax
  that you found difficult to implement, given your host language choice? Did you want to
  support multiple features, but you had trouble getting them to play well together?
- What's left to accomplish before the end of the project?
- If you worked as a pair, describe how you have divided your labor and whether that
  division has worked well.

## Critiques

_Finish your critique no later than Tuesday night of each week: **April 4, April 11, April
18, and April 25**._

Each week, you will meet with your critique group to discuss your progress and to give and
receive feedback. We will reserve Monday's class time for critique sessions, and you
should spend about 45-60 minutes on each critique session. Take notes during these
sessions, both on your own work and on your critique groups' work.

After the critique session, provide feedback for one member of your critique group. Add
your feedback to the **pull request for your partner's notebook entry**. Your job as a
critic is to help make the project as good as it can be. Is there something that the
language creator(s) missed? Do you know of a related language? Do you know something about
the domain? Can you think of good ways to evaluate the language? Are the users of the
language being served by the current design and implementation? Is (are) the language
creator(s) focusing on the things they said they wanted to focus on?

## Video

_Finish your video no later than **Friday, April 28**._

This is your chance to show off by giving a demo of your DSL. Create a short (5-10 minute)
video that describes your project.

In your video, you should cover:

- Your vision of a language in this domain. Why does the domain need a language, and what
  about your design is an interesting solution to problems in this language?
- Cool things that a programmer can do in your language (i.e., how are you easing domain
  experts' pain?). This is the "demo" part of the presentation: be sure to show us some
  example programs and their execution.
- A brief overview of you implementation techniques (e.g. "I implemented the language as an
  internal DSL in Scala using these techniques...", or "I implemented the language as an
  external DSL in Python, using these techniques...").
- One or two "lessons learned": interesting insights you had into language design and
  implementation (e.g., what did you think would be easy that wasn't, what did you think
  was difficult that wasn't, how would you advise other implementers of DSLs in your
  domain or otherwise, what would you do differently next time, what would you add/change
  if you had more time, etc.?).

Note: The demo portion doesn't require that your implementation be 100% complete. You can
"fake" the demo to show us your vision, if your vision is too ambitious for the project.

If you would like some advice on how to create a video,
[this
resource](https://www.howtogeek.com/205742/how-to-record-your-windows-mac-linux-android-or-ios-screen/)
may be helpful.

Closer to the deadline, I will provide information about how to submit your video.

## Artifact

_Finish your artifact no later than **Friday, April 28**._

Commit all the materials for your language, along with a few sample programs, to your
artifact repo. Be sure the `README.md` file describes how a user can run the sample
programs in your language, including any additional software, libraries, or tools that are
required. Test-drive this process to make sure that someone else can easily use your DSL.
Your code should follow good practices. In particular, it should be well-architected
(i.e., modular), well-tested, and well-documented.
