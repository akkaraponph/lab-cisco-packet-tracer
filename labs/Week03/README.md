# Week 03: Static IP และ Share IP

## วัตถุประสงค์
- เรียนรู้การตั้งค่า Static IP Address
- เรียนรู้การแชร์ IP Address (NAT/PAT)
- ทำความเข้าใจความแตกต่างระหว่าง Static IP และ Dynamic IP
- เรียนรู้การตั้งค่า Network Address Translation (NAT)

## เนื้อหาการเรียนรู้

### 1. Static IP Configuration
- การตั้งค่า IP Address แบบ Static
- การตั้งค่า Subnet Mask และ Default Gateway
- การตั้งค่า DNS Server

### 2. IP Sharing (NAT/PAT)
- Network Address Translation (NAT)
- Port Address Translation (PAT)
- การแชร์ IP Address ระหว่างเครือข่าย

## ไฟล์แล็บ

- `week03_ex01_StaticIP.pkt` - แล็บการตั้งค่า Static IP
- `week03_ex02_ShareIP.pkt` - แล็บการแชร์ IP Address

## ขั้นตอนการทำแล็บ

### Lab 1: Static IP Configuration
1. เปิดไฟล์ `week03_ex01_StaticIP.pkt`
2. ตั้งค่า Static IP Address ให้กับทุกอุปกรณ์
3. ตั้งค่า Default Gateway ให้ถูกต้อง
4. ทดสอบการเชื่อมต่อด้วย ping

### Lab 2: IP Sharing (NAT)
1. เปิดไฟล์ `week03_ex02_ShareIP.pkt`
2. ตั้งค่า NAT บน Router
3. ตรวจสอบการทำงานของ NAT
4. ทดสอบการเชื่อมต่อจากภายในไปภายนอก

## คำสั่งที่ใช้

### Static IP Configuration
```
interface FastEthernet 0/0
ip address [IP] [Subnet Mask]
no shutdown
```

### NAT Configuration
```
# กำหนด inside interface
interface FastEthernet 0/0
ip nat inside
exit

# กำหนด outside interface
interface Serial 0/0/0
ip nat outside
exit

# สร้าง NAT pool (ถ้าต้องการ)
ip nat pool [pool-name] [start-ip] [end-ip] netmask [subnet]
ip nat inside source list [ACL-number] pool [pool-name]

# หรือใช้ PAT (overload)
ip nat inside source list [ACL-number] interface [interface] overload
```

### การตรวจสอบ NAT
```
show ip nat translations        # ดู NAT translation table
show ip nat statistics          # ดูสถิติ NAT
debug ip nat                    # debug NAT (ใช้ใน privileged mode)
```

## การตรวจสอบ

- ✅ ทุกอุปกรณ์มี Static IP Address ที่ถูกต้อง
- ✅ NAT ทำงานถูกต้อง (ถ้ามี)
- ✅ อุปกรณ์ภายในสามารถเชื่อมต่อภายนอกได้
- ✅ การ translate IP Address ทำงานถูกต้อง

## หมายเหตุ

- Static IP ใช้เมื่อต้องการ IP Address ที่ไม่เปลี่ยนแปลง
- NAT ช่วยให้เครือข่ายภายในใช้ IP Address ส่วนตัว (Private IP) และแชร์ IP Address สาธารณะ (Public IP)
- PAT (Port Address Translation) เป็นการแชร์ IP Address แบบหลายต่อหนึ่ง

