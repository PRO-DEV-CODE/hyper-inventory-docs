# Rarity และข้อมูลไอเทม

ให้ทุกเมนูในเซิร์ฟใช้สีความหายาก หมวด และรายละเอียดไอเทมชุดเดียวกับกระเป๋า ไม่ต้องก๊อปตาราง config ไปไว้เอง — เรียกได้ทั้ง **client และ server** เป็นกลุ่มที่ใช้มากที่สุด (17 resource)

| Export | คืนค่า |
| --- | --- |
| `GetRarityInfo(name, isWeapon?)` | `{ tier, level, color, label }` |
| `GetRarity(name, isWeapon?)` | ชื่อ tier เช่น `"epic"` |
| `GetRarityColor(name, isWeapon?)` | สี hex |
| `HasRarity(name, isWeapon?)` | `true` ถ้ามีข้อมูลจริง (ไม่ใช่ค่า default) |
| `GetRarityPalette()` | `{ common = "#..", ..., mythic = "#.." }` |
| `GetItemDescription(name, isWeapon?)` | ข้อความรายละเอียดไอเทม (มี tag `<highlight>` ฯลฯ) |
| `GetItemCategoryInfo(name, isWeapon?)` | `{ key, label, icon }` หมวดเดียวกับแท็บกรองในกระเป๋า |
| `GetItemDetail(name, isWeapon?)` | ตารางการ์ดรายละเอียด (warn / sections / properties / stats / maxLevel) หรือ `nil` |

Tier มี 6 ระดับ: common → uncommon → rare → epic → legendary → mythic (level 0–5) ชื่ออาวุธใช้ตัวพิมพ์ใหญ่ เช่น `WEAPON_PISTOL`

## ตัวอย่าง: การ์ดไอเทมในร้านค้า

```lua
local r = exports["Hyper_Inventory"]:GetRarityInfo(item.name, item.type == "weapon")
-- r.tier = "legendary", r.level = 4, r.color = สี hex, r.label = ชื่อ tier ภาษาไทย
SendNUIMessage({ action = "item", name = item.name, rarity = r })
```

## ตัวอย่าง: tooltip แบบเดียวกับกระเป๋า (Hyper_Crafting)

```lua
local cat    = exports["Hyper_Inventory"]:GetItemCategoryInfo(name, isWeapon == true)
local detail = exports["Hyper_Inventory"]:GetItemDetail(name, isWeapon == true)
local desc   = exports["Hyper_Inventory"]:GetItemDescription(name, isWeapon == true)
```

## ตัวอย่าง: ใช้สีของกระเป๋าเฉพาะเมื่อมีข้อมูล (Hyper_Gacha)

```lua
if exports["Hyper_Inventory"]:HasRarity(name) then
    color = exports["Hyper_Inventory"]:GetRarityColor(name)
else
    color = myDefaultColor
end
```

## แนะนำใช้กับ

| เมนู | Export |
| --- | --- |
| ร้านค้า, ตลาด, เศรษฐกิจ, แอดมินเสกของ | `GetRarityInfo` |
| รางวัลกาชา, airdrop, event, warzone | `GetRarityInfo` หรือ `HasRarity` + `GetRarityColor` |
| คราฟต์, ช่างตีบวก — tooltip เต็ม | `GetItemDetail` + `GetItemDescription` + `GetItemCategoryInfo` |
| HUD / UI ที่ทำ legend สี | `GetRarityPalette` |
| แจ้งเตือนได้ของ | `GetRarityInfo` (Hyper_Notifyall) |

{% hint style="warning" %}
`GetItemDetail` ของเจม ดึงสดจาก Hyper_Profilestatus ซึ่งมี export อยู่ฝั่ง client เท่านั้น — ถ้าเรียกจาก server เจมจะไม่มีรายละเอียด
{% endhint %}
