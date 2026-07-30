# WinningHunter Research Notes
## Data Sources, Limitations & How It Really Works

> **Purpose**
>
> এই ডকুমেন্টটি WinningHunter-এর মতো SaaS বানানোর জন্য সবচেয়ে গুরুত্বপূর্ণ Data Sources সম্পর্কে ধারণা দেওয়ার জন্য লেখা হয়েছে।
>
> এখানে আমরা জানবো:
>
> - কোন Platform থেকে কী Data পাওয়া যায়
> - কোন Data কখনো পাওয়া যায় না
> - WinningHunter কীভাবে এত তথ্য দেখায়
> - কোনগুলো Official Data আর কোনগুলো Estimated Data

---

# 1. Meta Ads Library

## What is Meta Ads Library?

Meta Ads Library হচ্ছে Meta (Facebook & Instagram)-এর একটি **Public Ad Transparency Platform**।

এর মূল উদ্দেশ্য হচ্ছে Facebook ও Instagram-এ চলমান বিজ্ঞাপনগুলো সবাই যেন দেখতে পারে।

এটি কোনো Sales Dashboard নয় এবং এটি কোনো Ecommerce Analytics Platform-ও নয়।

WinningHunter-এর সবচেয়ে বড় Data Source হচ্ছে Meta Ads Library।

---

# Is it Free?

✅ Yes.

Meta Ads Library Public Data সম্পূর্ণ Free।

তবে API Access পাওয়ার জন্য Meta Developer Account প্রয়োজন।

---

# What Data Can We Get?

Meta থেকে অনেক গুরুত্বপূর্ণ Marketing Data পাওয়া যায়।

### Advertisement Information

- ✅ Ad Image
- ✅ Ad Video
- ✅ Carousel Images
- ✅ Ad Copy
- ✅ Primary Text
- ✅ Headline
- ✅ Description
- ✅ CTA Button

---

### Page Information

- ✅ Facebook Page Name
- ✅ Instagram Account
- ✅ Facebook Page Link
- ✅ Page ID

---

### Campaign Information

- ✅ Ad Status (Active / Inactive)
- ✅ Start Date
- ✅ Platform
- ✅ Multiple Creatives
- ✅ Sometimes Landing Page URL
- ✅ Languages
- ✅ Countries (depending on ad visibility)

---

### Creative Information

- ✅ Image
- ✅ Video
- ✅ Thumbnail
- ✅ Caption
- ✅ Text

---

# What We CANNOT Get?

Meta কখনো Public API দিয়ে নিচের Data দেয় না।

- ❌ Total Sales
- ❌ Total Revenue
- ❌ ROAS
- ❌ Profit
- ❌ Ad Spend
- ❌ Cost Per Purchase
- ❌ Conversion Rate
- ❌ Pixel Events
- ❌ Customer List
- ❌ Purchase Data
- ❌ Audience Targeting
- ❌ Age Targeting
- ❌ Interest Targeting
- ❌ Budget
- ❌ Daily Spend

---

# Example

Suppose Adidas runs a Facebook Ad.

From Meta we can know:

```
Brand: Adidas

Status: Active

Started: 45 Days Ago

Platform: Facebook

CTA: Shop Now

Video: Yes

Landing Page: adidas.com
```

But we CANNOT know:

```
Revenue

Profit

Sales

ROAS

Ad Spend

Conversions
```

Meta simply never shares these values publicly.

---

# Difficulty

⭐⭐☆☆☆

Collecting a few ads is easy.

Collecting millions of ads and updating them daily is the difficult part.

---

# 2. TikTok

## What is TikTok API?

TikTok provides multiple APIs.

However,

Business APIs are highly restricted.

Not everyone gets access.

---

# What We Can Get

Depending on access level:

- ✅ Video
- ✅ Caption
- ✅ Creator
- ✅ Likes
- ✅ Comments
- ✅ Shares
- ✅ Public Statistics
- ✅ Product Link (if available)

---

# What We Cannot Get

- ❌ Revenue
- ❌ Profit
- ❌ ROAS
- ❌ Purchase Data
- ❌ Ad Spend
- ❌ Customer Information

