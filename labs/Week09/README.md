# Week 09: แล็บพื้นฐาน

## วัตถุประสงค์
- ทบทวนความรู้พื้นฐานเกี่ยวกับเครือข่าย
- ฝึกทักษะการตั้งค่าอุปกรณ์เครือข่าย
- ทำความเข้าใจการทำงานของเครือข่าย

## เนื้อหาการเรียนรู้

### 1. Network Configuration Review
- การตั้งค่า IP Address
- การตั้งค่า Router
- การตั้งค่า Switch
- การทดสอบการเชื่อมต่อ

### 2. Network Troubleshooting
- การตรวจสอบการตั้งค่า
- การแก้ไขปัญหาเบื้องต้น
- การใช้คำสั่ง diagnostic

## ไฟล์แล็บ

- `W09LAB1.pkt` - แล็บพื้นฐาน Week 9

## ขั้นตอนการทำแล็บ

1. เปิดไฟล์ `W09LAB1.pkt`
2. ศึกษาโครงสร้างเครือข่าย
3. ตรวจสอบการตั้งค่าปัจจุบัน
4. ตั้งค่าตามที่กำหนด
5. ทดสอบการเชื่อมต่อระหว่างอุปกรณ์
6. ตรวจสอบการทำงานของเครือข่าย
7. แก้ไขปัญหาที่พบ

## คำสั่งที่ใช้

```
# Router Configuration
enable
configure terminal
interface FastEthernet 0/0
ip address [IP] [Subnet Mask]
no shutdown
exit

# การตรวจสอบ
show ip interface brief
show running-config
show ip route
show cdp neighbors

# การทดสอบ
ping [IP Address]
traceroute [IP Address]
```

## การตรวจสอบ

- ✅ อุปกรณ์ทั้งหมดเชื่อมต่อกันได้
- ✅ IP Address ถูกตั้งค่าถูกต้อง
- ✅ Default Gateway ถูกต้อง
- ✅ การ routing ทำงานถูกต้อง (ถ้ามี Router)
- ✅ ไม่มีข้อผิดพลาดในการตั้งค่า

## หมายเหตุ

- ตรวจสอบให้แน่ใจว่าทุก Interface ถูกเปิดใช้งาน
- ใช้คำสั่ง `show` เพื่อตรวจสอบสถานะ
- บันทึกการตั้งค่าด้วย `write memory`
- ใช้ Simulation Mode เพื่อดูการทำงานของ packets

