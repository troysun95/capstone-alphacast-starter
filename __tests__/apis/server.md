# Server API 的參考測項

- [ ] Base URL 為 `https://spotify-backend.alphacamp.io/api`

---

## 取得使用者資訊

- [ ] HTTP method: **`GET`**
- [ ] Entry point: **`/me`**
- [ ] 發出請求的 Header 物件中，需要帶有一組 key-value 描述 token 資訊
```javascript
{
    Authorization: Bearer <Token string>
}
```
- [ ] Server 回應請求成功，取得以下使用者資訊
```javascript
{
    id: string,
    favoriteEpisodeIds: string[]
}
```
- [ ] Server 回應請求失敗，根據 HTTP status code 顯示以下錯誤訊息後，執行後續處理－

| HTTP status code | 訊息 | 後續處理 |
| --- | --- |--- |
| `403` | 應用的登入資訊已過期，請重新操作 | Fallback (選擇性) |
| `404` | 找不到您的使用者資訊，請重新操作 | Fallback (選擇性) |
| other | 發生非預期的錯誤，請稍後再試 | Fallback (選擇性) |

---

## 建立使用者資料 / 取得新的 API Access Token

- [ ] HTTP method: **`POST`**
- [ ] Entry point: **`/users`**
- [ ] 需傳入從 Spotify 取得的 access token，作為請求 body 中的一組 key-value
```javascript
{
    spotifyToken: <Spotify access token string> 
}
```
- [ ] Server 回應請求成功，取得以下使用者資訊以及 Server API 的 token
```javascript
{
    id: string,
    favoriteEpisodeIds: string[],
    apiToken: string
}
```
- [ ] Server 回應請求失敗，根據 HTTP status code 顯示以下錯誤訊息後，執行後續處理－

| HTTP status code | 訊息 | 後續處理 |
| --- | --- | --- |
| `403` | 應用的登入資訊已過期，請重新操作 | Fallback (選擇性) |
| other | 發生非預期的錯誤，請稍後再試 | Fallback (選擇性) |

---

## 取得所有分類

- [ ] HTTP method: **`GET`**
- [ ] Entry point: **`/categories`**
- [ ] 發出請求的 Header 物件中，需要帶有一組 key-value 描述 token 資訊
```javascript
{
    Authorization: Bearer <Token string>
}
```
- [ ] Server 回應請求成功，取得以下分類
```javascript
{
    categories:  [
        {
            id: string,
            name: string,
            savedShows: string[]
        },
        ...
    ]
}
```
- [ ] Server 回應請求失敗，根據 HTTP status code 顯示以下錯誤訊息後，執行後續處理－

| HTTP status code | 訊息 | 後續處理 |
| --- | --- | --- |
| `403` | 應用的登入資訊已過期，請重新操作 | Fallback (選擇性) |
| other | 發生非預期的錯誤，請稍後再試 | Fallback (選擇性) |

---

## 建立分類

- [ ] HTTP method: **`POST`**
- [ ] Entry point: **`/categories`**
- [ ] 需傳入分類名稱，作為請求 body 中的一組 key-value
```javascript
{
    name: <The category name string> 
}
```
- [ ] Server 回應請求成功，取得以下回傳
```javascript
{
    success: true
}
```