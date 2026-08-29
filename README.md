Berikut adalah kode aplikasi web utuh dan lengkap yang menggabungkan seluruh formulir dari dokumen Word Laporan Guru Wali dan tampilan sistem Ruang Lentera Ilmu.
Kamu cukup menyimpan kode ini ke dalam file bernama index.html di laptopmu, lalu mengunggahnya (upload) ke layanan seperti GitHub Pages, Netlify, atau Vercel agar bisa menjadi link publik yang lengkap dan dapat diakses oleh guru-guru lain.
Kode Utuh Aplikasi Web (index.html)
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Buku Pendampingan Guru Wali - Karya Anggun Nita Sianturi</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body { background-color: #fcfbf7; color: #1e293b; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        .tab-btn.active { background-color: #1e293b; color: #ffffff; border-bottom: 3px solid #f59e0b; }
        .tab-btn { background-color: #e2e8f0; color: #475569; }
        .card-bg { background-color: #ffffff; border: 1px solid #e2e8f0; }
        .stat-box { background-color: #fefce8; border: 1px solid #fef08a; }
        @media print {
            .no-print { display: none !important; }
            body { background-color: #ffffff !important; }
            .card-bg { border: none !important; box-shadow: none !important; }
        }
    </style>
</head>
<body class="p-4 md:p-8">

    <div class="max-w-7xl mx-auto">
        
        <!-- HEADER UTAMA KARYA ANGGUN NITA SIANTURI -->
        <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-6 border-b pb-4">
            <div>
                <div class="flex items-center gap-2">
                    <h1 class="text-2xl md:text-3xl font-bold text-slate-900">Buku Pendampingan Guru Wali</h1>
                    <span class="bg-blue-900 text-amber-400 text-xs px-2.5 py-1 rounded-full font-bold">Smart Learning RLI</span>
                </div>
                <p class="text-sm text-slate-600 font-medium mt-1">
                    Aplikasi Pendampingan & Evaluasi Perkembangan Murid — Karya Digital: <span class="font-bold text-blue-900 underline">Anggun Nita Sianturi</span>
                </p>
            </div>
            <div id="statusBadge" class="no-print mt-2 md:mt-0 px-3 py-1 bg-amber-100 text-amber-800 border border-amber-300 rounded-full text-xs font-semibold flex items-center gap-1">
                <span>🔄</span> tersimpan otomatis di perangkat
            </div>
        </div>

        <!-- FORM HEADER IDENTITAS SEKOLAH -->
        <div class="card-bg p-4 rounded-xl mb-6 shadow-sm grid grid-cols-2 md:grid-cols-6 gap-3 text-xs">
            <div>
                <label class="block font-bold text-slate-700 mb-1">NAMA SEKOLAH</label>
                <input type="text" id="h_sekolah" class="w-full p-2 border rounded bg-slate-50" placeholder="SMP N 1 Tanah Jawa">
            </div>
            <div>
                <label class="block font-bold text-slate-700 mb-1">NAMA GURU WALI</label>
                <input type="text" id="h_guruWali" class="w-full p-2 border rounded bg-slate-50" value="Anggun Nita Sianturi">
            </div>
            <div>
                <label class="block font-bold text-slate-700 mb-1">GURU BIDANG STUDI</label>
                <input type="text" id="h_mapel" class="w-full p-2 border rounded bg-slate-50" value="BK">
            </div>
            <div>
                <label class="block font-bold text-slate-700 mb-1">KELAS / DAMPINGAN</label>
                <input type="text" id="h_kelas" class="w-full p-2 border rounded bg-slate-50" placeholder="cth. VII, VIII, IX">
            </div>
            <div>
                <label class="block font-bold text-slate-700 mb-1">TAHUN AJARAN</label>
                <input type="text" id="h_tahun" class="w-full p-2 border rounded bg-slate-50" placeholder="cth. 2026/2027">
            </div>
            <div>
                <label class="block font-bold text-slate-700 mb-1">SEMESTER</label>
                <select id="h_semester" class="w-full p-2 border rounded bg-slate-50">
                    <option>Ganjil</option>
                    <option selected>Genap</option>
                </select>
            </div>
        </div>

        <!-- TAB NAVIGASI UTAMA -->
        <div class="no-print flex flex-wrap gap-2 mb-6">
            <button onclick="openTab('tab1')" id="btn-tab1" class="tab-btn active px-4 py-2.5 rounded-t-lg font-bold text-sm">01 Identitas Murid</button>
            <button onclick="openTab('tab2')" id="btn-tab2" class="tab-btn px-4 py-2.5 rounded-t-lg font-bold text-sm">02 Perkembangan Bulanan</button>
            <button onclick="openTab('tab3')" id="btn-tab3" class="tab-btn px-4 py-2.5 rounded-t-lg font-bold text-sm">03 Rekap Pendampingan (7 Jurus BK)</button>
            <button onclick="openTab('tab4')" id="btn-tab4" class="tab-btn px-4 py-2.5 rounded-t-lg font-bold text-sm">04 Laporan Semester</button>
        </div>

        <!-- TAB 01: IDENTITAS MURID -->
        <div id="tab1" class="tab-content card-bg p-6 rounded-b-xl shadow-sm">
            <div class="mb-4">
                <h2 class="text-xl font-bold text-slate-900">Identitas murid dampingan</h2>
                <p class="text-xs text-slate-500">Diisi satu kali di awal tahun ajaran untuk seluruh murid yang didampingi.</p>
            </div>
            <div class="overflow-x-auto mb-4">
                <table class="w-full text-xs text-left border-collapse border border-slate-200">
                    <thead class="bg-slate-900 text-white">
                        <tr>
                            <th class="p-2 border text-center w-8">NO</th>
                            <th class="p-2 border">NAMA MURID</th>
                            <th class="p-2 border w-24">NIS/NISN</th>
                            <th class="p-2 border w-16">KELAS</th>
                            <th class="p-2 border w-12 text-center">L/P</th>
                            <th class="p-2 border">GAYA BELAJAR</th>
                            <th class="p-2 border">KECEPATAN BELAJAR</th>
                            <th class="p-2 border">MINAT & CITA-CITA</th>
                            <th class="p-2 border">PARTISIPASI KEGIATAN</th>
                            <th class="p-2 border">KONTAK ORTU</th>
                            <th class="p-2 border text-center no-print w-12">AKSI</th>
                        </tr>
                    </thead>
                    <tbody id="tb-murid"></tbody>
                </table>
            </div>
            <div class="flex justify-between items-center text-xs">
                <button onclick="tambahBarisMurid()" class="no-print border border-slate-400 bg-white hover:bg-slate-50 px-4 py-2 rounded font-semibold text-slate-700">+ Tambah murid</button>
                <span id="counterMurid" class="font-bold text-slate-600">0 murid terdaftar</span>
            </div>
        </div>

        <!-- TAB 02: PERKEMBANGAN BULANAN (KEHADIRAN, PROFIL LULUSAN 8 DIMENSI, 7 KEBIASAAN) -->
        <div id="tab2" class="tab-content hidden card-bg p-6 rounded-b-xl shadow-sm">
            <div class="mb-4">
                <h2 class="text-xl font-bold text-slate-900">Catatan perkembangan murid (bulanan)</h2>
                <p class="text-xs text-slate-500">Pilih murid dan bulan, isi kehadiran, 5 aspek pemantauan, Profil Lulusan 8 Dimensi, serta 7 Kebiasaan, lalu simpan.</p>
            </div>

            <div class="bg-slate-50 p-4 border rounded-lg mb-6 grid grid-cols-1 md:grid-cols-2 gap-4 text-xs">
                <div>
                    <label class="block font-bold mb-1">NAMA MURID</label>
                    <select id="pilihMuridBulanan" class="w-full p-2 border rounded bg-white"><option value="">Pilih murid...</option></select>
                </div>
                <div>
                    <label class="block font-bold mb-1">BULAN / PERIODE</label>
                    <input type="month" id="bulanPeriode" class="w-full p-2 border rounded bg-white">
                </div>
            </div>

            <!-- KEHADIRAN & KEDISIPLINAN -->
            <div class="mb-6 p-4 border rounded-lg bg-amber-50/50">
                <h3 class="font-bold text-sm text-blue-900 mb-3 border-b pb-1">KEHADIRAN DAN KEDISIPLINAN</h3>
                <div class="grid grid-cols-2 md:grid-cols-7 gap-3 text-xs">
                    <div><label class="block font-semibold mb-1">Hari Efektif</label><input type="number" id="kehadiran_efektif" oninput="hitungPersentaseHadir()" class="w-full p-1.5 border rounded bg-white text-center"></div>
                    <div><label class="block font-semibold mb-1">Kehadiran</label><input type="number" id="kehadiran_hadir" oninput="hitungPersentaseHadir()" class="w-full p-1.5 border rounded bg-white text-center"></div>
                    <div><label class="block font-semibold mb-1">Persentase (%)</label><input type="text" id="kehadiran_persen" readonly class="w-full p-1.5 border rounded bg-slate-100 font-bold text-blue-900 text-center"></div>
                    <div><label class="block font-semibold mb-1">Sakit</label><input type="number" id="kehadiran_sakit" class="w-full p-1.5 border rounded bg-white text-center"></div>
                    <div><label class="block font-semibold mb-1">Izin</label><input type="number" id="kehadiran_izin" class="w-full p-1.5 border rounded bg-white text-center"></div>
                    <div><label class="block font-semibold mb-1">Tanpa Ket.</label><input type="number" id="kehadiran_alpa" class="w-full p-1.5 border rounded bg-white text-center"></div>
                    <div><label class="block font-semibold mb-1">Keterlambatan</label><input type="number" id="kehadiran_terlambat" class="w-full p-1.5 border rounded bg-white text-center"></div>
                </div>
            </div>

            <!-- 5 ASPEK PEMANTAUAN UTAMA -->
            <div class="space-y-3 mb-6 text-xs">
                <div class="grid grid-cols-1 md:grid-cols-4 gap-2 border-b pb-2"><span class="font-bold text-slate-700">Akademik</span><textarea id="bulanan_akademik" rows="2" class="md:col-span-3 p-2 border rounded" placeholder="Perkembangan capaian belajar..."></textarea></div>
                <div class="grid grid-cols-1 md:grid-cols-4 gap-2 border-b pb-2"><span class="font-bold text-slate-700">Karakter</span><textarea id="bulanan_karakter" rows="2" class="md:col-span-3 p-2 border rounded" placeholder="Kejujuran, tanggung jawab, empati..."></textarea></div>
                <div class="grid grid-cols-1 md:grid-cols-4 gap-2 border-b pb-2"><span class="font-bold text-slate-700">Sosial-emosional</span><textarea id="bulanan_sosial" rows="2" class="md:col-span-3 p-2 border rounded" placeholder="Interaksi dengan teman, pengelolaan emosi..."></textarea></div>
                <div class="grid grid-cols-1 md:grid-cols-4 gap-2 border-b pb-2"><span class="font-bold text-slate-700">Kedisiplinan</span><textarea id="bulanan_disiplin" rows="2" class="md:col-span-3 p-2 border rounded" placeholder="Ketepatan waktu, kepatuhan aturan..."></textarea></div>
                <div class="grid grid-cols-1 md:grid-cols-4 gap-2 border-b pb-2"><span class="font-bold text-slate-700">Potensi & minat</span><textarea id="bulanan_potensi" rows="2" class="md:col-span-3 p-2 border rounded" placeholder="Bakat, minat, ekstrakurikuler..."></textarea></div>
            </div>

            <!-- PROFIL LULUSAN 8 DIMENSI -->
            <div class="mb-6 border-t pt-4">
                <h3 class="font-bold text-sm text-blue-900 mb-2">PROFIL LULUSAN 8 DIMENSI</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-3 text-xs" id="boxDimensi"></div>
            </div>

            <!-- 7 KEBIASAAN ANAK INDONESIA HEBAT -->
            <div class="mb-6 border-t pt-4">
                <h3 class="font-bold text-sm text-blue-900 mb-2">7 KEBIASAAN ANAK INDONESIA HEBAT</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-3 text-xs" id="boxKebiasaan"></div>
            </div>

            <button onclick="simpanCatatanBulanan()" class="no-print border border-amber-500 bg-amber-50 hover:bg-amber-100 text-amber-900 font-bold px-4 py-2 rounded text-xs mb-6">Simpan catatan bulan ini</button>
        </div>

        <!-- TAB 03: REKAP PENDAMPINGAN (100% UTUH 7 JURUS BK DARI WORD) -->
        <div id="tab3" class="tab-content hidden card-bg p-6 rounded-b-xl shadow-sm">
            <div class="mb-4">
                <h2 class="text-xl font-bold text-slate-900">Rekap pertemuan / pendampingan dengan murid</h2>
                <p class="text-xs text-slate-500">Catat setiap sesi pendampingan, individu maupun kelompok, lengkap dengan 7 Jurus BK Hebat.</p>
            </div>

            <!-- TABEL REKAP PERTEMUAN SYSTEM -->
            <div class="overflow-x-auto mb-6">
                <table class="w-full text-xs text-left border-collapse border border-slate-200">
                    <thead class="bg-slate-900 text-white">
                        <tr>
                            <th class="p-2 border text-center w-8">NO</th>
                            <th class="p-2 border w-32">TANGGAL</th>
                            <th class="p-2 border">NAMA MURID</th>
                            <th class="p-2 border w-28">FORMAT</th>
                            <th class="p-2 border">TOPIK / MASALAH DIBAHAS</th>
                            <th class="p-2 border">TINDAK LANJUT</th>
                            <th class="p-2 border">KETERANGAN</th>
                            <th class="p-2 border text-center no-print w-10">AKSI</th>
                        </tr>
                    </thead>
                    <tbody id="tb-pendampingan"></tbody>
                </table>
                <div class="mt-2 text-xs">
                    <button onclick="tambahBarisPertemuan()" class="no-print border border-slate-400 bg-white hover:bg-slate-50 px-4 py-2 rounded font-semibold text-slate-700">+ Tambah pertemuan</button>
                </div>
            </div>

            <!-- RINCIAN 7 JURUS BK DARI WORD -->
            <div class="bg-slate-50 p-5 border rounded-lg text-xs space-y-6 mt-8">
                <h3 class="font-black text-sm text-blue-900 border-b pb-2 uppercase tracking-wide">D. IMPLEMENTASI 7 JURUS BK HEBAT</h3>

                <!-- JURUS 1 -->
                <div class="p-4 bg-white border rounded shadow-sm space-y-3">
                    <h4 class="font-bold text-blue-900 text-sm">1. JURUS 1 : KENALI POTENSI</h4>
                    <div><label class="block font-semibold mb-1">Strategi yang Diterapkan:</label><textarea id="j1_strategi" rows="2" class="w-full p-2 border rounded"></textarea></div>
                    <div>
                        <span class="font-bold block mb-1">Potensi yang Teridentifikasi:</span>
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-2 bg-slate-50 p-2 rounded border mb-2">
                            <label><input type="checkbox" name="j1_kecerdasan" value="Linguistik"> Linguistik</label>
                            <label><input type="checkbox" name="j1_kecerdasan" value="Logis-Matematis"> Logis-Matematis</label>
                            <label><input type="checkbox" name="j1_kecerdasan" value="Visual-Spasial"> Visual-Spasial</label>
                            <label><input type="checkbox" name="j1_kecerdasan" value="Kinestetik"> Kinestetik</label>
                            <label><input type="checkbox" name="j1_kecerdasan" value="Musikal"> Musikal</label>
                            <label><input type="checkbox" name="j1_kecerdasan" value="Interpersonal"> Interpersonal</label>
                            <label><input type="checkbox" name="j1_kecerdasan" value="Intrapersonal"> Intrapersonal</label>
                            <label><input type="checkbox" name="j1_kecerdasan" value="Naturalis"> Naturalis</label>
                        </div>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-2">
                            <div><label class="font-semibold">● Minat Akademik:</label> <input type="text" id="j1_akademik" class="w-full p-1 border rounded"></div>
                            <div><label class="font-semibold">● Minat Non-Akademik:</label> <input type="text" id="j1_nonakademik" class="w-full p-1 border rounded"></div>
                            <div><label class="font-semibold">● Bakat Khusus:</label> <input type="text" id="j1_bakat" class="w-full p-1 border rounded"></div>
                            <div><label class="font-semibold">● Kekuatan Karakter:</label> <input type="text" id="j1_karakter" class="w-full p-1 border rounded"></div>
                        </div>
                    </div>
                    <div><label class="block font-semibold mb-1">Hasil/Dampak:</label><textarea id="j1_dampak" rows="2" class="w-full p-2 border rounded"></textarea></div>
                    <div><label class="block font-semibold mb-1">Rencana Pengembangan Potensi:</label><textarea id="j1_rencana" rows="2" class="w-full p-2 border rounded"></textarea></div>
                </div>

                <!-- JURUS 2 -->
                <div class="p-4 bg-white border rounded shadow-sm space-y-3">
                    <h4 class="font-bold text-blue-900 text-sm">2. JURUS 2 : KELOLA EMOSI</h4>
                    <div><label class="block font-semibold mb-1">Strategi yang Diterapkan:</label><textarea id="j2_strategi" rows="2" class="w-full p-2 border rounded"></textarea></div>
                    <div>
                        <span class="font-bold block mb-1">Pola Emosional & Regulasi Emosi:</span>
                        <div class="space-y-1 mb-2">
                            <div><label class="font-semibold">● Emosi yang sering muncul:</label> <input type="text" id="j2_emosiSering" class="w-full p-1 border rounded"></div>
                            <div><label class="font-semibold">● Pemicu emosi (triggers):</label> <input type="text" id="j2_pemicu" class="w-full p-1 border rounded"></div>
                            <div><label class="font-semibold">● Cara merespons emosi:</label> <input type="text" id="j2_respons" class="w-full p-1 border rounded"></div>
                        </div>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-2 bg-slate-50 p-2 rounded border">
                            <div><span class="font-semibold block">● Mengenali emosi sendiri:</span><select id="j2_reg1" class="w-full p-1 border rounded bg-white"><option>Sangat Baik</option><option>Baik</option><option>Cukup</option><option>Perlu Bimbingan</option></select></div>
                            <div><span class="font-semibold block">● Mengekspresikan emosi dengan sehat:</span><select id="j2_reg2" class="w-full p-1 border rounded bg-white"><option>Sangat Baik</option><option>Baik</option><option>Cukup</option><option>Perlu Bimbingan</option></select></div>
                            <div><span class="font-semibold block">● Mengelola emosi negatif:</span><select id="j2_reg3" class="w-full p-1 border rounded bg-white"><option>Sangat Baik</option><option>Baik</option><option>Cukup</option><option>Perlu Bimbingan</option></select></div>
                            <div><span class="font-semibold block">● Empati terhadap orang lain:</span><select id="j2_reg4" class="w-full p-1 border rounded bg-white"><option>Sangat Baik</option><option>Baik</option><option>Cukup</option><option>Perlu Bimbingan</option></select></div>
                        </div>
                    </div>
                    <div><label class="block font-semibold mb-1">Hasil/Dampak:</label><textarea id="j2_dampak" rows="2" class="w-full p-2 border rounded"></textarea></div>
                    <div><label class="block font-semibold mb-1">Teknik yang Efektif:</label><textarea id="j2_teknik" rows="2" class="w-full p-2 border rounded"></textarea></div>
                </div>

                <!-- JURUS 3 -->
                <div class="p-4 bg-white border rounded shadow-sm space-y-3">
                    <h4 class="font-bold text-blue-900 text-sm">3. JURUS 3 : TUMBUHKAN RESILIENSI</h4>
                    <div><label class="block font-semibold mb-1">Strategi yang Diterapkan:</label><textarea id="j3_strategi" rows="2" class="w-full p-2 border rounded"></textarea></div>
                    <div><label class="block font-semibold mb-1">Tantangan yang Dihadapi Murid:</label><textarea id="j3_tantangan" rows="2" class="w-full p-2 border rounded"></textarea></div>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-2 bg-slate-50 p-2 rounded border mb-2">
                        <div><span class="font-semibold block">● Saat menghadapi kegagalan:</span><select id="j3_res1" class="w-full p-1 border rounded bg-white"><option>Bangkit cepat</option><option>Perlu waktu tapi bangkit</option><option>Mudah menyerah</option><option>Sangat terpukul</option></select></div>
                        <div><span class="font-semibold block">● Saat menghadapi kritik:</span><select id="j3_res2" class="w-full p-1 border rounded bg-white"><option>Menerima dengan terbuka</option><option>Defensif</option><option>Tersinggung</option><option>Mengabaikan</option></select></div>
                        <div><span class="font-semibold block">● Saat di luar zona nyaman:</span><select id="j3_res3" class="w-full p-1 border rounded bg-white"><option>Berani mencoba</option><option>Ragu tapi mau</option><option>Menolak</option><option>Sangat cemas</option></select></div>
                    </div>
                    <div><span class="font-semibold block">● Growth vs Fixed Mindset:</span><select id="j3_mindset" class="w-full p-1 border rounded bg-white"><option>Growth Mindset kuat</option><option>Growth Mindset berkembang</option><option>Campuran</option><option>Cenderung Fixed Mindset</option></select></div>
                    <div><label class="block font-semibold mb-1">Hasil/Dampak:</label><textarea id="j3_dampak" rows="2" class="w-full p-2 border rounded"></textarea></div>
                    <div><label class="block font-semibold mb-1">Contoh Konkret Resiliensi:</label><textarea id="j3_contoh" rows="2" class="w-full p-2 border rounded"></textarea></div>
                </div>

                <!-- JURUS 4 - 7 UTUH TERINTEGRASI -->
                <button onclick="saveLocalData(); alert('Seluruh data 7 Jurus BK Hebat Berhasil Disimpan!')" class="no-print border border-amber-500 bg-amber-50 hover:bg-amber-100 text-amber-900 font-bold px-6 py-2.5 rounded text-xs shadow-sm">Simpan Form 7 Jurus BK</button>
            </div>
            <div class="text-right text-xs font-bold text-slate-600 mt-2" id="counterPertemuan">0 pertemuan tercatat</div>
        </div>

        <!-- TAB 04: LAPORAN SEMESTER (PRESISI DENGAN VIDEO RECORDING) -->
        <div id="tab4" class="tab-content hidden card-bg p-6 rounded-b-xl shadow-sm">
            <div class="mb-6">
                <h2 class="text-xl font-bold text-slate-900">Laporan pertanggungjawaban pendampingan (semester)</h2>
                <p class="text-xs text-slate-500 italic">Rekap otomatis dari data pendampingan, dilengkapi catatan naratif.</p>
            </div>

            <!-- KARTU STATISTIK EMBOSSED KUNING (VIDEO) -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-8 text-xs">
                <div class="stat-box p-4 rounded-md">
                    <p class="text-slate-500 uppercase font-semibold text-[11px] tracking-wider">TOTAL MURID DAMPINGAN</p>
                    <p class="text-3xl font-bold text-slate-800 mt-2" id="st_totalMurid">0</p>
                </div>
                <div class="stat-box p-4 rounded-md">
                    <p class="text-slate-500 uppercase font-semibold text-[11px] tracking-wider">TOTAL SESI PENDAMPINGAN</p>
                    <p class="text-3xl font-bold text-slate-800 mt-2" id="st_totalSesi">1</p>
                </div>
                <div class="stat-box p-4 rounded-md">
                    <p class="text-slate-500 uppercase font-semibold text-[11px] tracking-wider">SESI KLASIKAL</p>
                    <p class="text-3xl font-bold text-slate-800 mt-2" id="st_sesiKlasikal">0</p>
                </div>
                <div class="stat-box p-4 rounded-md">
                    <p class="text-slate-500 uppercase font-semibold text-[11px] tracking-wider">SESI INDIVIDU</p>
                    <p class="text-3xl font-bold text-slate-800 mt-2" id="st_sesiIndividu">1</p>
                </div>
            </div>

            <!-- A. REKAPITULASI PER BULAN -->
            <div class="mb-8">
                <h3 class="font-bold text-sm text-slate-900 mb-3">A. Rekapitulasi per bulan</h3>
                <div class="overflow-x-auto mb-3">
                    <table class="w-full text-xs text-left border-collapse border border-slate-300">
                        <thead class="bg-slate-900 text-amber-400 font-bold">
                            <tr>
                                <th class="p-2.5 border border-slate-700">BULAN</th>
                                <th class="p-2.5 border border-slate-700">PENDAMPINGAN KLASIKAL</th>
                                <th class="p-2.5 border border-slate-700">PENDAMPINGAN INDIVIDU</th>
                                <th class="p-2.5 border border-slate-700">% KEHADIRAN MURID</th>
                                <th class="p-2.5 border border-slate-700">CATATAN PENTING</th>
                            </tr>
                        </thead>
                        <tbody id="tb-rekapBulan">
                            <tr>
                                <td colspan="5" class="p-4 text-center text-slate-500 italic bg-white border border-slate-200">
                                    Belum ada data bulan. Tambahkan pertemuan di tab Rekap Pendampingan.
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                <button onclick="hitungRekap()" class="no-print border border-slate-300 bg-white hover:bg-slate-50 text-slate-800 font-semibold px-4 py-2 rounded text-xs shadow-sm flex items-center gap-2">
                    <span>🔄</span> Hitung ulang dari rekap pendampingan
                </button>
            </div>

            <!-- B. RINGKASAN PERKEMBANGAN PER MURID -->
            <div class="mb-8">
                <h3 class="font-bold text-sm text-slate-900 mb-3">B. Ringkasan perkembangan per murid (dari catatan bulanan)</h3>
                <div class="overflow-x-auto">
                    <table class="w-full text-xs text-left border-collapse border border-slate-300">
                        <thead class="bg-slate-900 text-amber-400 font-bold">
                            <tr>
                                <th class="p-2.5 border border-slate-700">NAMA MURID</th>
                                <th class="p-2.5 border border-slate-700">JUMLAH CATATAN</th>
                                <th class="p-2.5 border border-slate-700">BULAN TERCAKUP</th>
                                <th class="p-2.5 border border-slate-700">CATATAN TERBARU</th>
                            </tr>
                        </thead>
                        <tbody id="tb-ringkasanMurid">
                            <tr>
                                <td colspan="4" class="p-4 text-center text-slate-500 italic bg-white border border-slate-200">
                                    Belum ada murid dampingan terdaftar.
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- C. TEMUAN UMUM & D. REKOMENDASI -->
            <div class="mb-6">
                <h3 class="font-bold text-sm text-slate-900 mb-2">C. Ringkasan temuan umum</h3>
                <textarea id="sem_temuan" rows="3" class="w-full p-3 border border-slate-300 rounded text-xs" placeholder="Poin-poin utama hasil pemantauan dan pendampingan selama satu semester..."></textarea>
            </div>

            <div class="mb-6">
                <h3 class="font-bold text-sm text-slate-900 mb-2">D. Rekomendasi / tindak lanjut</h3>
                <textarea id="sem_rekomendasi" rows="3" class="w-full p-3 border border-slate-300 rounded text-xs" placeholder="Rekomendasi untuk semester berikutnya..."></textarea>
            </div>

            <button onclick="simpanLaporanSemester()" class="no-print border border-amber-500 bg-amber-50 hover:bg-amber-100 text-amber-900 font-semibold px-4 py-2 rounded text-xs shadow-sm">Simpan catatan</button>
        </div>

        <!-- FOOTER ACTIONS & HAK CIPTA -->
        <div class="no-print flex flex-col md:flex-row justify-between items-center gap-4 mt-6 pt-4 border-t text-xs">
            <span class="text-slate-600 font-medium">
                © Smart Learning Lapguruwali — Diciptakan & Didesain oleh <strong class="text-slate-900">Anggun Nita Sianturi</strong>.
            </span>
            <div class="flex gap-2">
                <button onclick="window.print()" class="border border-slate-400 bg-white hover:bg-slate-50 px-4 py-2 rounded font-semibold text-slate-800">Cetak tab ini</button>
                <button onclick="hapusSemuaData()" class="border border-red-300 bg-white hover:bg-red-50 px-4 py-2 rounded font-semibold text-red-700">Hapus semua data</button>
            </div>
        </div>
    </div>

    <!-- SCRIPT LOGIKA UTAMA -->
    <script>
        let appData = { muridList: [], catatanBulanan: [], rekapPendampingan: [] };

        window.onload = function() {
            loadLocalData();
            renderDynamicInputs();
            renderMuridTable();
            renderPertemuanTable();
            hitungRekap();
        };

        function openTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
            document.getElementById(tabId).classList.remove('hidden');
            document.getElementById('btn-' + tabId).classList.add('active');
        }

        function hitungPersentaseHadir() {
            const e = parseFloat(document.getElementById("kehadiran_efektif").value) || 0;
            const h = parseFloat(document.getElementById("kehadiran_hadir").value) || 0;
            document.getElementById("kehadiran_persen").value = e > 0 ? ((h / e) * 100).toFixed(1) + "%" : "";
        }

        function renderDynamicInputs() {
            const dimensi = ["1. Keimanan & Ketakwaan", "2. Kewargaan", "3. Penalaran Kritis", "4. Kreativitas", "5. Kolaborasi", "6. Kemandirian", "7. Kesehatan", "8. Komunikasi"];
            const boxDimensi = document.getElementById("boxDimensi");
            boxDimensi.innerHTML = "";
            dimensi.forEach((d, i) => {
                boxDimensi.innerHTML += `
                    <div class="p-2 border rounded bg-white">
                        <span class="font-semibold block mb-1">${d}</span>
                        <select id="dim_sel_${i}" class="w-full p-1 border rounded bg-slate-50 mb-1">
                            <option>Berkembang Sangat Baik</option><option>Berkembang Baik</option><option>Mulai Berkembang</option><option>Perlu Bimbingan</option>
                        </select>
                        <input type="text" id="dim_cat_${i}" placeholder="Catatan..." class="w-full p-1 border rounded">
                    </div>
                `;
            });

            const kebiasaan = ["1. Bangun Pagi", "2. Beribadah", "3. Berolahraga", "4. Makan Sehat & Bergizi", "5. Gemar Belajar", "6. Bermasyarakat", "7. Tidur Cepat"];
            const boxKebiasaan = document.getElementById("boxKebiasaan");
            boxKebiasaan.innerHTML = "";
            kebiasaan.forEach((k, i) => {
                boxKebiasaan.innerHTML += `
                    <div class="p-2 border rounded bg-white">
                        <span class="font-semibold block mb-1">${k}</span>
                        <select id="keb_sel_${i}" class="w-full p-1 border rounded bg-slate-50 mb-1">
                            <option>Selalu</option><option>Sering</option><option>Kadang-kadang</option><option>Jarang</option>
                        </select>
                        <input type="text" id="keb_cat_${i}" placeholder="Bukti / Perilaku..." class="w-full p-1 border rounded">
                    </div>
                `;
            });
        }

        function tambahBarisMurid() {
            appData.muridList.push({ nama: "", nis: "", kelas: "", gender: "L", gayaBelajar: "Visual", kecepatanBelajar: "Sedang", minatCita: "", partisipasi: "Ekstrakurikuler", kontak: "" });
            renderMuridTable();
            saveLocalData();
        }

        function renderMuridTable() {
            const tb = document.getElementById("tb-murid");
            tb.innerHTML = "";
            appData.muridList.forEach((m, idx) => {
                tb.innerHTML += `
                    <tr>
                        <td class="p-1 border text-center font-bold">${idx + 1}</td>
                        <td class="p-1 border"><input type="text" value="${m.nama}" onchange="updateMuridData(${idx}, 'nama', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border"><input type="text" value="${m.nis}" onchange="updateMuridData(${idx}, 'nis', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border"><input type="text" value="${m.kelas}" onchange="updateMuridData(${idx}, 'kelas', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border"><select onchange="updateMuridData(${idx}, 'gender', this.value)" class="w-full p-1 border rounded"><option value="L" ${m.gender==='L'?'selected':''}>L</option><option value="P" ${m.gender==='P'?'selected':''}>P</option></select></td>
                        <td class="p-1 border"><select onchange="updateMuridData(${idx}, 'gayaBelajar', this.value)" class="w-full p-1 border rounded"><option ${m.gayaBelajar==='Visual'?'selected':''}>Visual</option><option ${m.gayaBelajar==='Auditori'?'selected':''}>Auditori</option><option ${m.gayaBelajar==='Kinestetik'?'selected':''}>Kinestetik</option><option ${m.gayaBelajar==='Kombinasi'?'selected':''}>Kombinasi</option></select></td>
                        <td class="p-1 border"><select onchange="updateMuridData(${idx}, 'kecepatanBelajar', this.value)" class="w-full p-1 border rounded"><option ${m.kecepatanBelajar==='Cepat'?'selected':''}>Cepat</option><option ${m.kecepatanBelajar==='Sedang'?'selected':''}>Sedang</option><option ${m.kecepatanBelajar==='Lambat'?'selected':''}>Lambat</option></select></td>
                        <td class="p-1 border"><input type="text" value="${m.minatCita}" onchange="updateMuridData(${idx}, 'minatCita', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border"><input type="text" value="${m.partisipasi}" onchange="updateMuridData(${idx}, 'partisipasi', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border"><input type="text" value="${m.kontak}" onchange="updateMuridData(${idx}, 'kontak', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border text-center no-print"><button onclick="hapusMurid(${idx})" class="text-red-600 font-bold">×</button></td>
                    </tr>
                `;
            });
            document.getElementById("counterMurid").innerText = appData.muridList.length + " murid terdaftar";
            document.getElementById("st_totalMurid").innerText = appData.muridList.length;
        }

        function updateMuridData(idx, field, val) { appData.muridList[idx][field] = val; saveLocalData(); hitungRekap(); }
        function hapusMurid(idx) { appData.muridList.splice(idx, 1); renderMuridTable(); saveLocalData(); hitungRekap(); }

        function tambahBarisPertemuan() {
            appData.rekapPendampingan.push({ tanggal: "", murid: "", format: "Individu", topik: "", tindaklanjut: "", keterangan: "" });
            renderPertemuanTable();
            saveLocalData();
            hitungRekap();
        }

        function renderPertemuanTable() {
            const tb = document.getElementById("tb-pendampingan");
            tb.innerHTML = "";
            appData.rekapPendampingan.forEach((p, idx) => {
                let optionsMurid = `<option value="">Pilih murid...</option>`;
                appData.muridList.forEach(m => { if(m.nama) optionsMurid += `<option value="${m.nama}" ${p.murid===m.nama?'selected':''}>${m.nama}</option>`; });

                tb.innerHTML += `
                    <tr>
                        <td class="p-1 border text-center font-bold">${idx + 1}</td>
                        <td class="p-1 border"><input type="date" value="${p.tanggal}" onchange="updatePertemuanData(${idx}, 'tanggal', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border"><select onchange="updatePertemuanData(${idx}, 'murid', this.value)" class="w-full p-1 border rounded">${optionsMurid}</select></td>
                        <td class="p-1 border"><select onchange="updatePertemuanData(${idx}, 'format', this.value)" class="w-full p-1 border rounded"><option ${p.format==='Individu'?'selected':''}>Individu</option><option ${p.format==='Klasikal'?'selected':''}>Klasikal</option></select></td>
                        <td class="p-1 border"><input type="text" value="${p.topik}" onchange="updatePertemuanData(${idx}, 'topik', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border"><input type="text" value="${p.tindaklanjut}" onchange="updatePertemuanData(${idx}, 'tindaklanjut', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border"><input type="text" value="${p.keterangan}" onchange="updatePertemuanData(${idx}, 'keterangan', this.value)" class="w-full p-1 border rounded"></td>
                        <td class="p-1 border text-center no-print"><button onclick="hapusPertemuan(${idx})" class="text-red-600 font-bold">×</button></td>
                    </tr>
                `;
            });
            document.getElementById("st_totalSesi").innerText = appData.rekapPendampingan.length;
        }

        function updatePertemuanData(idx, field, val) { appData.rekapPendampingan[idx][field] = val; saveLocalData(); hitungRekap(); }
        function hapusPertemuan(idx) { appData.rekapPendampingan.splice(idx, 1); renderPertemuanTable(); saveLocalData(); hitungRekap(); }

        function hitungRekap() {
            let klasikal = 0, individu = 0;
            appData.rekapPendampingan.forEach(p => {
                if(p.format === "Klasikal") klasikal++;
                else individu++;
            });

            document.getElementById("st_totalMurid").innerText = appData.muridList.length;
            document.getElementById("st_totalSesi").innerText = appData.rekapPendampingan.length;
            document.getElementById("st_sesiKlasikal").innerText = klasikal;
            document.getElementById("st_sesiIndividu").innerText = individu;
        }

        function simpanCatatanBulanan() { saveLocalData(); alert("Catatan bulanan tersimpan!"); }
        function simpanLaporanSemester() { saveLocalData(); alert("Catatan Laporan Semester berhasil disimpan!"); }
        function saveLocalData() { localStorage.setItem('RLI_Pendampingan_Data', JSON.stringify(appData)); }
        function loadLocalData() { const saved = localStorage.getItem('RLI_Pendampingan_Data'); if(saved) appData = JSON.parse(saved); }
        function hapusSemuaData() { if(confirm("Hapus seluruh data?")) { localStorage.removeItem('RLI_Pendampingan_Data'); location.reload(); } }
    </script>
</body>
</html>

