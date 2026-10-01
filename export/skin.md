# สกินและรูปการ์ด

ใช้กับระบบสกินอาวุธ — เพิ่มปุ่ม **สกิน** ในเมนูคลิกขวา และเปลี่ยนรูปการ์ดในกระเป๋า ฝั่ง **client** (ใช้อยู่ใน Hyper_Weaponskin)

## SetSkinnable

```lua
exports["Hyper_Inventory"]:SetSkinnable({ "WEAPON_PISTOL", "WEAPON_KNIFE" })
```

ลงทะเบียนอาวุธที่ใส่สกินได้ ส่งมาทั้งชุด แทนที่ของเดิม ส่ง `nil` หรือตารางว่าง = ล้าง อาวุธในรายการจะมีปุ่ม **สกิน** ในเมนูคลิกขวา กดแล้วกระเป๋าปิดและเรียก `exports["Hyper_Weaponskin"]:openmenu(name)`

![เมนูคลิกขวา](../.gitbook/assets/03_context_menu.png)

## ApplyCustomImage

```lua
exports["Hyper_Inventory"]:ApplyCustomImage(kind, key, imageKey) -- → boolean
```

| Argument | ความหมาย |
| --- | --- |
| `kind` | `'weapon'` หรือ `'item'` |
| `key` | ชื่อไอเทม หรือชื่อ/แฮชอาวุธ |
| `imageKey` | ชื่อไฟล์ใน `html/img/items/` ไม่ต้องใส่ `.png` — ว่าง = คืนรูปเดิม |

## ResetCustomImage

```lua
exports["Hyper_Inventory"]:ResetCustomImage(kind, key) -- ไม่ส่ง key = คืนรูปเดิมทั้งหมดของ kind นั้น
```
