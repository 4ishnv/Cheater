# ✊✋✌️ Rigged Rock Paper Scissors

A rock-paper-scissors game you play with your actual hands. Your webcam reads your gesture and the computer responds, but there's a catch: **the computer cheats.** It looks at your move and picks whatever beats it.

Can you outsmart it?
[Play Cheater RPS now!!](https://cheater-opal.vercel.app)

## How to play

1. Allow camera access when asked and wait for the hand model to load.
2. Press **SPACE** or click **Play**.
3. Show your hand to the camera during the 3-2-1 countdown, then make your final move when **SHOOT!** appears.

| Gesture | How to make it |
| ------- | -------------- |
| Rock    | Tight fist |
| Paper   | Open hand, all four fingers extended |
| Scissors | Index and middle fingers up, the others folded |

Tips: keep your hand upright, facing the camera, in good lighting.

## Cheat level

The slider under the Play button controls how often the computer cheats:

- **100%** always counters the move it saw
- **50%** cheats half the time, guesses randomly otherwise
- **0%** a completely fair game

## The loophole

The computer locks in its read of your hand a split second **before** "SHOOT!". Your real move only counts a little **after** "SHOOT!". Show a decoy during the countdown, then switch at the last moment, and you can beat it even at 100%. Switch too early and it catches you. Switch too late and your move might not register.

## How it works

- **Hand tracking:** [MediaPipe Hand Landmarker](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker) finds 21 landmark points on your hand in each video frame, running in your browser.
- **Gesture rules:** A finger counts as extended if its tip is farther from the wrist than its middle joint, which works even when the hand is tilted. Then:
  - 0 fingers extended: rock
  - index and middle extended, ring and pinky folded: scissors
  - all four extended: paper
- **The cheat:** the computer looks up the move that beats what it saw (`rock → paper`, `paper → scissors`, `scissors → rock`).

## Privacy

Everything runs in your browser. Your camera video is never uploaded or stored.

## Built with

HTML, JavaScript, and MediaPipe Tasks Vision.
