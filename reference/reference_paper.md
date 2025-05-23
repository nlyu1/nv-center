
<!-- Page 1 -->

Muon Lifetime and Mass Experiment
Anthony Alexiades Armenakas1, ∗ and David Dye1, †
1Department of Physics, Harvard University, Cambridge, MA, 02138, USA
We measure the lifetime and mass of muons decaying in a plastic scintillator. Muons arising from
cosmic ray interactions in Earth’s atmosphere reach the planet’s surface, providing an opportunity
to study particle physics at sea level. We found appropriate conditions for capturing muon events
by setting threshold values and pulse widths for scintillator event discriminators, and we measured
the lifetime and mass of muons by recording the time between configured start and stop signals over
thousands of events. We fit a statistically-informed nonlinear function to the lifetime data to obtain
a muon lifetime estimate of 2.207 ± 0.013 µs. Finally, we determined muon mass by observing the
voltage signal height distribution of electrons generated by muon decays, obtaining an estimate of
85 ± 21 MeV c−2.
## I.
## Introduction
Muons are subatomic particles bearing the same neg-
ative charge as electrons but with a significantly greater
mass. They reach Earth’s surface through the interac-
tion of cosmic rays with Earth’s atmosphere. At sea level,
muons constitute approximately 80% of cosmic radiation,
with electrons composing the remaining 20 % [1]. Muons
are unstable and rapidly decay into an electron, muon
neutrino, and electron antineutrino [2]. This decay pro-
cess, known as a decay channel, is represented as:
µ− → e−νµ¯νe.
Similarly, muon antiparticles, which are known as posi-
tive muons, undergo the corresponding antiparticle decay
channel into a positron, muon antineutrino, and electron
neutrino:
µ+ → e+¯νµνe.
We measure the lifetime and mass of positive and neg-
ative muons in a plastic scintillator. Our setup consisted
of three vertically stacked plastic scintillators as detec-
tors.
The majority of muons have high energies and
pass through all three scintillators, while a fraction are
stopped in the detector and decay in the middle scintil-
lator [3]. We converted the signals from the three scin-
tillators into electrical signals, and using gate logic we
selected for events where a muon stopped and decayed
in the middle scintillator.
We used a disciminator to
filter events, ensuring that only signals exceeding a pre-
calibrated threshold were recorded, thereby selectively
capturing muon events.
Using gate logic, we set start
and stop conditions for the muon lifetime measurement
and measured the time between these conditions.
We
used a gate generator and delay box to record lifetimes
within a suitable range. The experimental setup is de-
scribed in detail in subsequent sections and is illustrated
in Fig. 1.
∗ aarmenakas@college.harvard.edu
† ddye@college.harvard.edu
We conducted a statistical analysis of the data ac-
quired from our experimental setup to estimate and sub-
tract background, thereby obtaining more accurate esti-
mates for the muon lifetime and mass. Our estimated
muon lifetime is 2.207 ± 0.013 µs, aligning with contem-
porary state-of-the-art measurements. We calculated the
muon mass to be 85 ± 21 MeV c−2, with the widely ac-
cepted value falling within one standard deviation of our
estimate.
## Ii.
## Experimental Methods
## A.
Apparatus Design and Muon Detection
A simplified circuit diagram (not showing logic) is pro-
vided in Fig. 1. Three vertically stacked plastic scintil-
lators detect ionizing particles by emitting a light pulse
upon particle absorption. An Amperex XP2020 photo-
multiplier tube (PMT) located at the end of each scintil-
lator converts the light signal into an electrical signal.
The three PMTs are powered by three distinct Ortec
556 high voltage power supplies, and the three electrical
signal outputs from the PMTs are connected to LeCroy
428F linear fan-out signal splitters. For each of the three
PMT signals, an output from their respective linear fan-
out is passed to a discriminator that converts a signal of
sufficient threshold voltage to a rectangular pulse of tun-
able duration. Thus, there are three parameters that may
be adjusted to control signal detection and pulse genera-
tion for each scintillator: supplied voltage, discriminator
threshold, and pulse duration.
Higher voltage increases the PMT sensitivity: too low,
and too few muons will elicit a signal; too high, and back-
ground noise not due to muon events may elicit a sig-
nal. Similarly, the discriminator threshold may be used
to eliminate noise events: too high of a threshold re-
sults in too few muons eliciting a pulse, and too low of
a threshold results in more background noise eliciting a
pulse. We aimed to find an optimal voltage and discrim-
inator threshold for each PMT in order to maximize the
number of muon events resulting in a pulse and minimize



