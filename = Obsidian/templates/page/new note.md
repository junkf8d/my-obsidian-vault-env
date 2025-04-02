---
created: 
modified: 
tags: 
aliases:
---
<%*

const dateValues = [
    tp.date.now("日付/YYYY年/MM月/DD日"),
    tp.date.now("日付/YYYY年/週番号/ww週目"),
    tp.date.now("日付/YYYY年/通算日/DDDD日目"),
    tp.date.now("日付/YYYY年/四半期/[Q]Q"),
    tp.date.now("日付/曜日/dddd")
];

tp.hooks.on_all_templates_executed(async () => {
    const file = tp.file.find_tfile(tp.file.path(true));
    await app.fileManager.processFrontMatter(file, (props) => {
        props["created"] = tp.date.now("YYYY-MM-DDTHH:mm:ss");
        props["tags"] = dateValues;
    });
});

-%>