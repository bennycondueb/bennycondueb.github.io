---
title: "Division Leader, managing a Software Team"
permalink: /_pages/portfolio/managing-a-software-team/
layout: single
author_profile: true
toc: true
toc_sticky: true 

---

# Why? 
The objective of this page is to explain the experience I've matured during my 
(more or less) 6-7 months of being a __Division Leader__ inside 
[Squadra Corse](https://squadracorse.webflow.io). 

# What does "Division Leader" mean? 
Squadra Corse is divided into **Divisions**, i.e. different sub-teams 
specialized into different categories of the car's components. 
If you are interested into understanding more deeply the internal functioning 
of Squadra Corse, I suggest you to visit the [website](https://squadracorse.webflow.io). 
**Division Leaders** are, in short, the managers of said divisions, being composed by a different number of members. 
Their role is to supervise the ongoing work, decide and assign tasks, 
manage the bureaucracy of the Team, refer to the Board and sometimes to the Stakeholders, 
integrate their division work with the work of other divisions and so on.

# How did you become "Division Leader"? 
The _usual_ way for a member to become division leader is roughly the following:
- Be an **active** member of the Team 
- Be knowledgeable in the Division's requirements 
- Show **passion & willpower** in the project 
- Candidate oneself into the position, then being chosen by the active Division Leader as the following one. 

The problem is... That **I wasn't part of Squadra Corse before joining in October!** \\
I became a Division Leader after an agreement between Squadra Corse ("SC")and [Squadra Corse Driverless](https://squadracorsedriverless.com) ("SCD"), the other FSAE team of the university whose focus was on Autonomous Driving. \\
I was member of SCD during my first year of the Bachelor and distinguished myself during such time for the technical knowledge. 
As SCD was unable to keep up for the following year and SC had technical problems on their car, 
the two teams decided to stop "fighting eachother" and just **merge together**. 
This merging was defined with some conditions. \\
One of such conditions was that I became the **Division Leader** of the new _"Autonomous"_ division, 
whose job was to implement the **Autonomous software inside the new SC vehicle**. 

# What did you do as a "Division Leader"? 
In this section, it's described most of the stuff I've learnt during my journey. 
Let me start by saying **thanks to everyone of the wonderful people I had the chance to work with: Alice, Alessio, Alp, Tommaso, Walter.** \\
I wouldn't be the person I'm now if it wasn't for the chance of working with you. \\
After this acknowledgments, in the following section different aspect of what I was doing are going to be descibed, 
with more or less detail depending on the context. 

## The core of a team: the people 
A team wouldn't exist without the **people** that compose it. \\
When the season started, in the Autonomous division we were in total 4 people _(Me, Alice, Alessio, Alp)_. 
A pretty low number considering that we needed to integrate all of the 
previously done software onto the new vehicle. \\
So, one of our first task was to handle the **recruitment**. \\
To handle such task, we prepared the following: 
- A _general form_ open to everyone who wanted to join 
- A _technical form_ sent only to those candidates who passed an initial screening based upon CV, age, general knowledge, etc.  \\
This technical form touched different topics: mainly Computer Science basics, 
then some open problem solving for "real-case scenarios" in our FSAE 
environment, such as Sensor Fusion or Localization of the vehicle.   
- An _oral interview_, where we would test both technical knowledge and attitude.
- To evaluate the candidates, we prepared **4 KPIs**: 
    - General Programming Knowledge 
    - General Robotics Knowledge 
    - CV, Previous Experiences 
    - Attitude, First Impression, Etc. 
- These categories had different scores attached to them, and different ranges of scores would differentiate candidates. 
- This way we tried to have an evaluation as objective as possible. 


Following this procedure, we recruited some new members, a couple of them left,
but we still had a positive outcome considering that Tommaso and Walter decided to stay. 

## Target Setting  

A very important step for the season was the Target Setting. \\
**Target Setting** is the answer to the question _"What are we going to achieve this year?"_ \\
For how simple it sounds, it's not trivial to answer, especially if you need to
do something that has never been done before. \\
After thoughtful considerations, the action plan was defined as following: 
1. What are the **steps** that need to be done before having a functioning vehicle? 
2. After having a functioning vehicle, what parameters have to be used as **metrics** for the performance? 
3. What performance are we **sure** we can achieve in this season? 

For Step 1, I remand you to [the proper page](system_integration_hw_sw_into_a_fsae_vehicle.md) 

For Step 2, the following metrics have been chosen: 

- **Car's performance on the 4 different tasks** \\
    It's easy to see that as the competition is based on time costraints,
    the faster the car goes the better. 
    As in the previous team we didn't have a benchmark of the time 
    required for said tasks, this year would've been the base for the 
    upcoming years and projects. 
- **Pipeline Critical Path computation time** \\
    A fast pipeline computation means that an higher frequency can be 
    used on the different sensors. Higher frequency of the sensors imply 
    better response with higher speeds. You see where I'm going? 
    For this, we had previous years' benchmarks to base ourselves upon! 
- **Pipeline Reliability** \\
    Sensors work in the real world, and for so they can encounter errors. 
    Our Pipeline had different exit points depending on the different Nodes 
    that could crash/throw an error. Therefore, improving such exit points and 
    overall synergy between the nodes was fundamental to enforce consistent 
    performance on every iteration. 

For Step 3, I'd like to share some real data with you, but given some _"Industrial Secret"_ I cannot share the actual values! \\
 
## Tasks & Deadlines 
Tasks and Deadlines are the main course of being a "Division Leader" or, 
more in general, a project manager. \\

### How were Deadlines decided? 
Deadlines were usually decided with the **Stakeholder** and the **Faculty** **altogether**, 
especially for medium-long term projects. 
For short terms deadlines, I always discussed the possible dates with my team, 
considering both their requests and Stakeholder's/Faculty's interests. 

### How were tasks decided? 
Let's divide between macro- and micro-tasks: 
- **Macro-Tasks**: after deadlines, macro-tasks were decided mainly between Us 
and Faculty's Advisors, considering also the opinion from External Advisors 
depending on the subject. 
- **Micro-Tasks**: after defining macro-tasks, micro-tasks were mainly handled by 
me, as these were the effective tasks that needed to be completed weekly to 
ensure smooth work operations. 

### What tools did you use? 
As programmers, we are blessed by the existence of **Git and GitHub**. \\
GitHub's built-in features for Issue tracking, Projects and such were used to 
their fully extent. \\
**Micro-tasks** were defined as single issues, people were assigned, branches were 
defined, deadlines were written, and so on. Commits were easily trackable to 
see "who has done what and when". \\
**Macro-tasks** were defined as Projects inside the repository, with deadlines, 
milestones, general comments on the overall project. \\
For communication between members we relied on **Telegram**, while for note-
taking and calendar we used **Notion**, coherent with the rest of the team. 

## Day-to-Day Life 
But in short, **how was a day in my shoes?** \\
Stressful to say the least, full of work to be done, and bla bla bla... \\
Jokes aside, it looked more or less like this: 
1. Wake up, go to the office 
2. Open Telegram, check any new messages/updates arrived during the night 
3. Open GitHub, check any new commit/PR/comment 
4. Open Notion, check the To-Do list, and choose the task for the morning 
5. Work 
6. Eat Lunch 
7. Repeat steps 2 to 5 up until evening 
8. Go Home 

Depending on the day of the week, there could've been the following: 
- Division Meeting 
- Division Leaders Meeting 
- Stakeholder Meeting 
- Faculty Meeting 
- Work in the workshop 
- Sponsor Event 

Coffee breaks were not included but I can assure you I had lots of caffeine in 
my blood any hour round.  

# Why did you leave? 
Tough topic, as everyone leaving a student team. \\
I'd like to keep things short and I'd prefer not to explain this topic with too much detail. 
Basically, I had some _serious conflict_ with members of the "Board" and I decided, 
for the sake of my own mental health and personal ethics, to leave the team. \\
Such conflicts were only "work-related", mostly on the way the overall integration of the Autonomous System should've been done. 