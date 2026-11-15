# Final project to-do list

2026-11-15 

The presentation is due **2026-12-03** and the tutorial plus code zip is due by end of day **2026-12-04**, with no late days. This plan finishes the build by Thanksgiving week so the last week goes to results and writing.

## Week 1 (Nov 15–21): pin down the problem, collect data, write the PDDL

- [ ] Agree with Mitchell on who owns what (suggestion: one person on data + PDDL, the other on the CSP translator, then swap to review)
- [ ] Write down the modeling assumptions in one place: nights 1–13, Rome nights 9–10, Dublin 2 nights, costs for both of you, June average prices booked in November
- [ ] Pick the transport modes to include (e.g. flight, train, bus)
- [ ] Collect lodging cost per night for each city and save it as a CSV with a source column
- [ ] Collect fares for each city pair and mode and save them as a CSV with sources
- [ ] Start an AI-use log now (tool, what for, how you checked it), since the tutorial requires an AI Usage section
- [ ] Install Python tools: `ortools`, `unified-planning`, plus VAL and ENHSP (or Fast Downward)
- [ ] Write the PDDL domain: cities, days, modes; `stay` and `travel` actions; numeric fluents for prices, nights per city, and total cost
- [ ] Write a small script that turns the CSVs into the PDDL problem file
- [ ] Sanity-check the PDDL by running a planner on a 3-city, 5-night version
- [ ] Read Russell & Norvig ch. 6 (CSPs) and skim CPlan and GP-CSP

## Week 2 (Nov 22–28): build and check the CSP solver

Thanksgiving is Nov 26, so aim to finish the core build by Wednesday.

- [ ] Parse the PDDL problem with unified-planning's `PDDLReader`
- [ ] Build the CP-SAT model from it: city, mode, and fare variables per night, plus your trip constraints (see the CSP primer)
- [ ] Decode the solver's answer into a PDDL plan, one action per day
- [ ] Validate the decoded plan with VAL against your PDDL files
- [ ] Hand-solve the 3-city toy version and confirm the solver gets the same answer
- [ ] Solve the real trip and record the itinerary, total cost, and solve time
- [ ] Baseline 1: a greedy "cheapest next hop" itinerary
- [ ] Baseline 2: a PDDL planner (ENHSP) on the same PDDL files
- [ ] Stretch: the generic encoding (one 0/1 variable per ground action per night) to compare with the compact model
- [ ] Start drafting the tutorial's Related Work (5+ published papers) and Technique sections while the details are fresh

## Week 3 (Nov 29–Dec 3): experiments, figures, presentation

- [ ] Define the metric as an equation for the tutorial (e.g. total cost, gap to the CSP optimum, solve time, constraints satisfied)
- [ ] Compare the CSP, greedy, and PDDL planner on the real trip
- [ ] Scaling runs: more cities, longer trips, looser date rules
- [ ] Price scenarios: vary prices by plus or minus 20% and re-solve several times
- [ ] Make the figures: cost by method, solve time vs. problem size, the final itinerary as a timeline
- [ ] Write down when the approach works and when it breaks (e.g. where the PDDL planner fails or the CSP slows down)
- [ ] Build the slides: 2 min motivation, 2 min technique (with one equation or pseudocode), 6 min results
- [ ] Rehearse together to 10 minutes
- [ ] Present in class on Dec 3, or upload the recorded video to Canvas by Dec 3

## Dec 3–4: finish and submit the tutorial

No late days, and one minute late costs 20%, so plan to submit the night of Dec 3.

- [ ] Introduction and motivation: why planning this trip is hard and who would use the tutorial (10%)
- [ ] Related work with at least 5 published papers, verified titles and years (10%)
- [ ] Technique, problem formulation, and metric equation: teach CSPs and the PDDL-to-CSP encoding using your trip, and say how it differs from class (15%)
- [ ] Approach, implementation, results, and analysis: how to run your code, install links, figures, what you built vs. what came from libraries or AI, and how you checked correctness (40%)
- [ ] Future work: a few sentences
- [ ] AI Usage section, written from your log
- [ ] Clarity pass: cut anything not needed, check every figure has a caption (10%)
- [ ] Clean the code, add a short README, zip it
- [ ] Export to PDF or HTML and check it opens
- [ ] Submit tutorial and code zip on Canvas
