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
