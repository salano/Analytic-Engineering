In this section we explore repeated analysis (growth, survivor and funnel analysis)

Note: growth and survivor analyses are best used on subscrption data.
The data definition used for growth and survivor analysis is below.

`create table exercises.cust_growth_accounting(
cust_id text,
first_active_date date,
last_active_date date,
daily_active_state text,
weekly_active_state text,
dates_active date[],
date date,
primary key (cust_id, date)
);

The definition detail -

cust_id - customer identifier
first_active_date - first active/order date
last_active_date - last active/order date
daily_active_state - daily active state of customer
weekly_active_state - weelly active state of customer
dates_active - list of active/order dates of the customer
date date - active/order date

The customers state is defined below.

`new (didnt exist yesterday, active today)
-retained (active yesterday, active today)
-churned(active yesterday, inactive today)
-resurrected(inactive yesterday, active today)
-stale(inactive yesterday, inactive today)

Daily active states are classified as
-customer didn't exist yesterday, but exist today (new)
-customer was last active yesterday and is active today (retained)
-customer wasn't active yesterday, but active today (ressurrected)
-customer made no purchases today, but purchases today (churn)
-customer is inactive for more than 2 days (stale)

-active customer (new, retained, resurrected)
-growth rate = new + resurrected -churned

We see the customers state on any given day from the table.
![Alt text](Repeat Analysis/cust_states.png)

In addition, we can look at the states summarised by day to to understand our customers growth over time.
![Alt text](Repeat Analysis/Daily_states.png)

Survivor analysis:

We can examine the survivorship of over customers. From the data we can see that of 710 customers only 0.0014% of them makes a further purchase after 2 days of their initial purchase.
![Alt text](Repeat Analysis/Pct_active.png)

We can further analyse the data to examine survivorship by the day of the week. Those customers who made a purchase on sunday (dow = 0), only 1 (0.125%) of them made a subsequent purchase after 12 days of their initial purchase.
![Alt text](Repeat Analysis/Pct_active_dow.png)
