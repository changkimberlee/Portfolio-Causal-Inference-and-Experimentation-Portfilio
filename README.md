# Data Science Portfolio 1: Causal Inference & Experimentation

## **Overview/ Design Approach**
This portfolio showcases how I apply my experience in behavioral policy research and causal inference to address challenges in the tech industry, including in areas of user growth, advertising, marketplaces, pricing, and policy impact. Beyond technical skills in coding and modeling, I aim to demonstrate my approach to framing research questions, designing studies, selecting indicators, choosing models, and presenting results across various scenarios.

Here I focuse on understanding causal relationships, designing and analyzing experiments, and measuring impact. This portfolio is tailored for roles that demand statistical rigor and expertise in causal inference techniques.

Here are some questions I ask when choosing causal inference designs:
- What is the timeline to seeing short-, mid- and long-term impact and to decision-making?

  *In my background in international development, we call this step building a Theory of Change. We spend time with stakeholders to talk through the (user) behavior and (business) impact intended to change, and develop the timeline and indicators accordingly. See below Indicator Selection section for more.*
- How does this experiment fit into product/ feature launch/ other cross-functional goals' timeline?
- How much control do we have on how the treatment (product/ feature/ campaign) will be launched?
- What is the unit of treatment? Individual user is usual for Growth and Digital Ads teams for most products where aim is engagement and/or ROI. Geo-based units is usual for Marketplace where the aim is supply-demand balancing. For Policy and Trust & Safety, the unit of treatment is often larger to minicipalities, states, countries, region (Whether the policy is external or internal).
- What is the scale of the experiment (how much time, monetary and engineering resources do we have?)? Or is this a natural experiment (i.e., external policies)?
  
*Answering the above questions requires consultations/ co-creation with cross-functional teams- Soft skills and experience. Again in international development, we always worked with a complicated network of stakeholders such as donors, NGOs, and small to large corporations. My consulting experience and communication skills I've developed through a wide variety of projects enabled me to come up with research design and timeline that matched vary different stateholders' short and long-term needs.*

The unit of treatment (product/ feature/ campaign) administration and control over treatment administration is one of the main factors that will help answer the following questions to determine the causal inference design to use. I am also assuming we have longtitudinal/ time series data. 

- Is a staggered rollout feasible? (This allows us the most control over treatment control choice, and allows for early feedback for faster iteration and agile development- using iterative experimentation to only develop features with the largest impacts, and optimize adoption/purchase potential to the right user segments)
- (If not natural experiment) Is randomization feasible within our timeframe and context? (-> RCT)
- If not possible, can we find a control group? (-> DiD)
- If there is still treatment selection bias, do we have pre-treatment observational data and enough observations that we can match on? (-> Propensity Score Matching or Weighting)
- Or is there a somewhat "arbitraty" cutoff or threshold in treatment assignment (i.e., income, geo-administrative boundaries, cell-tower)?(-> RDD, but interpret the results accordingly. May not be widely generalizable.)
- If not (treatment assignment is inherently connected to outcome), is there a confounding variable we can measure? (-> IV)
- 

n
clusters
covariates related to putcome or treatment (varian reduction and bias correction)

With all the above approaches, we can calculate:
- the Average Treatment Effect (the overall effect of the treatment across everyone in the control group) *"Did the new algorithm increase user engagement (CTR or bookings) overall?" "Did the new checkout flow increase purchases overall?"*
- the Conditional Treatment Effect (the effect of the treatment for specific subgroups, such as users with a certain profile). The Conditional Treatment Effect is a type of User Segment Analasys when we have pre-identified user segments. *"Did the new algorithm increase engagement in power users (CTR or bookings) compared to casual users?" "Did the new checkout flow help power users more than new users?"*


A even more flexible approach is Uplift Modeling. With Uplift Modeling, we can answer *"Which specific users should receive the new algorithm to maximize engagment (CTR or bookings)?" "Which specific users should receive the new checkout flow to maximize conversions?"*

With most of the above approaches, I can use Uplift Modeling to predict incremental impacts (impact of the treatment on each individual) and identify user segments. Uplift Modeling finds the individuals who are most likely to respond positively to a treatment (new product features, campaign or product). We can use uplift modeling to 1) increase resource efficiency by only targeting users with the highest potential impact; 2) increase resource efficieny by NOT targeting users who would have undertook the desired behavior anyways (i.e., users who will subscribe/ puchase anyways without recieving an email campaign or free trial extension offer; 3) prevent negative impacts from individuals who will potentially respond negatively to our intervention (i.e., push notifications or email campaigns could remind people to unsubscribe leading to churn); 4) build better personalized experiences for users, prioritizing the right features to the right users (bundle features to only relevent user segments who will have positive responses and NOT releasing features to users who will react negatively to the feature)


## Indicator Selection

## On Handling Large Dataset

## **Projects**

