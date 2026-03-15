# Drug Cost Dashboard (มูลค่าการสั่งยา แยกแพทย์)

Dashboard แสดงมูลค่าการสั่งยา แยกตามแพทย์ผู้สั่ง | Host บน GitHub Pages (ฟรี)

## เป้าหมายหลัก
ดูว่า **แพทย์คนใดสั่งยาให้สิทธิ์ UC มูลค่าสูงสุด** แยกตามสิทธิ์และประเภทยา

## ข้อมูล
- **ไฟล์:** `data.csv` (~70 MB)
- **ช่วงเวลา:** 1 มีนาคม 2568 – 28 กุมภาพันธ์ 2569 (12 เดือน)

### Columns
| Column | คำอธิบาย |
|--------|---------|
| dep | แผนก: IPD, OPD |
| dch_doctor_name | ชื่อแพทย์ผู้สั่ง |
| pttype | สิทธิ์: UC, SSO, SKS |
| type | ประเภทยา: ค่าว่าง = NED (นอกบัญชี), มีค่า = ED (ในบัญชี) |
| Sum of qty | จำนวนยาที่สั่ง |
| Sum of sum_costprice (THB) | มูลค่ายา (บาท) |
| lookup_drugitems - icode → drug_name | ชื่อยา |

### สิทธิ์การรักษา (pttype) — ลำดับแสดงผล
| รหัส | ชื่อ |
|------|------|
| **UC** | บัตรทอง |
| **SKS** | เบิกได้ (ข้าราชการ) |
| **SSO** | ประกันสังคม |

## หลักการสำคัญ
- **KPI Cards คลิกได้** — filter สิทธิ์ไปยังกราฟและตารางทั้งหมด
- **Sub-cards ED/NED** — คลิก filter ยาในบัญชี/นอกบัญชีได้
- **Global filter** ทั้งหมด/OPD/IPD — ใช้ร่วมกันทั้ง Tab 1 และ Tab 2

## โครงสร้าง Dashboard

### Tab 1: ภาพรวม (T1)
- **T1-2** KPI Cards: มูลค่ารวม UC / SKS / SSO / ทั้งหมด (คลิกได้ = filter)
  - Sub-cards: ED ในบัญชี / NED นอกบัญชี (คลิกได้)
- **T1-3a** Donut chart: สัดส่วนมูลค่าตามสิทธิ์
- **T1-3b** Bar chart: Top 15 แพทย์ มูลค่าสูงสุด
- **T1-4** ตาราง Top 20 แพทย์

### Tab 2: รายละเอียด (T2)
- **T2-F2** filter สิทธิ์ (UC/SKS/SSO/ทั้งหมด)
- **T2-F3** filter บัญชียา (ED/NED/ทั้งหมด)
- **T2-F4** dropdown เลือกแพทย์ (sort by cost DESC)
- **T2-D1** ชื่อแพทย์ที่เลือก + จำนวนรายการ
- **T2-D2** Donut สัดส่วน ED/NED
- **T2-D3** มูลค่ารวม + breakdown ED/NED
- **T2-D4** ตาราง Top 20 ยา (ชื่อยา, จำนวน, มูลค่า, %)

## Tech Stack
- HTML + PapaParse 5.4.1 + Chart.js 4.4.4
- Single file `index.html` + `data.csv`
- ไม่ต้อง install/build ใดๆ

## วิธี Deploy ขึ้น GitHub Pages
1. สร้าง repo ใหม่ (Public) บน GitHub
2. Upload `index.html` + `data.csv`
3. Settings → Pages → Branch: main → / (root) → Save
4. รอ 1-3 นาที → เปิด URL

## สถานะ
- [x] Tab 1: ภาพรวม (KPI, Donut, Bar, Top 20)
- [x] Tab 2: รายละเอียด (filter 4 ตัว, Donut, ตาราง Top 20 ยา)
- [x] Global dep filter ร่วม T1+T2
- [x] ทดสอบ local (port 7777)
- [ ] Upload GitHub + เปิด Pages
