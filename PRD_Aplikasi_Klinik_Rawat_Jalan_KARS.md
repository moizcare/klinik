# PRD APLIKASI MANAJEMEN KLINIK RAWAT JALAN
## Standar Akreditasi KARS Rumah Sakit

**Version:** 1.0  
**Tanggal:** Oktober 2026  
**Status:** For Stakeholder Review & Approval

---

## 1. EXECUTIVE SUMMARY

### 1.1 Deskripsi Singkat
Aplikasi Manajemen Klinik Rawat Jalan adalah sistem terintegrasi yang dirancang untuk mengelola seluruh proses pelayanan kesehatan rawat jalan di klinik/rumah sakit, mulai dari pendaftaran pasien hingga pelaporan keuangan dan rekam medis. Sistem ini dikembangkan sesuai dengan standar akreditasi KARS (Komisi Akreditasi Rumah Sakit) dan best practice dari sistem Khanza.

### 1.2 Tujuan Produk
- Meningkatkan efisiensi operasional klinik
- Memenuhi standar akreditasi KARS untuk dokumentasi dan rekam medis
- Meningkatkan kualitas pelayanan pasien
- Mengintegrasikan semua departemen (pendaftaran, poli, apotek, kasir)
- Menghasilkan laporan keuangan dan rekam medis yang akurat dan tepat waktu
- Mengurangi kesalahan administratif dan medis

---

## 2. TARGET USERS & STAKEHOLDERS

### 2.1 Pengguna Sistem
1. **Admin/Operator Pendaftaran** - Mengelola registrasi dan data pasien
2. **Dokter/Tenaga Medis** - Melakukan pemeriksaan dan input rekam medis
3. **Perawat** - Vital signs, supporting medical staff
4. **Apoteker** - Mengelola obat dan resep
5. **Staff Kasir** - Mengelola pembayaran
6. **Manager Klinik** - Monitoring operasional dan laporan
7. **Admin Keuangan** - Laporan keuangan dan akuntansi
8. **Pasien** - Antrian, riwayat, pembayaran online (fase 2)

---

## 3. SCOPE FASE 1 (RAWAT JALAN)

### 3.1 Modul Utama Fase 1
1. ✅ **Modul Pendaftaran & Data Pasien**
2. ✅ **Modul Rawat Jalan (Poli)**
3. ✅ **Modul Farmasi/Apotek**
4. ✅ **Modul Kasir/Pembayaran**
5. ✅ **Modul Rekam Medis Elektronik (RME)**
6. ✅ **Modul Laporan & Analytics**

### 3.2 Yang TIDAK Termasuk Fase 1
- ❌ Rawat inap
- ❌ IGD (Instalasi Gawat Darurat)
- ❌ Operasi/Kamar operasi
- ❌ Laboratorium (basic integration only)
- ❌ Radiologi (basic integration only)
- ❌ Sistem appointment online (fase 2)
- ❌ Mobile app patient (fase 2)

---

## 4. FITUR DETAIL SETIAP MODUL

### 4.1 MODUL PENDAFTARAN & DATA PASIEN

#### 4.1.1 Master Data Pasien

**Fungsionalitas:**
- Input data pasien baru (NIK, nama, alamat, kontak, pekerjaan, pendidikan)
- Verifikasi NIK real-time (integrasi BPJS optional)
- Kelola data pasien lama (update, edit, archive)
- Foto/biometrik pasien (optional)
- History pemeriksaan pasien
- Status pasien (aktif, non-aktif, pindah)

**Field Minimum yang Wajib:**
```
- NIK/No. Identitas (wajib)
- Nama lengkap
- Jenis kelamin
- Tanggal lahir (auto-calculate umur)
- Alamat (jalan, RT/RW, kelurahan, kecamatan, kabupaten, provinsi)
- No. Telepon & Email
- Pekerjaan
- Pendidikan terakhir
- Status perkawinan
- Agama
- Asuransi (BPJS/Umum/Swasta)
- No. Asuransi
- Rujukan dari
- Emergency contact
```

#### 4.1.2 Triage & Prioritas Pasien