### **1️⃣ User Growth & Engagement Optimization** (aquisition and retensio )
**Problem:** Companies today face significant challenges in accurately measuring the impact of user engagement strategies. Without clear insights into what truly drives user growth, businesses often implement ineffective or even counterproductive engagement tactics. They also struggle to segment users properly, leading to generalized approaches that don't work across diverse user bases.

**Objective:** Measure the effectiveness of user engagement campaigns.

**Potential Impact:** Improves retention and engagement by testing strategy or product feature impact, identifying ones that work best for different user segments.
- **Techniques to consider:** Uplift modeling, A/B Testing (RCTs), switch back experiment, cluster matching w Difference-in-Differences (DiD), Regression Discontinuity Design (RDD), Instrumental Variables (IV)
- **Considerations** What is the timeline to seeing long-term impact and to decision-making? How does this experiment fit into product feature launch timeline? What is the unit of treatment and relevant user segments and clustering? What is the scale of the experiment (how much resources do we have?)? Is randomization feasible within this timeframe (-> RCT)? If not possible, can we find a control group (-> DiD)? Or is there a somewhat "arbitraty" cuttoff or threshold in treatment assignment (i.e., income, geo-administrative boundaries, cell-tower) (->RDD) ? If not, can we measure the confounding variables (-> IV)?


- **Dataset:** [Online Retail Dataset (UCI)](https://archive.ics.uci.edu/ml/datasets/online+retail)
- similar contexts: promotion experiments for on-demand delivery apps
---

### **2️⃣ Advertising Effectiveness & ROI Optimization** (or promotions)??
**Problem:** In today's highly competitive market, companies often waste significant portions of their advertising budgets without knowing which campaigns or channels are truly driving revenue. Many companies rely on superficial metrics, like click-through rates, without evaluating the deeper, more direct impacts on sales or long-term brand value. This leads to inefficient ad spend allocation and missed opportunities for optimization.

**Objective:** Optimize advertising spend and measure ad impact.

**Potential Impact:** Improves ROI by identifying high-performing campaigns and reducing ineffective ad spend.
- **Techniques:** Geo-based /clister based experiments, Regression Discontinuity Design (RDD), Synthetic Control Method (SCM)
- **Dataset:** [Facebook Ad Campaign Performance (Kaggle)](https://www.kaggle.com/datasets/sriraheel/facebook-ad-campaign-performance)

---

### **3️⃣ Marketplace Optimization: Balancing Supply & Demand**
**Problem:** In a two-sided marketplace, companies face a persistent challenge of balancing supply and demand efficiently. Without accurate real-time data and predictive models, companies often struggle with overstocked or understocked inventory, leading to lost revenue and customer dissatisfaction. Dynamic pricing and the timing of supply allocation are key to ensuring balance, yet many companies lack the insights to optimize these variables.

**Objective:** Analyze price elasticity and demand fluctuations in a two-sided marketplace.

**Potential Impact:** Helps optimize dynamic pricing strategies and supply allocation.
- **Techniques:** Price elasticity estimation, Instrumental Variables (IV), Discrete Choice Modeling
- **Dataset:** [Uber Pickups (Kaggle)](https://www.kaggle.com/datasets/itsahmad/uber-pickups-in-new-york-city)

---

### **4️⃣ Pricing Strategy: Maximizing Revenue & Retention**
**Problem:** Companies frequently struggle to determine the optimal pricing strategy that both maximizes revenue and maintains customer retention. While companies may use data-driven pricing models, they often overlook critical elements like price sensitivity, customer willingness to pay, and market segmentation. Without a clear understanding of these factors, pricing decisions can inadvertently alienate customers or leave money on the table.

**Objective:** Test pricing strategies to optimize revenue while maintaining retention.

**Potential Impact:** Enhances pricing strategies by identifying customer price sensitivity and willingness to pay.
- **Techniques:** demand elascitity modeling, A/B Testing, Synthetic Control Method (SCM), Regression Discontinuity Design (RDD)
- **Dataset:** [Instacart Market Basket Analysis (Kaggle)](https://www.kaggle.com/datasets/c/instacart/instacart-market-basket-analysis)

---

### **5️⃣ Policy & Trust & Safety Impact Analysis**
**Problem:** Policy changes, especially in areas like user safety and fraud prevention, can have unintended consequences that impact user trust or lead to increases in fraudulent activity. Companies often implement policy changes in reaction to emerging issues but lack the ability to evaluate their true effectiveness, sometimes inadvertently making problems worse or creating new issues.

**Objective:** Measure the impact of policy changes on fraud and user trust.

**Potential Impact:** Helps companies refine policies to enhance safety while minimizing unintended negative effects.
- **Techniques:** Difference-in-Differences (DiD), Instrumental Variables (IV), Regression Discontinuity Design (RDD)
- **Dataset:** [Credit Card Fraud Detection (Kaggle)](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
