# ⚖️ RandomOrder-Balance

<p align="center">
  <img alt="Python" src="https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white">
  <img alt="License" src="https://img.shields.io/badge/License-MIT-lightgrey">
</p>

---

## What this project is about

Imagine you're running a data center and jobs keep coming in, one at a time. Each job has to be assigned to a machine the moment it arrives — you can't wait to see what's coming next, and once you've made a decision, you're stuck with it. Your goal is to keep every machine's workload as even as possible, so no single machine gets overloaded.

That's the real-world problem behind this project. I built it to explore a specific question: **does it help if jobs arrive in a random order instead of the worst possible order?** Intuitively it feels like it should — and it turns out the answer is "a little, but not nearly as much as you'd hope." This project lets you actually see that play out, instead of just reading about it in a paper.

I built this after reading a 2024 research paper on the topic, as a way to turn the math into something visual and hands-on.

---

## What it does

- Simulates jobs (or in the simplest version, tree "edges") arriving one at a time
- Runs a simple, greedy assignment algorithm that decides where each job goes as soon as it shows up
- Tests that algorithm under two conditions: a worst-case order designed to trip it up, and a random, shuffled order
- Tracks how balanced (or unbalanced) the workload ends up in each case
- Generates charts comparing the two, so you can see the difference visually instead of just in theory
- Includes a step-by-step animation showing exactly how the algorithm makes decisions in real time

---

## Why it's interesting

This isn't just a toy exercise — it's a simplified version of a real problem companies like Google, Amazon, and Uber solve at massive scale every day: assigning work to machines/servers efficiently, in real time, without knowing what's coming next. Building this helped me get hands-on with:

- **Online algorithms** — making irreversible decisions with incomplete information
- **Randomized vs. worst-case analysis** — a core idea in how engineers reason about system reliability
- **Clean separation of concerns** — the "how jobs arrive," "how they get assigned," and "how we measure success" are all independent pieces, so I can swap any one of them out without touching the others

---

## How it's organized

```
randomorder-balance/
├── src/
│   ├── scheduling/         → the assignment algorithms
│   ├── arrival_orders/     → generates worst-case or random job orders
│   ├── metrics/            → measures how balanced the result is
│   └── benchmark/          → runs experiments and collects results
├── visualizations/         → animations and charts
├── tests/                  → unit tests for the algorithms
├── notebooks/              → results and analysis
└── README.md
```

The idea is simple: **arrival order**, **algorithm**, and **measurement** are three separate, swappable pieces. That way I can test any algorithm against any arrival pattern without rewriting anything.

---

## Try it yourself

```bash
git clone https://github.com/your-username/randomorder-balance.git
cd randomorder-balance
pip install -r requirements.txt

# Compare worst-case vs. random arrival order side by side
python -m src.benchmark.runner --arrival-order adversarial,random --plot

# Watch the algorithm make decisions step by step
python -m visualizations.animate_tree_balancing
```

---

## What I'd add next

- A version of the algorithm that uses randomness itself, not just a fixed rule
- A simulation mode that mimics an actual multi-server cluster
- An interactive, browser-based version of the animation

---

## Credit

This project was inspired by the research paper *"Online Load and Graph Balancing for Random Order Inputs"* (SPAA 2024), which studies exactly this question — how much randomness in arrival order actually helps — and proves new limits on how well these algorithms can perform.

---

## License

MIT — see `LICENSE` for details.
