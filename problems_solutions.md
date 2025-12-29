# Background, problems and proposed solutions

The aim of Open Protector Standard is to address the problems with the EN harness back protector standard.

The problems are two fold:

1. The EN standard is not public - it is a copyrighted standard only accessible behind a paywall.
2. The standard itself has serious safety problems in both the current versions and in the up-and-coming EN draft.

## Standard behind a paywall

Now, the first point is not the manufacturers' fault and is an active debate in the EU right now. (This might sound strange to international readers, but currently both paragliders and harnesses are certified according to an EU standard.)

Recently, in 2024 the European Court of Justice ruled that certain European safety standards must be free to access (Case C-588/21 P). The logic was simple: if you're legally required to follow a standard, that standard is basically law. And you shouldn't have to pay to read the law.

This ruling specifically applies to "harmonised standards" - standards that are officially linked to EU safety regulations. Our harness back protector standards don't fall into that category, so this ruling doesn't automatically open them up.

But the principle still makes sense for us: we're talking about equipment that protects pilots from spine injuries. Pilots, manufacturers, and safety researchers should all be able to read and evaluate how back protectors are being tested. Hiding safety standards behind a paywall doesn't help anyone.

That said, even if the standard became free tomorrow, it wouldn't fix the real issue. The real issue is that the standard has serious safety flaws which need to be addressed.

**Proposed solution**: make an open-source standard which CIVL / EN WG6 / DHV can adopt and contribute to.



## Safety problems with the current EN standard

### 1. Lack of weight range

The biggest safety problem by far is that there are no weight ranges defined for protector certification: every protector is tested on a **fixed 50 kg dummy weight**.

This is such a serious issue that I believe there is no point of talking about any measurement until this basic flaw is addressed.

#### The ball drop experiment

Before I go into more details, let's imagine an experiment: drop two balls with the same size and shape from the same drop height onto the same foam mattress. One ball is 1 kg, the other is 10 kg.

- They hit the foam at the same speed $v = \sqrt{2gh}$
- But the 10 kg ball hits with 10× more impact energy $E = mgh$

What does the foam do with that extra energy?

To absorb more energy, the foam needs to compress more, so the heavier ball will push deeper into the foam.

If we use a simple model where the foam behaves roughly like a spring, then the impact energy equals the spring compression energy:

$$E = mgh = \tfrac12 kx^2$$

So the compression depth is:

$$x = \sqrt{\tfrac{2mgh}{k}}$$

That means $x \propto \sqrt{m}$, so the 10x heavier ball compresses it $\sqrt{10} \approx 3.2$ times deeper.

So if the 1 kg ball needs about 10 cm of compression to stop, the 10 kg ball might need about 32 cm.

**Thick foam vs thin foam:**

- With a thick mattress (say 50 cm), both balls can be stopped smoothly because there is plenty of thickness available.
- If you keep making the foam thinner, eventually you reach a point where the lighter ball can still be stopped smoothly, but the heavier ball reaches the foam's limit and **bottoms out**.

**Bottoming out** means the foam reaches the end of its usable compression and stiffens. From this point on, forces and peak deceleration spike sharply, effectively like hitting a hard layer.

I believe when such bottoming out happens, we can measure extreme acceleration and jerk values - way above any safe limit we are normally even discussing in our standards.

_Note: I'm looking for drop test CSV files of such bottomed out drop tests on foam protectors. If you can, please share sample files._

#### Drop tests

Now you can see the core of the problem: if we make a drop test with a 50 kg dummy, we have no information about what happens on the same protector with a 60-70-80 kg dummy.

It might bottom out at 70 kg or it might not. No one knows, possibly not even the manufacturers!

**The only way to know if a protector bottoms out on a 70 kg dummy is to test it with a 70 kg dummy.** No way around it.

At this point I have to note that I'm absolutely puzzled by the fact that in our industry where both paragliders and rescue parachutes have weight ranges by definition, we don't have weight ranges for back protectors.

**Proposed solution**: introduce weight ranges. Test each protector at both ends of the weight range.



### 2. Under-calculated dummy weight

There is another problem with the existing test's 50 kg dummy weight: it has been extremely under-calculated.

It is based on the faulty assumption that if we measure the forces acting on the pilot, then we only care about the weight compressing the spine, so the current formula took the average adult torso weight of 50 kg and used it for decades.

But here lies a very serious logical fallacy! The primary criteria for all our measurements is to make sure that the protectors don't bottom out: it doesn't matter what's compressing them, it can be a pilot + harness + ballast or even a bag of sand! We are measuring how the protector behaves under real-world compression, thus we have to simulate the real-world compression events. 

Which, for a competition pilot flying at 125 kg take off weight cannot be a 50 kg dummy weight!

