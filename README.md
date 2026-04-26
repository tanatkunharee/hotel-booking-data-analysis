# CP372 Data Analytics Project

## Azure Stay: Strategic Distribution & Profit Optimization

การวิเคราะห์เพื่อเพิ่มประสิทธิภาพช่องทางการจัดจำหน่ายและเพิ่มกำไรสุทธิสูงสุดให้กับธุรกิจโรงแรม

---

## สมาชิกกลุ่ม
* **6610201013** ณัฐวุฒิ เคลือบทอง
* **66102010142** ธนัท กันหารี
* **66102010571** อนันตสิน ลาภวิสุทธิสาโรจน์

---

## Problem Statement
โรงแรม **Azure Stay** กำลังเผชิญกับภาวะ **“รายได้สูง แต่กำไรสุทธิต่ำ” (Profit Margin Erosion)** แม้จะมียอดจอง (Volume) เข้ามาอย่างต่อเนื่อง แต่ธุรกิจต้องสูญเสียรายได้ไปกับ "ต้นทุนแฝง" จำนวนมหาศาล ได้แก่ ค่าคอมมิชชันจากตัวแทนขายออนไลน์ (OTAs) ที่สูงถึง 15-20% และค่าใช้จ่ายทางการตลาด (Marketing Spend) ในช่องทาง Direct Web โครงการนี้จึงมุ่งเน้นการวิเคราะห์ Data เพื่อค้นหาช่องทางที่สร้างกำไรสุทธิ (Net Profit) อย่างแท้จริง และอุดรอยรั่วไหลของรายได้จากการยกเลิกห้องพัก (Revenue Leakage)

## SMART Objectives
- **S (Specific):** ปรับสัดส่วนช่องทางการจัดจำหน่ายห้องพักโดยเพิ่มการเข้าพักที่มีคุณภาพและลดต้นทุนแฝง
- **M (Measurable):** เพิ่ม Net RevPAR 10% และ ลดค่า Commission & Marketing รวมกัน 15%
- **A (Achievable):** ทำ Customer Segmentation ตามช่วงเวลา (Weekday/Weekend) และปรับนโยบายราคา (Rate Code) เพื่อป้องกันการยกเลิกห้อง
- **R (Relevant):** ลดการพึ่งพา OTA สร้างฐานลูกค้าประจำ (Direct Booking) เพื่อเพิ่มอัตรากำไรสุทธิสูงสุด
- **T (Time-bound):** วัดผลการเปลี่ยนแปลงและบรรลุเป้าหมายภายใน 1 ไตรมาส (3 เดือน)

## Analytical Questions
- ช่องทางการจองใดที่สร้าง "กำไรสุทธิต่อการจอง" (True Net ADR) สูงที่สุดเมื่อหักต้นทุนทั้งหมดแล้ว?
- โมเดลการคิดค่าคอมมิชชันแบบใด (Flat Fee vs Percentage) ส่งผลกระทบต่อต้นทุนของโรงแรมมากกว่ากัน?
- พฤติกรรมการเข้าพักในวันธรรมดา (Mon-Fri) และวันหยุด (Sat-Sun) ส่งผลต่อยอดจองและกำไรของแต่ละช่องทางอย่างไร?
- อัตราการยกเลิก (Cancellation Rate) ของแต่ละช่องทางส่งผลให้เกิดค่าเสียโอกาส (Opportunity Cost) มากน้อยเพียงใด?
- นโยบายราคา (Rate Code) ประเภทใดที่เป็นต้นเหตุหลักของการกั๊กห้องพักและการยกเลิก?

## Hypothesis