<!-- Page 2 -->

(a)
(b)
FIG. 1. (a) Simplified circuit diagram. Each PMT is powered by its own high voltage power source, and the resulting signal
is processed by the linear fan-out (LFO), discriminator (D), coincidence modules (C), and gate generator (GG). A successful
start signal triggers a delay from the delay box, after which a stop signal indicates the muon’s decay. When the stop signal
is read by the oscilloscope, the LabVIEW controller records the muon’s lifetime and electron signal height. (b) Example of a
lifetime signal measured by the LabVIEW controller.
the number of background events resulting in a pulse.
To determine the optimal voltage and discriminator
threshold for each PMT, we measured the relative effi-
ciency of each detector using the ratio of events detected
in all three scintillators to events detected in the other
two scintillators. For example, the efficiency of the mid-
dle PMT, EM, is given by:
EM = N(T ∧ M ∧ B, t)
N(T ∧ B, t)
,
(1)
where ∧ is the logical “and” operation, T, M, and B
represent detected events in the top, middle, and bottom
scintillators, respectively, and N(x, t) counts the number
of times x was observed over a time duration t. Anal-
ogous definitions are used to compute ET and EB. We
plot ET , EM, and EB as functions of voltage and dis-
criminator threshold in Fig. 2, where t was chosen such
that N(x, t) ≥ 100 for a given x.
In theory, the optimal voltage and threshold are found
when efficiency changes slowly compared to the voltage
or threshold, since this regime occurs when noise is not
yet detected and most muons result in a pulse detection.
However, we observe in Fig. 2 that there is no clear regime
where efficiencies plateau that is not near 100% or 0%
efficiency, where the efficiency is guaranteed to plateau.
Thus, we instead opted to maximize the number of events
observed while accounting for any plateau regimes in the
efficiency curves. This approach requires accounting for
additional background noise through statistical methods
in Section III. We specifically chose to work with two
sets of values, and we compare estimated background
noise rates for these two parameter settings. For the first
settings, we chose discriminator threshold values to be
−1100 mV, −600 mV, and −500 mV and input voltages
to be −2.2 kV, −2.3 kV, and −2.2 kV for the top, middle,
and bottom scintillators, respectively.
For the second
settings, we chose discriminator threshold values to be
−1200 mV, −900 mV, and −1100 mV and input voltages
to be −2.1 kV, −2.3 kV, and −2.2 kV for the top, middle,
and bottom scintillators, respectively.
## B.
Muon Lifetime Experiment
With these threshold and voltage values set, we then
define our trigger logic and pulse widths. This consists
of defining consistent, non-overlapping start and stop sig-
nals for muon events.
Because we are interested in muon lifetimes, we need
to find the subset of detected muons that stop moving
within our detection apparatus and then decay some time
later. A muon that stops within the middle scintillator
is detected by the event T ∧ M ∧ B, where an overbar
signifies negation—intuitively, this logic attempts to cap-
ture the event when a muon enters the top and middle
scintillators but does not enter the bottom scintillator.
This event is the start condition for a given lifetime ex-
periment trial.
A muon trapped in the middle detector will eventu-
ally decay into either (i) an electron, muon neutrino, and
electron antineutrino or (ii) a positron, electron neutrino,
and muon antineutrino. We can set a stop condition to be
when the electron or positron exits the stack of detectors
by passing through either both the middle and bottom or
both the middle and top detectors. Thus, the stop signal
for the muon lifetime is: (T ∧ M ∧ B) ∨ (T ∧ M ∧ B),
where ∨ is the logical “or” operation.
Of note is that the start condition also satisfies the stop
condition. This means a new muon that stops within the
middle scintillator will appear like a decay of the pre-
viously detected muon, causing a false stop event. Be-
sides a new muon event, it is also possible for background
noise to spuriously trigger a stop event. We assume that
both background noise and new muon events should oc-



<!-- Page 3 -->

