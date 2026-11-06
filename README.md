# ระบบลงทะเบียนและประเมินความเสี่ยงสุขภาพเบื้องต้น
## Patient Health Risk Assessment and Registration System

เว็บแอปพลิเคชันเพื่อคัดกรองผู้ป่วยเบื้องต้นก่อนเข้ารับการรักษา โดยรับข้อมูลส่วนบุคคล คำนวณค่าดัชนีมวลกาย (BMI) ประเมินความเสี่ยงตามเงื่อนไขที่กำหนด และออกใบสรุปผลการคัดกรอง

---

### คุณสมบัติของระบบ (Features)
1. **การตรวจสอบความถูกต้องของข้อมูล (Input Validation)**:
   - ตรวจสอบชื่อ-นามสกุล, อายุ (1-120 ปี), น้ำหนัก (10-300 กก.), ส่วนสูง (40-250 ซม.)
   - แจ้งเตือนข้อผิดพลาดด้วย `Alert` สีแดง และปฏิเสธการคำนวณหากข้อมูลไม่ถูกต้อง
2. **การคำนวณและประเมินระดับความเสี่ยง (Risk Assessment Logic)**:
   - คำนวณ BMI = น้ำหนัก (kg) / [ส่วนสูง (m)]²
   - ประเมินผลร่วมกับพฤติกรรมเสี่ยง (การสูบบุหรี่, การดื่มแอลกอฮอล์) และกลุ่มโรคประจำตัว
   - จำแนกออกเป็น 3 ระดับ:
     - 🟢 **ความเสี่ยงต่ำ (Low Risk)**: สุขภาพปกติ สมส่วน ไม่มีโรคเรื้อรัง ไม่สูบบุหรี่
     - 🟠 **ความเสี่ยงปานกลาง (Moderate Risk)**: น้ำหนักเกิน, สูบบุหรี่ หรือมีโรคเรื้อรังทั่วไป
     - 🔴 **ความเสี่ยงสูง (High Risk)**: ค่า BMI ≥ 30 หรือมีโรคเรื้อรังรุนแรง (โรคหัวใจ, โรคไต) หรือมีหลายปัจจัยเสี่ยงร่วม
3. **การแสดงผลลัพธ์ (Result Display & Summary)**:
   - แสดงหน้าต่างสรุปผล `Dialog` แสดงข้อมูลผู้ป่วย ค่า BMI ระดับความเสี่ยงด้วย `Chip`
   - แนะนำการปฏิบัติตนเฉพาะบุคคล
   - มีปุ่มพิมพ์ใบสรุปผลการคัดกรอง (Print Report)
4. **ส่วนประกอบ MUI Components ที่ใช้ครบถ้วนตามข้อกำหนด**:
   - **Structure & Layout**: `Container`, `Paper`, `Grid`, `Stack`
   - **Inputs**: `TextField`, `RadioGroup` / `Radio`, `Select` / `MenuItem`, `Button`
   - **Feedback & Displays**: `Alert`, `Dialog` / `DialogTitle` / `DialogContent` / `DialogActions`, `Chip`

---

### วิธีนำขึ้น GitHub Pages (Deployment Steps)

1. **สร้าง Repository ใหม่บน GitHub**:
   - ไปที่ https://github.com/new
   - ตั้งชื่อคลัง เช่น `health-risk-assessment`
   - เลือกเป็น **Public** แล้วกด **Create repository**

2. **เชื่อมต่อและ Push โค้ดขึ้น GitHub**:
   เปิด Terminal หรือ PowerShell ในโฟลเดอร์นี้ แล้วพิมพ์คำสั่ง:
   ```bash
   git add .
   git commit -m "Initial commit: Patient Health Risk Assessment System"
   git remote add origin https://github.com/<YOUR_USERNAME>/health-risk-assessment.git
   git push -u origin main
   ```

3. **เปิดใช้งาน GitHub Pages**:
   - ไปที่หน้า Repository ของคุณบน GitHub
   - คลิกแท็บ **Settings** > เมนูด้านซ้ายเลือก **Pages**
   - ในหัวข้อ **Build and deployment**:
     - **Source**: เลือก `Deploy from a branch`
     - **Branch**: เลือก `main` และโฟลเดอร์ `/ (root)`
     - กดปุ่ม **Save**
   - รอประมาณ 1-2 นาที คุณจะได้ลิงก์เว็บไซต์ เช่น:
     `https://<YOUR_USERNAME>.github.io/health-risk-assessment/`