---

# Difficulty

⭐⭐⭐☆☆

Harder than Meta because API access is more restricted.

---

# 3. Pinterest

Pinterest also provides APIs.

Mostly useful for Pinterest Marketing.

---

# What We Can Get

- ✅ Pins
- ✅ Images
- ✅ Descriptions
- ✅ Boards
- ✅ Profile
- ✅ Campaign Data (Own Account Only)

---

# What We Cannot Get

- ❌ Competitor Revenue
- ❌ Competitor Sales
- ❌ Private Campaign Statistics
- ❌ Customer Data

---

# Difficulty

⭐⭐☆☆☆

Fairly straightforward.

---

# Where Does WinningHunter Actually Get Its Data?

Many people think:

```
Meta API

↓

WinningHunter

↓

Website
```

This is WRONG.

WinningHunter combines multiple sources together.

```
                 Meta Ads Library
                        │
                        │
        ┌───────────────┼───────────────┐
        │               │               │
     TikTok         Pinterest      Other Sources
        │               │               │
        └───────────────┼───────────────┘
                        │
                 Web Crawlers
                 Web Scrapers
                        │
                        ▼
               Internal Processing
                        │
                        ▼
                 Own Database
                        │
                        ▼
                 AI Analysis
                        │
                        ▼
              WinningHunter Dashboard
```

WinningHunter does NOT rely on a single API.

It continuously collects data from different platforms.

Then it stores everything inside its own database.

---

# Why Store Everything in Our Own Database?

Imagine every user searches:

```
Nike

Adidas

Gym Products

Skincare
```

If every search goes directly to Meta,

the website becomes extremely slow.

Instead,

WinningHunter works like this:

```
Meta

↓

Crawler

↓

Database

↓

User Search

↓

Instant Result
```

This makes searching very fast.

---

# Can API Tell Us Sales?

Simple answer:

**NO.**

Example

Adidas launches an advertisement.

API can tell us:

✅ Ad is Active

✅ Video

✅ Image

✅ Caption

✅ CTA

✅ Facebook Page

✅ Landing Page

But API can NEVER tell us:

❌ Sales

❌ Revenue

❌ Profit

❌ Orders

❌ Customer Count

❌ ROAS

---

# Then How Does WinningHunter Show Revenue?

This is one of the biggest misconceptions.

WinningHunter usually DOES NOT know the real revenue.

Instead,

it estimates.

---

# Estimated Metrics

WinningHunter uses multiple signals.

Example

```
Ad Running Days

+

Number of Countries

+

Number of Creatives

+

Store Traffic

+

Product Price

+

Engagement

+

Historical Performance

↓

Custom Algorithm

↓

Estimated Score
```

Notice the word:

**Estimated**

Not Official.

---

# Example

Suppose an ad

- Running for 320 days
- Available in 18 countries
- Has 35 creatives
- Store receives huge traffic

WinningHunter may estimate

```
Winning Score

95 / 100
```

This DOES NOT mean Meta said

```
95
```

This score is completely generated by WinningHunter.

---

# What Can Be Estimated?

These values are usually calculated using internal algorithms.

- Estimated Revenue
- Estimated Sales
- Estimated Profit
- Winning Score
- Scaling Score
- Trend Score
- Popularity Score
- Competition Score

None of these come directly from Meta.

---

# Example of a Simple Winning Score Algorithm

```
Running Days > 180

+

Countries > 10

+

Creatives > 15

+

Store Traffic High

+

Good Engagement

↓

Winning Score = 92
```

This is NOT Meta data.

This is our own business logic.

---

# Final Conclusion

WinningHunter is NOT simply a Meta Ads Viewer.

It is a complete Data Intelligence Platform.

Its biggest strength is NOT the frontend.

Its biggest strength is:

- Massive Data Collection
- Own Database
- Fast Search Engine
- AI Analysis
- Custom Algorithms
- Estimated Business Metrics

The website UI is only the final layer.

The real power is the data infrastructure running behind the scenes.