### 1. Hypothesis 1: ช่องทาง Direct Web ให้รายได้สุทธิต่อการจอง (True Net ADR) สูงกว่า OTA แม้จะต้องแบกรับต้นทุนค่าโฆษณา (Marketing Spend) เองก็ตาม
* **What to explore:** ต้องการเปรียบเทียบว่าช่องทางการขายช่องทางใดสร้างรายได้สุทธิต่อการจองได้สูงกว่าหลังจากหักค่า commission และ marketing เพื่อประเมินประสิทธิภาพเชิงกำไรของแต่ละช่องทาง
* **Why this chart is appropriate:** ใช้ Bar Chart เนื่องจากเหมาะสำหรับการเปรียบเทียบค่าระหว่างกลุ่มอย่างชัดเจน ทำให้เห็นความแตกต่างของ Net ADR ระหว่างแต่ละ channel ได้ทันที และช่วยให้ตีความได้ง่ายจากความสูงของแท่งกราฟ
<img width="715" height="492" alt="image" src="https://github.com/user-attachments/assets/616822b7-4b44-4be8-9131-1af63c1d3582" />

### 2. Hypothesis 2: โมเดลค่าคอมมิชชันแบบ Flat Fee มีสัดส่วนต้นทุนต่อรายได้ (Cost %) ที่คุ้มค่ากว่าแบบ Percentage
* **What to explore:** วิเคราะห์ว่า Model ค่าคอมมิชชั่นแบบ Flat Fee และ Percentage มีสัดส่วนต้นทุนต่อรายได้ แตกต่างกันอย่างไร เพื่อเข้าใจว่า Model ใดมี impact ต่อรายได้มากกว่า
* **Why this chart is appropriate:** ใช้ Bar chart เพื่อเปรียบเทียบสัดส่วนระหว่าง Model ทำให้เห็นชัดว่า Model ใดมีต้นทุนสูงกว่ากันเมื่อเทียบกับรายได้รวม
<img width="784" height="483" alt="image" src="https://github.com/user-attachments/assets/2ef06c78-66c8-4537-adf6-3fe4eb149956" />

### 3. Hypothesis 3: พฤติกรรมการเข้าพักในวันธรรมดาและวันหยุด มีผลต่อการเลือกช่องทางการจองและความสามารถในการทำกำไร (Net ADR) ที่แตกต่างกันอย่างมีนัยสำคัญ
* **What to explore:** ต้องการวิเคราะห์พฤติกรรมการเข้าพักระหว่าง "วันธรรมดา" และ "วันหยุด" ว่ามีความแตกต่างกันอย่างไร ทั้งในปริมาณการจองผ่านแต่ละช่องทาง และความสามารถในการทำกำไรต่อห้อง เพื่อใช้เป็นแนวทางในแบ่งกลุ่มลูกค้า
* **Why this chart is appropriate:** ใช้ Bar Chart 2 กราฟควบคู่กัน โดยกราฟแรกแสดงปริมาณการจอง (Volume) และกราฟที่สองแสดงความสามารถในการทำกำไรสุทธิ (Net ADR) ทำให้สามารถวิเคราะห์ได้ทั้งเชิงปริมาณและมูลค่าพร้อมกันอย่างครบถ้วน
<img width="1783" height="584" alt="Hypothesis 3 Weekend vs Weekday Performance" src="https://github.com/user-attachments/assets/b4877af3-557c-4610-8fe0-07c7c2abcb68" />

---

## Data Dictionary (โครงสร้างแบบ Galaxy Schema / Fact Constellation)

ชุดข้อมูลถูกออกแบบในลักษณะ **Galaxy Schema** เนื่องจากมี Fact Table 2 ตาราง (ยอดจอง และ ค่าโฆษณา) ที่ใช้งาน Dimension Table ร่วมกัน ประกอบไปด้วย:

