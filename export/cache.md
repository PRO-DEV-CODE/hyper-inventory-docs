# ล้าง cache

กระเป๋าจำรายการกุญแจรถและเครื่องประดับไว้ชั่วคราวเพื่อไม่ต้องอ่าน DB ทุกครั้งที่เปิด ถ้า resource อื่นแก้ข้อมูลใน DB ต้องเรียก export เหล่านี้ ไม่งั้นผู้เล่นจะเห็นของเก่า — ฝั่ง **server**

## InvalidateKeys

```lua
exports["Hyper_Inventory"]:InvalidateKeys(playerId)
```

เรียกหลังแก้ตาราง `owned_vehicles` — ซื้อรถ ขายรถ โอนรถ ยึดรถ (Hyper_Gang ใช้ตอนโอนรถแก๊ง)

## InvalidateAccessories

```lua
exports["Hyper_Inventory"]:InvalidateAccessories(playerId)
```

เรียกหลังเพิ่ม/ลบแถวเครื่องประดับใน DB — ร้านเสื้อผ้า กาชาเครื่องประดับ (Hyper_Skinui) ถ้าผู้เล่นออนไลน์ กระเป๋าจะส่งข้อมูลใหม่ให้ทันที

## แนะนำใช้กับ

| เมนู | Export |
| --- | --- |
| ร้านรถ, ประมูลรถ, โอนรถ, ยึดรถ | `InvalidateKeys` ทั้งผู้ขายและผู้ซื้อ |
| ร้านเสื้อผ้า, กาชาแฟชั่น, แอดมินเสกเครื่องประดับ | `InvalidateAccessories` |
