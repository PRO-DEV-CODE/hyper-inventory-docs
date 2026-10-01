# เทคโนโลยีและโครงสร้าง

ฝั่ง server เป็นผู้ตัดสินทุก action ส่วน client และ NUI ทำหน้าที่แสดงผลและส่งคำขอเท่านั้น

| ชั้น | เทคโนโลยี | ไฟล์หลัก | ขนาด |
| --- | --- | --- | --- |
| NUI (หน้าจอ) | HTML + CSS + JavaScript, Font Awesome, Iconify, ฟอนต์ Kanit | html/index.html, css/style.css, js/app.js | 5,607 บรรทัด |
| Client | Lua 5.4 | core/client/main.lua, accessories.lua | 1,892 บรรทัด |
| Server | Lua 5.4 + oxmysql | core/server/main.lua, extensions.lua | 1,820 บรรทัด |
| Shared | Lua | core/shared/common.lua | 279 บรรทัด |
| ฐานข้อมูล | MySQL | owned_vehicles, owned_properties, meeta_accessory_inventory | — |

## ความปลอดภัย

* ทุก action ที่มีมูลค่า (ใช้, ทิ้ง, มอบ, เทรด, เก็บ/หยิบตู้) ตรวจซ้ำที่ server: จำนวนที่มีจริง, ระยะห่าง, blacklist
* มอบของเช็คระยะ 3 เมตรเสมอ เทรดเช็ค 4 เมตรทั้งตอนขอ รับ และปิดดีล
* โค้ดฝั่ง client ส่งผ่าน Hyper_Check Code Vault ตอนรัน ไม่เก็บ cache ในเครื่องผู้เล่น
* ส่ง Discord log ตอนมอบ/ทิ้งของผ่าน Hyper_Discordlogs

## Exports

**Server:** OpenStash, OpenStashExternal, GetStashItems, SetStashItems, RefreshStash, AddBadge, RemoveBadge, InvalidateKeys, InvalidateAccessories

**Client:** OpenInventory, CloseInventory, IsOpen, SetVehicleKeys, SetSkinnable, ApplyCustomImage, ResetCustomImage

```lua
-- เปิดตู้เก็บของให้ผู้เล่น
exports['Hyper_Inventory']:OpenStash(playerId, stashId, label, slots)
```

## Dependencies

| จำเป็น | ไม่บังคับ |
| --- | --- |
| es_extended, oxmysql, Hyper_Check | Hyper_Notifyall, Hyper_Discordlogs, esx_skin + skinchanger |