### Table 1: `fact_bookings` (ตารางบันทึกการจอง)
| Attribute | Description | Data Type | Valid Range/Example |
| :--- | :--- | :--- | :--- |
| `booking_id` (PK) | รหัสการจองห้องพักแต่ละรายการ | Nominal | BK_00001, BK_00050 |
| `booking_date` | วันที่ทำการจอง | Interval (Date) | 2022-12-06, 2023-04-22 |
| `check_in_date` | วันที่ลูกค้าเข้าพักจริง | Interval (Date) | 2023-01-10, 2023-05-11 |
| `channel_id` (FK) | รหัสช่องทางการจัดจำหน่าย | Nominal | CH_01, CH_03 |
| `Channel Name` | ชื่อช่องทาง (Denormalized) | Nominal | Booking.com, Walk-in |
| `rate_code_id` (FK)| รหัสประเภทราคา/โปรโมชัน | Nominal | RT_RACK, RT_PROMO |
| `gross_room_revenue`| รายได้รวมก่อนหักค่าใช้จ่าย (บาท) | Ratio (Continuous) | 2500, 8000 |
| `Commission Rate` | อัตราค่าคอมมิชชันที่หัก (%) | Ratio (Continuous) | 0.15, 0.18, 0 |
| `commission_amount` | จำนวนเงินค่าคอมมิชชัน (บาท) | Ratio (Continuous) | 450, 1440, 0 |
| `net_room_revenue` | รายได้สุทธิ (บาท) | Ratio (Continuous) | 2050, 6560 |
| `status` | สถานะการจอง | Nominal | Checked-Out, Cancelled, Confirmed |

### Table 2: `dim_channels` (ตารางข้อมูลช่องทางการจัดจำหน่าย)
| Attribute | Description | Data Type | Valid Range/Example |
| :--- | :--- | :--- | :--- |
| `channel_id` (PK) | รหัสอ้างอิงช่องทาง | Nominal | CH_01, CH_02 |
| `channel_name` | ชื่อแพลตฟอร์มการจอง | Nominal | Booking.com, Direct Web |
| `channel_type` | ประเภทของช่องทาง | Nominal | OTA, Direct, Wholesale |
| `commission_model` | รูปแบบการคิดค่าธรรมเนียม | Nominal | Percentage, Flat Fee, Merchant |
| `default_commission_rate`| อัตราค่าธรรมเนียมมาตรฐาน | Ratio (Continuous) | 0.15, 500, 0 |
| `contract_owner` | พนักงานขายที่รับผิดชอบสัญญา | Nominal | Alice, Bob, Charlie |

### Table 3: `dim_rate_codes` (ตารางข้อมูลแพ็กเกจราคา)
| Attribute | Description | Data Type | Valid Range/Example |
| :--- | :--- | :--- | :--- |
| `rate_code_id` (PK) | รหัสประเภทแพ็กเกจราคา | Nominal | RT_PROMO, RT_CORP |
| `rate_name` | ชื่อแพ็กเกจราคา | Nominal | Promotional, Corporate |
| `is_commissionable` | เงื่อนไขว่าแพ็กเกจนี้คิดคอมมิชชันหรือไม่ | Nominal (Boolean) | True / False |

### Table 4: `fact_marketing_spend` (ตารางข้อมูลค่าใช้จ่ายการตลาด)
| Attribute | Description | Data Type | Valid Range/Example |
| :--- | :--- | :--- | :--- |
| `spend_id` (PK) | รหัสรายการลงโฆษณา | Nominal | SP_001, SP_002 |
| `spend_date` | วันที่บันทึกค่าใช้จ่าย | Interval (Date) | 2023-01-01, 2023-02-01 |
| `channel_id` (FK) | รหัสช่องทาง (มักเชื่อมกับ Direct) | Nominal | CH_03 |
| `platform` | แพลตฟอร์มที่ลงโฆษณา | Nominal | Google Ads, Facebook |
| `cost_amount` | ค่าใช้จ่ายทางการตลาด (บาท) | Ratio (Continuous) | 6428, 13135 |
| `clicks` | จำนวนคลิกที่ได้รับจากโฆษณา | Ratio (Continuous) | 1752, 556 |

---

