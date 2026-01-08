# Week 02: การทดสอบการตั้งค่า

## วัตถุประสงค์
- ทดสอบการตั้งค่าพื้นฐานของอุปกรณ์เครือข่าย
- ฝึกการตรวจสอบการทำงานของ network
- ทำความเข้าใจการตั้งค่า IP และการเชื่อมต่อ

## เนื้อหาการเรียนรู้

### 1. การทดสอบการตั้งค่า
- การตรวจสอบการตั้งค่า IP Address
- การทดสอบการเชื่อมต่อระหว่างอุปกรณ์
- การใช้คำสั่งตรวจสอบสถานะ

### 2. การแก้ไขปัญหาเบื้องต้น
- การตรวจสอบการเชื่อมต่อสาย
- การตรวจสอบการตั้งค่า Interface
- การใช้คำสั่ง diagnostic

## ไฟล์แล็บ

- `week2_test_config.pkt` - แล็บทดสอบการตั้งค่าพื้นฐาน

## ขั้นตอนการทำแล็บ

1. เปิดไฟล์ `week2_test_config.pkt`
2. ตรวจสอบการตั้งค่า IP Address ของอุปกรณ์ทั้งหมด
3. ทดสอบการเชื่อมต่อด้วยคำสั่ง ping
4. ตรวจสอบสถานะ Interface ด้วย `show ip interface brief`
5. ตรวจสอบ routing table ด้วย `show ip route` (ถ้ามี Router)

## คำสั่งที่ใช้

```
show ip interface brief         # ดูสถานะ interface ทั้งหมด
show running-config             # ดูการตั้งค่าปัจจุบัน
ping [IP Address]               # ทดสอบการเชื่อมต่อ
traceroute [IP Address]         # ติดตามเส้นทางของ packet
show ip route                   # ดู routing table
```

## การตรวจสอบ

- ✅ ทุกอุปกรณ์สามารถ ping ถึงกันได้
- ✅ Interface ทั้งหมดมีสถานะ UP
- ✅ IP Address ถูกตั้งค่าถูกต้อง
- ✅ Default Gateway ถูกตั้งค่าถูกต้อง

## หมายเหตุ

- ตรวจสอบให้แน่ใจว่าทุก Interface ถูกเปิดใช้งานด้วย `no shutdown`
- ใช้ Simulation Mode เพื่อดูการทำงานของ packets
- บันทึกการตั้งค่าด้วย `write memory` หรือ `copy running-config startup-config`

