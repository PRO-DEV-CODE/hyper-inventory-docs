# Export

Hyper_Inventory มี 24 export แบ่งเป็น 6 กลุ่ม และมี 25 resource ในเซิร์ฟเรียกใช้อยู่แล้ว ใช้ตารางแรกเลือก export ตามเมนูที่กำลังทำ แล้วกดเข้าหน้ากลุ่มเพื่อดู parameter และตัวอย่างโค้ด

```lua
exports["Hyper_Inventory"]:<ชื่อ export>(...)
```

## เลือก export ตามเมนูที่จะทำ

| ถ้าจะทำเมนู / ระบบ | ใช้ export | ฝั่ง | ตัวอย่างในเซิร์ฟ |
| --- | --- | --- | --- |
| ร้านค้า, ตลาด, รางวัล, กาชา — ให้การ์ดไอเทมสีตรงกับกระเป๋า | `GetRarityInfo` | ทั้งสอง | Hyper_Shop, Hyper_Market, Hyper_Airdrop |
| tooltip / การ์ดรายละเอียดไอเทมแบบเดียวกับกระเป๋า | `GetItemDetail`, `GetItemDescription`, `GetItemCategoryInfo` | ทั้งสอง | Hyper_Crafting |
| HUD หรือ UI ที่ต้องใช้สี rarity ทั้งชุด | `GetRarityPalette` | ทั้งสอง | Hyper_Bountyhunt, Hyper_Gacha |
| ท้ายรถ, ตู้เซฟ, ตู้บ้าน ที่เก็บของลง DB เอง | `OpenStashExternal` + `RefreshStash` | server | Hyper_Garage, Hyper_Vault |
| เปิดกระเป๋าผู้เล่นคนอื่นเป็นตู้ (แอดมิน, ปล้น/ค้นตัว) | `OpenStashExternal` + `RefreshStash` | server | Hyper_Admin, Hyper_Thief |
| ตู้ชั่วคราว ไม่ต้องเซฟ | `OpenStash` | server | — |
| ติดตรา "ใช้งานอยู่" บนไอเทม (ลำโพง, ของติดตัว) | `AddBadge` / `RemoveBadge` | server | Hyper_Music, Hyper_Attacher |
| ไอเทมมีวันหมดอายุ → ขึ้นแผง "หมดอายุ" | `AddBadge` key `expired` | server | Hyper_Expire |
| เปิดเมนูของตัวเอง (NUI) ทับกระเป๋า | `CloseInventory` ก่อนเปิด | client | Hyper_Skinui, Hyper_Thief, Hyper_Profilestatus |
| ซื้อ/ขาย/โอนรถ | `InvalidateKeys` | server | Hyper_Gang |
| ร้านเสื้อผ้า, กาชาเครื่องประดับ | `InvalidateAccessories` | server | Hyper_Skinui |
| ระบบสกินอาวุธ | `SetSkinnable`, `ApplyCustomImage`, `ResetCustomImage` | client | Hyper_Weaponskin |

## Export ทั้งหมด

| กลุ่ม | Export | ฝั่ง |
| --- | --- | --- |
| [ตู้เก็บของ (Stash)](stash.md) | OpenStash, OpenStashExternal, RefreshStash, GetStashItems, SetStashItems | server |
| [Badge บนไอเทม](badge.md) | AddBadge, RemoveBadge | server |
| [ล้าง cache](cache.md) | InvalidateKeys, InvalidateAccessories | server |
| [ควบคุมกระเป๋า](control.md) | OpenInventory, CloseInventory, IsOpen, SetVehicleKeys | client |
| [สกินและรูปการ์ด](skin.md) | SetSkinnable, ApplyCustomImage, ResetCustomImage | client |
| [Rarity และข้อมูลไอเทม](rarity.md) | GetRarity, GetRarityColor, GetRarityInfo, HasRarity, GetRarityPalette, GetItemDescription, GetItemCategoryInfo, GetItemDetail | ทั้งสอง |

## Resource ที่เชื่อมอยู่แล้ว

| Resource | Export ที่ใช้ | ใช้ทำอะไร |
| --- | --- | --- |
| Hyper_Garage | OpenStashExternal, RefreshStash | ท้ายรถ |
| Hyper_Vault | OpenStashExternal, RefreshStash | ตู้เซฟ |
| Hyper_Admin | OpenStashExternal, RefreshStash, GetRarityInfo | เปิดกระเป๋าผู้เล่นจากเมนูแอดมิน |
| Hyper_Music | AddBadge, RemoveBadge | ตราลำโพงที่กำลังเปิด |
| Hyper_Attacher | AddBadge, RemoveBadge, GetRarityInfo | ตราของที่ติดตัว |
| Hyper_Weaponskin | SetSkinnable, ApplyCustomImage, ResetCustomImage | ปุ่ม "สกิน" และรูปการ์ดอาวุธ |
| Hyper_Skinui | CloseInventory, InvalidateAccessories | ร้านเสื้อผ้า |
| Hyper_Thief | OpenStashExternal, RefreshStash, CloseInventory | ปล้น / ค้นตัว — เปิดกระเป๋าเหยื่อเป็นตู้ |
| Hyper_Expire | AddBadge, RemoveBadge | ตราหมดอายุ → แผง "หมดอายุ" |
| Hyper_Profilestatus | CloseInventory, GetRarityInfo | โปรไฟล์ / เจม |
| Hyper_Gang | InvalidateKeys | โอนรถแก๊ง |
| Hyper_Crafting | GetItemDetail, GetItemDescription, GetItemCategoryInfo, GetRarityInfo | tooltip สูตรคราฟต์ |
| Hyper_Gacha | HasRarity, GetRarityColor, GetRarityPalette | สีรางวัลกาชา |
| Hyper_Bountyhunt | GetRarityPalette | สี HUD |
| Hyper_Fishing | GetRarity, GetRarityInfo | สีปลา |
| Hyper_Shop, Hyper_Market, Hyper_Economy, Hyper_Notifyall, Hyper_Jobagency, Hyper_Event, Hyper_Airdrop, Hyper_Warzone, Hyper_TradingJobs, Hyper_Heist | GetRarityInfo | สีการ์ดไอเทม |

ยังไม่มี resource ไหนเรียก OpenStash, GetStashItems, SetStashItems, OpenInventory, IsOpen และ SetVehicleKeys

{% hint style="info" %}
export ฝั่ง client ทั้ง 7 ตัวถูกส่งผ่าน Hyper_Check Code Vault (`hyper_vault_export` ใน fxmanifest) — ถ้าเพิ่ม export ฝั่ง client ใหม่ ต้องเพิ่มชื่อในรายการนั้นด้วย ไม่งั้น resource อื่นเรียกไม่ได้
{% endhint %}