**Fungsionalitas:**
- Input tekanan darah, suhu, nadi, respirasi saat pendaftaran
- Sistem prioritas (urgent/masuk poli langsung)
- Catatan alergi & riwayat penyakit utama
- Informed consent digital

#### 4.1.3 Daftar Antrian Harian

**Fungsionalitas:**
- Antrian per poli dengan no. urut otomatis
- Estimasi waktu tunggu
- Display antrian real-time di waiting area (monitor)
- Call pasien ke poli
- Skip/defer antrian dengan reason
- Statistik antrian harian
- Average waiting time tracking

---

### 4.2 MODUL RAWAT JALAN (POLI)

#### 4.2.1 Input Rekam Medis Elektronik (RME)

**Fungsionalitas:**
- Keluhan utama (chief complaint)
- Riwayat penyakit sekarang (HPI - History of Present Illness)
- Riwayat penyakit dahulu (Past Medical History)
- Riwayat penyakit keluarga
- Riwayat alergi obat & makanan
- Riwayat pengobatan sebelumnya
- Status vitals (BP, HR, RR, Temp, O2sat, Weight, Height)
- Pemeriksaan fisik (sistem organ per sistem)
- Diagnosis (multi-diagnosis, ICD-10 compatible)
- Assessment & Plan

**KARS Compliance Requirements:**
- ✅ Wajib ada tanda tangan digital/e-signature dokter
- ✅ Timestamp otomatis setiap entry
- ✅ Tidak boleh ada perubahan data tanpa audit trail
- ✅ Data locked setelah dokter sign-off
- ✅ Retention policy 5 tahun minimum
- ✅ Encryption data sensitive

#### 4.2.2 Template Spesialisasi
- Template untuk setiap poli (umum, gigi, THT, mata, orthopedi, dsb)
- Template customizable per klinik
- Mandatory fields per poli

#### 4.2.3 Resep Digital
- Generate resep dari diagnosis & treatment plan
- Template resep per dokter
- Kalimat standar obat (copy from library)
- Validasi interaksi obat (drug interaction checker)
- Resep print/digital ke apotek
- Signature dokter digital

#### 4.2.4 Referral/Rujukan
- Generate surat rujukan ke poli lain atau RS lain
- Rujukan balik (reverse referral)
- Tracking rujukan status
- Terintegrasi ke poli tujuan

#### 4.2.5 Follow-up Appointment
- Schedule follow-up otomatis dari dokter
- Reminder ke pasien (SMS/Email fase 2)
- Kalender booking poli

---

### 4.3 MODUL FARMASI/APOTEK

#### 4.3.1 Master Data Obat

**Fungsionalitas:**
- Katalog obat lengkap (nama generik, brand, dosis, satuan)
- Harga obat (HNA, markup, jual ke pasien)
- Stok obat real-time
- Expired date tracking
- Batch number tracking
- Supplier management
- Klasifikasi obat (OTC, resep, antibiotik, narkotika, psikotropika)

**KARS Compliance:**
- ✅ Master obat sesuai HNA (Harga Nasional Acuan)
- ✅ Obat terlarang/terbatas ada izin distribusi
- ✅ Narkotika & psikotropika ada dokumentasi khusus

#### 4.3.2 Penerimaan Stok Obat (PO)
- PO ke supplier
- Receiving goods dengan QC check
- Input batch & expiry date
- Update stok otomatis
- Retur obat
- Adjusment stok (kadaluarsa, rusak)

#### 4.3.3 Peracikan & Dispensing Resep
- List resep menunggu dari poli
- Validasi stok ketersediaan obat
- Peracikan obat (jika obat kombinasi)
- Labeling resep
- Pengecekan ulang (double-check) apoteker
- Rekam siapa yang meracik dan memeriksa
- Print label & packaging
- Status resep (pending, racik, serah, done)

#### 4.3.4 Edukasi Obat
- Leaflet obat otomatis print
- Informasi pemakaian & efek samping
- Interaksi obat warning

#### 4.3.5 Stock Opname
- Fisik count vs sistem
- Report varian stok
- Adjustment pencatat
- Schedule rutin opname

