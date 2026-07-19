# Weekly Progress Log

> Update this file **every week**. Add a new entry at the top for each week.
> This is the first thing we check during review. Keep it honest and specific — it also feeds your attendance record (Rule 1).

**How to use:** copy the *Week template* block below for each new week. Newest week goes at the top.

---

## Week template — copy me

### Week N — 2026-MM-DD

**Attended this week's meeting:** Yes / No (if No, did you email leave? Yes / No)

**Progress this week**
- _What did you actually do / finish?_

**Challenges & blockers**
- _What got in the way? What are you stuck on?_

**Next steps**
- _What will you do next week?_

**Hours spent:** _e.g. 6h_

**Links of External resources used:** _commits, notebooks, docs, datasets..._

---

<!-- =================  YOUR ENTRIES BELOW  ================= -->

### Week 5 — 2026-07-19

**Attended this week's meeting:** Yes

**Progress this week**
- Read theoretical part of DWBLocalPlanner
- Tried to implement DWBLocalPlanner into the code instead of current RPP //as mentioned in previous day log
- Current code: [nav2_params.yaml](https://github.com/user-attachments/files/30164417/nav2_params.yaml)
- DWB generally works, however there is a specific case that causes issues. //check challenges & blockers

**Challenges & blockers**
- I have no idea why but scales used for 'PathAlign, GoalAlign and PathDist' are divided by 40 during the simulation. Also, 'ObstacleFootprint' scale value is divided by 20, however BaseObstacle scale value is as written in the yaml file. I have checked exact values through 'ros2 topic echo /evaluation'. Param dump for controller_server doesn't show anything unusual. I have just noticed that with current value of the 'PathAlign' scale, simulation considers it as 0.0. I'll look into it on the next week. //This issue is partly solved by multiplying every scale by its ratio, however would be nice to understand what is going on.
- Second issue I have encountered is that critics don't take into account curvature of the path, therefore may stuck in specific occasions when goal is just after the curvature.
- Thirdly, BaseObstacle critic or ObstacleFootprint critic are not working properly //I've never seen their raw_score to go above 0.0
- Last note: robot is just slow. I'll look into it after solving previous issues.

**Next steps**
- Solve every issue discussed earlier

**Hours spent:** 20-30h

**Links of External resources used:** https://docs.nav2.org/configuration/packages/dwb-params/controller.html#dwb-controller

---

### Week 4 Update

Debugging of the yaml file revealed that I made a mistake in the yaml file itself (to be specific, I did not configure local and global costmap in the right way) and therefore simluation ignored them. Nav2 works nicely right now, no further issues found. As written in the week 4 "Next steps" I'll implement DWB, AMCL etc.

Current params: [nav2_params.yaml](https://github.com/user-attachments/files/30002128/nav2_params.yaml)

### Week 4 — 2026-07-12

**Attended this week's meeting:** No //it was cancelled

**Progress this week**
- Put the Nav2 into the demo case.
- It works, however has significant issues. The process will be explained and showed further:
- I have decided to start with easiest steps required to start my learning path, therefore file doesn't modify (or uses Nav2 standard values): velocity_smoother, goal_checker, progress_checker, smoother_server, AMCL or slam in localization mode.
- I have decided to use slam_toolbox from previous assignment almost unchanged #//lowered resolution to lower cpu usage
- I have decided to use Regulated Pure Pursuit instead of DWB since this assignment (in my opinion) doesn't require DWB
- The code looks as follows: [nav2_params.yaml](https://github.com/user-attachments/files/29962586/nav2_params.yaml)
- Please note that during tests I have changed some values, therefore they may look weird (as footprint_padding and inflation_radius) #//this is directly linked to issues described in **Challenges & blockers**.


**Challenges & blockers**
- Code generally works, however parameters set in local_costmap and global_costmap of the yaml file are not the ones used by simulation. For some (unknown yet) reason, simulation ignores parameters in the yaml file. Refer to the image below and pay attention to resolution for local and global costmap values used in the simulation and in the yaml file.

<img width="554" height="619" alt="image" src="https://github.com/user-attachments/assets/b315c062-6ea8-45c6-8d27-a24b8a22aea1" />

Param dump for local_costmap:

<img width="809" height="587" alt="image" src="https://github.com/user-attachments/assets/791321ec-3804-481d-ad3e-5bbd6b5d0722" />

Param dump for global_costmap:

<img width="786" height="593" alt="image" src="https://github.com/user-attachments/assets/3dc1b087-a9eb-490e-92f8-c8d00c76bf1b" />



**Next steps**
- Debug to understand what is the happening with the local and global costmap.
- Implement DWB, AMCL, velocity_smoother and others.

**Hours spent:** 30h

**Links of External resources used:** https://docs.nav2.org/

---

### Week 3 — 2026-07-05 

**Attended this week's meeting:** Yes

**Progress this week**
- Played with slam parameters enough to understand them better //as mentioned in previous day log
- Started learning Nav2 and getting familiar with it //mostly theory and how things work on a paper

**Challenges & blockers**
- Had issues with understanding how to put it into work on practice.

**Next steps**
- Add Nav2 point navigation for demo case sent by supervisor

**Hours spent:** 20 h

**Links of External resources used:** https://docs.nav2.org/

---

### Week 2 — 2026-06-28

**Attended this week's meeting:** No //lesson was in Chinese and I'm not (quite surprising)

**Progress this week**
- Wrote simple publisher and subscriber on C++ //as mentioned in previous week log
- Wrote simple service and client on C++
- Created custom msg and srv files 
- Implemented custom interface
- Started demo case sent by project lead //tuesday 16:44
- Read through documentation of the file sent and learnt about main ideas using AI. //wednesday
- Spent 3 days playing with the config parameters and here's how it went:
<img width="139" height="158" alt="maze_map" src="https://github.com/user-attachments/assets/38634965-0124-4546-a490-c73da6587fc4" />

First configuration had minimum_interval_time = 0.333; didn't had loop_closure or max_laser_range parameters (defaults used) and map wasn't good. Apparently I started the executables wrongly (I think so at least). Therefore map wasn't updating even though I did move the robot around the maze. Anyway first day of playing brought me to this map.

<img width="159" height="172" alt="map_1782549382" src="https://github.com/user-attachments/assets/387168a4-1239-401d-b79c-e03787ed86d4" />

Second day was more successful. Added max_laser_range = 6 (seemed valid as entire map is around 11 x 11), minimum_interval_time = 0.1 (since hz of /scan is nearly 10), resolution data I don't remember (sorry). Map looks better, yet important to note that are not ideal /absence of loop_closure param shows.

<img width="591" height="584" alt="maze_map" src="https://github.com/user-attachments/assets/d7b98b8c-f300-41a8-840b-8a41590a0424" />

Third day map looks nicely. Resolution = 0.03 and loop_closure added.
slam_toolbox:
  ros__parameters:
  
    use_sim_time: true
    
    #// TF tree map -> odom -> base_link (robot itself) -> lidar_link (laser)
    map_frame: map
    odom_frame: odom
    base_frame: base_link
    
    #// Sensor
    scan_topic: /scan
    
    #// Settings
    resolution: 0.03
    max_laser_range: 6.0
    
    #// Refresh rate
    minimum_time_interval: 0.1

    #// loop closure stuff
    loop_match_minimum_chain_size: 10
    loop_match_minimum_response_coarse: 0.35    
    loop_match_minimum_response_fine: 0.45
    loop_search_maximum_distance: 3.0

Some of the test photos
<img width="1246" height="779" alt="image" src="https://github.com/user-attachments/assets/90998b31-72a3-4795-ab5b-143bcedd44bd" />

<img width="2505" height="1418" alt="image (1)" src="https://github.com/user-attachments/assets/f2f7a359-f9dc-4f23-976e-bca77060859c" />

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Decided to check how does it go with disabled loop_closure (not default but disabled completely, this one is one of the best attempts)

<img width="2434" height="1418" alt="image (2)" src="https://github.com/user-attachments/assets/d8868386-4d79-45b9-9ff5-171d8fbc94a4" />
<img width="2434" height="1418" alt="image (3)" src="https://github.com/user-attachments/assets/fef3cd2a-cba0-4ed3-83a3-9cc941985c23" />
<img width="2558" height="1431" alt="image (4)" src="https://github.com/user-attachments/assets/7826a52f-c2cc-4f2f-a4ac-275e3ccbd138" />

**Challenges & blockers**
- None for now

**Next steps**
- Play with parameters and try some online stuff near this topic

**Hours spent:** 15 hours

**Links of External resources used:** https://github.com/SteveMacenski/slam_toolbox
__________________________________________

### Week 1 — 2026-06-21

**Attended this week's meeting:** Yes //however meeting was in Chinese, therefore I was told that I may leave

**Progress this week**
- Followed up on "How to ask questions" guide //as mentioned in previous week log
- Got a deeper understanding nodes, topics, services, paramaters and actions //as mentioned in previous week log
- Learnt how to use rqt to inspect logs //rqt_graph included
- Learnt how to record and playback data.
- Learnt how to create isolated workspace through colcon //underlays
- Sourced underlay and tested how it does work //basically played with it, since it's isolated playground
- Created my own package //by CMake, since I understand it better

**Challenges & blockers**
- None for now

**Next steps**
- Create a simple publisher and subscriber 

**Hours spent:** ~10 hours

**Links of External resources used:** https://youtu.be/HJAE5Pk8Nyw?si=cGPGFdZ1Q_mpDz07
__________________________________________

### Week 0 — 2026-06-15

**Attended this week's meeting:** Yes //Optional meeting on Monday

**Progress this week**
- Set up github repository and made it public.
- Installed and set up: VMWare, Linux, ROS2 Humble and Visual Studio Code.
- Tested and got familiar with provided main Linux commands (cd, mkdir, find, grep etc.)
- Read and followed provided ROS2 Humble tutorials and therefore got familiar with main ideas (nodes, topics...) and commands.
- Ran talker and listener as a test.

**Challenges & blockers**
- Not a challenge but, I would need a bit more time to get familiar with "How to ask questions" guide.

**Next steps**
- Follow up on "How to ask questions" guide and get familiar with it.
- Get a deeper understanding on nodes, topics, services, parameters and actions.

**Hours spent:** Around 8 hours.

**Links of External resources used:** https://youtu.be/HJAE5Pk8Nyw?si=cGPGFdZ1Q_mpDz07
