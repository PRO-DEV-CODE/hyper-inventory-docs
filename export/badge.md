# Badge บนไอเทม

ติดตราเล็ก ๆ บนการ์ดไอเทม เช่น ลำโพงที่กำลังเปิด หรือของที่ติดตัวอยู่ — ไอเทมที่มี badge จะขึ้นในแผง **ใส่อยู่** ด้วย (ยกเว้น key `expired` ซึ่งไปอยู่แผง **หมดอายุ**) ฝั่ง **server**

## AddBadge

```lua
exports["Hyper_Inventory"]:AddBadge(playerId, {
    name = "speaker",      -- ชื่อไอเทม (จำเป็น)
    key = "speaker_active", -- รหัสของ badge (ไม่ใส่ = "badge")
    icon = "icon",
    type = "item",
    options = { priority = 1, iconScale = 1.0, iconColor = "#046b5877" },
})
```

ไอเทมเดียวมีหลาย badge ได้ แยกกันด้วย `key`

## RemoveBadge

```lua
exports["Hyper_Inventory"]:RemoveBadge(playerId, { name = "speaker", key = "speaker_active", type = "item" })
```

## แนะนำใช้กับ

| เมนู / ระบบ | Badge |
| --- | --- |
| ลำโพง / วิทยุที่เปิดอยู่ | ติดตอนเปิด ถอดตอนปิด (Hyper_Music) |
| ของติดตัว / แฟชั่น | ติดตอนสวม ถอดตอนถอด (Hyper_Attacher) |
| ไอเทมมีวันหมดอายุ | key `expired` → ไปแผง หมดอายุ (Hyper_Expire) |

Badge เก็บใน RAM ต่อผู้เล่น — ผู้เล่นออกแล้วหาย ต้องติดใหม่ตอนเข้าเกม