(a) Scintillator Efficiency vs. Voltage
(b) Scintillator Efficiency vs. Discriminator
Threshold
FIG. 2. Scintillator efficiency curves—especially for voltage—do not show clear plateaus for optimal operation regimes.
cur with uniform probability over the lifetime experiment
duration, and we account for these events accordingly in
Section III A.
Assuming no background events occur, the time be-
tween the start and stop signals is the muon lifetime. In
order to reduce triggering on background measurements
that do not correspond to accurate muon lifetimes, we
construct a 24 µs delay gate to start 120 ns after the start
pulse. We chose 24 µs as the delay since it is much longer
than the typical muon lifetime, and should therefore be
sufficient for observing any stop events. By applying an
AND gate between the delay gate and the stop signa-
ture and taking its output to signal the end of the muon
lifetime, we only record start and stop signals that are
within 24 µs of each other. We encoded the start and
stop signals with appropriate discriminator pulse widths
and delays using a coaxial delay box, Lecroy 622 Quad
Coincidence Unit, and Lecroy 222 Dual Gate Generator.
An OR gate between the start and stop pulse was visual-
ized on an oscilloscope that was triggered by a LabVIEW
virtual instrument on the stop event.
## C.
Muon Mass Experiment
Besides the logic applied to the muon lifetime exper-
iment, the muon mass experiment additionally required
the direct signal from the middle PMT. To record this,
we sent a secondary output from the LeCroy 428F linear
fan-out signal splitter directly to the oscilloscope. The
PMT signal lagged behind the start and stop pulses due
to the discriminator and various logic gates applied to the
signal, so the LabVIEW script for the muon mass exper-
iment was set to search 240 ns before a pulse to find the
associated middle PMT signal. Note that there will al-
ways be a middle PMT signal for a start or stop pulse.
The mass LabVIEW script extracts and saves the maxi-
mum height of the middle PMT signal within the 240 ns
lag before the stop event as well as the lifetime associated
with the observed muon decay. If the stop signal corre-
sponds to a muon decay, then the measured signal height
is due to absorption of the electron or positron emitted
during the decay. We will denote this as the “electron
signal height.”
Each electron signal height is recorded in volts, but
we can find a linear transformation to energy by finding
the voltage at which the most electrons pass through the
entire scintillator apparatus, since this corresponds to the
muons that lose the least energy as they move through
the scintillator material. In Section III B, we show how
this voltage informs the transformation from voltage to
energy. We find this optimal voltage by experimentally
computing a distribution of middle PMT signal heights
for muons that triggered a T ∧M ∧B event. The voltage
corresponding to the highest number of events must have
the minimum energy loss in the scintillator material.
Thus, the muon mass experiment has two components.
The first component is finding a calibration point to
convert an observed voltage to energy, and the second
component is measuring a distribution of electron signal
heights. In Section III B, we show how these two experi-
ment components can be used to compute muon mass.
## Iii.
## Analysis Methods
## A.
Computing the Muon Lifetime
In this section, we consider the computation of a single
muon lifetime from multiple experiments that may have
different rates of background noise. We perform M ex-
periments producing {Nj}M
j=1 individual muon lifetime



<!-- Page 4 -->

