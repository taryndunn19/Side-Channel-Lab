# Side-Channel Lab

An interactive, browser-based teaching module for the **Algorithmic Complexity and Side-Channel Attacks** unit. It shows how an algorithm that is mathematically correct can still leak its secrets through *how long it takes* or *how much power it draws*, and how a leak like that turns an exponential search into a linear one.

Everything is simulated from a simple cost model in the page. Nothing is measured on a real system and no network requests are made, so it is safe to use in a classroom.

## Running it

No build step and no dependencies.

1. Clone or download this repository.
2. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge).

You can also host it with **GitHub Pages**: go to *Settings → Pages* and deploy from the `main` branch, root folder.

## What's inside

The app has three tabs.

### 1. Timing attack on a password check
- The server compares a password with an **early-exit** loop that returns at the first wrong character.
- The attacker tries all 26 letters at the next position, measures the average response time of each, and keeps the slowest one. That letter got one comparison further.
- **Interactive controls:** secret password, comparison algorithm (early-exit or constant-time), measurement noise slider, samples-per-guess slider, step/run/reset buttons, and an instructor-view toggle.
- **Lesson:** noise can be averaged away with more samples, and a constant-time comparison removes the signal entirely.

### 2. Power trace of RSA square-and-multiply
- Modular exponentiation `c^d mod N` with square-and-multiply needs O(log d) operations instead of O(d).
- The leaky version only multiplies when a key bit is 1, so the simulated power trace reads the key bit by bit (**S M** = 1, **S** = 0).
- **Interactive controls:** secret exponent input, random key button, algorithm dropdown (leaky or square-and-multiply-always), probe-noise slider, and a toggle that highlights dummy operations.
- **Lesson:** an efficient algorithm whose control flow depends on secret data leaks that data. The fix trades some performance for uniform behavior.

### 3. Why complexity matters
- Plots brute force (`kⁿ`, exponential) against a character-by-character side-channel attack (`k · n · samples`, linear) on a log scale.
- **Interactive controls:** alphabet size, secret length, samples per guess, attacker speed.
- Converts guess counts into wall-clock time, from seconds up to multiples of the age of the universe.

## Concepts covered
- Big-O growth: exponential vs. linear vs. logarithmic
- Timing side channels and early-exit comparisons
- Constant-time programming (`diff |= a ^ b`)
- Simple power analysis (SPA) on square-and-multiply
- Countermeasures and their performance cost
- Averaging repeated measurements to beat noise

## Project structure
```
.
├── index.html      # the whole app (HTML + CSS + JavaScript, no dependencies)
├── README.md       # this file
└── reflection.md   # reflection on building the app
```

## Simulation model
- **Timing:** each request costs `40 + 10 × (characters compared) + noise`, where noise is Gaussian with the selected standard deviation.
- **Power:** a square is drawn as a short, low pulse and a multiply as a longer, higher pulse, plus Gaussian probe noise.
- The modular exponentiation result (`7^d mod 1,000,003`) is computed with `BigInt` to show that both algorithms give the same answer.

## AI usage
This app was built with AI assistance (Claude Code). I reviewed, tested, and adjusted the generated code and text. See `reflection.md` for the workflow.

## Security note
This repository contains no API keys, passwords, tokens, or personal information. The default "password" in the demo is a public placeholder.