## Data Preparation & Cleansing 
- **Data Integration:** เชื่อมต่อข้อมูล (Merge) ตาราง `fact_bookings` กับ `dim_channels` และ `dim_rate_codes` แบบ Star Schema / Galaxy Schema
- **Remove Financial Noise:** ตั้งค่า `calculated_net_revenue` ของบุ๊กกิ้งที่มีสถานะ **Cancelled ให้เป็น 0** เพื่อป้องกันตัวเลขรายได้พองโตเกินจริง (Overstated Revenue)
- **Opportunity Cost Calculation:** สร้างคอลัมน์เก็บมูลค่าความเสียหายจากห้องที่ถูกยกเลิก เพื่อวัดขนาดของ Revenue Leakage
- **Feature Engineering:**
  - สกัดข้อมูลวันที่ (Datetime) เพื่อสร้างตัวแปร `is_weekend`
  - แบ่งประเภทวันเข้าพักเป็น **Weekday (Mon-Fri)** และ **Weekend (Sat-Sun)**
- **True Net Profit Logic:** กระจายต้นทุนค่าการตลาด (Marketing Spend) เข้าไปในทุกบุ๊กกิ้งของ Direct Web เพื่อหา **True Net ADR** ที่หักต้นทุนแฝงครบทุกมิติ

---

## Exploratory Data Analysis (EDA) 

**1. True Net ADR Comparison (Direct vs OTA)**
* **เป้าหมาย:** เปรียบเทียบรายได้สุทธิต่อการจองหลังจากหักต้นทุนแฝงทั้งหมด (ค่าคอมมิชชัน + ค่าโฆษณา)
* **การนำเสนอ:** เลือกใช้ Stacked Bar Chart เพราะสามารถแสดงรายได้รวมและค่า commission ไปพร้อมกัน ทำให้เปรียบเทียบรายได้ของแต่ละช่องทางได้ทันที 
<img width="984" height="584" alt="image" src="https://github.com/user-attachments/assets/bdeca9c0-22cf-4791-a77e-cdfe7dc7e3ab" />

**2. Final Net Profit by Channel**
* **เป้าหมาย:** วิเคราะห์หา "ผู้ชนะ" ในเชิงกำไรสุทธิรวม (Contribution Margin) หลังจากหักต้นทุนผันแปรทั้งหมด
* **การนำเสนอ:** Sorted Bar Chart (เรียงลำดับจากมากไปน้อย)
<img width="984" height="584" alt="image" src="https://github.com/user-attachments/assets/f753ac54-d8cc-4a00-9bd0-563f573eb8e0" />

**3. High Cancellation Channels (Cancellation Impact)**
* **เป้าหมาย:** ระบุช่องทางที่มีความเสี่ยงสูง (High-Risk) จากอัตราการยกเลิก (Cancellation Rate) และมูลค่าที่สูญเสียไป
* **การนำเสนอ:** Side-by-side Bar Chart (กราฟคู่ % ความเสี่ยง และ มูลค่าความเสียหาย)
<img width="984" height="584" alt="image" src="https://github.com/user-attachments/assets/cf2b36fb-ab05-4b65-88dd-4391b9875d8a" />

**4. Booking Volume and Quality by Channel**
* **เป้าหมาย:** ตรวจสอบ "คุณภาพของการจอง" โดยเปรียบเทียบสัดส่วนการเข้าพักสำเร็จ (Checked-Out) เทียบกับการจองที่ถูกยกเลิก (Cancelled)
* **การนำเสนอ:** Grouped Bar Chart
<img width="1184" height="684" alt="image" src="https://github.com/user-attachments/assets/91dcf2d1-5458-47bd-832c-0377ba32b768" />

---

## Findings and Insights 

จากการวิเคราะห์ข้อมูล เราพบประเด็นสำคัญที่ส่งผลกระทบต่อกำไรสุทธิของโรงแรม Azure Stay ดังนี้:

**1. The Profit Gap (ยอดขายรวม vs กำไรที่แท้จริง)**
แม้ช่องทาง Direct Web จะดูเหมือนมีต้นทุนคอมมิชชันเป็น 0% แต่งบการตลาดที่สูงลิ่วทำให้กำไรสุทธิ (Net Profit) หดตัวอย่างรุนแรง ในขณะเดียวกัน ฝั่ง OTA ยักษ์ใหญ่ที่สร้างยอดจองมหาศาล ก็ดึงผลกำไรออกไปในรูปแบบของค่าคอมมิชชันที่สูงถึง 15-20%
<img width="1184" height="683" alt="image" src="https://github.com/user-attachments/assets/e361fb52-3545-449c-b615-1f110330c37e" />

