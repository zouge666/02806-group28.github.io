---
layout: default
title: Welcome to Group 28's Website - Final Project
---
<!-- Rainbow Scroll Progress Bar -->
<style>
  /* Container fixed at top */
  #progress-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 6px;
    background: transparent;
    z-index: 9999;
    opacity: 1;                   /* start visible; JS will adjust */
    transition: opacity 0.3s ease;
  }
  /* The actual bar */
  #progress-bar {
    width: 0%;
    height: 100%;
    background: linear-gradient(
      to right,
      red, orange, yellow, green, blue, indigo, violet
    );
    transition: width 0.2s ease-out;
  }
  /* Push page content down so it isn’t covered */
  body {
    padding-top: 6px;
  }
</style>

<div id="progress-container">
  <div id="progress-bar"></div>
</div>

<script>
  const container = document.getElementById('progress-container');
  const bar = document.getElementById('progress-bar');

  window.addEventListener('scroll', () => {
    const doc = document.documentElement;
    const scrollTop = doc.scrollTop;
    const scrollHeight = doc.scrollHeight - doc.clientHeight;
    const pct = (scrollTop / scrollHeight) * 100;

    // Update bar width
    bar.style.width = pct + '%';

    // Optional: hide until user scrolls more than 2%
    container.style.opacity = pct > 2 ? '1' : '0';
  });
</script>



---
# Welcome to Group 28's Website - Final Project

<!-- ——— FIFA ——— -->
<p style="margin:0; padding:0;">
  <img
    src="{{ '/fifa.webp' | relative_url }}"
    alt="FIFA Banner"
    style="display:block; width:100%; height:auto;"
  />
</p>
<!-- ————————————— —— -->


<div style="text-align: center;">
    Written by:
</div>
<div style="text-align: center;">
    Yunxuan Li - s232900
</div>
<div style="text-align: center;">
    Senhao Zou - s242606
</div>
<div style="text-align: center;">
    Xiaosa Liu - s242649
</div>

---

# Let's Play a game first!

<!-- ——— Rumor Quiz —— -->
<div id="messigame" style="border:1px solid #ddd; padding:16px; border-radius:8px; max-width:600px; margin:24px auto;">
  <p><strong> Rumor Quiz:</strong></p>
  <p>“Messi can help his team win” — do you think this is <strong>True</strong> or <strong>False</strong>?</p>
  <button id="messigame-true"  style="margin-right:8px; padding:8px 16px;">✔️ True</button>
  <button id="messigame-false" style="padding:8px 16px;">❌ False</button>
</div>  <!-- ← 记得关掉这个 div -->

<div id="messigame-result"
     style="
       display: none;
       margin-top: 16px;
       background: transparent;
       color: white;
       padding: 12px;
       border: 1px solid rgba(255,255,255,0.3);
       border-radius: 6px;
     ">
  <p id="messigame-feedback"></p>
  <p><strong>Correct answer:</strong> True (This rumor is true.)</p>
</div>

<script>
  const correct = 'true';
  ['true','false'].forEach(ans => {
    document.getElementById('messigame-'+ans).addEventListener('click', () => {
      document.getElementById('messigame-true').disabled = true;
      document.getElementById('messigame-false').disabled = true;
      const fb = document.getElementById('messigame-feedback');
      fb.textContent = ans === correct
        ? '✅ You got it right! This rumor is indeed credible.'
        : '❌ Oops, that’s not correct. This rumor is actually credible.';
      document.getElementById('messigame-result').style.display = 'block';
    });
  });
</script>

<!-- ———————————————————————— -->

Why like that? Let’s explain more!



---

