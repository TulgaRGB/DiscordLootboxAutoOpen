# DiscordAutoLootboxes
Discord Otomatik Lootbox'ları (2024 Nisan Şakası Etkinlik)
# Nasıl kullanılır
- Discord'u aç (Discord web'i tercih et)
- Ctrl + Shift + I tuşlarına basın
- Aşağıdaki kodu kopyalayıp konsol sekmesine yapıştırın.

```javascript
// Discord API'den oturum açma belirteci al
var thisToken = (webpackChunkdiscord_app.push([[""],{},e=>{
    for(let s in m=[],e.c) m.push(e.c[s])
}]),m).find(e => e?.exports?.default?.getToken !== void 0).exports.default.getToken();

// İstek gönderme işlevi
function sendRequest() {
    var xhr = new XMLHttpRequest();
    xhr.open("POST", "https://discord.com/api/v9/users/@me/lootboxes/open", true);
    xhr.setRequestHeader("Authorization", thisToken);
    xhr.setRequestHeader("X-Super-Properties", "eyJvcyI6IldpbmRvd3MiLCJicm93c2VyIjoiQ2hyb21lIiwiZGV2aWNlIjoiIiwic3lzdGVtX2xvY2FsZSI6InZpIiwiYnJvd3Nlcl91c2VyX2FnZW50IjoiTW96aWxsYS81LjAgKFdpbmRvd3MgTlQgMTAuMDsgV2luNjQ7IHg2NCkgQXBwbGVXZWJLaXQvNTM3LjM2IChLSFRNTCwgbGlrZSBHZWNrbykgQ2hyb21lLzEyMy4wLjAuMCBTYWZhcmkvNTM3LjM2IiwiYnJvd3Nlcl92ZXJzaW9uIjoiMTIzLjAuMC4wIiwib3NfdmVyc2lvbiI6IjEwIiwicmVmZXJyZXIiOiIiLCJyZWZlcnJpbmdfZG9tYWluIjoiIiwicmVmZXJyZXJfY3VycmVudCI6IiIsInJlZmVycmluZ19kb21haW5fY3VycmVudCI6IiIsInJlbGVhc2VfY2hhbm5lbCI6InN0YWJsZSIsImNsaWVudF9idWlsZF9udW1iZXIiOjI4MDY4NiwiY2xpZW50X2V2ZW50X3NvdXJjZSI6bnVsbH0=");
    xhr.onload = function() {
        if (xhr.status === 200) {
            console.log(xhr.responseText);
        } else if (xhr.status === 429) {
            var retryAfter = parseFloat(xhr.getResponseHeader("Retry-After")) || 1;
            retryAfter = Math.round((retryAfter + 0.1) * 10) / 10;
            console.log("Çok fazla istek. Yeniden dene " + retryAfter + " saniye sonra.");
            setTimeout(sendRequest, 1000 * retryAfter);
        } else {
            console.error(xhr.statusText);
        }
    };
    xhr.onerror = function() {
        console.error("İstek başarısız, yeniden dene...");
    };
    xhr.send();
}

// İlk isteği gönder
sendRequest();

// Belirli aralıklarla istek gönder
setInterval(sendRequest, 2500);
```

- Done Have fun!

