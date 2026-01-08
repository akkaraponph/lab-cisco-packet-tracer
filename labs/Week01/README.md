# Week 01: Introduction to Cisco Packet Tracer

## วัตถุประสงค์
- ทำความคุ้นเคยกับ Cisco Packet Tracer Interface
- เรียนรู้การเพิ่มและเชื่อมต่ออุปกรณ์พื้นฐาน
- เรียนรู้การตั้งค่า IP Address
- เรียนรู้คำสั่งพื้นฐานของ Router
- เรียนรู้การตรวจสอบการเชื่อมต่อ

## เนื้อหาการเรียนรู้

### 1. การใช้งาน Cisco Packet Tracer
- Interface และ Tools พื้นฐาน
- การเพิ่มอุปกรณ์ (Devices)
- การเชื่อมต่อด้วยสาย (Connections)

### 2. การตั้งค่า IP Address
- การตั้งค่า IP บน PC
- การตั้งค่า IP บน Router Interface
- Subnet Mask และ Default Gateway

### 3. คำสั่ง Router พื้นฐาน
- Privileged Mode และ Configuration Mode
- การตั้งค่า Interface
- การเปิด/ปิด Interface

### 4. การตรวจสอบการเชื่อมต่อ
- คำสั่ง ping
- คำสั่ง show ต่างๆ
- การดูสถานะ Interface

## แล็บที่แนะนำ

### Lab 1: Basic Network Setup
สร้าง network พื้นฐานที่มี:
- 2 PCs
- 1 Switch
- 1 Router

**ขั้นตอน:**
1. เพิ่มอุปกรณ์: 2 PCs, 1 Switch, 1 Router
2. เชื่อมต่อ PCs กับ Switch ด้วยสาย Straight-through
3. เชื่อมต่อ Switch กับ Router ด้วยสาย Straight-through
4. ตั้งค่า IP:
   - PC0: 192.168.1.10/24, Gateway: 192.168.1.1
   - PC1: 192.168.1.20/24, Gateway: 192.168.1.1
   - Router Fa0/0: 192.168.1.1/24
5. เปิด Router Interface: `no shutdown`
6. ทดสอบ ping ระหว่าง PC0 และ PC1

### Lab 2: Router Configuration Practice
ฝึกการตั้งค่า Router:
1. เข้าสู่ Privileged Mode: `enable`
2. เข้าสู่ Configuration Mode: `configure terminal`
3. ตั้งค่า Interface: `interface FastEthernet 0/0`
4. ตั้งค่า IP: `ip address 192.168.1.1 255.255.255.0`
5. เปิด Interface: `no shutdown`
6. ตรวจสอบ: `show ip interface brief`

## คำสั่งที่ควรจำ

```
enable                          # เข้าสู่ privileged mode
configure terminal              # เข้าสู่ configuration mode
interface FastEthernet 0/0      # เลือก interface
ip address [IP] [Subnet]         # ตั้งค่า IP
no shutdown                     # เปิดใช้งาน interface
exit                            # ออกจาก mode ปัจจุบัน
show ip interface brief         # ดูสถานะ interface
ping [IP]                       # ทดสอบการเชื่อมต่อ
```

## เอกสารเพิ่มเติม
ดูไฟล์ `docs/introduction.txt` สำหรับคำสั่งและขั้นตอนโดยละเอียด

