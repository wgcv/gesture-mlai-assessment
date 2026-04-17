# Gesture — AI/ML Engineer Assessment

**Time:** 2–3 hours (please keep within this range)
**Submission:** Fork this repo, complete the task, share your fork
**Goal:** We want to see how you think and make decisions — not how much you can ship in 2 hours

---

## The Setup

Two files. One task.

### `data/user_events.csv`

A log of synthetic user behavior, each row is one event.

| Column         | Description                                                        |
| -------------- | ------------------------------------------------------------------ |
| `event_id`     | Unique event identifier                                            |
| `user_id`      | User who took the action                                           |
| `event_type`   | `app_open`, `product_view`, `add_to_cart`, `purchase`, `gift_send` |
| `timestamp`    | When it happened                                                   |
| `sku_id`       | Product involved (null for `app_open`)                             |
| `price_usd`    | Price at event time (null for `app_open`)                          |
| `recipient_id` | Who received the gift (`gift_send` only)                           |
| `platform`     | `ios`, `android`, `web`                                            |
| `user_type`    | `b2c` or `b2b`                                                     |

### `data/product_catalog.csv`

The product catalog.

| Column        | Description         |
| ------------- | ------------------- |
| `sku_id`      | Product identifier  |
| `title`       | Product name        |
| `category`    | Product category    |
| `price_usd`   | Retail price        |
| `description` | Product description |

---

## The Task

Build a simple behavioral intelligence system that does two things:

1. Predict which users are likely to send a gift
2. Recommend relevant products to those users

---

## Part 1 — Activation Scoring

**Build a model that predicts: will this user send a gift in the next 7 days?**

**Output:** `user_id` | `activation_score` (0–1) for all users

**Requirements:**

- Use a time-based train/test split — not random
- Build a small set of meaningful features (≤10 is a good guideline)
- Handle any data quality issues you find

**Write a brief inline explanation (~10 lines) covering:**

- How you defined your labels
- Your top features and why you chose them
- What metric you used and why accuracy isn't it

---

## Part 2 — Personalized SKU Ranking

Take the **top 20 users** by activation score from Part 1.

For each user, return their **top 5 recommended SKUs**.

**Output:** `user_id` | `sku_id` | `rank` (1–5)

---

## Part 3 — Production Thinking

In ≤150 words:

> If this system went live tomorrow, what are the top 3 things most likely to break or degrade silently — and how would you catch each one?

---

## What We're Looking For

- How you frame the problem and define labels correctly
- The signals you choose and why — not the count of features
- Whether your evaluation reflects real business tradeoffs
- That your SKU rankings are actually personalized
- Practical awareness of what breaks in production

## What We're Not Looking For

- Perfect model performance
- Complex pipelines or heavy tuning
- Long writeups or polished visualizations

---

## Deliverable

One notebook or script in `submission/` that:

1. Loads and cleans the data (with notes on what you found)
2. Engineers features
3. Trains a model
4. Outputs activation scores + SKU recommendations
5. Includes the Part 3 production thinking section

Commit as you go. We like seeing process, not just the final answer.

---

## One Last Thing

The dataset has **intentional data quality issues** in it.

We're not telling you what they are. Finding them — and deciding what to do about each one — is part of the exercise.