#### 4.3.6 Laporan Farmasi
- Laporan pemakaian obat harian
- Stok opname report
- Laporan obat expired
- Reorder point suggestion

---

### 4.4 MODUL KASIR/PEMBAYARAN

#### 4.4.1 Invoice/Tagihan

**Fungsionalitas:**
- Auto-generate invoice dari konsultasi dokter + resep + tindakan
- Itemisasi: administrasi, konsultasi, resep, tindakan, lab, etc
- Tarif flexible (BPJS, umum, corporate)
- Multi-currency (IDR minimum)
- Diskon/promos
- Tax calculation (PPN jika ada)

#### 4.4.2 Metode Pembayaran
- ✅ Cash (tunai)
- ✅ Debit/Credit card (POS integration)
- ✅ Transfer bank
- ✅ E-wallet (OVO, GoPay, DANA - future)
- ✅ BPJS (billing ke BPJS)
- ✅ Asuransi korporat
- ✅ Cicilan
- ✅ Hutang (untuk pasien tertentu)

#### 4.4.3 Kasir Register
- List invoice pelunasan hari ini
- Input pembayaran & hitung kembalian otomatis
- Receipt print (thermal printer)
- Signature/digital signature pasien
- Opening & closing shift kasir
- Kas report per shift
- Discrepancy reconciliation

#### 4.4.4 Refund/Retur
- Refund partial/full dengan reason
- Approval workflow
- Refund back ke payment method original
- Refund ledger

#### 4.4.5 Piutang/Hutang Pasien
- Track piutang pasien
- Reminder pembayaran
- Aging report
- Write-off approval
- Cicilan tracking

#### 4.4.6 Banking Integration
- Rekonsiliasi bank otomatis
- Settlement report
- Payment reconciliation

#### 4.4.7 Laporan Kasir
- Daily cash report
- Revenue by poli/service
- Revenue by payment method
- Aging piutang
- Top patients by value

---

### 4.5 MODUL REKAM MEDIS ELEKTRONIK (RME)

#### 4.5.1 View Rekam Medis Pasien
- Timeline riwayat kunjungan pasien
- Filter by date, poli, dokter
- Summary medical history
- Allergies highlighted
- Problem list (daftar diagnosa aktif)
- Medication list current
- Lab results (jika ada)

#### 4.5.2 Rekam Medis dalam Format SOAP
- Subjective
- Objective (vitals & physical exam)
- Assessment (diagnosa ICD-10)
- Plan (treatment & medication)
- Wajib tanda tangan dokter

#### 4.5.3 Integritas & Security Data RME
**KARS Requirement:**
- ✅ Enkripsi data pasien
- ✅ Audit trail semua akses RME
- ✅ Read-only RME yang sudah ditandatangani
- ✅ Backup rutin minimum 3 hari
- ✅ Disaster recovery plan
- ✅ Data retention 5 tahun minimum
- ✅ Ekspor RME hanya dengan izin pasien/dokter

#### 4.5.4 Export RME
- Export to PDF (ringkasan)
- Export to XML (full data, untuk referral)
- Letter/Surat serah RME

#### 4.5.5 Analisis Rekam Medis
- Top 10 diagnosa di klinik
- Trend penyakit per periode
- Medication usage statistics
- Readmission rate analysis

---

### 4.6 MODUL LAPORAN & ANALYTICS

#### 4.6.1 Dashboard Operasional Real-time

**Key Metrics:**
- Jumlah pasien registrasi hari ini
- Pasien menunggu di waiting area
- Revenue hari ini
- Outstanding piutang
- Stok obat status (low stock alert)
- Antrian per poli
- Average waiting time

#### 4.6.2 Laporan Klinik Harian
- Laporan kunjungan pasien per poli
- Laporan diagnosa (top 10 per poli)
- Laporan obat paling sering diresepkan
- Laporan revenue harian
- Patient demographics snapshot

#### 4.6.3 Laporan Keuangan (Sesuai Standar Akuntansi)

**A. Laporan Penjualan/Revenue**
- Daily revenue report
- Monthly revenue summary
- Revenue by service type
- Revenue by payment method
- Revenue by poli/departemen
- Trend revenue YoY