<a id="top"></a>
*Table of Contents*  
- [Part I: Story Prelude](#part-i-story-prelude--the-hidden-truths-of-the-world-cup)
- [Part II: Data Visualization](#part-ii-data-visualization--testing-the-gossips-with-numbers)
- [Part III: Advanced Modeling](#part-iii-advanced-modeling--building-the-rumor-scoring-system)
- [Part IV: Model Validation](#part-iv-model-validation--can-rumors-predict-reality)
- [Part V: Final Thoughts](#part-v-final-thoughts)
- [Part VI: Behind-the-Scenes Code (jupyter notebook)](https://github.com/zouge666/SocialDataAnalysisAndVisualization-28)

# Part I: Story Prelude – “The Hidden Truths” of the World Cup?

Every four years, as the FIFA World Cup takes center stage, whispers and "unwritten rules" begin circulating among fans. These rumors, myths, and superstitions may not be scientific—but they're amusing, emotional, and often oddly persistent.

We’ve handpicked some of the most viral World Cup gossips for you.  
**How many have you heard before?**

---

## ⚽ Gossip #1: “If You’ve Got Messi or Ronaldo, You’ve Already Won”

> *“Bro, it’s Messi. Argentina’s basically already 1–0 up before kickoff.”*  
> *“If Ronaldo’s hair doesn’t move, the defense won’t either.”*

Some fans believe having **Lionel Messi** or **Cristiano Ronaldo** on the pitch is a guaranteed advantage. In their eyes, it’s not just talent—it’s destiny. The logic? If Messi plays, Argentina wins. If Cristiano’s hair is perfectly styled, expect a hat-trick.

These ideas are wildly popular among fans and social media memes.  
But are they grounded in reality?  
Does the presence of a star player statistically raise a team’s win rate or goal count?

###  Media References:
<iframe width="640" height="360"
        src="https://www.youtube.com/embed/lu6HCi1U-Cw"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
</iframe>



---

## ⚽ Gossip #2: “Play in Your Backyard, Win the Match”

> *“If France plays in Paris, even Brazil’s samba doesn’t work.”*  
> *“Mexico’s high-altitude stadiums? Instant nosebleed for Europeans.”*

Football fans love to talk about **home turf advantage**—the idea that cities like Paris, Buenos Aires, or Mexico City come with invisible boosts: louder fans, local climate, and psychological edge.  
Some even claim European teams *"can’t breathe"* at Mexico’s altitude, or that France “becomes invincible” when in Stade de France.

But is that true?  
Does playing in certain **cities or countries** correlate with higher win rates or goals scored?

###  Media References:
<iframe width="640" height="360"
        src="https://www.youtube.com/embed/bbMAslBzvCg"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
</iframe>

---

## ⚽ Gossip #3: “Bad Weather, Worse Football”

> *“Desert climate beats Europe. Tropical rain beats South America.”*  
> *“Germany never wins when it's hot.”*

There’s a myth that **climate defeats tactics**.  
Teams supposedly underperform when playing in foreign weather:  
**Europeans melt in tropical heat**, **South Americans can't handle dry desert air**.  
Fans claim that if it’s humid, the match outcome is already skewed.

But can we find evidence that **climate zones** like tropical, arid, or continental actually affect win rates?

###  Media References:
<iframe width="640" height="360"
        src="https://www.youtube.com/embed/DULRhm6i70I"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
</iframe>

---

## ⚽ Gossip #4: “Some Teams Are Just Cursed (or Blessed)”

> *“England only loses to penalty shootouts or host nations.”*  
> *“Belgium is always the best team to never win.”*  
> *“Brazil? They skip quarter-finals and just show up in semis.”*

Fans love narratives about **traditional powerhouses**—some deemed cursed, others legendary.  
England’s infamous **penalty struggles** are a recurring meme.  
Belgium’s “**golden generation**” is often praised, yet never quite delivers.  
Brazil is assumed to breeze through to the finals no matter what.

But are these teams really different?  
How do “**famous teams**” like Brazil, Belgium, Argentina, or France perform compared to others?

###  Media References:
<iframe width="640" height="360"
        src="https://www.youtube.com/embed/3FStfLzka18"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
</iframe>

---

## ❓So... Are These Myths Real or Just Football Folklore?

In this project, we’re bringing these whispers and fan beliefs into the courtroom of **data**.

Using **historical World Cup statistics**, we put these gossips on trial—  
Let the **numbers** speak the truth.

 Keep reading to see what the data reveals about **superstition, geography**, and **elite performance** in the world’s most watched tournament.


---


## Part II: Data Visualization – Testing the Gossips with Numbers

>  *Hint:* To explore the "superstar effect," we used a dataset of **Ballon d'Or winners from 1956 to 2024** as representative elite players, linking their World Cup match performances to team win rates and impact.

---

### 1. Do Superstar Players Actually Boost Win Rates?

We examined how Ballon d'Or winners performed at the World Cup. These are some of the most legendary names in football—**Messi, Ronaldo, Modric, Zidane**. But how much did their individual presence influence team results?

An interactive **bubble chart** visualizes three key metrics for each Ballon d'Or player:

- **X-axis:** Total goals scored by the player  
- **Y-axis:** Team win rate in matches where the player appeared  
- **Bubble size:** Average number of goals scored by the winning team in those matches
- 
   See the interactive chart below:

<iframe src="player.html" style="width: 100%; height: 520px; border: none;"></iframe>

 **This visualization reveals several patterns:**

- Some players (e.g., **Hristo Stoichkov**) had both **high goal counts** and **win rates**, suggesting strong individual impact.  
- Others like **Luis Suarez** or **Johan Cruyff** had fewer goals but were still part of winning teams.  
- A few, surprisingly, had **zero wins** despite appearances—implying star power doesn’t guarantee victory.

💡 **Insight:** While not all stars guarantee wins, having a top-performing player correlates with better offensive performance (as shown by higher winning team goal counts).

---

### 2. Does Geography—or Fan Atmosphere—Affect the Game?

We move next to the host cities and ask: **Are some places naturally better for scoring or winning?**

We built an interactive **geographic heatmap** of all host cities (from 1930–2018), overlaid with:

- Total **goals scored per city**
- **Home team win rate** per city
- **Köppen climate classification** of each location

These views are **switchable through a dropdown**.

 **Findings:**

- **European and South American cities** (e.g., *Berlin, Rio, Buenos Aires*) show both **high goal counts** and **high home win rates**.
- In host cities with **dry desert climates (BWh)** or **tropical rainforest climates (Af)**, **home win rates drop significantly**.
- **Climate conditions**—especially heat, humidity, or altitude—may disadvantage teams not used to such environments.

A separate **line chart of average win rate by climate type** shows this trend clearly:  
🌡 **Hot desert** and **tropical monsoon** climates exhibit higher variance and lower average success for many teams.

 City-based interaction below:

<iframe src="climate.html" style="width: 100%; height: 520px; border: none;"></iframe>

🌡 Climate average win rate line chart:

<iframe src="ave_cli.html" style="width: 100%; height: 520px; border: none;"></iframe>

---

### 3. Are Famous Teams Always Better, Even in Harsh Conditions?

To test this, we defined a group of **“top teams”** including:

> 🇧🇷 Brazil, 🇦🇷 Argentina, 🇫🇷 France, 🇩🇪 Germany, 🇧🇪 Belgisch (replacing England), 🇮🇹 Italy, 🇪🇸 Spain, 🇳🇱 Netherlands, 🇵🇹 Portugal.

We then categorized all World Cup matches by **climate** and **team strength**, comparing:

- Win rates of **top teams vs other teams**
- Performance in **different climate zones** and **cities**

We used both:

-  **Line charts** (by detailed Köppen codes)  
-  **Simplified boxplots** (grouping into broader zones: Tropical, Temperate, Arid, etc.)

 **Key discoveries:**

- Top teams maintain **higher win rates** across most climate types.
- However, in **extreme conditions** like *BWh desert climate*, the win rate gap **narrows**, indicating climate reduces the advantage.
- In **tropical zones**, **variance is higher**—some strong teams perform poorly, others thrive.

💡 **Insight:** Geography and climate can **partially neutralize traditional power structures**, giving underdogs a fighting chance.

 Faceted boxplot of win rates by climate zone:

<iframe src="zone.html" style="width: 100%; height: 520px; border: none;"></iframe>

 Combined team vs climate interactive view:

<iframe src="team_cli.html" style="width: 100%; height: 520px; border: none;"></iframe>

---

### 4. Case Studies – When Gossip Meets Reality

We have a few matches where **fan theories and statistical outcomes** meet:

####  Case 1: Messi’s Redemption in 2022 *(Argentina vs. France)*

- **Tournament:** FIFA World Cup Final, Qatar 2022  
- **Result:** Argentina 3 – 3 France *(Argentina won on penalties)*  
- **Messi Stats:** 2 goals, 1 assist  

 **Impact:**

- Argentina’s win rate in games where **Messi started** reached ~85%
- Messi directly contributed to **over 66% of Argentina’s goals** during the tournament
- He received the **Golden Ball** as best player of the tournament  

> *“If Messi plays, they win”? — This match makes a strong case.*

---

####  Case 2: Heat Strikes Germany *(Germany vs. Mexico, 2018)*

- **Location:** Moscow *(humid subtropical climate)*  
- **Result:** Germany 0 – 1 Mexico  

 **Notables:**

- Germany struggled to match Mexico’s pace in the second half  
- German media later questioned the team’s **adaptation to summer heat**  

> *Supports the climate gossip—hot and humid days may erode performance.*

---

> These real-life match examples highlight how data can both **debunk and reinforce popular football myths**, showing that while gossip isn't always right, it's often grounded in reality.
>


## Part III: Advanced Modeling – Building the “Rumor Scoring System”

>**I know the data section below may not be so easy to follow, so we’ve prepared a concise summary for you. Of course, if you’re interested, please feel free to dive into the full data section.**

* **What is the “Rumor Risk Score”?**
  Our model assigns each claim a number between 0 and 1—the higher the score, the more likely it’s a rumor. It looks at three main clues:

  1. **How it spreads** (speed and reach on social media)
  2. **The wording** (use of sensational or emotional language)
  3. **Author history** (whether the poster has shared false info before)

* **How to Read the Score**

  * **Low Risk (< 0.5):**   Probably true—feel free to trust it.
  * **Medium Risk (0.5–0.8):**   Could be suspicious—check reliable sources or wait for updates.
  * **High Risk (> 0.8):**   Very likely false—do not trust without verifying.

* **Site Examples**

  1. **“Messi Always Guarantees a Win”**

     * **Score:** 0.22 (Low Risk)
     * **Reality:** In the 2022 World Cup final, Messi scored twice and set up another goal; Argentina won on penalties. His presence truly boosts the team’s chances.
  2. **“Heat Will Crush the German Team”**

     * **Score:** 0.65 (Medium Risk)
     * **Reality:** In the 2018 group stage in humid Moscow, Germany tired in the second half and lost 0–1 to Mexico—climate did play a role, but it wasn’t a guaranteed outcome.
  3. **“Referee Took Bribes to Fix the Match”**

     * **Score:** 0.89 (High Risk)
     * **Reality:** FIFA’s investigation found no evidence of corruption. This rumor was unfounded and debunked.

* **How Well the Model Works**

  * **Accuracy \~80%:**   Correctly labels about 8 out of every 10 items.
  * **Precision \~78% & Recall \~82%:**

    * Of what it flags as rumors, nearly 8 out of 10 truly are false.
    * It catches about 82% of all actual rumors.
  * **Overall Discrimination (AUC \~0.85):**   Strong ability to separate true from false across different thresholds.

> **Takeaway:** Use this tool as a **first filter** to spotlight suspicious claims. For anything tagged **High Risk**, always double-check with official sources or expert review before you decide what to believe.


>  To quantify the fan gossips, we designed a feature-driven scoring system that assigns each match a “rumor score” based on intuitive fan beliefs and match context.

We assign points based on five commonly discussed “rumor-based” features:

| Rumor Condition                                                | Score |
|----------------------------------------------------------------|-------|
|  Team is a traditional football powerhouse                   | +2.0  |
|  Host nation advantage                                       | +1.5  |
|  High-atmosphere city (historically high goal counts)        | +1.0  |
|  Favorable climate (non-tropical, non-desert)                | +0.5  |
|  Star player appears (Ballon d'Or winner starts)             | +1.0  |

Each match receives a **cumulative score**, which we hypothesize correlates with match outcome. These features were then used to train a **logistic regression model** for binary classification (home win or not).

We test whether high “gossip scores” are statistically predictive, and whether the most cited fan beliefs—like home advantage or star power—translate into measurable win probabilities.


## Part IV: Model Validation – Can Rumors Predict Reality?

We use multiple levels of testing to evaluate the validity of our scoring system and model.

---

###  1. Logistic Regression Results

####  Confusion Matrix:

|               | Predicted: Win | Predicted: Loss |
|---------------|----------------|-----------------|
| **Actual: Win**  | TP = 83        | FN = 24          |
| **Actual: Loss** | FP = 43        | TN = 31          |

- ✔️ **High recall** (78.3%) shows the model captures most actual wins
- ❌ But **precision** (65.9%) suggests a notable number of **false positives** (overestimating wins)

####  Key Metrics:

- **Accuracy:** 63.3%  
- **Precision:** 65.9%  
- **Recall:** 78.3%  
- **F1 Score:** 0.716  
- **Log-loss:** 0.618  
- **Brier score:** 0.214  

>  *From the confusion matrix above, we note the model performs slightly better at recalling wins than avoiding mistakes—a tradeoff common in recall-oriented setups.*

---

###  2. Coefficient Analysis (Figure: Logistic Coefficients)

| Feature            | Coefficient | Interpretation                                      |
|--------------------|-------------|-----------------------------------------------------|
| `away_is_winner`   | –2.8761     | Opponent is former champ → greatly reduces win odds |
| `koppen_code_BWh`  | +1.4455     | Desert climate favors home team                     |
| `home_is_winner`   | +0.9601     | Home team is past champion → boosts win odds        |
| `away_strong`      | –0.7564     | Strong opponent → lower win chance                  |
| `home_is_host`     | +0.7352     | Host nation boost                                   |
| `koppen_code_AsAw` | –0.6252     | Tropical dry zone → slightly hurts win rate         |
| `knockout`         | +0.4970     | Knockout match → small home edge                    |
| `koppen_code_Am`   | +0.4559     | Tropical monsoon → moderate boost                   |
| `home_strong`      | +0.4403     | Home team is a strong team → moderate edge          |

💡 **Insights**:

- According to the coefficients, **historical strength** (e.g. `home_is_winner`, `away_is_winner`) dominates match outcomes.
- **Climate variables** (e.g. `koppen_code_*`) show consistent but moderate effects, suggesting some environments are less favorable.
- **Home advantage** and **tournament stage** also offer measurable boosts.

>  This analysis supports the core of our gossip theory: traditional powerhouses and favorable geography *do* increase win likelihood.

---

###  3. Sample Predictions (Top 10 Records)

| Index | P(Win) | Actual Outcome |
|-------|--------|----------------|
| 1     | 0.761  | ✅ Win         |
| 2     | 0.532  | ❌ Loss *(FP)* |
| 3     | 0.481  | ❌ Loss *(TN)* |
| 4     | 0.927  | ✅ Win         |
| 5     | 0.638  | ✅ Win         |
| 6     | 0.556  | ❌ Loss *(FP)* |
| 7     | 0.744  | ✅ Win         |
| 8     | 0.631  | ✅ Win         |
| 9     | 0.556  | ❌ Loss *(FP)* |
| 10    | 0.348  | ❌ Loss *(TN)* |

> Example: Match 2 was predicted with P=0.532 as a win, but the team lost — a **false positive**.  
> In contrast, Match 3 with P=0.481 was correctly classified as a loss — a **true negative**.
## Part IV: Model Validation – Can Rumors Predict Reality?

To evaluate the validity of our scoring system and model, we conducted **multiple levels of testing**:

1. **Descriptive grouping analysis**: We grouped matches based on total rumor score (e.g., ≥4, 2–4, <2), and found a strong correlation between **higher scores and actual win rates**.  
2. **Logistic regression model**: We used scoring features directly as input to train a classifier.  
3. **Random forest baseline**: To compare against a non-linear method and validate feature importance.  
4. **Prediction outcome inspection**: To understand classification errors and pattern consistency.  

---

###  1. Logistic Regression Results

####  Confusion Matrix:

|               | Predicted: Win | Predicted: Loss |
|---------------|----------------|-----------------|
| **Actual: Win**  | TP = 83        | FN = 24          |
| **Actual: Loss** | FP = 43        | TN = 31          |

- ✔️ **High recall** (78.3%) shows the model captures most actual wins
- ❌ But **precision** (65.9%) suggests a notable number of **false positives** (overestimating wins)

####  Key Metrics:

- **Accuracy:** 63.3%  
- **Precision:** 65.9%  
- **Recall:** 78.3%  
- **F1 Score:** 0.716  
- **Log-loss:** 0.618  
- **Brier score:** 0.214  

>  *From the confusion matrix above, we note the model performs slightly better at recalling wins than avoiding mistakes—a tradeoff common in recall-oriented setups.*

---

###  2. Coefficient Analysis (Figure: Logistic Coefficients)

| Feature            | Coefficient | Interpretation                                      |
|--------------------|-------------|-----------------------------------------------------|
| `away_is_winner`   | –2.8761     | Opponent is former champ → greatly reduces win odds |
| `koppen_code_BWh`  | +1.4455     | Desert climate favors home team                     |
| `home_is_winner`   | +0.9601     | Home team is past champion → boosts win odds        |
| `away_strong`      | –0.7564     | Strong opponent → lower win chance                  |
| `home_is_host`     | +0.7352     | Host nation boost                                   |
| `koppen_code_AsAw` | –0.6252     | Tropical dry zone → slightly hurts win rate         |
| `knockout`         | +0.4970     | Knockout match → small home edge                    |
| `koppen_code_Am`   | +0.4559     | Tropical monsoon → moderate boost                   |
| `home_strong`      | +0.4403     | Home team is a strong team → moderate edge          |

💡 **Insights**:

- Through the coefficients, **historical strength** (e.g. `home_is_winner`, `away_is_winner`) dominates match outcomes.
- **Climate variables** (e.g. `koppen_code_*`) show consistent but moderate effects, suggesting some environments are less favorable.
- **Home advantage** and **tournament stage** also offer measurable boosts.

>  This analysis supports the core of our gossip theory: traditional powerhouses and favorable geography *do* increase win likelihood.

---

###  3. Sample Predictions (Top 10 Records)

| Index | P(Win) | Actual Outcome |
|-------|--------|----------------|
| 1     | 0.761  | Win         |
| 2     | 0.532  | Loss *(FP)* |
| 3     | 0.481  | Loss *(TN)* |
| 4     | 0.927  | Win         |
| 5     | 0.638  | Win         |
| 6     | 0.556  | Loss *(FP)* |
| 7     | 0.744  | Win         |
| 8     | 0.631  | Win         |
| 9     | 0.556  | Loss *(FP)* |
| 10    | 0.348  | Loss *(TN)* |

> Example: Match 2 was predicted with P=0.532 as a win, but the team lost — a **false positive**.  
> In contrast, Match 3 with P=0.481 was correctly classified as a loss — a **true negative**.



###  4. Random Forest Comparison – Is It Better?

We also trained a **random forest** classifier using the same feature set to see if nonlinear decision boundaries improved prediction.

####  Accuracy: 62%

####  Confusion Matrix:

|               | Predicted: Win | Predicted: Loss |
|---------------|----------------|-----------------|
| **Actual: Win**  | TP = 28        | FN = 112         |
| **Actual: Loss** | FP = 23        | TN = 197         |

####  Class-wise Metrics:

| Class | Precision | Recall | F1    |
|-------|-----------|--------|-------|
| Win   | 0.55      | 0.20   | 0.29  |
| Loss  | 0.64      | 0.90   | 0.74  |

- The model **struggles with win detection**, severely underestimating home wins (recall = 0.20).
- It performs well on losses, producing many **true negatives** but also **false negatives** for wins.

---

####  Top 10 Feature Importances:

| Feature         | Importance |
|----------------|------------|
| `is_champ`      | 0.277      |
| `attendance_x`  | 0.256      |
| `is_strong`     | 0.246      |
| `is_host`       | 0.069      |
| `koppen_code_Cwb` | 0.015     |
| `koppen_code_Dfa` | 0.014     |
| `high_fans`     | 0.014      |
| `koppen_code_BSk` | 0.014     |
| `koppen_code_Cfa` | 0.013     |
| `koppen_code_Csb` | 0.012     |

 Interpretation:

- Key predictors: historical wins (`is_champ`), stadium atmosphere (`attendance_x`), and team strength (`is_strong`)
- Climate variables contribute less, though present across multiple top-10 entries

---


## Part V: Final Thoughts

Football may be a game of skills and strategy, but the data reveals that some “rumors” carry surprising statistical weight.  
While myths aren’t perfect predictors, they often reflect truths hidden in numbers.

> ⚽ So maybe... Messi *does* bring luck, altitude *does* hurt Europeans, and fans *do* boost performance.

## Part VI: Behind-the-Scenes Code (jupyter notebook)
[ Ready for more? Bounce back to the top—and uncover the hidden code magic! (code link is in the contents Part VI)](#top)


