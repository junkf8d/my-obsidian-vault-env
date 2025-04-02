---
created: <% tp.date.now("YYYY-MM-DDTHH:mm:ss") %>
modified:
tags:
---

<%*

const WEEK_DAYS = "日月火水木金土";

const highlightToday = () => {
    const today = WEEK_DAYS[moment().day()];
    return WEEK_DAYS.replace(new RegExp(`^(.*)(${today})`), '~~$1~~**$2**');
};

const now = moment();
const year = now.format("YYYY年");
const month = now.format("M月");
const day = now.format("D日");
const weekDay = "(" + WEEK_DAYS[now.day()] + ")";
const weekNum = now.week() + "週目";

const daysLeft = moment().endOf('year').diff(now, 'days');
const yearPercent = Math.round((daysLeft / (moment().endOf('year').diff(moment().startOf('year'), 'days') + 1)) * 100);

const daysLeftInMonth = moment().endOf('month').diff(now, 'days');
const monthPercent = Math.round((daysLeftInMonth / (moment().endOf('month').diff(moment().startOf('month'), 'days') + 1)) * 100);

const daysLeftInWeek = 7 - now.day();
const weekPercent = Math.round((daysLeftInWeek / 7) * 100);

const weeksLeft = moment().weeksInYear() - now.week();

tR = `| ${year} | ${month} | ${day}${weekDay} | ${weekNum} |
| :-: | :-: | :-: | :-: |
| 残${daysLeft}日(${yearPercent}%) | 残${daysLeftInMonth}日(${monthPercent}%) | ${highlightToday()} | 残${weeksLeft}週 |`;

%>

## summary
### やりたいこと
- 

### やったこと
- 

## timeline
- 

## memo
- 