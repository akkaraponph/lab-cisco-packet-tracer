# Week 07: VLAN Configuration

## วัตถุประสงค์
- เรียนรู้การสร้างและจัดการ VLAN (Virtual LAN)
- เรียนรู้การตั้งค่า VLAN บน Switch
- เรียนรู้การเชื่อมต่อระหว่าง VLAN (Inter-VLAN Routing)
- ทำความเข้าใจประโยชน์ของ VLAN

## เนื้อหาการเรียนรู้

### 1. VLAN Basics
- ความหมายและประโยชน์ของ VLAN
- การแยกเครือข่ายแบบลอจิก
- VLAN ID และ VLAN Name

### 2. VLAN Configuration
- การสร้าง VLAN
- การกำหนด Port ให้กับ VLAN
- การตั้งค่า Trunk Port
- การตั้งค่า Access Port

### 3. Inter-VLAN Routing
- การเชื่อมต่อระหว่าง VLAN ด้วย Router
- Router-on-a-Stick Configuration
- การตั้งค่า Sub-interface

## ไฟล์แล็บ

- `W7LAB01.pkt` - แล็บ VLAN พื้นฐาน
- `W7LAB02.pkt` - แล็บ VLAN ขั้นสูง
- `W7LAB03.pkt` - แล็บ Inter-VLAN Routing
- `ExtraClass_VLAN.pkt` - แล็บเพิ่มเติม VLAN

## ขั้นตอนการทำแล็บ

### Lab 1: Basic VLAN Configuration
1. เปิดไฟล์ `W7LAB01.pkt`
2. สร้าง VLAN ใหม่
3. กำหนด Port ให้กับ VLAN
4. ทดสอบการเชื่อมต่อภายใน VLAN เดียวกัน

### Lab 2: Multiple VLANs
1. เปิดไฟล์ `W7LAB02.pkt`
2. สร้าง VLAN หลายตัว
3. กำหนด Port ให้กับ VLAN ที่เหมาะสม
4. ทดสอบการแยกเครือข่าย

### Lab 3: Inter-VLAN Routing
1. เปิดไฟล์ `W7LAB03.pkt`
2. ตั้งค่า Router-on-a-Stick
3. สร้าง Sub-interface สำหรับแต่ละ VLAN
4. ทดสอบการเชื่อมต่อระหว่าง VLAN

## คำสั่งที่ใช้

### สร้าง VLAN
```
configure terminal
vlan [VLAN-ID]
name [VLAN-NAME]
exit
```

### กำหนด Port ให้กับ VLAN
```
configure terminal
interface FastEthernet 0/[port-number]
switchport mode access
switchport access vlan [VLAN-ID]
no shutdown
exit
```

### ตั้งค่า Trunk Port
```
configure terminal
interface FastEthernet 0/[port-number]
switchport mode trunk
switchport trunk allowed vlan [VLAN-IDs]
no shutdown
exit
```

### Router-on-a-Stick (Inter-VLAN Routing)
```
configure terminal
interface FastEthernet 0/0.[VLAN-ID]
encapsulation dot1Q [VLAN-ID]
ip address [IP] [Subnet Mask]
no shutdown
exit
```

### การตรวจสอบ VLAN
```
show vlan                    # ดู VLAN ทั้งหมด
show vlan brief              # ดู VLAN แบบย่อ
show interfaces switchport    # ดูการตั้งค่า switchport
show interfaces trunk        # ดู trunk port
```

## เอกสารเพิ่มเติม
ดูไฟล์ `docs/vlan.txt` สำหรับคำสั่งและขั้นตอนโดยละเอียด

## การตรวจสอบ

- ✅ VLAN ถูกสร้างและตั้งค่าถูกต้อง
- ✅ Port ถูกกำหนดให้กับ VLAN ที่ถูกต้อง
- ✅ อุปกรณ์ใน VLAN เดียวกันสามารถสื่อสารกันได้
- ✅ อุปกรณ์ใน VLAN ต่างกันไม่สามารถสื่อสารกันได้ (ถ้าไม่มี Router)
- ✅ Inter-VLAN Routing ทำงานถูกต้อง (ถ้ามี Router)

## หมายเหตุ

- VLAN ช่วยแยกเครือข่ายแบบลอจิกโดยไม่ต้องแยกทางกายภาพ
- Access Port ใช้สำหรับเชื่อมต่อกับ End Device
- Trunk Port ใช้สำหรับเชื่อมต่อระหว่าง Switch
- Router-on-a-Stick ใช้ Router เพียงตัวเดียวในการเชื่อมต่อหลาย VLAN

