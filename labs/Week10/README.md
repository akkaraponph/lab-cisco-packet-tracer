# Week 10: RIP Routing Protocol

## วัตถุประสงค์
- เรียนรู้การตั้งค่า RIP (Routing Information Protocol)
- ทำความเข้าใจการทำงานของ Distance Vector Routing Protocol
- เรียนรู้การแชร์ routing information ระหว่าง Router
- เรียนรู้การตรวจสอบและแก้ไขปัญหา RIP

## เนื้อหาการเรียนรู้

### 1. RIP Basics
- ความหมายและหลักการทำงานของ RIP
- Distance Vector Routing Protocol
- RIP Version 1 และ Version 2
- Administrative Distance และ Metric

### 2. RIP Configuration
- การเปิดใช้งาน RIP
- การประกาศ Network
- การตั้งค่า RIP Version
- การตรวจสอบ RIP

### 3. RIP Troubleshooting
- การตรวจสอบ RIP Routes
- การแก้ไขปัญหา RIP
- การใช้คำสั่ง debug

## ไฟล์แล็บ

- `W10LAB01.pkt` - แล็บการตั้งค่า RIP

## ขั้นตอนการทำแล็บ

1. เปิดไฟล์ `W10LAB01.pkt`
2. ศึกษาโครงสร้างเครือข่ายและ Router ทั้งหมด
3. ตั้งค่า IP Address ให้กับทุก Interface
4. เปิดใช้งาน RIP บน Router ทุกตัว
5. ประกาศ Network ที่เชื่อมต่ออยู่
6. ตรวจสอบ Routing Table
7. ทดสอบการเชื่อมต่อระหว่างเครือข่าย

## คำสั่งที่ใช้

### การตั้งค่า RIP
```
configure terminal
router rip
version 2                    # ใช้ RIP version 2 (ถ้าต้องการ)
network [network-address]    # ประกาศ network ที่เชื่อมต่ออยู่
no auto-summary             # ปิดการสรุปอัตโนมัติ (RIP v2)
exit
```

### การตรวจสอบ RIP
```
show ip route                # ดู routing table
show ip protocols           # ดู routing protocol ที่ใช้งาน
show ip rip database        # ดู RIP database
debug ip rip                # debug RIP (ใช้ใน privileged mode)
```

### การตั้งค่า Interface
```
configure terminal
interface FastEthernet 0/0
ip address [IP] [Subnet Mask]
no shutdown
exit
```

## เอกสารเพิ่มเติม
ดูไฟล์ `docs/text.txt` สำหรับคำสั่งและขั้นตอนโดยละเอียด

## ตัวอย่างการตั้งค่า

```
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 192.168.1.0
Router(config-router)# network 192.168.2.0
Router(config-router)# no auto-summary
Router(config-router)# exit
```

## การตรวจสอบ

- ✅ RIP ทำงานบน Router ทุกตัว
- ✅ Network ถูกประกาศถูกต้อง
- ✅ Routing Table มี RIP routes
- ✅ อุปกรณ์ในเครือข่ายต่างกันสามารถสื่อสารกันได้
- ✅ Router แชร์ routing information กันได้

## หมายเหตุ

- RIP ใช้ Hop Count เป็น Metric (สูงสุด 15 hops)
- RIP Version 2 รองรับ VLSM และ CIDR
- ใช้ `network` command เพื่อประกาศ network ที่ Router เชื่อมต่ออยู่
- ตรวจสอบให้แน่ใจว่า Router ทุกตัวประกาศ network ที่ถูกต้อง
- ใช้ `show ip route` เพื่อตรวจสอบว่า Router เรียนรู้ routes จาก RIP

## เปรียบเทียบ RIP กับ Static Routing

- **Static Routing**: ต้องตั้งค่าเองทุกเส้นทาง, ไม่มีการอัปเดตอัตโนมัติ
- **RIP**: เรียนรู้ routes อัตโนมัติ, มีการอัปเดตเป็นระยะ, เหมาะกับเครือข่ายขนาดเล็ก-กลาง

