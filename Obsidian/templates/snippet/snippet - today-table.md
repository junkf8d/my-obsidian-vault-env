<%*
const now = moment();
const year = now.format("YYYY年");
const month = now.format("M月");
const day = now.format("D日");
const weekDayJp = ["日", "月", "火", "水", "木", "金", "土"];
const weekDay = "(" + weekDayJp[now.day()] + ")";
const weekNum = now.week() + "週目";

const daysLeft = moment().endOf('year').diff(now, 'days');
const yearPercent = Math.round((daysLeft / (moment().endOf('year').diff(moment().startOf('year'), 'days') + 1)) * 100);

const daysLeftInMonth = moment().endOf('month').diff(now, 'days');
const monthPercent = Math.round((daysLeftInMonth / (moment().endOf('month').diff(moment().startOf('month'), 'days') + 1)) * 100);

const daysLeftInWeek = 7 - now.day();
const weekPercent = Math.round((daysLeftInWeek / 7) * 100);

const weeksLeft = moment().weeksInYear() - now.week();
const yearWeekPercent = Math.round((weeksLeft / moment().weeksInYear()) * 100);

let result = "";
result += "| " + year + " | " + month + " | " + day + weekDay + " | " + weekNum + " |";
result += "\n| :-: | :-: | :-: | :-: |";
result += "\n| 残" + daysLeft + "日(" + yearPercent + "%) | 残" + daysLeftInMonth + "日(" + monthPercent + "%) | 残" + daysLeftInWeek + "日(" + weekPercent + "%) | 残" + weeksLeft + "週(" + yearWeekPercent + "%) |";

tR = result;
%>