**B. Laporan Piutang**
- Outstanding invoice list
- Aging analysis (current, 30, 60, 90+ days)
- Bad debt reserve estimation
- Collection summary

**C. Laporan Obat/Farmasi**
- COGS (Cost of Goods Sold) obat
- Margin/profit per obat
- Slow-moving items
- Expired obat losses
- Stok value report

**D. Laporan Operasional**
- Cost per patient visit
- Avg revenue per patient
- Staff productivity
- Patient satisfaction (if available)
- Average length of stay per poli

**E. Laporan Komprehensif/Konsolidasi**
- Income Statement (P&L - sesuai SAK ETAP)
- Balance Sheet (simplified)
- Cash flow report
- Budget vs actual

#### 4.6.4 Export Laporan
- Export to Excel
- Export to PDF
- Scheduled email reports
- Custom report builder

#### 4.6.5 Compliance Reporting
- KARS reporting requirements
- Pemerintah/Dinas Kesehatan reporting
- Asuransi reporting (BPJS, corporate)

---

## 5. WORKFLOW PROSES BISNIS

### 5.1 Alur Pasien Baru
```
Pasien datang → Pendaftaran (input data) → Triage/vitals → Antri → 
Konsultasi dokter → Resep → Ke apotek → Pembayaran → Pulang
```

### 5.2 Alur Pasien Lama
```
Pasien datang → Cek data → Triage/vitals → Antri → 
Konsultasi dokter (dengan riwayat) → Resep → Ke apotek → Pembayaran → Pulang
```

### 5.3 Alur Data Keuangan
```
Invoice generated → Presented to patient → Payment received → 
Receipt printed → Cash reconcile → Daily report → Monthly accounting → 
Financial statements
```

### 5.4 Alur Farmasi
```
Resep dari poli → Validasi stok → Peracikan → Check ulang → 
Labeling → Serah ke pasien → Stok update → Laporan
```

---

## 6. STANDAR AKREDITASI KARS COMPLIANCE

### 6.1 Dokumentasi Rekam Medis
✅ Lengkap (no blank)
✅ Jelas & terbaca (digital)
✅ Akurat (sesuai kondisi pasien)
✅ Tepat waktu (input real-time)
✅ Tanda tangan dokter (digital allowed)
✅ Aman dari perubahan (locked after sign)
✅ Privacy & kerahasiaan terjaga (encryption)
✅ Accessible untuk clinical use

### 6.2 Patient Safety
✅ Identifikasi pasien unik (NIK/no. rekam medis)
✅ Allergy alert system
✅ Drug interaction checker
✅ Dose verification
✅ Time-out procedure

### 6.3 Informed Consent
✅ Digital consent capture
✅ Documented dalam RME
✅ Revocable by patient

### 6.4 Data Privacy & Security (PP 71/2019)
✅ Encryption in transit & at rest
✅ Access control (role-based)
✅ Audit logging
✅ Regular backup & disaster recovery
✅ Data retention policy (min 5 tahun)

### 6.5 Komunikasi & Kolaborasi
✅ Referral system terintegrasi
✅ Consultation notes terintegrasi
✅ Data sharing dengan persetujuan

---

## 7. PERSYARATAN TEKNIS

### 7.1 Platform & Teknologi
- **Backend**: CodeIgniter 3 atau 4
- **Database**: MySQL 5.7+ atau MariaDB 10.3+
- **Frontend**: Bootstrap/responsive design
- **Server OS**: Linux (Ubuntu/CentOS) atau Windows Server
- **Browser**: Chrome, Firefox, Safari, Edge (terbaru)
- **Mobile**: Responsive web (future: native app)

### 7.2 Performance
- Page load time: < 2 detik
- Database query: < 1 detik
- Support: 100-500 concurrent users
- Response time: < 500ms
- Uptime: 99.5% (maintenance excluded)

