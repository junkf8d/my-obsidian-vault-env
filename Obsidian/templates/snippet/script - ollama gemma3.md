<%*

{
    async function sendChatRequest(message, apiUrl = "http://localhost:11434/api/chat", modelName = "gemma3:12b") {
      const headers = {
        "Content-Type": "application/json"
      };
      
      const requestBody = {
        "model": modelName,
        "messages": [
            {
              "role": "user",
              "content": "あなたはとても賢いAIアシスタントです。ユーザーの質問に手短に回答して。"
            },
            {
              "role": "user",
              "content": message
            }
        ],
        "stream": false  // ストリーミングを無効化
      };
    
      try {
        const response = await fetch(apiUrl, {
          method: 'POST',
          headers: headers,
          body: JSON.stringify(requestBody)
        });
        
        if (!response.ok) {
          throw new Error(`HTTP error! Status: ${response.status}`);
        }
        
        const data = await response.json();
        return data.message.content;
      } catch (error) {
        console.error("リクエスト中にエラーが発生しました:", error);
        throw error;
      }
    }

    function quote(str) {
        return str.split("\n").map(line=>`> ${line}`).join("\n");
    }

    async function main() {
        let msg = await tp.system.prompt("AIに聞く: ");
        msg = msg.trim();
        if (!msg) return;
        
        let callOut = `> [!faq] あなた:\n${quote(msg)}\n`;
      try {
        const result = await sendChatRequest(msg);
        callOut += quote(`> [!note] ollama:\n${quote(result)}\n`);
      } catch (error) {
        callOut +=  `エラーが発生しました: ${error}`;
      }
      
        tR = callOut;
    }
    
    await main();
}

-%>