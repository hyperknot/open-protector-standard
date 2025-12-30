# Questions

### Wouldn't heavy pilots need bigger protectors, thus giving them an aerodynamic disadvantage?

This might seem surprising, but heavier pilots don't actually need thicker protectors. They need a different protector material, like stiffer foams in the case of foam protectors. A protector certified for 50 - 60 kg could be equally thin as one certified for 100 - 120 kg.

What makes a protector thick is the need to cover a wide weight range, like 50 - 120 kg.

Interesting bit: the lower end of the weight range is critical for the jerk test, while the upper end is critical for the acceleration / G test.

### What about visibility?

Manufacturers say that making thicker protectors will make visibility worse. I don't agree with this direction.

We used to have good visibility and good protectors. This work now addresses the protectors, and we can look into visibility in the coming years.

The manufacturer statement is based on the assumption that every harness needs to have a perfectly circular cross-section with a symmetrical cigar shape along the horizontal axis.

None of this is a rule set in stone; it's just easier to make harnesses like this.

Manufacturers can use 3D shaping to make the front part narrower compared to the back part, or to add a protector "bump" on the back.

We can also work on making XC racing less gaggle-focused via rules and task setting.

### Who certifies it?

In the current form, no one. The point of the Open Protector Standard is that it can be adopted by CIVL, EN WG6, DHV, or any other standards body.

So in practice, this could become the CIVL Protector Standard and be certified like CCC gliders today. Or DHV can adopt it into their standard. Or EN can address these points, and then we can make this standard shorter and shorter over time.



### Isn't measuring jerk complicated and expensive?

No, it's not. We can do it using the existing drop test equipment. We can simply calculate it from the drop test CSV files via software tools.

As a first step, we need to filter the acceleration data. I believe this is unrelated to measuring jerk; this step would be required for calculating any composite measures, like DRI. Even simple "max G" tests could be affected by noise and should be using filtered data.

The acceleration filter I proposed is the well-known and extremely well-researched "CFC" filter, used for filtering crash test acceleration sensors - exactly what we need. Case in point, EAPR was using this filter in their harness drop tests 18 (?) years ago. It is defined both in the ISO 6487 and [SAE J211/1](https://law.resource.org/pub/us/cfr/ibr/005/sae.j211-1.1995.pdf) standards.

The only value we need to agree on here is the CFC class. I propose CFC 75, based on the CSV samples Fred shared. We can look at more CSV files and settle on a value that filters the noise while keeping the signal.

A bigger problem is self-resonance / ringing of badly attached sensors on the drop test equipment. But this part needs to be fixed anyway, as it can invalidate all kinds of tests, not just jerk measurements. This shows up as resonance / waves on the jerk graph.

Once we have the sensor attachments fixed and the CFC filter applied, getting jerk from acceleration is actually quite simple. I propose calculating the derivative using the Savitzky-Golay filter as it results in smooth derivatives. The only parameter we need to agree on is the window size, for which I propose 15 ms.

### Isn't this expensive for small manufacturers?

This is only an additional test for those manufacturers who want to make racing harnesses for Cat1 and high-level comps. Manufacturers not targeting this group are not affected.

### What about Koroyd tubes rotating / not crumpling?

We can add drop tests on 30 / 45 / 60-degree anvils, but we might never be able to cover all possible failure cases.

The real solution would be to allow CIVL to suspend equipment from Cat1 events where real-world behavior differs from the one shown in the test environment.

### Can we test a harness's behavior for higher impact velocities by testing with higher weights?

Unfortunately not. Even though a 50 kg weight dropped from 1.6 meters has the same energy as a 100 kg weight dropped from 0.8 meters ($E = mgh$), their compression behaviors are different.

Thus we cannot simulate for higher impact velocities by adding weight; we'll need to use higher drop machines to measure that.

### Where is the research for NASA's jerk studies?

The relevant reports are:

[Eiband, A. Martin, 1959 - Human Tolerance to Rapidly Applied Accelerations](https://ntrs.nasa.gov/api/citations/19980228043/downloads/19980228043.pdf)

[Mckenney, William R., 1970 - Human Tolerance To Abrupt Accelerations](https://apps.dtic.mil/sti/tr/pdf/AD0708916.pdf)

[U.S. NAVAL Flight Surgeon's Manual](https://www.scribd.com/doc/49951730/FlightSurgeonsManual).

The Eiband 1959 PDF shows the duration graph on page 78:

![nasa-duration](assets/nasa-duration.png)

And page 81 shows the onset = jerk graph:

![nasa-onset](assets/nasa-onset.png)