measurements, denoted {{ℓij}Nj
i=1}M
j=1. The approach we
take will be estimating the jth muon lifetime from the
jth set of lifetime measurements, and then estimating a
final muon lifetime by taking a weighted average of the
M estimates.
We assume that the stop event can be triggered in
one of three ways: (1) the muon decays into an electron,
muon neutrino, and electron antineutrino, (2) the muon
decays into a positron, electron neutrino, and muon an-
tineutrino, or (3) a background noise event occurs, due
to either a new muon producing a start event or ran-
dom noise.
We further assume that both (1) and (2)
give decays with the same lifetime; the random variable
representing the time at which a muon decays is dis-
tributed exponentially with the same decay parameter
regardless of the decay type. Finally, we assume that the
random variable representing a background noise event is
distributed uniformly over the time during which events
are measured.
We now define key variables and parameters. Let ti
be the first time after the start pulse that noise can be
observed (with no gates or data processing, ti = 0), and
let tf be the last time after the start pulse that noise
can be observed. Additionally, let L ∼ Expo(1/λ) be a
random variable representing the muon lifetime, where λ
is the muon lifetime that we want to estimate. Then, let
B ∼ U(ti, tf) be a uniformly distributed random variable
representing the time at which background noise or a
new muon start pulse is observed, and let S ∈ [0, ∞) be
the random variable representing the observed lifetimes.
Finally, let EB be the event that background noise or a
new muon start pulse is observed, EL be the event that
a muon decay is observed, and γ be the probability that
an observed event is due to noise.
This is enough to write out the log-likelihood of observ-
ing {ℓij}Nj
i=1 given the parameters γ and λ. Let pX(x) be
the probability density function for a random variable X
evaluated at X = x. Then, by the law of total probabil-
ity:
pS(ℓ) = pS(ℓ|EL)P(EL) + pS(ℓ|EB)P(EB),
(2)
which, by the above definitions, is:
pS(ℓ) =
� 1−γ
λ exp
�
− ℓ
λ
�
+
γ
tf −ti ,
ti ≤ ℓ ≤ tf
1−γ
λ exp
�
− ℓ
λ
�
,
otherwise
.
(3)
Since each lifetime measurement is taken independently
of all the others, the joint probability density function
for the dataset {ℓij}Nj
i=1 is simply:
pS1,...,SNj (ℓ1j, . . . , ℓNjj) =
Nj
�
i=1
pSi(ℓij),
(4)
and the log-likelihood function is:
## L
�
λ, γ|{ℓij}Nj
i=1
�
=
Nj
�
i=1
ln (pSi(ℓij)) .
(5)
We will only consider ℓij ∈ [ti, tf], so the log-likelihood
becomes:
L(λ, γ) =
Nj
�
i=1
ln
�1 − γ
λ
exp
�
−ℓij
λ
�
+
γ
tf − ti
�
.
(6)
Then, let λj and γj be the parameters maximizing the
probability of observing {ℓij}Nj
i=1, which is equivalent to
maximizing the log-likelihood. Thus:
(λj, γj) =
arg max
(λ,γ)∈(0,∞)×[0,1]
## L
�
λ, γ|{ℓij}Nj
i=1
�
,
(7)
which can be solved numerically using a standard numer-
ical optimization algorithm.
The next task is computing the error on our estimate
for λj. Assuming Nj is sufficiently large, the estimate for
λj must obey a central limit theorem (CLT) as Nj → ∞
since {λij}Nj
i=1 are independent events. Specifically, we
have estimated that the number of independent draws of
L is given by (1 − γj)Nj, where L ∼ Expo(1/λ). The
CLT for n independent, identically distributed random
variables {X} with mean µ and variance σ2 is:
√n( ¯X − µ)
a.s.
→ N(0, σ2).
(8)
Plugging in L for {X}, using properties of the exponen-
tial distribution, and taking Nj → ∞ gives:
(λj − λ)
�
(1 − γj)Nj ˙∼ N(0, λ2
j).
(9)
Using properties of the normal distribution gives:
λj ˙∼ N
�
λ,
λ2
j
(1 − γj)Nj
�
,
(10)
which shows that the variance of λj is:
σ2
λj =
λ2
j
(1 − γj)Nj
(11)
as Nj → ∞.
So far,
we have derived a way of converting a
dataset {{ℓij}Nj
i=1}M
j=1 to a set of lifetime estimates, noise
probabilities, and lifetime variances, which we denote
{(λj, γj, σ2
λj)}M
j=1, by solving the optimization problem
given by Eq. (7) M times. The final task is to compute
a single lifetime estimate ˆλ from this reduced set. A rea-
sonable choice is to take a weighted average of {λj}M
j=1,
where the weights are given by {1/σ2
λj}M
j=1:
ˆλ =
## �M
j=1 λj/σ2
λj
## �M
j=1 1/σ2
λj
.
(12)
This is a good choice for the estimate because its vari-
ance is guaranteed to be at most the smallest variance



<!-- Page 5 -->