**2. The Promotional Cancellation Trap (หลุมพรางราคาโปรโมชัน)**
พบความผิดปกติพฤติกรรมลูกค้ากลุ่มที่ใช้ Rate Code แบบ **"Promotional"** ซึ่งดึงดูดกลุ่ม Serial Cancellers (จองกั๊กแล้วยกเลิก) ทำให้มี Cancellation Rate สูงทะลุ **24.5%** ซึ่งสูงกว่าราคาประเภทอื่นๆ อย่างชัดเจน สร้างค่าเสียโอกาส (Opportunity Cost) มหาศาล
<img width="976" height="583" alt="image" src="https://github.com/user-attachments/assets/2b6fb6ef-cf31-4e0a-ae22-6bb6eb1014f5" />

**3. Booking Quality & Direct Value (คุณภาพที่ซ่อนอยู่ในการจองตรงและ B2B)**
เมื่อเปรียบเทียบคุณภาพการจอง พบว่าลูกค้าที่จองผ่าน **Direct Web** มีอัตราการยกเลิกต่ำที่สุดเพียง **6.5%** รวมถึงกลุ่ม **Corporate Rate และ Wholesale (B2B)** ที่มียอดการยกเลิกต่ำและมีความเสถียรของการเข้าพัก (โดยเฉพาะในวันธรรมดา) ทำให้มั่นใจได้ว่าเป็นกลุ่มลูกค้าที่มี High-Intent อย่างแท้จริง
<img width="1181" height="683" alt="image" src="https://github.com/user-attachments/assets/ac994764-ec5a-4e7f-a1ec-69961ac706f0" />

---

## Actionable Recommendations

เพื่อแก้ไขปัญหาและเพิ่มประสิทธิภาพตาม SMART Objectives กลุ่มเรามีข้อเสนอแนะเชิงกลยุทธ์ดังนี้:

**1. ตรวจสอบและรีดประสิทธิภาพงบการตลาด (Audit Direct Marketing ROI)**
* **Action:** ชะลอการอัดฉีดงบยิง Ads ชั่วคราว และหันไปตรวจสอบ Conversion Rate ของหน้าเว็บไซต์ ปรับปรุง UI/UX ให้ง่ายต่อการจอง
* **Impact:** หยุดการละลายทรัพย์ไปกับค่าโฆษณาที่ปิดการขายไม่ได้ และลดต้นทุนการหาลูกค้า (CAC)

**2. ล้างบางปัญหา "กั๊กห้อง" ด้วยนโยบายการเงินที่รัดกุม**
* **Action:** ปรับเงื่อนไข Rate Code แบบ "Promotional" ใหม่ทั้งหมดให้เป็น **"Non-refundable" (จองแล้วไม่คืนเงิน)** หรือบังคับเก็บมัดจำล่วงหน้า (Pre-payment) ทันที
* **Impact:** คัดกรองเฉพาะลูกค้าที่ตั้งใจเข้าพักจริง ลดปัญหาห้องว่างกะทันหัน และทำให้ฝ่ายบริหารคาดการณ์รายได้ (Revenue Forecast) ได้แม่นยำ 100%

**3. แปลงฐานลูกค้า OTA สู่การจองตรง (OTA to Direct Conversion)**
* **Action:** เลิกจ่ายแพงเพื่อหาลูกค้าใหม่ แต่ใช้แคมเปญ **"Book Direct & Get More"** เสนอ Value-Add (เช่น Early Check-in, ฟรีอาหารเช้า) ให้ลูกค้า OTA ทันทีที่มาถึงหน้าฟร้อนท์ เพื่อให้พวกเขาสมัครสมาชิกและจองตรงในครั้งถัดไป
* **Impact:** ตัดวงจรการเสียค่าคอมมิชชันและค่าแอดซ้ำซ้อนในลูกค้าคนเดิม เพิ่ม Net RevPAR ได้อย่างยั่งยืน
