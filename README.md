# Honey House Store

Landing page ร้านน้ำผึ้งตัวอย่าง 2 SKUs (HH-001 น้ำผึ้งดอกไม้ป่า 189 บาท, HH-002 น้ำผึ้งดอกลำไย 229 บาท) พร้อมตะกร้าสินค้า, ฟอร์มสั่งซื้อ, Google Sheets backend, หน้าหลังร้าน และพิมพ์ใบจ่าหน้าพัสดุ

## Deploy เว็บไซต์บน Vercel
1. สร้าง Google Sheet ใหม่ > Extensions > Apps Script แล้ววางโค้ดจาก `google-apps-script/Code.gs`
2. Apps Script > Project Settings > Script Properties เพิ่ม `ADMIN_TOKEN` เป็นรหัสลับที่คุณเลือก
3. Deploy > New deployment > Web app; Execute as: Me; Who has access: Anyone. คัดลอก URL /exec.
4. เปิด `app.js` ใน GitHub แล้วแทนที่ `const SCRIPT_URL=""` ด้วย URL /exec จากข้อ 3
5. GitHub repository นี้เป็น static site ใช้ Vercel Import Git Repository ได้เลย (Framework Preset: Other; Build Command: เว้นว่าง; Output Directory: .)
6. เปิดโดเมน Vercel แล้วทดสอบสั่งซื้อ และเข้า /admin.html ใส่ URL Apps Script กับ ADMIN_TOKEN เพื่อดูออเดอร์

## จัดการคำสั่งซื้อ
หน้า `admin.html` แสดงออเดอร์ที่บันทึกใน Google Sheets, เปลี่ยนสถานะหยิบ/แพ็ก/จัดส่ง และพิมพ์ใบจ่าหน้าขนาด 100 x 150 มม.

## รูปสินค้า
เก็บภาพแยกไว้ใน `images/` เปลี่ยน `wildflower.svg` และ `longan.svg` เป็นรูปสินค้าจริงได้ โดยคงชื่อไฟล์เดิม

## ข้อควรรู้
- ตัวอย่างนี้ยังไม่มีระบบรับชำระเงินออนไลน์และไม่มีการเชื่อม API บริษัทขนส่ง/Tracking number
- ใบจ่าหน้าเป็นแบบพิมพ์ข้อมูลผู้รับ ยังไม่ใช่ใบปะหน้าที่มีบาร์โค้ดขนส่งที่ใช้ส่งจริง ต้องนำข้อมูลไปสร้างใบปะหน้าจากระบบขนส่งอีกครั้ง
- อย่าเผยแพร่ ADMIN_TOKEN ในไฟล์สาธารณะ; ใส่เฉพาะในหน้า admin ตอนใช้งาน และควรจำกัดสิทธิ์/เพิ่มระบบล็อกอินก่อนใช้งานเชิงพาณิชย์
- ก่อนเปิดร้านจริง เปลี่ยน LINE และภาพตัวอย่างเป็นข้อมูลจริงของร้าน
