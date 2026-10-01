# ควบคุมกระเป๋า

เปิด ปิด และเช็คสถานะกระเป๋าจาก resource อื่น — ฝั่ง **client**

| Export | คืนค่า | ใช้ทำอะไร |
| --- | --- | --- |
| `OpenInventory()` | — | เปิดกระเป๋า |
| `CloseInventory()` | — | ปิดกระเป๋า (ปิดตู้ที่เปิดอยู่ด้วย) |
| `IsOpen()` | boolean | กระเป๋าเปิดอยู่ไหม |
| `SetVehicleKeys(keys)` | — | ส่งรายการกุญแจรถเข้าแผงกุญแจ `{ {label = "RGB 909"}, ... }` |

## แนะนำ: ปิดกระเป๋าก่อนเปิดเมนูของตัวเอง

เมนู NUI สองตัวที่เปิดพร้อมกันจะแย่ง focus กัน ให้ปิดกระเป๋าก่อนเสมอ

```lua
if exports["Hyper_Inventory"]:IsOpen() then
    exports["Hyper_Inventory"]:CloseInventory()
end
-- แล้วค่อย SetNuiFocus / เปิดเมนูของคุณ
```

ใช้อยู่ใน Hyper_Skinui (ร้านเสื้อผ้า), Hyper_Thief (ค้นตัว), Hyper_Profilestatus (โปรไฟล์)

| เมนู | ควรเรียก |
| --- | --- |
| ร้านค้า, คราฟต์, ร้านเสื้อผ้า, โปรไฟล์, เมนูงาน | `CloseInventory` ก่อนเปิด |
| ค้นตัว / ปล้น / จับกุม | `CloseInventory` ของผู้ถูกกระทำ |
| ระบบกุญแจรถแยก | `SetVehicleKeys` แทนการดึงจาก owned_vehicles |
