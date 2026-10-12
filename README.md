<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Keuangan Mahasiswa</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', 'Segoe UI', sans-serif;
        }
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');

        :root {
            --biru: #4361ee;
            --ungu: #7209b7;
            --pink: #f72585;
            --hijau: #10b981;
            --merah: #ef4444;
            --abu: #64748b;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #4361ee 0%, #7209b7 100%);
            position: relative;
            overflow-x: hidden;
            padding: 40px 20px;
        }

        /* ========== ELEMEN LATAR RINGAN ========== */
        .bg-layer {
            position: absolute;
            inset: 0;
            pointer-events: none;
        }
        .blob {
            position: absolute;
            border-radius: 50%;
            opacity: 0.15;
            will-change: transform;
        }
        .blob:nth-child(1) {
            width: 400px; height: 400px;
            background: #4cc9f0;
            top: -120px; right: -100px;
            animation: apung 12s ease-in-out infinite;
        }
        .blob:nth-child(2) {
            width: 300px; height: 300px;
            background: #f72585;
            bottom: -80px; left: -80px;
            animation: apung 15s ease-in-out infinite reverse;
        }
        .bintang {
            position: absolute;
            width: 18px; height: 18px;
            background: white;
            clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
            animation: kedip 3s ease-in-out infinite;
        }
        .bintang:nth-child(3) { top: 10%; left: 8%; }
        .bintang:nth-child(4) { top: 18%; right: 12%; animation-delay: 0.5s; }
        .bintang:nth-child(5) { top: 72%; right: 10%; animation-delay: 1.5s; }
        .lingkaran {
            position: absolute;
            border-radius: 50%;
            border: 2px solid rgba(255,255,255,0.15);
        }
        .lingkaran:nth-child(6) { width: 100px; height: 100px; top: 15%; left: 25%; animation: apung 8s ease-in-out infinite; }
        .lingkaran:nth-child(7) { width: 70px; height: 70px; top: 55%; right: 30%; animation: apung 9s ease-in-out infinite reverse; }
        .titik {
            position: absolute;
            width: 8px; height: 8px;
            background: rgba(255,255,255,0.6);
            border-radius: 50%;
            animation: naikTurun 5s ease-in-out infinite;
        }
        .titik:nth-child(8) { top: 25%; left: 40%; }
        .titik:nth-child(9) { top: 55%; left: 75%; animation-delay: 1.2s; }

        @keyframes apung {
            0%,100% { transform: translate(0,0); }
            50%     { transform: translate(15px,-20px); }
        }
        @keyframes kedip {
            0%,100% { opacity: 0.6; transform: scale(1); }
            50%     { opacity: 1; transform: scale(1.15); }
        }
        @keyframes naikTurun {
            0%,100% { transform: translateY(0); opacity: 0.5; }
            50%     { transform: translateY(-12px); opacity: 1; }
        }

        /* ========== KOTAK UMUM ========== */
        .wrapper {
            position: relative;
            z-index: 10;
            max-width: 480px;
            margin: 0 auto;
        }
        .card {
            background: rgba(255,255,255,0.96);
            border-radius: 24px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.18);
            padding: 35px 30px;
            animation: muncul 0.7s ease-out;
        }
        @keyframes muncul {
            from { opacity: 0; transform: translateY(25px); }
            to   { opacity: 1; transform: translateY(0); }
        }
        .sembunyi { display: none !important; }
        .icon {
            text-align: center;
            font-size: 50px;
            margin-bottom: 8px;
        }
        h1 {
            text-align: center;
            background: linear-gradient(135deg, var(--biru), var(--ungu));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-size: 23px;
            font-weight: 700;
            margin-bottom: 5px;
        }
        .sub {
            text-align: center;
            color: var(--abu);
            font-size: 14px;
            margin-bottom: 25px;
        }
        .input-group { margin-bottom: 18px; }
        label {
            display: flex;
            align-items: center;
            gap: 8px;
            color: #334155;
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 15px;
        }
        input {
            width: 100%;
            padding: 13px 16px;
            border: 2px solid #e2e8f0;
            border-radius: 12px;
            font-size: 16px;
            transition: 0.25s ease;
            background: #fafbfc;
        }
        input:focus {
            outline: none;
            border-color: var(--biru);
            box-shadow: 0 0 0 4px rgba(67,97,238,0.12);
            background: white;
        }
        button {
            width: 100%;
            padding: 14px;
            background: linear-gradient(135deg, var(--biru), var(--ungu));
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            transition: transform 0.25s ease;
            margin-top: 5px;
            box-shadow: 0 8px 20px rgba(67,97,238,0.3);
        }
        button:hover {
            transform: translateY(-3px);
            filter: brightness(1.05);
        }
        button:active { transform: translateY(0); }
        .btn-kedua {
            background: transparent;
            color: var(--biru);
            border: 2px solid var(--biru);
            margin-top: 12px;
            box-shadow: none;
        }
        .btn-kedua:hover {
            background: rgba(67,97,238,0.08);
            border-color: var(--ungu);
            color: var(--ungu);
        }
        .btn-keluar {
            background: linear-gradient(135deg, #6b7280, #4b5563);
            margin-top: 12px;
        }
        .pesan {
            margin-top: 15px;
            padding: 12px;
            border-radius: 10px;
            text-align: center;
            font-weight: 500;
            display: none;
            font-size: 14px;
        }
        .pesan.salah {
            display: block;
            background: #fef2f2;
            color: var(--merah);
            border: 1px solid #fecaca;
        }
        .pesan.benar {
            display: block;
            background: #f0fdf4;
            color: var(--hijau);
            border: 1px solid #bbf7d0;
        }

        /* ========== HALAMAN KALKULATOR ========== */
        .selamat-datang {
            background: #f0f4ff;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 25px;
            border-left: 4px solid var(--biru);
        }
        .selamat-datang p {
            color: #1e293b;
            font-weight: 500;
            margin: 4px 0;
        }
        .selamat-datang span {
            font-weight: 700;
            color: var(--ungu);
        }
        .hasil {
            margin-top: 25px;
            padding: 22px;
            background: linear-gradient(135deg, #f0f4ff, #faf0ff);
            border-radius: 16px;
            border-left: 4px solid var(--ungu);
            display: none;
            animation: geser 0.5s ease forwards;
        }
        .hasil.tampil { display: block; }
        @keyframes geser {
            from { opacity: 0; transform: translateY(15px); }
            to   { opacity: 1; transform: translateY(0); }
        }
        .hasil h3 {
            color: var(--ungu);
            margin-bottom: 15px;
            font-size: 17px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .baris {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px dashed #d4c9e8;
            color: #475569;
            font-size: 15px;
        }
        .total {
            margin-top: 12px;
            padding-top: 15px;
            border-top: 2px solid;
            border-image: linear-gradient(90deg, var(--biru), var(--pink)) 1;
            font-size: 23px;
            font-weight: 800;
            background: linear-gradient(135deg, var(--biru), var(--ungu));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-align: right;
        }

        @media (max-width: 480px) {
            body { padding: 20px 12px; }
            .card { padding: 25px 18px; }
        }
    </style>
</head>
<body>
    <div class="bg-layer">
        <div class="blob"></div>
        <div class="blob"></div>
        <div class="bintang"></div>
        <div class="bintang"></div>
        <div class="bintang"></div>
        <div class="lingkaran"></div>
        <div class="lingkaran"></div>
        <div class="titik"></div>
        <div class="titik"></div>
    </div>

    <!-- ============= HALAMAN DAFTAR AKUN ============= -->
    <div class="wrapper" id="halamanDaftar">
        <div class="card">
            <div class="icon">📝</div>
            <h1>Daftar Akun Baru</h1>
            <p class="sub">Buat akun untuk mengakses sistem keuangan</p>

            <div class="input-group">
                <label>👤 Nama Lengkap</label>
                <input type="text" id="d_nama" placeholder="Masukkan nama lengkap">
            </div>
            <div class="input-group">
                <label>🆔 NIM</label>
                <input type="text" id="d_nim" placeholder="Contoh: 12345678">
            </div>
            <div class="input-group">
                <label>🔒 Buat Password</label>
                <input type="password" id="d_pass" placeholder="Minimal 4 karakter">
            </div>
            <div class="input-group">
                <label>🔒 Ulangi Password</label>
                <input type="password" id="d_pass2" placeholder="Ketik ulang password di atas">
            </div>

            <button onclick="daftarAkun()">✅ Daftar Sekarang</button>
            <button class="btn-kedua" onclick="keLogin()">Sudah punya akun? Login di sini</button>

            <div class="pesan" id="pesanDaftar"></div>
        </div>
    </div>

    <!-- ============= HALAMAN LOGIN ============= -->
    <div class="wrapper sembunyi" id="halamanLogin">
        <div class="card">
            <div class="icon">🔐</div>
            <h1>Login Akun</h1>
            <p class="sub">Masukkan data yang sudah didaftarkan</p>

            <div class="input-group">
                <label>🆔 NIM</label>
                <input type="text" id="l_nim" placeholder="Masukkan NIM kamu">
            </div>
            <div class="input-group">
                <label>🔒 Password</label>
                <input type="password" id="l_pass" placeholder="Masukkan password">
            </div>

            <button onclick="masuk()">➡️ Masuk</button>
            <button class="btn-kedua" onclick="keDaftar()">Belum punya akun? Daftar dulu</button>

            <div class="pesan" id="pesanLogin"></div>
        </div>
    </div>

    <!-- ============= HALAMAN KALKULATOR ============= -->
    <div class="wrapper sembunyi" id="halamanKalkulator">
        <div class="card">
            <div class="icon">🎓</div>
            <h1>Kalkulator Biaya Kuliah</h1>
            <p class="sub">Sistem Perhitungan Keuangan Mahasiswa</p>

            <div class="selamat-datang">
                <p>👋 Selamat datang, <span id="namaUser">-</span></p>
                <p>🆔 NIM: <span id="nimUser">-</span></p>
            </div>

            <div class="input-group">
                <label>💵 Biaya per SKS (Rp)</label>
                <input type="number" id="biayaSks" placeholder="Contoh: 250000" min="0">
            </div>
            <div class="input-group">
                <label>📚 Jumlah SKS Diambil</label>
                <input type="number" id="jmlSks" placeholder="Contoh: 24" min="1">
            </div>
            <div class="input-group">
                <label>📎 Biaya Tambahan Lainnya (Rp)</label>
                <input type="number" id="biayaTambah" placeholder="Daftar ulang, asuransi, dll" min="0" value="0">
            </div>

            <button onclick="hitung()">🔢 Hitung Total Pembayaran</button>
            <button class="btn-keluar" onclick="keluar()">🚪 Keluar</button>

            <div class="hasil" id="kotakHasil">
                <h3>📋 Rincian Biaya</h3>
                <div class="baris">
                    <span>Biaya SKS</span>
                    <span id="hargaSks">-</span>
                </div>
                <div class="baris">
                    <span>Biaya Tambahan</span>
                    <span id="hargaTambah">-</span>
                </div>
                <div class="total">Total: <span id="totalBayar">-</span></div>
            </div>
        </div>
    </div>

    <script>
        // ===== PENYIMPANAN DATA =====
        // Simpan akun ke penyimpanan browser
        function simpanAkun(nama, nim, password) {
            let daftarAkun = JSON.parse(localStorage.getItem('akunMahasiswa') || '[]');
            daftarAkun.push({ nama, nim, password });
            localStorage.setItem('akunMahasiswa', JSON.stringify(daftarAkun));
        }

        // Cek apakah NIM sudah terdaftar
        function nimSudahAda(nim) {
            let daftarAkun = JSON.parse(localStorage.getItem('akunMahasiswa') || '[]');
            return daftarAkun.some(akun => akun.nim === nim);
        }

        // Cek login
        function cariAkun(nim, password) {
            let daftarAkun = JSON.parse(localStorage.getItem('akunMahasiswa') || '[]');
            return daftarAkun.find(akun => akun.nim === nim && akun.password === password);
        }

        // ===== FORMAT RUPIAH =====
        function formatRupiah(angka) {
            return new Intl.NumberFormat('id-ID', {
                style: 'currency',
                currency: 'IDR',
                minimumFractionDigits: 0
            }).format(angka);
        }

        // ===== HALAMAN DAFTAR =====
        function daftarAkun() {
            const nama = document.getElementById('d_nama').value.trim();
            const nim = document.getElementById('d_nim').value.trim();
            const pass = document.getElementById('d_pass').value.trim();
            const pass2 = document.getElementById('d_pass2').value.trim();
            const pesan = document.getElementById('pesanDaftar');

            if (!nama || !nim || !pass || !pass2) {
                pesan.className = 'pesan salah';
                pesan.textContent = '⚠️ Semua kolom harus diisi!';
                return;
            }
            if (nim.length < 4) {
                pesan.className = 'pesan salah';
                pesan.textContent = '⚠️ NIM minimal 4 karakter!';
                return;
            }
            if (pass.length < 4) {
                pesan.className = 'pesan salah';
                pesan.textContent = '⚠️ Password minimal 4 karakter!';
                return;
            }
            if (pass !== pass2) {
                pesan.className = 'pesan salah';
                pesan.textContent = '⚠️ Password tidak sama! Coba lagi.';
                return;
            }
            if (nimSudahAda(nim)) {
                pesan.className = 'pesan salah';
                pesan.textContent = '⚠️ NIM ini sudah terdaftar! Silakan login.';
                return;
            }

            // Simpan akun
            simpanAkun(nama, nim, pass);
            pesan.className = 'pesan benar';
            pesan.textContent = '✅ Berhasil daftar! Pindah ke halaman login...';

            // Pindah ke login
            setTimeout(() => {
                keLogin();
                document.getElementById('pesanLogin').className = 'pesan benar';
                document.getElementById('pesanLogin').textContent = '✅ Akun sudah dibuat! Silakan login.';
            }, 1200);
        }

        // ===== HALAMAN LOGIN =====
        function masuk() {
            const nim = document.getElementById('l_nim').value.trim();
            const pass = document.getElementById('l_pass').value.trim();
            const pesan = document.getElementById('pesanLogin');

            if (!nim || !pass) {
                pesan.className = 'pesan salah';
                pesan.textContent = '⚠️ Isi NIM & Password dulu!';
                return;
            }

            const akun = cariAkun(nim, pass);
            if (!akun) {
                pesan.className = 'pesan salah';
                pesan.textContent = '❌ NIM atau Password salah!';
                return;
            }

            // Berhasil masuk
            pesan.className = 'pesan benar';
            pesan.textContent = '✅ Login berhasil!';

            // Tampilkan data user
            document.getElementById('namaUser').textContent = akun.nama;
            document.getElementById('nimUser').textContent = akun.nim;

            // Pindah ke kalkulator
            setTimeout(() => {
                document.getElementById('halamanLogin').classList.add('sembunyi');
                document.getElementById('halamanKalkulator').classList.remove('sembunyi');
            }, 1000);
        }

        // ===== HALAMAN KALKULATOR =====
        function hitung() {
            const pSks = +document.getElementById('biayaSks').value || 0;
            const jSks = +document.getElementById('jmlSks').value || 0;
            const pTambah = +document.getElementById('biayaTambah').value || 0;

            const biayaSks = pSks * jSks;
            const total = biayaSks + pTambah;

            document.getElementById('hargaSks').textContent = formatRupiah(biayaSks);
            document.getElementById('hargaTambah').textContent = formatRupiah(pTambah);
            document.getElementById('totalBayar').textContent = formatRupiah(total);
            
            document.getElementById('kotakHasil').classList.add('tampil');
        }

        // ===== NAVIGASI & KELUAR =====
        function keLogin() {
            document.getElementById('halamanDaftar').classList.add('sembunyi');
            document.getElementById('halamanLogin').classList.remove('sembunyi');
            resetSemua();
        }
        function keDaftar() {
            document.getElementById('halamanLogin').classList.add('sembunyi');
            document.getElementById('halamanDaftar').classList.remove('sembunyi');
            resetSemua();
        }
        function keluar() {
            resetSemua();
            document.getElementById('halamanKalkulator').classList.add('sembunyi');
            document.getElementById('halamanDaftar').classList.remove('sembunyi');
        }
        function resetSemua() {
            // Reset semua input
            document.querySelectorAll('input').forEach(input => input.value = '');
            document.querySelectorAll('.pesan').forEach(pesan => pesan.style.display = 'none');
            document.getElementById('kotakHasil').classList.remove('tampil');
        }
    </script>
</body>
</html>
