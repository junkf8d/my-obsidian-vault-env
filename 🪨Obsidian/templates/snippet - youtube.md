<%*

async function getYoutubeInfo(str) {
  if (!str.match(/youtube\.com|youtu\.be/)) {
    return `**Youtubeのurlをコピーして実行してください: ${str}**`;
  }

  try {
    const api = `https://www.youtube.com/oembed?url=${encodeURIComponent(str)}&format=json`;
    const res = await fetch(api);

    if (!res.ok) throw new Error(`HTTP error: ${res.status}`);

    return await res.json();
  } catch (error) {
    return `**youtube error: ${error.message}**`;
  }
}

const escapeMarkdown = (text) => {
  return text.replace(/([|*_`#[\]])/g, '\\$1');
};

async function buildYoutubeInfo(str) {
  const info = await getYoutubeInfo(str);
  if (info[0] === '*') {
    return info;
  }

  const { title, html } = info;
  fullWidthHtml = html.replace(/\s(width|height)=\S+/g, '').replace(/iframe/, 'iframe style="width:100%;aspect-ratio:16/9;" ');
  return `[${escapeMarkdown(title)}](${str})\n${fullWidthHtml}\n`;
}

const cb = await navigator.clipboard.readText();
tR = await buildYoutubeInfo(cb);
-%>