### 7.3 Security
- **Authentication**: Username/password + 2FA (optional)
- **Authorization**: Role-based access control (RBAC)
- **Encryption**: SSL/TLS, AES-256 untuk sensitive data
- **Audit**: Log semua perubahan data + user access
- **Backup**: Daily automatic backup, retain 30 hari
- **Disaster Recovery**: RTO < 4 jam, RPO < 1 jam

### 7.4 Scalability
- Modular architecture
- Database normalization
- Caching layer (Redis optional)
- Load balancing ready
- Horizontal scaling capable

### 7.5 Usability
- Intuitive UI/UX
- Minimal training required
- Keyboard shortcuts
- Multi-language support (Indonesian minimum)
- Accessibility (WCAG 2.1 AA)

### 7.6 Reliability
- Graceful error handling
- Data validation (client + server)
- Transaction integrity
- Concurrent access handling
- Version control (Git)

---

## 8. DATA MODEL (Entitas Utama)

### 8.1 Core Entities

**PATIENTS** - Data pasien
**VISITS** - Kunjungan pasien
**MEDICAL_RECORDS** - RME
**PRESCRIPTIONS** - Resep
**PRESCRIPTION_ITEMS** - Detail obat dalam resep
**MEDICATIONS** - Master obat
**INVOICES** - Tagihan
**INVOICE_ITEMS** - Detail tagihan
**PAYMENTS** - Pembayaran
**INVENTORY** - Stok obat
**USERS** - User system
**ROLES_PERMISSIONS** - RBAC
**AUDIT_LOGS** - Audit trail
**DEPARTMENTS/POLICLINICS** - Poli/departemen
**DOCTORS** - Data dokter

### 8.2 Key Relationships
- Patient 1 : M Visits
- Visit 1 : M Medical Records
- Visit 1 : M Prescriptions
- Visit 1 : M Invoices
- Prescription 1 : M Prescription Items
- Medication M : M Invoices

---

## 9. IMPLEMENTASI TIMELINE (FASE 1)

### Week 1-2: Planning & Setup
- [ ] Finalize requirements & sign-off
- [ ] Setup development environment
- [ ] Database design & schema creation
- [ ] User story breakdown

### Week 3-4: Core Infrastructure
- [ ] Authentication system
- [ ] RBAC framework
- [ ] Audit logging system
- [ ] Backup & recovery setup

### Week 5-6: Master Data & Patient Module
- [ ] Patient master data CRUD
- [ ] Patient search & filter
- [ ] Triage module
- [ ] Antrian management

### Week 7-8: Medical Records Module
- [ ] RME creation form per poli
- [ ] E-signature implementation
- [ ] RME view & search
- [ ] Amendment procedure

### Week 9-10: Prescription & Pharmacy
- [ ] Prescription creation
- [ ] Medication master data
- [ ] Inventory management
- [ ] Dispensing workflow

### Week 11-12: Billing & Cashier
- [ ] Invoice auto-generation
- [ ] Payment recording
- [ ] Receipt printing
- [ ] AR tracking

### Week 13-14: Reporting & Analytics
- [ ] Daily report templates
- [ ] Revenue reporting
- [ ] Dashboard basic
- [ ] Export to Excel

### Week 15: Testing & QA
- [ ] Functional testing
- [ ] Integration testing
- [ ] Performance testing
- [ ] Security testing
- [ ] KARS compliance checklist

### Week 16: UAT & Deployment
- [ ] User acceptance testing
- [ ] Bug fixes
- [ ] Production setup
- [ ] Go-live support

**Total: 4 months (16 weeks) untuk MVP Fase 1**

---

## 10. ACCEPTANCE CRITERIA & TESTING

### 10.1 Functional Testing
- All modules work per specification
- Data integrity maintained
- Audit trail captured
- Reports generated accurately

### 10.2 Performance Testing
- Response time < 2 sec
- Support 100+ concurrent users
- Database queries optimized

### 10.3 Security Testing
- SQLi prevention
- XSS prevention
- CSRF prevention
- Authentication/authorization working
- Audit logs captured

### 10.4 KARS Compliance Testing
- RME signature enforcement
- Data retention verified
- Backup & recovery tested
- Privacy controls verified