of {σ2
λj}M
j=1. To see that this is true, we compute the
variance of ˆλ as:
σ2
ˆλ =
## �M
j=1 1/σ2
λj
,
(13)
which implies that 1/σ2
ˆλ = �M
j=1 1/σ2
λj. Thus, for this
choice of weights:
σ2
ˆλ ≤ min
j [σ2
λj].
(14)
To summarize, the process for computing a lifetime
estimate and its variance given a dataset {{ℓij}Nj
i=1}M
j=1
is to (1) compute {(λj, γj, σ2
λj)}M
j=1 using Eqs. (7) and
(11), then (2) compute ˆλ and σ2
ˆλ using Eqs. (12) and
(13).
## B.
Computing the Muon Mass
As discussed in Section II C, our goal is to find a con-
version between a PMT voltage signal V and the energy
E of the particle that generating it. We only need a sin-
gle point to find such a conversion since E = aV for some
constant a. Because the greatest number of muons will
pass through the scintillators when the energy loss of the
muons in the scintillator is minimized, we use the scin-
tillator geometry, the maximum of a voltage height dis-
tribution, and existing data on the energy loss of muons
in carbon to compute a.
A figure giving the energy loss rate of muons in carbon
is provided by [4] and shown in Fig. 3(a). The minimum
in ⟨−dE/dx⟩ at ⟨−dE/dx⟩min = 1.75 ± 0.03 MeV g−1
cm2 represents the minimum energy loss rate for muons
travelling through carbon. The scintillators we use are
hydrocarbons, and, because muons do not interact with
the hydrogen molecules, we can use the carbon curve to
find the energy loss rate in our scintillators.
From the muon mass experiment described in Section
II C, we obtain calibration data giving a set of N middle
PMT signal heights that we denote {hµ
i }N
i=1. These signal
heights are plotted as a histogram in Fig. 3(b). We see a
clear peak in the distribution occuring at the histogram
bin centered at V µ
max = 0.11 ± 0.01.
To find a, we introduce two more parameters. Let ρ
be the density of the scintillators, and let d be the height
of a scintillator. Then:
Emin = ρd
�
−dE
dx
�
min
.
(15)
Since a = E/V and we know Emin corresponds to V µ
max:
a =
ρd
V µ
max
�
−dE
dx
�
min
.
(16)
Thus, the conversion from a PMT voltage signal V and
the energy E of the particle that generated it is given by:
E(V ) = ρd
## � V
V µ
max
� �
−dE
dx
�
min
.
(17)
Now equipped with a conversion from signal voltage to
particle energy, we are ready to address the muon mass
calculation. We assume that neutrinos and antineutrinos
have a negligible mass contribution to their energy in
comparison to the contribution due to momentum. In
addition, we simplify the physics to consider a single-
step decay in which a muon decays into the electron,
neutrino, and antineutrino simultaneously, ignoring the
intermediate W-boson decay. We also only consider the
electron decay and not the positron decay by assuming
that the mass of a muon is the same as the mass of an
antimuon.
The neutrino and antineutrino will decay in opposite
angles about the electron momentum vector (see Fig. 4).
Let θ ∈ (−π/2, π/2) be the angle along which the neu-
trino decays relative to the electron momentum vector,
and let Eµ, Ee, Eν, and E¯ν represent the energies of the
muon, electron, neutrino, and antineutrino, respectively.
Similarly, define pµ, pe, pν and p¯ν as the particles’ mo-
menta.
The energy of a relativistic particle x is given by:
Ex =
�
m2xc4 + c2∥px∥2.
(18)
Thus, we have Eν = c∥pν∥ and E¯ν = c∥p¯ν∥ = c∥pν∥. The
muons decay from rest since they are trapped in the mid-
dle scintillator; therefore, Eµ = mµc2. By conservation
of energy and momentum, we have:
mµc2 = 2c∥pν∥ + Ee,
∥pe∥ = 2∥pν∥ cos θ.
(19)
Simplifying and writing everything in terms of Ee and θ
gives:
mµ = 1
c2
�
Ee +
�
E2e − m2ec4
cos θ
�
.
(20)
As we do not know the distribution of θ in terms of Ee,
we must find the muon mass in a limiting case. For this
case, notice that the electron energy must be bounded
by the muon energy minus the neutrino energies; thus,
there is a maximum possible electron energy that we may
observe. The problem now becomes finding the value of
θ that maximizes Ee. We can use Eq. (20) to write Ee
in terms of θ:
Ee =
−mµc2 cos2 θ + c2�
m2µ cos2 θ + m2e sin2 θ
sin2 θ
.
(21)
Computing dEe/dθ = 0 shows that Ee is maximized as
θ → 0; i.e.:
θmax =
arg sup
θ∈(−π/2,π/2)
[Ee(θ)] = 0.
(22)
Applying this to Eq. (20) gives:
mµ = 1
c2
�
Emax
e
+
�
(Emax
e
)2 − m2ec4
�
.
(23)



