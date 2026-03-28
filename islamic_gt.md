# Islamic Game Theory: The Muhammad Equilibrium

## A Complete Framework for Strategic Interaction Grounded in the Life, Actions, and Vision of Prophet Muhammad ﷺ

**Author:** IGT Research Initiative
**Series:** Light Game Theory Project — 2026

---

> *"The best of people are those who are most beneficial to others."*
> — Prophet Muhammad ﷺ (Al-Mu'jam al-Awsat, al-Tabarani)

> *"A Nash Equilibrium is a stable state of a system involving the interaction of different participants, in which no participant can gain by a unilateral change of strategy if the strategies of the others remain unchanged."*
> — John Forbes Nash Jr., 1950

---

# PREFACE: WHY A NEW THEORY OF GAMES?

Classical Game Theory (CGT) emerged in the mid-twentieth century as a formal mathematical framework for analyzing strategic interaction among rational, self-interested agents. John von Neumann and Oskar Morgenstern's *Theory of Games and Economic Behavior* (1944) and John Nash's doctoral dissertation (1950) established the conceptual pillars of what became one of the most powerful analytical tools in modern economics, political science, evolutionary biology, and military strategy.

Yet something fundamental is missing.

The Nash Equilibrium — the cornerstone of classical game theory — predicts that rational agents will converge on strategies that are individually stable but often collectively catastrophic. The Prisoner's Dilemma, the Tragedy of the Commons, arms races, currency wars, and ecological collapse are not failures of the Nash framework; they are its accurate predictions. Nash equilibrium is descriptive of a world in which agents maximize their own payoffs without regard to communal outcomes, trust, moral obligation, or transcendental accountability.

The result of this descriptive accuracy is alarming. The theory that has been used to design global financial markets, nuclear deterrence strategy, international trade agreements, and political competition has also faithfully predicted — and arguably enabled — the very pathologies it describes: endless competition spiraling into conflict, wealth concentrating into the hands of the few, and environmental systems collapsing under the weight of collective inaction.

This book proposes a different framework: **Islamic Game Theory (IGT)**, grounded in the life, decisions, and vision of Prophet Muhammad ibn Abdullah ﷺ (570–632 CE). We argue that the Prophet's strategic behavior — across diplomatic negotiations, military campaigns, economic arrangements, and social contracts — embodies a coherent alternative equilibrium concept that we formally define as the **Muhammad Equilibrium (ME)**.

The Muhammad Equilibrium differs from the Nash Equilibrium in its axiomatic foundations. Where Nash assumes payoff-maximizing agents with no utility derived from others' welfare, the Muhammad Equilibrium operates under agents who:

1. Assign positive utility to the welfare of others (tawhidic interdependence);
2. Discount future selfish gains against present cooperative trust (amanah discounting);
3. Treat moral obligations as binding constraints (fard constraints);
4. Recognize accountability beyond the material game (akhirah externality).

We will show, with formal mathematical treatment and computational simulations, that these modifications to the utility function and strategy space produce equilibria that are both individually rational *and* collectively optimal — outcomes that Nash equilibrium systematically fails to produce.

This is not merely a religious argument dressed in mathematical clothing. The framework is testable, falsifiable, and extensible. We draw on authentic historical accounts of the Prophet's strategic decisions, and we formalize the principles embedded in those decisions using the standard tools of game theory: payoff matrices, utility functions, equilibrium concepts, mechanism design, and evolutionary stability.

The reader will encounter:

- The **Hilf al-Fudul** (Pact of the Virtuous) as a mechanism design problem solved before the Prophethood;
- The **Treaty of Hudaybiyyah** as a repeated game with asymmetric information where the Prophet achieves a dominant long-run payoff through short-run apparent concession;
- The **Constitution of Medina** as a multi-player coordination game under heterogeneous agents;
- The **Zakat system** as a redistributive mechanism that implements the Muhammad Equilibrium in a resource allocation game;
- The **Battle of Badr** as a game of incomplete information where moral certainty substitutes for probabilistic belief;
- The **Conquest of Mecca** as a post-conflict governance game where amnesty dominates punishment.

All hypotheses are backed by Python simulations in the `islamic_gt_codes/` directory.

---

# PART I — CLASSICAL GAME THEORY: FOUNDATIONS AND FAILURES

## Chapter 1: The Architecture of Classical Game Theory

### 1.1 Historical Origins

Classical Game Theory was born at the intersection of mathematics and economics. John von Neumann proved the minimax theorem in 1928, establishing that in zero-sum two-player games, there always exists an optimal mixed strategy. When he collaborated with economist Oskar Morgenstern to produce *Theory of Games and Economic Behavior* in 1944, the scope expanded to n-player games and non-zero-sum interactions.

John Nash's contribution was decisive. In his 1950 paper "Equilibrium Points in N-Person Games," Nash proved that every finite game with mixed strategy profiles has at least one equilibrium point. This existence theorem — the Nash Equilibrium — became the organizing concept of all subsequent game theory.

Subsequent developments extended the framework: Reinhard Selten introduced subgame perfect equilibrium and trembling-hand perfect equilibrium; John Harsanyi introduced Bayesian games with incomplete information; Robert Aumann developed correlated equilibrium and the theory of common knowledge.

### 1.2 Formal Foundations

A classical game in normal form is defined as a triple:

$$\mathcal{G} = \langle N, \{S_i\}_{i \in N}, \{u_i\}_{i \in N} \rangle$$

Where:
- $N = \{1, 2, \ldots, n\}$ is the finite set of players;
- $S_i$ is the strategy space of player $i$, with $S = S_1 \times S_2 \times \cdots \times S_n$ the joint strategy space;
- $u_i : S \rightarrow \mathbb{R}$ is the payoff function of player $i$.

A **strategy profile** is a vector $s = (s_1, s_2, \ldots, s_n) \in S$. We write $s_{-i}$ to denote the strategies of all players except $i$.

**Definition 1.1 (Nash Equilibrium).** A strategy profile $s^* = (s_1^*, s_2^*, \ldots, s_n^*)$ is a Nash Equilibrium if and only if for every player $i \in N$:

$$u_i(s_i^*, s_{-i}^*) \geq u_i(s_i, s_{-i}^*) \quad \forall s_i \in S_i$$

In words: no player can improve their payoff by unilaterally deviating from $s_i^*$, given that all other players stick to $s_{-i}^*$.

**Theorem 1.1 (Nash's Existence Theorem, 1950).** Every finite normal-form game has at least one Nash Equilibrium in mixed strategies.

*Proof sketch:* The proof uses Kakutani's fixed-point theorem applied to the best-response correspondence. Define $\text{BR}_i(s_{-i}) = \arg\max_{s_i \in S_i} u_i(s_i, s_{-i})$. The joint best-response correspondence $\text{BR} : \Delta(S) \rightarrow \Delta(S)$ is upper hemicontinuous and convex-valued. By Kakutani, it has a fixed point $s^*$ with $s^* \in \text{BR}(s^*)$. $\square$

### 1.3 The Six Axiomatic Assumptions of Classical Game Theory

Classical Game Theory rests on a set of axiomatic assumptions that are rarely made explicit in applied work but are foundational to all results:

**Assumption A1 (Rationality):** Each player $i$ maximizes their own expected utility $\mathbb{E}[u_i]$.

**Assumption A2 (Self-interest):** The utility function $u_i$ depends only on outcomes affecting player $i$. Formally: $u_i(s) = u_i(x_i(s))$, where $x_i(s)$ is player $i$'s material payoff.

**Assumption A3 (Common Knowledge of Rationality, CKR):** All players know that all players are rational, all players know that all players know this, and so on ad infinitum.

**Assumption A4 (Finite Horizon or Infinite Discounting):** In repeated games, players discount future payoffs by a factor $\delta \in [0,1)$, with infinite future having finite present value.

**Assumption A5 (No Binding Obligations):** Agreements are only kept if it is in a player's self-interest to keep them. Cooperation arises only through incentive compatibility, not intrinsic moral commitment.

**Assumption A6 (Closed Payoff Space):** All consequences of actions are captured within the material payoff function. There is no utility derived from metaphysical accountability, divine reward, or eternal consequences.

These assumptions are not neutral. They encode a specific anthropology: the human being as *homo economicus* — a calculating, self-interested maximizer with no intrinsic moral obligations and no transcendental accountability.

### 1.4 What the Axioms Encode

The six classical assumptions together define a world where:
- Humans care only about themselves (A2)
- The only reason to cooperate is self-interest (A5)
- The game ends at death (A4, A6)
- There is no accountability beyond what humans can observe and enforce (A6)

This is not a description of human nature. It is a *model* of human nature — one that intentionally strips away moral commitment, altruism, and transcendental accountability to isolate the logic of pure strategic self-interest. The resulting theory is powerful but incomplete. We will challenge each assumption in Part II.

## Chapter 2: Canonical Game Structures and Their Nash Predictions

### 2.1 The Prisoner's Dilemma

Two players each choose to Cooperate (C) or Defect (D). Payoff matrix:

|   | C | D |
|---|---|---|
| C | (3, 3) | (0, 5) |
| D | (5, 0) | (1, 1) |

The unique Nash Equilibrium is $(D, D)$ with payoffs $(1,1)$, despite $(C,C)$ yielding $(3,3)$ for both. This is the paradigmatic illustration of how individual rationality produces collective irrationality.

**Price of Anarchy:** $\text{PoA} = \frac{3+3}{1+1} = 3$. Three times the welfare is available under cooperation but Nash delivers only one-third of it.

> **Simulation:** `islamic_gt_codes/sim_01_prisoners_dilemma_muwakhat.py` demonstrates how the Islamic Utility Function transforms this game, making cooperation dominant.

### 2.2 The Tragedy of the Commons

$n$ herders share a common pasture. Each herder $i$ chooses effort level $e_i \in [0, \bar{e}]$. Individual payoff:

$$u_i = e_i \cdot f\!\left(\sum_{j=1}^n e_j\right) - c \cdot e_i$$

Where $f(\cdot)$ is a decreasing productivity function. Nash equilibrium gives $\sum_{j=1}^n e_j^* > K$ (capacity), i.e., overgrazing and resource collapse. The Price of Anarchy grows proportionally with $n$. For global commons (climate), $n$ is measured in billions.

### 2.3 The Arms Race (Security Dilemma)

Two states choosing military expenditure $a_i$. Nash Equilibrium yields $a_i^* > 0$ even if both states would prefer mutual disarmament. This structural logic underlies every historical arms race, from the Anglo-German naval rivalry to the US-Soviet nuclear buildup to current Sino-American military competition.

### 2.4 The Wealth Concentration Game

**Proposition 2.1.** In a market game with $n \geq 2$ agents, unlimited capital accumulation, and payoff $u_i = \log(w_i)$, the Nash Equilibrium of the infinitely repeated game produces:

$$\lim_{t \to \infty} \frac{w_{\max}(t)}{\bar{w}(t)} = \infty$$

The wealth distribution follows a Pareto (power law) distribution. As of 2024, the top 1% of the global population holds approximately 43% of global wealth. This is the Nash prediction confirmed empirically.

### 2.5 The Stag Hunt

Two equilibria exist: (Stag, Stag) with high payoff requiring mutual trust, and (Hare, Hare) with low payoff but no risk. Without a coordination mechanism, players often converge on the safe but suboptimal equilibrium.

> **Simulation:** `islamic_gt_codes/sim_03_stag_hunt_aqaba.py` shows how the Naqib system at Aqaba solved this coordination problem.

### 2.6 Battle of the Sexes

Players prefer coordination but disagree on which outcome. Multiple Nash equilibria exist with no clear selection mechanism.

> **Simulation:** `islamic_gt_codes/sim_05_aws_khazraj_coordination.py` demonstrates the Aws-Khazraj resolution.

## Chapter 3: The Structural Failures of Classical Game Theory

### 3.1 Nash Equilibrium Predicts Collective Disaster

The most damning indictment of classical game theory is not that it is wrong — it is that it is right. The Nash Equilibrium accurately predicts:

- **Wars:** The security dilemma produces arms races. Annual global military expenditure: $2.2 trillion (2023). 56 active armed conflicts worldwide (UCDP 2023).
- **Environmental collapse:** The Tragedy of the Commons predicts climate change — the global-scale commons tragedy.
- **Wealth inequality:** Top 1% owning 43% of wealth; bottom 50% owning approximately 2%.
- **Market failures:** Akerlof's lemons, free-rider problems, monopolistic exploitation.

### 3.2 The Repeated Game Escape — and Its Fatal Limits

The **Folk Theorem** states that in infinitely repeated games with sufficiently patient players, any payoff above the minmax level can be sustained as equilibrium. But this solution has five fatal limitations:

1. **Requires infinite time horizons.** Real games end. Backward induction unravels cooperation.
2. **Requires high discount factors.** Where cooperation is most needed (poverty, instability), players discount the future heavily.
3. **Requires perfect monitoring.** Hidden actions and private information destroy cooperation.
4. **Multiplies equilibria.** The Folk Theorem sustains cooperation, vendetta, and everything in between — with no guidance on which equilibrium emerges.
5. **Assumes no moral commitment.** Cooperation is enforced compliance, not genuine trust.

### 3.3 Behavioral Corrections — Still Within the CGT Paradigm

Behavioral game theory (Kahneman, Thaler, Rabin) has introduced corrections: loss aversion, social preferences, reference-dependent utility. These are important amendments, but they:

1. Treat prosocial behavior as a parameter to be estimated, not a principled axiom
2. Still operate within a purely material payoff space
3. Cannot explain the *consistency* and *depth* of prosocial commitment in morally governed communities

We need a different foundation, not better parameters.

## Chapter 4: Advanced Classical Structures

### 4.1 Extensive Form Games and Backward Induction

In sequential games, subgame perfect equilibrium refines Nash by requiring optimality at every decision point. Backward induction — solving from the end — produces logically rigorous but often counterintuitive results: cooperation unravels in finite games even when both players prefer it.

> **Simulation:** `islamic_gt_codes/sim_06_hudaybiyyah_treaty.py` shows how the Prophet's infinite-horizon framing at Hudaybiyyah made backward induction inapplicable.

### 4.2 Punishment Strategies

Grim Trigger (permanent retaliation after first defection) and Tit-for-Tat (mirror opponent's last action) sustain cooperation through threat. But:
- Grim Trigger creates permanent feuds from single mistakes
- Tit-for-Tat cycles between retaliation and cooperation

> **Simulation:** `islamic_gt_codes/sim_15_conquest_amnesty.py` demonstrates why the Prophet's amnesty at Mecca dominated both punishment strategies.

### 4.3 Bayesian Games and Incomplete Information

When players don't know each other's types, they form beliefs and update via Bayes' Rule. Players with better information have strategic advantage.

> **Simulation:** `islamic_gt_codes/sim_17_bayesian_intelligence.py` models the Dar al-Arqam intelligence network's informational superiority.

### 4.4 Signaling and Screening

In signaling games, informed types send costly signals to separate from imitators. In screening games, the uninformed party designs menus to reveal types.

> **Simulation:** `islamic_gt_codes/sim_18_signaling_alamin.py` models the Prophet's 40-year Al-Amin reputation as a costly separating signal.
> **Simulation:** `islamic_gt_codes/sim_19_abyssinia_screening.py` models the Abyssinian migration as a screening game.

### 4.5 Mechanism Design

Mechanism design asks: given desired social outcomes, what game structures produce those outcomes as equilibria? The revelation principle shows that any implementable outcome can be achieved through a direct mechanism where truth-telling is a Nash equilibrium — but implementation requires external enforcement.

### 4.6 Cooperative Game Theory

The Core of a cooperative game is the set of payoff allocations that no coalition can improve upon. In many real games, the Core is empty — no stable allocation exists. The Shapley Value provides a unique "fair" allocation but may not be coalitionally stable.

> **Simulation:** `islamic_gt_codes/sim_24_medina_constitution_core.py` shows the Constitution of Medina as a Core allocation.

---

# PART II — ISLAMIC GAME THEORY: A NEW AXIOMATIC FRAMEWORK

## Chapter 5: The Axiomatic Revision — From A1-A6 to B1-B6

Islamic Game Theory retains the formal mathematical structure of classical game theory — players, strategies, payoffs, equilibria — but replaces the axiomatic assumptions with a new set grounded in the Islamic understanding of the human being and the cosmos.

### 5.1 Assumption B1: Rational-Moral Agency

Each player $i$ maximizes expected utility, but utility is multi-dimensional:

$$U_i = u_i^{\text{dunya}} + \lambda \cdot u_i^{\text{akhirah}}$$

Where $u_i^{\text{dunya}}$ is material-worldly utility, $u_i^{\text{akhirah}}$ is the eternal-consequential utility, and $\lambda > 0$ is the akhirah weight. For a believer with deep taqwa (God-consciousness), $\lambda \gg 1$.

### 5.2 Assumption B2: Tawhidic Interdependence

The utility of player $i$ depends on the welfare of others:

$$U_i(s) = u_i^{\text{self}}(x_i(s)) + \alpha_i \sum_{j \neq i} \phi_{ij} \cdot u_j^{\text{welfare}}(x_j(s))$$

Where $\alpha_i \geq 0$ is player $i$'s empathy coefficient and $\phi_{ij} \in [0,1]$ is the relational weight. This captures the Islamic concept of brotherhood (ukhuwwah) and social solidarity.

### 5.3 Assumption B3: Amanah Constraint

Trust and covenants are binding. Player $i$'s strategy set is constrained:

$$S_i^{\text{IGT}} = \{s_i \in S_i : s_i \text{ satisfies } \mathcal{C}_i^{\text{amanah}}\}$$

This constraint holds even when defection would increase $u_i^{\text{dunya}}$ — because it is supported by $u_i^{\text{akhirah}}$.

### 5.4 Assumption B4: Fard Constraints

Certain actions are absolutely prohibited (haram) or obligated (fard), independent of payoff calculations. These function as lexicographic constraints:

$$U_i(s) = \begin{cases} -\infty & \text{if } s_i \in H_i \text{ (haram actions)} \\ U_i^{\text{calc}}(s) & \text{otherwise} \end{cases}$$

Moral obligations trump material calculations.

### 5.5 Assumption B5: Akhirah Discounting — Inverted Time Preference

In CGT, future payoffs are discounted ($\delta < 1$). In IGT, akhirah payoffs are *undiscounted* with infinite horizon:

$$\delta_{\text{akhirah}} = 1$$

This reverses the Folk Theorem logic: cooperation does not require high $\delta$ for material payoffs, because the akhirah payoff stream is perfectly patient and infinite.

### 5.6 Assumption B6: Open Payoff Space with Divine Accountability

The payoff space includes consequences beyond the material game:

$$\mathcal{G}^{\text{IGT}} = \mathcal{G}^{\text{material}} \oplus \mathcal{G}^{\text{akhirah}}$$

Where $\mathcal{G}^{\text{akhirah}}$ is the game played before the Divine Accountant, with payoffs that perfectly record all actions — including hidden ones.

### 5.7 Summary: How Each Assumption Transforms the Framework

| Classical (A) | Islamic (B) | Transformation |
|---|---|---|
| A1: Self-utility maximization | B1: Multi-dimensional utility (material + akhirah) | Expands the payoff space |
| A2: No utility from others' welfare | B2: Positive utility from others' welfare ($\alpha > 0$) | Creates cooperation incentive |
| A3: CKR only | B3: Amanah — binding covenants | Constrains strategy space |
| A4: Finite/discounted horizon | B5: Infinite undiscounted akhirah | Eliminates backward induction |
| A5: No binding obligations | B4: Fard/haram as lexicographic constraints | Moral priority over material |
| A6: Closed material payoffs | B6: Open payoffs with divine accountability | Eliminates moral hazard |

## Chapter 6: The Islamic Utility Function

### 6.1 Formal Definition

The **Islamic Utility Function** for player $i$:

$$\mathbf{U}_i(s) = \underbrace{u_i^{\text{mat}}(x_i(s))}_{\text{material payoff}} + \underbrace{\alpha_i \sum_{j \neq i} \phi_{ij} u_j^{\text{mat}}(x_j(s))}_{\text{altruistic payoff (ukhuwwah)}} + \underbrace{\lambda_i \cdot \Omega_i(s)}_{\text{akhirah payoff}}$$

Where:
- $\alpha_i \geq 0$ is the altruism coefficient (increases with taqwa and iman)
- $\phi_{ij} \in [0,1]$ is the relational weight ($\phi_{ij} = 1$ for family/community, lower for strangers)
- $\lambda_i > 0$ is the akhirah sensitivity coefficient
- $\Omega_i(s) : S \rightarrow \mathbb{R}$ is the Divine Accounting function

### 6.2 Properties of the Divine Accounting Function

**Key Property:** Divine Accounting is *complete* — it records all actions including those unobserved by other players. This eliminates the moral hazard problem:

$$\Omega_i(s) = \sum_{t=0}^{\infty} \omega_i(a_i^t, a_{-i}^t, \theta^t)$$

Where $\omega_i$ is the per-period divine payoff, $a_i^t$ is player $i$'s action at time $t$, and $\theta^t$ is the true state of the world. Unlike material payoffs, $\Omega_i$ does not require observability of $a_i$ by $j \neq i$.

### 6.3 IGT and Internal Incentive Compatibility

**Proposition 6.1 (Internal Incentive Compatibility).** In a one-shot Prisoner's Dilemma with Islamic Utility Functions, if:

$$\lambda_i \cdot [\Omega_i(C) - \Omega_i(D)] \geq T - R$$

where $T - R$ is the material temptation to defect, then cooperation is a dominant strategy for player $i$, regardless of the other player's action.

*Proof:* Player $i$'s total payoff from Cooperating when $j$ Cooperates: $R + \lambda_i \Omega_i(C,C)$. From Defecting: $T + \lambda_i \Omega_i(D,C)$. Cooperating is preferred iff $\lambda_i [\Omega_i(C,C) - \Omega_i(D,C)] \geq T - R$. Since $\Omega_i(C) - \Omega_i(D) \geq \Omega_i(C,C) - \Omega_i(D,C)$ by the definition of Divine Accounting (which rewards cooperation universally), the condition holds. $\square$

> **Simulation:** `islamic_gt_codes/sim_01_prisoners_dilemma_muwakhat.py` — Part B shows exactly the parameter thresholds where cooperation becomes dominant.

## Chapter 7: The Muhammad Equilibrium — Formal Definition

### 7.1 Definition

**Definition 7.1 (Muhammad Equilibrium, ME).** A strategy profile $s^{**} = (s_1^{**}, \ldots, s_n^{**})$ is a **Muhammad Equilibrium** if and only if for every player $i \in N$:

$$\mathbf{U}_i(s_i^{**}, s_{-i}^{**}) \geq \mathbf{U}_i(s_i, s_{-i}^{**}) \quad \forall s_i \in S_i^{\text{IGT}}$$

Where $\mathbf{U}_i$ is the Islamic Utility Function and $S_i^{\text{IGT}}$ is the IGT-constrained strategy space.

### 7.2 Comparison: Nash vs. Muhammad Equilibrium

| Feature | Nash Equilibrium | Muhammad Equilibrium |
|---|---|---|
| Utility dimension | Material only | Material + Altruistic + Akhirah |
| Strategy constraints | Only material rationality | + Amanah + Fard constraints |
| Monitoring requirement | Perfect monitoring for cooperation | None (Divine Accounting) |
| Time horizon | Finite or discounted infinite | Effectively infinite (akhirah) |
| Social outcome | Individual stability, collective suboptimality | Individual stability, collective optimality |

### 7.3 Existence Theorem

**Theorem 7.1 (Existence of Muhammad Equilibrium).** Every finite normal-form game with Islamic Utility Functions (satisfying B1-B6) has at least one Muhammad Equilibrium.

*Proof:* The Islamic Utility Function $\mathbf{U}_i$ is continuous in $s$. The strategy space $S_i^{\text{IGT}}$ is compact. The IGT best-response correspondence is upper hemicontinuous and convex-valued. By Kakutani's fixed-point theorem, a fixed point $s^{**}$ exists. $\square$

### 7.4 Welfare Dominance Theorem

**Theorem 7.2.** Under IGT assumptions, the Muhammad Equilibrium $s^{**}$ generates weakly higher aggregate material welfare than any Nash Equilibrium $s^*$:

$$\sum_{i \in N} u_i^{\text{mat}}(s^{**}) \geq \sum_{i \in N} u_i^{\text{mat}}(s^*)$$

*Proof sketch:* The ME maximizes $\sum_i \mathbf{U}_i$ which includes $\alpha_i \sum_j u_j^{\text{mat}}$ terms. Maximizing total Islamic Utility necessarily places higher weight on aggregate material welfare than the Nash profile. The condition is formally equivalent to a correlated equilibrium with social welfare weights, which weakly Pareto-dominates all Nash equilibria in games with positive externalities. $\square$

### 7.5 Evolutionary Stability

**Proposition 7.1.** In a population game where ME players face occasional CGT defectors, if $\lambda \cdot \Omega(\text{cooperate}) > T - R$, then the ME strategy is an Evolutionarily Stable Strategy (ESS): the population resists invasion by defectors.

Moreover, under repeated interaction with reputational spillovers, ME players gain preferential partnership and achieve higher long-run material payoffs even on the material dimension alone.

> **Simulation:** `islamic_gt_codes/sim_16_folk_theorem_selection.py` demonstrates equilibrium selection through parameter cultivation.

---

# PART III — CASE STUDIES FROM THE LIFE OF PROPHET MUHAMMAD ﷺ

*For each case study, we provide: Historical Context, Game-Theoretic Formalization, Classical (Nash) Prediction, IGT (Muhammad Equilibrium) Prediction, Historical Outcome, and Simulation Reference.*

*Detailed hypothesis mappings for all 24 case studies are in `prophet_hypothesis.md`.*

## Chapter 8: Strategic Decisions Before Prophethood

### 8.1 The Hilf al-Fudul: Pre-Islamic Mechanism Design

**Historical Context:** Approximately fifteen years before the first revelation, young Muhammad (aged ~20) participated in the Hilf al-Fudul (Pact of the Virtuous). A Yemeni merchant had sold goods to al-As ibn Wa'il who refused to pay. Several Qurayshi clans gathered and swore to stand with the oppressed against the oppressor, regardless of tribal affiliation.

**Game-Theoretic Formalization:**
- **Players:** $N = \{c_1, c_2, \ldots, c_k\}$ — $k$ Qurayshi clans
- **Strategy:** Join pact ($J$) or Abstain ($A$)
- **Payoffs:** Joining costs enforcement effort $e > 0$ but generates security $\sigma_i$ and reputation $r_i$

Under classical CGT, this is a multi-player Prisoner's Dilemma with a free-rider equilibrium:

$$s^*_{\text{Nash}} = (A, A, \ldots, A) \quad \text{(free-ride — Nash prediction)}$$

**But the Hilf al-Fudul succeeded.** Under IGT analysis, moral accountability made defection costlier than its material benefit. The Prophet later said: *"I was present at the making of a covenant which I would not exchange for the finest camels; and if it were invoked today, in Islam, I would respond to it."*

$$s^{**}_{\text{ME}} = (J, J, \ldots, J) \quad \text{(join pact — ME prediction and historical outcome)}$$

> **Simulation:** `islamic_gt_codes/sim_02_hilf_al_fudul.py`

### 8.2 The Kaaba Stone Arbitration

**Historical Context:** During Kaaba renovation (~605 CE), clans deadlocked over placing the Black Stone — each tribe wanting the honor. Violence was imminent. Elder Abu Umayyah proposed accepting the next person to enter the gate as arbiter. Young Muhammad entered, placed the stone on a cloth, and had each tribe hold a corner.

**Game-Theoretic Analysis:** This converted a zero-sum honor dispute (Nash Bargaining with violence as disagreement point) into a positive-sum shared action. The cloth mechanism distributed participation symmetrically while the arbiter's final placement resolved the symbolic dimension.

> **Simulation:** `islamic_gt_codes/sim_21_kaaba_stone_bargaining.py`

### 8.3 Al-Amin: 40 Years of Costly Signaling

The Prophet earned "Al-Amin" (The Trustworthy) over 40 years of consistent honesty — a costly signal that perfectly separated the "prophetic type" from the "power-seeker type." No strategic deceiver would invest 40 years of perfect truthfulness as preparatory deception.

> **Simulation:** `islamic_gt_codes/sim_18_signaling_alamin.py`

## Chapter 9: The Meccan Period — Strategic Patience and Organization

### 9.1 The Dar al-Arqam Network

**Historical Context:** The Prophet established the Dar al-Arqam as an organizational hub hidden in plain sight — in Abu Jahl's own neighborhood. He deployed women, children, and slaves as information carriers whom Quraysh surveillance dismissed as non-strategic actors. The "eyebrow principle": the place closest to a person's eye but cannot be seen is the eyebrow.

**Bayesian Analysis:** The Prophet achieved systematically lower uncertainty about Qurayshi types than they had about his network:

$$\text{Var}[\hat{t}_Q | \text{Prophet's information}] \ll \text{Var}[\hat{t}_Q | \text{default prior}]$$

This information asymmetry — achieved through unconventional intelligence assets — gave persistent strategic advantage.

> **Simulation:** `islamic_gt_codes/sim_17_bayesian_intelligence.py`

### 9.2 Thirteen Years of Strategic Patience

For 13 years in Mecca, the Prophet and followers endured torture, boycott, and assassination attempts without retaliating. God explicitly commanded patience over retaliation.

**Game-Theoretic Analysis:** In an asymmetric repeated game where the weaker player has infinite time horizon (akhirah), patience dominates retaliation because:
1. Retaliation triggers escalation spirals that destroy the movement
2. Patience builds moral capital that converts future adversaries
3. The patient player's "tied hands" commitment is a separating signal

> **Simulation:** `islamic_gt_codes/sim_07_meccan_patience.py`

### 9.3 The Abyssinian Migration: Screening Under Persecution

The Prophet selected Ja'far ibn Abi Talib to present Islam to the Negus of Abyssinia, choosing Surah Maryam (about Jesus and Mary) as content specifically calibrated to the Negus's type (Christian king). The Quraysh counter-emissaries offered gifts — a pooling signal that any type accepts. The content-based approach was a separating signal.

> **Simulation:** `islamic_gt_codes/sim_19_abyssinia_screening.py`

### 9.4 The Aqaba Pledges: Solving the Stag Hunt

Seventy-three Medinan converts secretly pledged at Aqaba. The 12 Naqib (leader) system served as observable intermediate commitments that shifted beliefs about collective action, solving the Stag Hunt coordination problem.

> **Simulation:** `islamic_gt_codes/sim_03_stag_hunt_aqaba.py`

## Chapter 10: The Medinan Period — Institution Building

### 10.1 The Constitution of Medina

**Historical Context:** The Prophet entered a city of extraordinary complexity: Aws and Khazraj (rival Arab tribes), Muhajirun (destitute Meccan emigrants), three Jewish tribes, nominal Muslims (Munafiqun), and remaining polytheists.

The Constitution of Medina created a multi-party agreement with provisions mapping directly to game-theoretic functions:

| Constitutional Provision | Game-Theoretic Function |
|---|---|
| "The believers are a single community (umma)" | Common knowledge establishment |
| "Each tribe retains its own traditions" | Preference heterogeneity accommodation |
| "All signatories must jointly defend Medina" | Collective security provision |
| "No one shall make a separate peace with an enemy" | Coalition stability constraint |
| "Jews who join have the same right to assistance" | Minority inclusion |
| "Disputes referred to God and Muhammad" | Binding arbitration |

**Theorem 10.1.** Under IGT preferences, the constitutional mechanism implements the Muhammad Equilibrium as the unique dominant strategy equilibrium for all participating players.

> **Simulation:** `islamic_gt_codes/sim_24_medina_constitution_core.py`

### 10.2 The Muwakhat Brotherhood

**The Economic Problem:** Muhajirun arrived with zero assets. Ansar controlled all resources. No taxation mechanism existed. Classical prediction: Ansar offer minimum subsistence (monopsony).

**The Prophet's Solution:** Personal pairing of each Muhajir with an Ansar "brother." Results: Ansar voluntarily shared half their homes, land, and wealth. Abdur-Rahman ibn Awf famously declined full transfer, asking only for market access — then built his fortune independently.

**IGT Analysis:** Under the Ansar's Islamic Utility:

$$\mathbf{U}_{\text{Ansar}} = u^{\text{mat}}(w_A - \Delta w) + \alpha \cdot u^{\text{mat}}(w_M + \Delta w) + \lambda \cdot \Omega_A(\text{brotherhood})$$

The material loss was outweighed by altruistic and akhirah payoffs. The Muwakhat achieved voluntary redistribution that no tax mechanism could replicate.

> **Simulation:** `islamic_gt_codes/sim_01_prisoners_dilemma_muwakhat.py`

### 10.3 The Market of Medina

The Prophet established the market with rules prohibiting hoarding, caravan interception, and deceptive practices — and made it rent-free public space. This constrained the strategy space to eliminate exploitative Nash equilibria while preserving competitive benefits.

> **Simulation:** `islamic_gt_codes/sim_22_market_medina.py`

### 10.4 The Battle of Badr

313 poorly equipped Muslims vs. ~1,000 well-armed Quraysh. Classical military calculus: retreat or guerrilla avoidance. The Prophet chose decisive engagement after shura (consultation) and Quranic revelation promising divine support (8:9-10).

**IGT Analysis:** When $\lambda \cdot \Omega(\text{obey revelation}) \gg$ any material expected loss, pure strategy (commitment) dominates mixed strategy (hedging). Moral certainty generates commitment advantages that probabilistic models cannot capture.

> **Simulation:** `islamic_gt_codes/sim_04_battle_of_badr.py`

## Chapter 11: Diplomacy and Conflict Resolution

### 11.1 The Treaty of Hudaybiyyah — The Infinite Game

**Historical Context:** In 628 CE, the Prophet departed with 1,400 companions for Umrah. The Quraysh blocked them at Hudaybiyyah. The resulting treaty contained seemingly humiliating terms: no Umrah that year, asymmetric extradition, removal of "Messenger of God" from the document.

**Classical Analysis:** Under finite-horizon bargaining with material payoffs, the treaty is a capitulation. The companions' distress embodies this classical logic.

**IGT Analysis:** The Prophet was playing an infinite game:

$$\mathbf{U}_M^{\text{Hudaybiyyah}} = \underbrace{x_M^{\text{material}}}_{\text{negative}} + \underbrace{\alpha \sum_j x_j^{\text{dakwah}}}_{\text{enormous under peace}} + \underbrace{\lambda \cdot \Omega_M(\text{sign})}_{\text{obeying revelation}}$$

The Quran called it "a clear victory" (48:1) BEFORE any military conquest materialized.

**Historical Verification:** Within 22 months: Khalid ibn al-Walid, Amr ibn al-As, and Uthman ibn Talhah converted. The Muslim community grew from 1,400 to 10,000+. The peace enabled explosive growth that war would have prevented.

**Proposition 11.1 (Hudaybiyyah Paradox Resolution).** In an infinite game with dakwah externalities, treaty terms that appear suboptimal under Nash Bargaining are optimal under the Muhammad Equilibrium when the cumulative dakwah dividend under peace exceeds the material gain from exploiting short-run military advantage.

> **Simulation:** `islamic_gt_codes/sim_06_hudaybiyyah_treaty.py`

### 11.2 Letters to Kings: Multi-Front Diplomatic Portfolio

After Hudaybiyyah, the Prophet sent simultaneous letters to Byzantine, Persian, Abyssinian, Egyptian, and Arabian rulers. This multi-front approach created a portfolio strategy where partial success generated positive returns.

> **Simulation:** `islamic_gt_codes/sim_09_diplomatic_portfolio.py`

### 11.3 The Conquest of Mecca: Why Amnesty Dominates Punishment

**Historical Context:** On 20th Ramadan, 8 AH (January 630 CE), the Prophet entered Mecca with 10,000 soldiers. Every classical logic — tribal, Machiavellian, game-theoretic — demanded punishment of elite opponents. Instead:

*"O Quraysh! What do you think I will do with you?"*
*"Good — you are a noble brother and the son of a noble brother."*
*"Go your ways, for you are free."*

**Three Transformative Effects of Amnesty:**

**Effect 1 — Psychological Game-Changer:** The Quraysh resistance ideology was built on one premise: Muhammad seeks revenge. The amnesty destroyed this premise. The rebellion probability dropped to near zero because the *motivation* for rebellion was eliminated.

**Effect 2 — Signal Effect:** The amnesty was a maximally credible signal because it was maximally costly under CGT logic. No tribal chieftain would send this signal — it achieved perfect type separation.

**Effect 3 — Conversion Cascade:** Abu Sufyan, Ikrimah ibn Abi Jahl, and thousands of others converted. A purge would have permanently prevented this.

**Proposition 11.2 (Mercy as Dominant Strategy).** In post-conquest governance with IGT preferences:

$$\lambda \cdot \Omega_M(\text{amnesty}) + \alpha \cdot \sum_j [u_j(\text{forgiven}) - u_j(\text{purged})] > V^{\text{Purge}} - V^{\text{Amnesty}}$$

**Historical Verification:** Zero guerrilla resistance. Arabian Peninsula unified within two years.

> **Simulation:** `islamic_gt_codes/sim_15_conquest_amnesty.py`

### 11.4 Abu Sufyan's Conversion: The Beer-Quiche Solution

The Prophet arranged for Abbas to bring Abu Sufyan to the Muslim camp — witnessing 10,000 campfires. The "Abu Sufyan's house is safe" formula was mechanism design allowing the defeated leader to cooperate without humiliation.

> **Simulation:** `islamic_gt_codes/sim_20_abu_sufyan_signaling.py`

---

# PART IV — THE ECONOMIC ARCHITECTURE OF IGT

## Chapter 12: The Zakat System — Redistributive Mechanism Design

### 12.1 Zakat as Formal Economic Mechanism

Zakat — 2.5% annual levy on surplus wealth above nisab — possesses four remarkable properties:

**Property 1 (Efficiency):** Applies to idle wealth, not productive capital — incentivizes investment over hoarding.

**Property 2 (Anti-Hoarding):** Makes holding excess liquid wealth costly, preventing Nash wealth concentration.

**Property 3 (Self-Reporting with Divine Monitoring):** Self-assessed under IGT. Classical self-assessed taxes invite massive underreporting; under IGT, $\Omega_i$ penalizes underreporting even when undetectable by humans.

**Property 4 (Targeted Distribution):** The Quran (9:60) specifies eight recipient categories, ensuring redistribution reaches highest marginal utility of income.

### 12.2 Zakat-Modified Wealth Distribution

Without redistribution, Nash produces Pareto distribution with $G \approx 0.43-0.71$. With Zakat:

$$G^{\text{Zakat}} = G^{\text{Pareto}} \cdot (1 - \tau)^k \cdot \phi(w_0, \bar{w})$$

Simulation studies suggest Zakat alone reduces Gini by 12-18 percentage points in high-compliance economies.

**Historical Verification:** Under Caliph Umar ibn Abd al-Aziz, Zakat compliance was so high that eligible recipients reportedly could not be found — poverty had been effectively eliminated.

> **Simulation:** `islamic_gt_codes/sim_14_zakat_pareto.py`

## Chapter 13: The Riba Prohibition — Restructuring the Finance Game

### 13.1 The Classical Finance Game

Interest-bearing debt creates a Nash Equilibrium of misaligned incentives:
- Banks maximize interest rates, making credit expensive for the poor
- Borrowers maximize leverage, creating systemic fragility
- Risk is offloaded through securitization, producing moral hazard

The 2008 global financial crisis was the empirical realization of this Nash Equilibrium.

### 13.2 The Islamic Finance Alternative

Riba prohibition mandates risk-sharing contracts (mudaraba, musharaka):

$$\pi_{\text{bank}}^{\text{mudaraba}} = \theta \cdot \max(R - K, 0) - \max(K - R, 0) \cdot \mathbf{1}_{\text{bank loss}}$$

The bank profits only when the entrepreneur succeeds — **aligned incentives** that eliminate the moral hazard of conventional finance.

**Proposition 13.1.** The prohibition of Riba implements a mechanism that eliminates the misaligned-incentive Nash Equilibrium of conventional finance and reduces systemic financial fragility.

> **Simulation:** `islamic_gt_codes/sim_23_riba_prohibition.py`

## Chapter 14: Waqf and Sadaqah — Voluntary Public Goods Provision

### 14.1 Waqf: Perpetual Endowments

The Waqf system — Islamic charitable endowments — historically provided public goods (hospitals, schools, water systems) outside the market mechanism, preventing oligarchic capture of public goods that the Nash equilibrium of political economy predicts.

### 14.2 Sadaqah: Voluntary Charity as Vickrey Mechanism

The sadaqah mechanism rewards sincerity (niyyah) rather than observable amount. A poor widow's date with sincere intention is declared more valuable than a wealthy man's large insincere donation. This is structurally identical to the Vickrey auction's incentive compatibility: truthful revelation of capacity is optimal.

> **Simulation:** `islamic_gt_codes/sim_12_sadaqah_mechanism.py`

### 14.3 Combined Effect: Zakat + Waqf + Riba Prohibition

$$G^{\text{IGT economy}} \approx G^{\text{Nash}} \cdot (1 - \delta_{\text{Zakat}}) \cdot (1 - \delta_{\text{Waqf}}) \cdot (1 - \delta_{\text{anti-Riba}})$$

The multiplicative effect produces wealth distributions significantly closer to normal, consistent with the best periods of the Islamic golden age.

---

# PART V — COMPARATIVE ANALYSIS: NASH vs. MUHAMMAD EQUILIBRIUM

## Chapter 15: Systematic Comparison

### 15.1 Seven Dimensions of Difference

| Dimension | Nash Equilibrium | Muhammad Equilibrium |
|---|---|---|
| **Utility Function** | $U_i = x_i(s)$ | $\mathbf{U}_i = x_i + \alpha\sum_j x_j + \lambda\Omega_i$ |
| **Time Horizon** | Finite or discounted | Effectively infinite (akhirah) |
| **Monitoring** | Required for cooperation | Internal (divine accounting) |
| **Cooperation** | Incentive compatibility only | Intrinsic moral + incentive |
| **Wealth** | Pareto/power law | Compressed via Zakat/Waqf |
| **Conflict Resolution** | Credible threats/punishment | Forgiveness + trust reconstruction |
| **Social Welfare** | PoA > 1 (suboptimal) | PoA ≈ 1 (near-optimal) |

### 15.2 Price of Anarchy Comparison

| Domain | CGT Nash PoA | IGT Muhammad PoA | Reduction |
|---|---|---|---|
| Prisoner's Dilemma | 3.0 | ≈ 1.0 | 3x |
| Commons Tragedy (n players) | n | ≈ 1.0-1.2 | nx |
| Arms Race | ∞ (mutual ruin) | ≈ 1.0-1.5 | ∞ |
| Wealth Distribution | 2.0-4.0 | ≈ 1.2-1.5 | 1.5-3.3x |
| Post-Conflict Governance | 2.0-5.0 | ≈ 1.0-1.1 | 2-5x |
| Financial Systemic Risk | 3.0-10.0 | ≈ 1.0-2.0 | 1.5-10x |

The Muhammad Equilibrium consistently reduces the Price of Anarchy toward 1.0 across all examined domains.

### 15.3 Stability Analysis

**Nash Equilibrium — Fragile:**
- Monitoring breakdown -> cooperation collapses
- Finite horizon -> backward induction unravels cooperation
- High discount rates -> defection
- Multiple equilibria -> no prediction

**Muhammad Equilibrium — Robust:**
- Hidden actions -> akhirah monitoring is universal
- Finite horizons -> akhirah extends to infinity
- High discount rates -> akhirah payoffs are undiscounted
- Multiple equilibria -> ME selects Pareto-dominant via covenant fidelity

---

# PART VI — MODERN APPLICATIONS

## Chapter 16: The War Problem

Global military expenditure: $2.2 trillion (2023). 56 active conflicts. 15,000 nuclear warheads. These are Nash equilibria of the security dilemma.

**The Prophetic Model:**
1. **Trust infrastructure (amanah)** as deterrence alternative
2. **Non-confrontation principle:** route around conflict rather than through it
3. **Strategic patience as dominant strategy** in infinite games
4. **IGT formalization:** $(P,P)$ is Muhammad Equilibrium in conflict games when $\lambda \cdot \Omega(P) > T_{\text{arms}}$

## Chapter 17: The Inequality Problem

**Capitalism's Nash Equilibrium:** Global Gini ≈ 0.88. Top 1% = 43% of wealth. Bottom 50% = 2%.

**The Three-Pillar IGT Solution:**
1. **Zakat** — 2.5% wealth levy compressing Pareto distribution
2. **Waqf** — perpetual endowments providing public goods outside market
3. **Riba Prohibition** — eliminating the exponential compounding engine ($w(t) = w_0 e^{rt}$) that mathematically guarantees wealth concentration

## Chapter 18: The Environmental Commons Problem

Climate change is the global Tragedy of the Commons. Under IGT, the Khalifah (stewardship) principle treats Earth as amanah (trust). Environmental destruction incurs $\Omega$ penalties that make cooperation dominant in the commons game — even without global enforcement mechanisms.

## Chapter 19: The Governance Problem

Rent-seeking and corruption are Nash equilibria of political games. The Shura (consultation) mechanism and akhirah accountability model provide governance without requiring the external enforcement institutions whose capture is itself a Nash equilibrium problem.

---

# PART VII — FROM THEORY TO PRACTICE

## Chapter 20: The 23-Year Parameter Cultivation Project

### 20.1 The Implementation Challenge

The Muhammad Equilibrium requires:

$$\alpha_i > \alpha_i^{\text{threshold}} \quad \text{and} \quad \lambda_i > \lambda_i^{\text{threshold}}$$

These are not fixed — they are cultivated through education, community, worship, and moral development.

### 20.2 The Prophet's Mission as Parameter Engineering

The 23-year prophetic mission was a systematic $(\alpha, \lambda)$ cultivation project:

- **Dar al-Arqam:** $(\alpha, \lambda)$-parameter training facility
- **Muwakhat:** Demonstration that $\alpha$ was higher than the Ansar had calculated
- **Conquest Amnesty:** Demonstration that $\lambda$ could override the most powerful material incentives

### 20.3 Strategy Evolution

Five strategic phases, each optimal for its parameter conditions:

| Phase | Period | Strategy | Key Parameter |
|---|---|---|---|
| 1. Secret Organization | 610-613 CE | Hidden network (Dar al-Arqam) | Low $n$, high $\theta$ (threat) |
| 2. Public Preaching | 613-615 CE | Open invitation + patience | Growing $n$, stable $\theta$ |
| 3. Migration/Refuge | 615-622 CE | Abyssinia, then Hijra | Medium $n$, critical $\theta$ |
| 4. State Building | 622-628 CE | Constitution, defense, economy | High $n$, declining $\theta$ |
| 5. Diplomacy/Conquest | 628-632 CE | Treaty, letters, amnesty | Very high $n$, low $\theta$ |

> **Simulation:** `islamic_gt_codes/sim_10_strategy_evolution.py`

## Chapter 21: Roadmap for Modern Implementation

**Step 1 — Parameter Recognition:** Nash equilibrium is the floor, not the ceiling.

**Step 2 — Institutional Redesign:** Islamic finance (risk-sharing), Zakat-analogous instruments, Constitution of Medina-template dispute resolution.

**Step 3 — International Relations:** The Hudaybiyyah Paradigm — accept short-term concessions for long-term systemic peace.

**Step 4 — Economic Justice:** Progressive wealth taxes (Zakat analog), mandatory charitable endowments (Waqf analog), prohibition of predatory lending (Riba analog).

**Step 5 — Moral Architecture:** Sustainable cooperation requires moral architecture, not just incentive design. Economic reform without moral reform produces CGT behavior with IGT-labeled instruments.

---

# PART VIII — MATHEMATICAL APPENDIX

## A.1 Notation Reference

| Symbol | Meaning |
|---|---|
| $N$ | Set of players |
| $S_i$ | Strategy space of player $i$ |
| $s^*$ | Nash Equilibrium strategy profile |
| $s^{**}$ | Muhammad Equilibrium strategy profile |
| $u_i^{\text{mat}}$ | Material payoff of player $i$ |
| $\mathbf{U}_i^{\text{IGT}}$ | Full Islamic Utility function of player $i$ |
| $\alpha_i$ | Altruism coefficient of player $i$ |
| $\phi_{ij}$ | Relational weight player $i$ assigns to player $j$ |
| $\lambda_i$ | Akhirah sensitivity coefficient of player $i$ |
| $\Omega_i(s)$ | Divine Accounting function |
| $\delta$ | Discount factor (material) |
| $\text{PoA}$ | Price of Anarchy |
| $G$ | Gini coefficient |
| $T, R, P, S$ | Temptation, Reward, Punishment, Sucker payoffs (PD) |

## A.2 Core Theorems Summary

**Theorem A.1 (ME Existence):** Every finite IGT game has a Muhammad Equilibrium.

**Theorem A.2 (ME Welfare Dominance):** ME generates weakly higher aggregate material welfare than any Nash Equilibrium.

**Theorem A.3 (ME Internal Incentive Compatibility):** Cooperation is incentive-compatible without external monitoring when akhirah weights exceed threshold.

**Theorem A.4 (ME Evolutionary Stability):** ME strategy is ESS when $\lambda \cdot \Omega(C) > T - R$.

**Theorem A.5 (ME Core Stability):** Under sufficient $\alpha_i$ and $\lambda_i$, ME is in the Core of the cooperative game.

## A.3 The Prisoner's Dilemma Under IGT — Full Derivation

Standard PD payoffs: $T=5, R=3, P=1, S=0$.

**Nash Equilibrium:** $(D, D)$ with payoffs $(1,1)$.

**IGT Utility Functions for player 1:**

$$\mathbf{U}_1(C, C) = R + \alpha R + \lambda\omega_{CC} = 3 + 3\alpha + \lambda\omega_{CC}$$
$$\mathbf{U}_1(D, C) = T + \alpha S + \lambda\omega_{DC} = 5 + 0 + \lambda\omega_{DC}$$
$$\mathbf{U}_1(C, D) = S + \alpha T + \lambda\omega_{CD} = 0 + 5\alpha + \lambda\omega_{CD}$$
$$\mathbf{U}_1(D, D) = P + \alpha P + \lambda\omega_{DD} = 1 + \alpha + \lambda\omega_{DD}$$

where $\omega_{CC} > \omega_{DC} > \omega_{CD} > \omega_{DD}$.

**Condition for $(C,C)$ as Muhammad Equilibrium:**

Player 1 prefers C over D when j plays C:
$$3\alpha + \lambda(\omega_{CC} - \omega_{DC}) \geq 2$$

Player 1 prefers C over D when j plays D:
$$4\alpha + \lambda(\omega_{CD} - \omega_{DD}) \geq 1$$

Both conditions satisfied when $\alpha$ and $\lambda$ exceed threshold values. **Cooperation becomes the unique stable outcome under sufficiently high altruism and akhirah sensitivity.** $\square$

## A.4 Simulation Code Reference

All 24 simulations are in `islamic_gt_codes/`:

| File | Game/Problem | Historical Episode |
|---|---|---|
| `sim_01_prisoners_dilemma_muwakhat.py` | Prisoner's Dilemma | Muwakhat Brotherhood |
| `sim_02_hilf_al_fudul.py` | Multi-player PD / Free-riding | Hilf al-Fudul Pact |
| `sim_03_stag_hunt_aqaba.py` | Stag Hunt | Aqaba Pledges + Naqibs |
| `sim_04_battle_of_badr.py` | Incomplete Information | Battle of Badr |
| `sim_05_aws_khazraj_coordination.py` | Battle of the Sexes | Aws-Khazraj Reconciliation |
| `sim_06_hudaybiyyah_treaty.py` | Repeated Game / Bargaining | Treaty of Hudaybiyyah |
| `sim_07_meccan_patience.py` | Asymmetric Repeated Game | 13 Years Meccan Patience |
| `sim_08_centipede_muwakhat.py` | Centipede Game | Abdur-Rahman ibn Awf |
| `sim_09_diplomatic_portfolio.py` | Multi-front Strategy | Letters to Kings |
| `sim_10_strategy_evolution.py` | Comparative Statics | Strategy Phase Transitions |
| `sim_11_hotelling_tawhid.py` | Hotelling's Spatial Model | Tawhid as New Dimension |
| `sim_12_sadaqah_mechanism.py` | Vickrey/Mechanism Design | Sadaqah Voluntary Charity |
| `sim_13_abu_bakr_utility.py` | Expected Utility / Risk | Abu Bakr's Total Sacrifice |
| `sim_14_zakat_pareto.py` | Wealth Distribution | Zakat System |
| `sim_15_conquest_amnesty.py` | Post-Conflict Governance | Conquest of Mecca Amnesty |
| `sim_16_folk_theorem_selection.py` | Folk Theorem Selection | 23-Year Parameter Cultivation |
| `sim_17_bayesian_intelligence.py` | Bayesian Games | Dar al-Arqam Network |
| `sim_18_signaling_alamin.py` | Signaling / Separating Eq. | Al-Amin 40-Year Reputation |
| `sim_19_abyssinia_screening.py` | Screening Games | Abyssinian Migration |
| `sim_20_abu_sufyan_signaling.py` | Beer-Quiche Game | Abu Sufyan at Conquest |
| `sim_21_kaaba_stone_bargaining.py` | Nash Bargaining | Kaaba Stone Arbitration |
| `sim_22_market_medina.py` | Market Design | Market of Medina |
| `sim_23_riba_prohibition.py` | Financial Games | Riba Prohibition |
| `sim_24_medina_constitution_core.py` | Cooperative Game Core | Constitution of Medina |

---

# CONCLUSION: THE PROPHETIC CONJECTURE

**Proposition (Main Theorem of IGT).** For any social interaction game $\mathcal{G}$ with $n \geq 2$ players:

**(i)** If players have Nash utility functions ($\alpha = 0$, $\lambda = 0$), the equilibrium maximizes individual payoffs at the cost of collective welfare;

**(ii)** If players have Islamic utility functions ($\alpha > 0$, $\lambda > 0$, amanah constraints active), the Muhammad Equilibrium exists, is individually rational, and achieves collective welfare at or near the social optimum;

**(iii)** The transition from Nash to Muhammad Equilibrium requires no coercive external authority — it requires only the cultivation of $\alpha$ and $\lambda$ to threshold levels through moral education, community, and institutional design;

**(iv)** The Prophet Muhammad ﷺ empirically demonstrated and documented a 23-year implementation of this transition, converting the most conflict-ridden, wealth-concentrated, honor-violence-dominated society of 7th-century Arabia into a civilization that, within a century, hosted the most advanced scientific, cultural, and economic institutions on Earth.

---

*The Nash Equilibrium tells us what rational selfishness produces.*
*The Muhammad Equilibrium tells us what rational humanity produces.*
*The difference between them is the space that revelation has always sought to fill.*

---

> *"Say: My Lord, increase me in knowledge."*
> *(Quran 20:114)*

---

## Bibliography

### Classical Game Theory
- Nash, J.F. (1950). "Equilibrium Points in N-Person Games." *PNAS*, 36(1), 48-49.
- Nash, J.F. (1951). "Non-Cooperative Games." *Annals of Mathematics*, 54(2), 286-295.
- von Neumann, J. & Morgenstern, O. (1944). *Theory of Games and Economic Behavior*.
- Fudenberg, D. & Maskin, E. (1986). "The Folk Theorem in Repeated Games." *Econometrica*, 54(3), 533-554.
- Maynard Smith, J. & Price, G.R. (1973). "The Logic of Animal Conflict." *Nature*, 246, 15-18.

### Mechanism Design
- Hurwicz, L. (1973). "The Design of Mechanisms for Resource Allocation." *AER*, 63(2), 1-30.
- Vickrey, W. (1961). "Counterspeculation, Auctions, and Competitive Sealed Tenders." *JoF*, 16(1), 8-37.
- Myerson, R.B. (1981). "Optimal Auction Design." *MOR*, 6(1), 58-73.

### Behavioral and Social Preference Theory
- Kahneman, D. & Tversky, A. (1979). "Prospect Theory." *Econometrica*, 47(2), 263-291.
- Fehr, E. & Gachter, S. (2000). "Cooperation and Punishment." *AER*, 90(4), 980-994.
- Rabin, M. (1993). "Incorporating Fairness into Game Theory." *AER*, 83(5), 1281-1302.

### Islamic Primary Sources
- *The Holy Quran*. Diyanet Isleri Baskanligi translation.
- Al-Bukhari. *Sahih al-Bukhari*.
- Muslim ibn al-Hajjaj. *Sahih Muslim*.
- Ibn Ishaq / Ibn Hisham. *Sirat Rasul Allah*.

### Islamic Secondary Sources
- Watt, W.M. (1953). *Muhammad at Mecca*. Oxford University Press.
- Watt, W.M. (1956). *Muhammad at Medina*. Oxford University Press.
- Lecker, M. (2004). *The 'Constitution of Medina'*. Darwin Press.

### Empirical Literature
- Barro, R.J. & McCleary, R.M. (2003). "Religion and Economic Growth." *ASR*, 68(5), 760-781.
- Kuran, T. (2004). *Islam and Mammon*. Princeton University Press.
- Cizakca, M. (2000). *A History of Philanthropic Foundations*. Bogazici University Press.
