# UX Prototypes: Quick Reference Card

## What You Have
**One Interactive HTML Artifact** with 3 tabs:
- **Ranking Algorithm Visualizer** — Adjust weights, see score changes instantly
- **Live Booking Simulator** — Watch students book in queue, manual or automated  
- **Load Balancing Dynamics** — Simulate bookings, monitor fairness

**File**: `tutoring-scheduler-ux-prototypes.html` (319 KB, no external dependencies)

---

## Tab 1: Ranking Algorithm
**Goal**: Understand how 5 factors combine into a score

| Factor | Range | Purpose |
|--------|-------|---------|
| Tutor Preference | 0-50% | Favor chosen tutors |
| Time Pattern | 0-50% | Match past habits |
| Explicit Time | 0-50% | Honor stated times |
| Load Balance | 0-50% | Prevent overload |
| Satisfaction | 0-50% | Use past ratings |

**Try**: Set Tutor Preference to 0 → See how other factors rank options differently

**Key Insight**: 85.7% of students pick option #1 (their top recommendation)

---

## Tab 2: Live Booking
**Goal**: See FCFS queue + human choice in action

### States
| Student | Status | Meaning |
|---------|--------|---------|
| A, B, C, D, E | ✅ Booked | Locked in their choice |
| F | ❌ No Options | Hard constraint violation (unsolvable) |
| G, H | ⏳ Waiting | Haven't booked yet |

**Try**: 
- Click **Run Simulation** → Auto-book everyone at 1x speed
- Change speed to 3x → Watch it zoom
- Click **Reset** → Start over

**Key Insight**: Student F is caught early (no Chemistry @8am). Production UX would offer: "Emma teaches 4pm-7pm. Would that work?"

---

## Tab 3: Load Balancing
**Goal**: Monitor fairness across tutors

### Health Indicators
| Status | Utilization | Color |
|--------|-------------|-------|
| 🟢 Available | 0-30% | Green |
| 🔵 Balanced | 30-60% | Blue |
| 🟡 Busy | 60-80% | Amber |
| 🔴 Overloaded | 80%+ | Red |

### Fairness Metrics
```
Average:      All tutors' avg utilization
Std Dev (σ):  Measure of evenness
Target:       σ < 15 (fair), no tutor > 80%
```

**Try**:
- Click **+** to book tutors until Sarah hits 80%+  
- Increase Load Balance Weight to 40%  
- Reset and see if distribution changes

**Key Insight**: Load-balance heuristic steers students away from overloaded tutors

---

## Key Numbers (Validated in Spike)
```
Feasible options/student:    10.7 avg (target: 8-15)      ✓
First-choice match:          85.7% (target: ≥80%)        ✓
Fulfillment rate:            87.5% (target: ≥95% prod)   ← Room to improve
Scheduling conflicts:        0 (target: 0)               ✓
Hard constraint catches:     1 (Student F scenario)      ✓
```

---

## Philosophy

**Brett Victor**: "Make the invisible visible"
- Every score is explained
- Adjust weights → see changes instantly
- No magic, all transparent

**Steve Wittens**: "Mathematical elegance"
- 5-factor scoring is simple & powerful
- Visual bars & colors tell the story
- Explore to discover system properties

---

## How This Becomes Production

```
Prototype                    → Production
├─ Ranking Visualizer       → Admin analytics dashboard
├─ Booking Simulator        → Student booking interface
└─ Load Balancing           → Tutor utilization monitor
```

**Timeline**: 12 weeks (see PRODUCTION_ROADMAP.md)

---

## Try This First

1. **Open the artifact**
2. Go to **Ranking Algorithm** tab
3. Set "Tutor Preference" to 0%
4. Notice how the rankings change
5. Move to "Booking" tab, click "Run Simulation"
6. Watch the FCFS queue execute
7. Check "Load Balancing" tab, click **+** a few times

**You just understood the entire system.** 🚀

---

## Files to Read Next

| File | Time | Purpose |
|------|------|---------|
| `UX_PROTOTYPES_GUIDE.md` | 5 min | Full documentation |
| `SPIKE_SUMMARY.md` | 15 min | Algorithm validation |
| `ARCHITECTURE.md` | 20 min | System design |
| `PRODUCTION_ROADMAP.md` | 30 min | 12-week plan |

---

## One-Sentence Summary

**Three interactive prototypes showing how a fair, transparent tutoring scheduler balances hard constraints, soft preferences, and human choice using multi-factor ranking and FCFS queuing.**

---

*Built: Brett Victor + Steve Wittens edition*  
*Technology: React 19 + TypeScript + Tailwind + shadcn/ui*  
*Status: Production-ready artifacts for learning & validation*
