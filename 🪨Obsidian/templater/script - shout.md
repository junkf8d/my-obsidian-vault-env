<%*
const fujiwaraTatsuya = s => s.normalize('NFD').replace(/.[\u3099\u309a]?/gu, '$&\u3099').normalize('NFC');
const selection = tp.file.selection();
tR = fujiwaraTatsuya(selection);
-%>