<!-- Page 6 -->

(a)
(b)
## Fig. 3.
(a) Muon energy loss rate in various materials [4].
The minimum for muons traveling through carbon occurs at
⟨−dE/dx⟩ = 1.75 ± 0.03 MeV g−1 cm2. (b) Muon signal height distribution from the middle PMT, computed from {hµ
i }N
i=1.
FIG. 4. Simplified muon decay diagram according to our as-
sumptions. The muon decays from rest.
Finally, we assume that Emax
e
≫ mec2 to obtain an equa-
tion for mµ in terms of Emax
e
:
mµ = 2Emax
e
c2
,
(24)
or, using Eq. (17) to convert Emax
e
to V e
max:
mµ = 2ρd
c2
�V e
max
V µ
max
� �
−dE
dx
�
min
.
(25)
Note that V µ
max refers to the voltage due to muon events
at which a maximum in a count distribution occurs,
whereas V e
max refers to the voltage due to a muon decay
(electron) event at which any higher voltage readings are
due to background noise.
We assume that ρ, d, V e
max, V µ
max, and ⟨−dE/dx⟩min
are independent variables, which means the error in these
measured quantities can be propagated to mµ using:
σ2
mµ = m2
µ
� �dE
dx
�−2
min
σ2
⟨ dE
dx ⟩min + σ2
ρ
ρ2 + σ2
d
d2
+
σ2
V e
max
(V e
max)2 +
σ2
V µ
max
(V µ
max)2
�
.
(26)
Equations (25) and (26) can be used to find and estimate
error for the mass of a muon using muon and electron
signal height data.
## C.
Computational Methods
We used Python 3 running in a Google Colab file to
perform all data analysis and numerical methods. Three
Python libraries aided computation: we used (i) NumPy
as a general computational toolbox for scientific com-
puting, (ii) SciPy’s optimize.minimize for numerically
optimizing Eq. (7), which we multiply by negative one
to switch the maximization problem to a minimization
problem, and (iii) Matplotlib for histogram binning and
plotting.
## Iv.
## Results
## A.
Muon Lifetime Results
We report a single lifetime measurement of ˆλ = 2.207±
0.013 µs.
We performed M = 3 experiments to esti-
mate muon lifetime. We plot histograms of the recorded
muon lifetimes for each of the three experiments in Fig. 5.
We cut off values below 0.2 µs and above 20 µs to avoid
boundary effects near the edges of our measurement win-
dow.



<!-- Page 7 -->

(a) λ1 = 2.201 ± 0.042 µs,
γ1 = 0.0304
(b) λ2 = 2.189 ± 0.016 µs,
γ2 = 0.0283
(c) λ3 = 2.270 ± 0.029 µs,
γ3 = 0.0739
FIG. 5. Count histogram, computed lifetime estimate λj, and noise probability γj from each of the muon lifetime experiments.
The first two experiments were run with the first list of settings, and the third experiment was run with the second list of
settings, as described in Section II A.
FIG. 6. Comparison of our mean lifetime estimate with the
true mean muon lifetime.
In the first experiment, we obtained a lifetime estimate
of 2.201 ± 0.042 µs and an estimated noise probability of
0.0304. The second experiment yielded a lifetime esti-
mate of 2.189±0.016 µs and a noise probability estimate
of 0.0283.
From the third experiment, we obtained a
lifetime estimate of 2.270 ± 0.029 µs and a noise proba-
bility estimate of 0.0739. We thus have λ1 = 2.201 µs,
λ2 = 2.189 µs, λ3 = 2.270 µs, and variances σ2
λ1 = 0.042
µs, σ2
λ2 = 0.016 µs, and σ2
λ3 = 0.029 µs. By Eq. (12), our
single lifetime measurement is ˆλ = 2.207 ± 0.013 µs.
We compare our estimate to the true muon lifetime
as documented in the 2022 Particle Data Group listings,
which has a value of 2.1969811 ± 0.0000022 µs [5]. As
seen in Fig. 6, the true mean lifetime falls within one
standard deviation of our estimate.
FIG. 7. Histogram from the muon mass experiment showing
the frequency of events over different signal heights. We esti-
mate the maximum value Emax
e
that is not due to background
to be 0.9 V.
## B.
Muon Mass Results
We compute a muon mass of 85 ± 21 MeV c−2. Our
calculation of the conversion ratio a is 47.5±5.4 MeV/V.
As seen in Fig. 3(a), ⟨−dE/dx⟩min = 1.75 ± 0.03 MeV
g−1 cm2. The scintillators are made of plastic of density
1.08 ± 0.05 g/cm3 [2].
The scintillator height is d =
2.5 ± 0.05 cm, and the value of V µ
max is 0.0996 ± 0.01 V.
We plot the histogram of electron signal heights which
we used to estimate V e
max (see Fig. 7). From this data,
we estimated V e
max = 0.9 ± 0.2 V, where our error is so
large because it is not clear exactly where the maximum
voltage height is observed due to background noise in
our measurements. Using Eqs. (17) and (25), we obtain
our estimate for the muon mass, with the error estimate
computed by Eq. (26).



