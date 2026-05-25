# instagram-api-research
Documenting Instagram's private API — endpoints, data flows, and behaviour discovered through reverse engineering the Android app.
# instagram-api-research

Documenting Instagram's private API — endpoints, data flows, and behaviour 
discovered through reverse engineering the Android app.

This is live research. Updated as I find new things.

---

## Why This Exists

Instagram controls what you see and who sees you.
Understanding how their API works is the first step to building 
tools that put that control back in your hands.

---

## Tools Used

- **Frida** — runtime hooking on Android
- **jadx** — decompiling the Instagram APK
- **Burp Suite** — intercepting HTTPS traffic
- **Android Debug Bridge (adb)** — device communication
- **Python** — scripting and testing endpoints

---

## Findings

### Authentication
| Endpoint | Method | Description |
|---|---|---|
| `/api/v1/accounts/login/` | POST | Main login endpoint |
| `/api/v1/accounts/two_factor_login/` | POST | 2FA verification |

### Feed & Content
| Endpoint | Method | Description |
|---|---|---|
| `/api/v1/feed/timeline/` | GET | Main home feed |
| `/api/v1/feed/user/{user_id}/` | GET | User's post feed |

### User Data
| Endpoint | Method | Description |
|---|---|---|
| `/api/v1/users/{user_id}/info/` | GET | User profile info |
| `/api/v1/friendships/{user_id}/followers/` | GET | Followers list |

*More endpoints being added as research continues.*

---

## Headers Instagram Expects

```
X-IG-App-ID: 567067343352427
X-IG-Capabilities: 3brTvw==
X-IG-Connection-Type: WIFI
User-Agent: Instagram 275.0.0.27.98 Android
```

---

## Methodology

```
1. Install Instagram APK on rooted Android device
2. Hook with Frida to bypass SSL pinning
3. Intercept traffic through Burp Suite
4. Decompile APK with jadx to understand request structure
5. Reproduce endpoints with Python requests
6. Document findings here
```

---

## Status

- [x] Authentication endpoints mapped
- [x] Basic feed endpoints discovered  
- [ ] Story endpoints — in progress
- [ ] Direct message API — in progress
- [ ] Notification system — not started
- [ ] Reels endpoints — not started

---

## Disclaimer

This research is for educational purposes only.
All findings are from passive observation and decompilation.
No Instagram systems were harmed or exploited.