<img src="assets/sandbag.jpeg" alt="Illustration with a bag of sand" width="600">

**Proposed solution:**

**Test with 80% of clip-in weight** - (clip in-weight means: take-off-weight excluding glider)

This assumes that the majority of the falls happen leg first, hence the 20% reduction.

Still, in cases where the pilot arrives back-first, this number would be close to 100%.

Quick estimation for the leg-first case: 

- a comp pilot is flying a 125 kg glider @ 120 kg
- glider is about 6 kg
- => the pilots clip-in weight is 114 kg

I believe a realistic dummy weight for such pilot would be about:

114 kg * 0.8 => **91 kg**.

It is **almost double **of the currently used **50 kg dummy** weight!

---



I believe there is no point of even discussing measurements, G, jerk, time based values or composite measures like HIC until we are putting pilots on protectors which are overloaded by almost a factor of 2x!

If pilots were getting injured on overloaded rescue parachutes, it'd be a scandal. Yet with protectors we continue like nothing happens and start discussing complex measurements like HIC before even addressing the basic fault in the standard.



---

### 3. Spine area not protected

There are two kind of injuries we need to take into account.

1. **Compression fractures**
1. **Direct impact injuries**



<img src="assets/directhit.png" alt="directhit">

The existing standard takes care of the compression fracture direction quite well, using the following dummy configuration.



<img src="assets/fixed-drop-test.jpeg" alt="fixed-drop-test" width="250">