<!-- Page 8 -->

FIG. 8. Comparison of our mass estimate with the true muon
mass.
We compare our estimated muon mass to the updated
value reported by the Particle Data Group, which is
105.6583755 MeV c−2 [5]. As seen in Fig. 8, the true
muon mass falls just within one standard deviation of
our estimate.
## V.
## Discussion
The muon mean lifetime and mass estimates agree with
state of the art contemporary measurements. Taking the
constants reported by the Particle Data Group to be the
true values, our mean lifetime measurement has an error
of 0.45% from the true value, and our mass measurement
has an error of 19.5%.
Both official values fall within
our reported standard deviations. The third experiment
produced the highest noise probability estimate, which is
due to the higher voltage and lower discriminator settings
used in the third experiment.
Lowering the threshold
made it more probable that the PMTs produced a sig-
nal satisfying the pulse threshold on the discriminator.
Increasing the voltage made the PMTs more sensitive to
both muon and background noise events. This increased
sensitivity to background can be seen in Fig. 5, where
more counts remain above zero at later times in panel
(c) compared to panels (a) and (b). Our statistically-
informed estimation protocol for computing γj and λj for
each of the three lifetime experiments ultimately gave an
extremely accurate and precise single estimate for ˆλ.
The greater difference between the center of our muon
mass estimate and the true value is mainly due to the
high variance in the estimation of V e
max. We account for
this variance in our error estimate via the error propaga-
tion by equation (26). With the true muon mass falling
within our error margin, we believe our estimate of the
muon mass to be a success. However, taking additional
measurements and performing more experiments would
help improve the error on our mass estimate.
## Vi.
## Acknowledgements
Both authors would like to thank the teaching staff
of Physics 191:
Jieping Fang, Jason Hoffman, Jenny
Hoffman, and Joe Peidle.
Contributions: Both au-
thors worked on the experimental setup and execution
together. Author AAA wrote the introduction, results,
and discussion sections, i.e. Sections I, IV, and V. Au-
thor DD wrote all of the analysis methods, i.e. Section
III. Both authors worked on the experimental methods
section, with author AAA working primarily on section
II C and author DD primarily on sections II A and II C.
[1] G. F. Knoll, Radiation detection and measurement, 2nd
ed. (Wiley, New York, 1989).
[2] M. Franklin, B4. muon lifetime (1999).
## [3] T.
Ward,
## M.
Barker,
## J.
Breeden,
## K.
Komisarcik,
M. Pickar, D. Wark, and J. Wiggins, Laboratory study of
the cosmic-ray muon lifetime, American journal of physics
53, 542 (1985).
[4] C. Amsler,
J. F. Arguin,
D. M. Asner,
H. Baer,
H. R. Band, T. Basaglia, J. J. Beatty, V. I. Belousov,
G. Bernardi, S. Bethke, et al., Review of particle physics
particle data group, Chinese physics C 38, 10.1088/1674-
1137/38/9/090001 (2014).
[5] R. L. Workman and Others (Particle Data Group), Review
of Particle Physics, PTEP 2022, 083C01 (2022).