### 10.5 UAT Criteria
- End-users sign-off per module
- User documentation complete
- Training delivered
- Go-live readiness confirmed

---

## 11. SUPPORT & MAINTENANCE

### 11.1 SLA (Service Level Agreement)
- Critical issues: 2 hour response, 4 hour resolution
- High priority: 8 hour response, 24 hour resolution
- Medium priority: 24 hour response, 72 hour resolution
- Low priority: 72 hour response, 1 week resolution

### 11.2 Maintenance
- Monthly security patches
- Quarterly feature updates
- Annual performance optimization
- Continuous monitoring & alerting

### 11.3 Support Channels
- Email support
- Phone hotline
- Ticketing system
- Knowledge base (FAQ)

---

## 12. TRAINING & DOCUMENTATION

### 12.1 User Documentation
- User manual per role
- Quick start guide
- FAQ
- Video tutorials
- In-app help/tooltips

### 12.2 System Documentation
- Technical architecture
- Database schema
- API documentation
- Deployment guide
- Troubleshooting guide

### 12.3 Training Plan
- Administrator training (system setup)
- Clinic manager training (reporting)
- Clinical staff training (RME, patient data)
- Pharmacy training (inventory, dispensing)
- Cashier training (payment, reconciliation)
- On-going support & updates

---

## 13. BUDGET & RESOURCE ESTIMATE (FASE 1)

### 13.1 Development Team (16 weeks)
- 1 Project Manager
- 1 System Analyst
- 2 Backend Developers (CodeIgniter)
- 1 Frontend Developer
- 1 Database Admin/DevOps
- 1 QA Engineer
- 1 Documentation/Training specialist

**Total: 8 orang, ~100 person-weeks**
**Estimated Cost: Rp 260-330 juta (4 bulan)**

### 13.2 Infrastructure
- Server (cloud/on-premise): Rp 5-10 juta/month
- Database server: included
- Backup storage: Rp 1-2 juta/month
- Network & security: Rp 2-3 juta/month

### 13.3 Third-party Licenses
- Payment gateway: FREE (commission-based)
- SMS gateway (optional): Rp 2-5 juta/month
- Email service: Rp 0.5-1 juta/month
- Backup solution: Rp 1-2 juta/month

**TOTAL PROJECT BUDGET: Rp 330-510 juta (Fase 1 MVP)**

---

## 14. SUCCESS METRICS

### 14.1 Adoption Metrics
- User active daily rate: > 80%
- System uptime: > 99.5%
- Page load time: < 2 sec (avg)
- Support ticket resolution rate: > 90% in SLA

### 14.2 Clinical Metrics
- RME completion rate: 100%
- Average visit time: < 15 min
- Patient satisfaction: > 4/5
- Medication error reduction: > 50%

### 14.3 Financial Metrics
- Revenue tracking accuracy: 99%+
- AR aging reduction: < 30 days
- Admin cost savings: > 20%
- System ROI: within 12-18 months

---

## 15. RISK MANAGEMENT

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|-----------|
| Data loss/corruption | Medium | Critical | Daily backup, disaster recovery plan |
| Security breach | Low | Critical | Encryption, audit, regular security audit |
| Poor adoption | Medium | High | User training, good UX, support |
| Performance degradation | Low | High | Load testing, optimization, scaling plan |
| Integration failure | Medium | High | Early testing with integrating systems |
| Scope creep | High | Medium | Strict change control, phased rollout |

---

## 16. REFERENCE: SISTEM KHANZA

Sistem ini terinspirasi dari Khanza Hospital Management System:
- GitHub: https://github.com/mas-elkhanza/khanza-lite
- Technology: CodeIgniter, MySQL, Bootstrap
- Modular architecture
- KARS compliant
- Open-source community

**Customizations untuk klinik:**
- Simplified untuk outpatient only (fase 1)
- Enhanced reporting untuk cashflow tracking
- Better RBAC implementation
- Improved UI/UX
- Modern security practices

---

**Document Version:** 1.0
**Last Updated:** Oktober 2026
**Status:** READY FOR DEVELOPMENT
**Prepared By:** Product & Technical Team

---

**END OF DOCUMENT**
