<%*

{
  const HEIGHT = 240;

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

    let { title, html, author_name, author_url } = info;

    html = html.replace(/\s(width|height)=\S+/g, '');
    //html = html.replace(/iframe/, '"iframe style="width:100%;aspect-ratio:16/9;" ');
    html = html.replace(/iframe/, `iframe style="height:${HEIGHT}px;aspect-ratio:16/9;" `);
    title = escapeMarkdown(title);
    author_name = escapeMarkdown(author_name)

    return `[${title}](${str}) ([${author_name}](${author_url}))\n${html}\n`;
  }

  const url = await tp.system.prompt("Youtubeの動画URL: ");

  if (url.trim()) {
    tR = await buildYoutubeInfo(url.trim());
  }
}
-%>

