---
title: 'Calypso-1'
description: 'Psychological Horror Co-op game'
pubDate: 'Jun 01 2026'
heroImage: '/public/assets/06_Thesis/00_Logo.png'
bannerImage: '/public/assets/06_Thesis/00_Logo.png'
keywords: "Unity, System Programming, Network Programming, C#"
---

<!-- summary -->

For my Bachelor thesis, I am collaborating with **three fellow students** to develop the game **Calypso-1**. Calypso-1 is a psychological horror co-op puzzle game featuring two engineers sent to an oil rig to maintain critical infrastructure, only to discover that something is deeply wrong.

This project is still ongoing as we are currently working on releasing this game on steam.

Get the demo game on <a href="https://julianletsche.itch.io/calypso-1" target="_blank" rel="noopener noreferrer">itch.io</a>. Only playable on Windows.

<!-- my focus -->
### Dynamic Difficulty Adjustment

My research focuses on developing a **Dynamic Difficulty Adjustment (DDA) System** within the game. The goal is to provide each player with an individual difficulty level based on their skill. In a psychological horror game, player immersion is the most important aspect; therefore, keeping both players in the Flow state is essential. To gather data for my thesis I added a Data Log in the background which logged in game data and events that enabled me to create graphs that I could use in my thesis.

<figure class="center">
  <img src="/assets/06_Thesis/01_Difficulty.png" alt="Difficulty Graph" width="800" />
  <figcaption>Difficulty between the player over one playthrough</figcaption>
</figure>

After completing my research, I identified three important aspects for designing a DDA system for a puzzle game: establishing an initial difficulty level, including the current game state in the calculation, and allowing players to fail without immediately reducing the difficulty.

The research paper is released on <a href="https://uu.diva-portal.org/smash/record.jsf?pid=diva2%3A2071353&dswid=-7262" target="_blank" rel="noopener noreferrer">DiVA</a>

```c#
int successfullTasks = 0;
foreach (bool attempt in mostRecentTaskAttempts)
{
    if (attempt) successfullTasks++;
}

float taskSuccessRatio = (float)successfullTasks / mostRecentTaskAttempts.Count;

//distance
float playerDistance = GetPlayerDistance();
float normalizedDistance = Mathf.Clamp01(playerDistance / 20f);

//progress
float progress = myLevelManager.currentList.Value / 6;

//biases
float time01 = Mathf.Clamp01((Time.time - startTime) / targetTime);
float baseTarget = taskSuccessRatioGraph.Evaluate(time01);

float distanceBias = Mathf.Lerp(0f, 0.1f, normalizedDistance);
float progressBias = Mathf.Lerp(0f, 0.2f, progress);

float modifiedTarget = baseTarget + progressBias + distanceBias;

modifiedTarget = Mathf.Clamp01(modifiedTarget);

float delta = modifiedTarget - taskSuccessRatio;
```

Through iteration during the research process, these factors were found to provide the most reliable difficulty adjustments. Another important aspect was establishing the initial difficulty before the players entered the game. The difficulty was recalculated whenever a player started a new task.

### QTE Algorithm

To make the difficulty easily adjustable, most tasks in the game were built around **Quick Time Events (QTEs)**. Since QTEs can range from simple button presses to complex input sequences, they provided a flexible foundation for dynamically adjusting challenge levels.

The final version included:
* Button press
* Timed button press
* Hold button
* Tap button
* Directional joystick input

Each QTE type had individual percentage-based difficulty graphs, as well as parameters controlling the length of input sequences. This allowed the frequency and complexity of each challenge type to be adjusted for different difficulty levels.

<div class="grid-gallery">
  <figure>
    <img src="/assets/06_Thesis/02_QTEAlgorithmList.png" alt="QTE Algorithm List" width="250" />
    <figcaption>List of possible QTE</figcaption>
  </figure>

  <figure>
    <img src="/assets/06_Thesis/03_QTEAlgorithmCurve.png" alt="QTE Algorithm Curve" width="550" />
    <figcaption>Percentage Curve</figcaption>
  </figure>
</div>

### Networking

This was my first networked game project. I used Unity's **Netcode for GameObjects** to connect two game instances over LAN. One instance acted as the Server/Host while the other became a Client.

Since the game was designed as an individual audiovisual experience, only the larger game state (such as tasks and events) and player positions needed to be synchronized. This was handled through ServerRpc and ClientRpc functions.

To enable voice chat and make it work during the Gotland Game Conference, I implemented <a href="https://github.com/adrenak/univoice" target="_blank" rel="noopener noreferrer">UniVoice</a> by Adrenak. This was the only voice chat solution I found that supported a fully local LAN setup, which was required for the conference demonstration.

### Static Camera System

To achieve the specific visual style we wanted, we decided to use the static camera approach found in older **Resident Evil** games.

To implement this system, I used **Cinemachine** cameras attached to trigger boxes that changed camera priorities depending on the player's location.

During the later stages of development, a roaming monster was added to the oil rig. The monster could not be seen directly by the players, but when approaching certain areas, the player's perspective could switch to the monster's viewpoint. This was implemented using additional Cinemachine cameras combined with visual effects and animations.

### Dread System

To strengthen the psychological horror elements and make players question their own perception, we created a system called the **Dread System**.

As the game progressed, the player's individual dread level increased and the environment started to change. This was handled separately for each player, creating uncertainty around questions such as: "Did I really hear or see that if the other player did not?"

I implemented this system as a custom editor tool used by the level designers. This allowed them to configure and place dread events without requiring additional programming.

<div class="grid-gallery">
  <figure>
    <img src="/assets/06_Thesis/04_Corridor1.png" alt="Corridor Player One" width="400" />
    <figcaption>Layout POV Player One</figcaption>
  </figure>

  <figure>
    <img src="/assets/06_Thesis/05_Corridor2.png" alt="Corridor Player Two" width="400" />
    <figcaption>Layout POV Player Two</figcaption>
  </figure>
</div>

<!-- links -->
This project was showcased at the <a href="https://gotlandgameconference.com/2026/" target="_blank" rel="noopener noreferrer">Gotland Game Conference 2026</a> where we received the **Jury Spotlight Award** as well as a nomination for **Best Audio**.