*(Illustration started as the one from Fred's video, I fixed the angle and made it cleaner.)*



What's not addressed is **direct impact injuries**.

Direct impact injuries are extremely common on failed takeoff and landings with stalled gliders. Previous generation racing harnesses have covered this area quite well, and many non-competition XC harnesses cover it today. The problem is that some aerodynamically optimised harnesses lack this protection altogether.

**Proposed solution:** **Add 2 more testing points along the spine**, in addition to the sitting position test point being done today.

Proposed new testing points:

- **thoracolumbar junction (T11 - L2 region)**
- **lumbosacral junction (L5 - S1 region)**

both critical points for direct impact injuries.

Anatomy illustration from Wikipedia:

<img src="assets/vertebrae-wikipedia.png" alt="Vertebrae column" width="200">

### 4. Missing jerk limit

The NASA studies frequently referred in back protector discussions do studies on 3 kinematic variables:

- acceleration (e.g. 42 G)
- jerk (e.g. 1300 G/s)
- time based measurements (e.g. 25 ms over 20 G)

The current EN standard incorporates limits on acceleration and time based measurements, while missing the jerk limit test.

This is especially relevant: problematic protectors, like Koroyd has multiple times the safe jerk limit of what NASA suggests.

Meanwhile previous generation foam protectors are within the safe limits.

**Proposed solution:** add a **jerk limit criteria** to the test.

I'm not proposing to take the NASA limit. I'm proposing to re-measure this value on previous-generation known-safe harnesses (Exoceat, Kanibal 2) at a realistic dummy weight for an average comp pilot. (e.g. 75 kg).



### 5. Single-use protectors allowed on competitions

An other big problem with protectors like Koroyd is they are single-use materials: if they get crashed, they'll crumple and have to be replaced.

<img src="assets/koroyd-crumpled.jpg" alt="Koroyd crumpled" width="600">

(Source: DHV)

This might not be problem for a hobbyist pilot making an XC flight, as they can just wait with their next flight until they bought a new protector.

Meanwhile for cross-country competitions it is not acceptable: if someone uses their protector on the 1st day of a Cat1, they should not be risking their life flying with a crumpled protector during the next 9 tasks.

**Proposed solution:** introduce two classes of protectors:

- single use (-S)
- multi-use (-M)

The tests are identical, except for multi-use protectors, the process starts with stress-test: making 5 unmeasured drops at the upper weight limit. The real, measured drop tests start afterward.

Who decides which class to use: the manufacturers submit their product in the class they choose.

The decision between -S and -M would be enforced on competition level, for example cross-country Cat1 events could require multi-use (-M) protectors.

Meanwhile, H&F events with supporters, might allow single-use (-S) protectors as well, as a supporter in the car can carry a spare protector.



## Problems with the upcoming EN draft

*Note: As EN draft is not public and is still a work-in-progress, I'm referring to Fred Pieri's work as "EN draft". Fred's work can be seen in his great [video](https://www.youtube.com/watch?v=EnRK16sgj8A) and [article](https://fredvol.bitbucket.io/Misc/jerk_analysis/p2/report_jerk_p2.html).*

The main problems with the EN draft is that none of the previous points are being addressed.

Moreover instead of introducing a jerk test, they introduce a measure called HIC (or SIC).

### Problems with HIC and "SIC"

HIC (Head Injury Criterion) sounds interesting, but I believe it's not a substitute for jerk limit.

I believe first we need to get the basic, wildly researched kinematic variables right: acceleration, jerk, time-based limits

Only once we got the basic variables right, we can start evaluating if HIC and other composite measures would bring an improvement.

As for "SIC", I cannot wrap my head around the fact that the proposal takes something called "Head Injury Criterion" and changes an exponent from 2.5 -> 2 and renames it to "Spine Injury Criterion".

<img src="assets/sic.gif" alt="sic">

This is wrong on many levels. Science doesn't work like this. We cannot just invent medical "criterions" by changing names and exponents without doing medical studies.

I understand the idea behind it: it is to replace the step function limits (white line below) with a single line. We adjust the exponent to get the line angle correct. [Fred's video](https://www.youtube.com/watch?v=EnRK16sgj8A) does a brilliant job of explaining it.

<img src="assets/CleanShot 2025-12-29 at 14.28.20@2x.png" alt="SIC comparison">

But please don't call it "Spine Injury Criterion", call it "Time-Acceleration Limit" or similar. I believe it's worth discussing, it's an interesting idea, it's just the name which I cannot get over.



### Problems with time based limits

Now we've arrived at what I believe is the biggest question in back protectors:

**Are time based limits actually reflecting pilot injuries?**

I believe based on the pilot reports I collected for the article: [Protector Incident Research: Koroyd vs Airbag](https://hyperpilot.substack.com/p/protector-incident-research-koroyd), that the answer is **no**.

Take this example from Fred's video.

<img src="assets/CleanShot 2025-12-29 at 14.33.47@2x.png" alt="blue vs orange G">

- The blue protector could be a below-average foam protector @ 40 G (Exoceat and Kanibal is at 36-37 G).
- The orange protector could be a high quality inflatable airbag @ 31 G.

The blue graph shows higher jerk (steeper sides) while the orange shows lower jerk (less steepness).

Fred reasons that the blue is the safer protector and this is reflected in the SIC measure he is proposing: the blue protector gets the lower SIC value (10) vs the orange one (11).

<img src="assets/CleanShot 2025-12-29 at 18.56.51@2x.png" alt="blue vs orange SIC">



This is exactly the opposite of what I've found in my research: I'd clearly choose the orange protector for my own protection today.

**Why?**

Because real-world pilot injury reports show that the best protectors available today are **low G, low jerk full-sized airbags**, exactly like the orange protector.

Moreover, if we look a bit on these graphs, we can see that jerk and time-based limits are inversely correlated: the steeper the curve => the shorter the "time above 20 G" horizontal line is.

This is confirmed by the existing EN test reports and their estimated jerk values:

- Gin GR5: 17.5 ms | jerk ~5369 G/sec

- Submarine: 18.3 ms | jerk ~8000 G/sec

- Exoceat: 19.5 ms | jerk ~ 1245 G/sec
- Kanibal: 19.6 ms | jerk ~1216 G/sec
- Skywalk RXA3: 22.5 ms | jerk ~1186 G/sec

We can see that **protectors with the lowest jerk have the highest time-based limits.**

*Note: this comparison was only for the "time over 20 G" value, not the full HIC computation. It'd be great to calculate the exact values for these 5 harnesses above.*

So here are my biggest problems with the HIC:

- We don't know if HIC reflects real world injuries, whereas we know that high jerk does. The NASA studies and the pilot reports agree in this.
- Time-based limits are inversely correlated with jerk. I'm afraid HIC is also behaving like this, possibly pushing us in the wrong direction and killing the safest protectors available today: inflatable airbags.

Of course this is just my view and is only based on a few dozen accident reports, so feel free to question it. I understand that the accident reports are just "anecdata", but they do correlate with the NASA study.



**Proposed solution 1**: I'd propose to go lower on jerk limits for now and set up a website to collect as much "back protector incident report" as we can. If there were 50 fatalities in Switzerland and France alone in a single year, then I believe there are thousands of cases where a protector makes a difference between hospital and walking away.

CIVL should set up a very simple to use "back protector incident report" website where pilots can write a few line about their incident outcomes and upload IGC files. With IGC files, we can analyse impact speeds, instead of just trusting pilot anecdotes.



**Proposed solution 2**: Also, an interesting approach would be to make comp harnesses with multiple protectors and let the market figure out the answer to which one is safer.

For example, if Submarine 2 came out with an option of inflatable airbag and a honeycomb protector, within a few season pilots would settle on the one with better real-world performance.

Of course this would require that the available space for a protector allow an inflatable protector to function correctly, for example 15 cm, but jerk limits would take care of that.
