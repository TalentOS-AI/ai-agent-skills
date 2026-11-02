---
name: venue-deadlines
description: >-
  Use when choosing where to submit a paper or tracking submission deadlines, to
  get official dates converted to local time plus sourced acceptance rates.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# Venue & deadline tracking
1. Take dates only from the official CFP page (the conference site or the workshop's own page, and ACL Rolling Review at https://aclrollingreview.org/dates for ACL-family venues). Use aggregators (aideadlin.es, ccfddl) only as leads to check.
2. Record for each venue: name, URL, abstract deadline, paper deadline, timezone stated, commitment deadline (ARR), notification date, page limits, anonymity period, and the date you checked.
3. Convert times. AoE = UTC-12. Example: `python3 -c "from datetime import datetime;from zoneinfo import ZoneInfo as Z;print(datetime(2026,12,15,23,59,tzinfo=Z('Etc/GMT+12')).astimezone(Z('Asia/Shanghai')))"` (Etc/GMT+12 means UTC-12). Use the reader's timezone and label it.
4. Acceptance rates: cite the venue's own stats or opening slides, the proceedings front matter, or the ACL wiki "Conference acceptance rates" page. Give the year and the source link, and mark any estimate as an estimate.
5. Recheck deadlines a week before. Extensions get posted on the CFP page and the venue's X/Twitter account.
