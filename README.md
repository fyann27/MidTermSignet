<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Teknik Geomatika UPN</title>

  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet"/>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css"/>

  <!-- Leaflet CSS -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />

  <style>
    .judul {
      background-color: #ffe100;
      font-weight: bold;
      padding: 15px;
      text-align: center;
    }
    .footer {
      background-color: #ffb100;
      color: black;
      text-align: center;
      font-weight: bold;
      padding: 10px;
    }
    .sidebar {
      background-color: #d9d9d9;
      padding: 15px;
      font-weight: bold;
      min-height: 100%;
    }
    .content {
      padding: 15px;
      min-height: 300px;
    }
    .kbk-link {
      display: block;
      background-color: #eaeaea;
      padding: 10px 15px;
      border-radius: 5px;
      margin-bottom: 10px;
      color: black;
      text-decoration: none;
      transition: background-color 0.3s ease, transform 0.2s ease;
      cursor: pointer;
    }
    .kbk-link:hover {
      background-color: #ffd700;
      transform: translateX(5px);
      text-decoration: none;
    }
    .kbk-icon {
      margin-right: 10px;
    }
  </style>
</head>
<body>
  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <span class="navbar-brand fw-bold">Teknik Geomatika</span>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <a class="nav-link active" href="#" onclick="showContent('home')">
              <i class="bi bi-house-door-fill"></i> Home
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" onclick="showContent('peta')">
              <i class="bi bi-map"></i> Jenis dan Contoh Peta
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" onclick="showContent('petaInteractive')">
              <i class="bi bi-globe"></i> Peta Interaktif
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Header -->
  <div class="judul">
    Teknik Geomatika UPN “Veteran” Yogyakarta
  </div>

  <div class="container-fluid">
    <div class="row">
      <!-- Sidebar -->
      <div class="col-md-3 sidebar">
        <p class="mb-3">Kelompok Bidang Keahlian (KBK)</p>
        <div onclick="showContent('terestris')" class="kbk-link">
          <i class="bi bi-compass kbk-icon"></i> KBK Terestris
        </div>
        <div onclick="showContent('sig')" class="kbk-link">
          <i class="bi bi-globe2 kbk-icon"></i> KBK Sistem Informasi Geografis
        </div>
        <div onclick="showContent('fotogrametri')" class="kbk-link">
          <i class="bi bi-camera2 kbk-icon"></i> KBK Fotogrametri
        </div>
        <div onclick="showContent('pj')" class="kbk-link">
          <i class="bi bi-eye kbk-icon"></i> KBK Penginderaan Jauh
        </div>
        <div onclick="showContent('petaInteractive')" class="kbk-link">
          <i class="bi bi-globe kbk-icon"></i> Peta Interaktif
        </div>
      </div>

      <!-- Konten Utama -->
      <div class="col-md-6 content" id="mainContent">
        <!-- Konten default HOME -->
        <h5>Selamat datang di Website Teknik Geomatika</h5>
        <p>Salah satu mata kuliah yang termasuk dalam KBK Sistem Informasi Geografis (SIG) adalah SIG Berbasis Internet. Pada mata kuliah ini mahasiswa mempelajari pengaplikasian SIG dengan berbasis pada platform internet. Mahasiswa mempelajari konsep kerja internet, proses <em>request</em> dan <em>respond</em> oleh <em>user</em> dan <em>client</em>, serta pembangunan website itu sendiri.</p>
        <p>Memahami HTML dan CSS merupakan langkah selanjutnya bagi mahasiswa yang membuat halaman website. Kali ini, salah satu tugas adalah membangun tampilan halaman web sederhana ini. Selanjutnya halaman sederhana ini dikembangkan kembali dengan mengaplikasikan penggunaan Bootstrap.</p>
      </div>

      <!-- Gambar -->
      <div class="col-md-3 p-3">
        <img src="https://th.bing.com/th/id/R.d03d8d2ed3d5375ffe9e38134daa5789?rik=J8j%2fYbZicPoxRw&riu=http%3a%2f%2fwww.ezega.com%2fuserfiles%2fOnline-world.jpg&ehk=I3wVFR8tYKA8Ld9p9qr6qZzDHWt74wfiDe8fNi%2f7zdI%3d&risl=&pid=ImgRaw&r=0" 
             class="img-fluid rounded shadow-sm" alt="Representasi Dunia Online">
      </div>
    </div>

    <!-- Footer -->
    <div class="row">
      <div class="col-12 footer">
        Copyright @Achmad Sofyan_NIM
      </div>
    </div>
  </div>

  <!-- JavaScript untuk dinamis konten -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
  <!-- Leaflet JS -->
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

  <script>
    function showContent(section) {
      const content = {
        home: `
          <h5>Selamat datang di Website Teknik Geomatika</h5>
          <p>Salah satu mata kuliah yang termasuk dalam KBK Sistem Informasi Geografis (SIG) adalah SIG Berbasis Internet. Pada mata kuliah ini mahasiswa mempelajari pengaplikasian SIG dengan berbasis pada platform internet. Mahasiswa mempelajari konsep kerja internet, proses <em>request</em> dan <em>respond</em> oleh <em>user</em> dan <em>client</em>, serta pembangunan website itu sendiri.</p>
          <p>Memahami HTML dan CSS merupakan langkah selanjutnya bagi mahasiswa yang membuat halaman website. Kali ini, salah satu tugas adalah membangun tampilan halaman web sederhana ini. Selanjutnya halaman sederhana ini dikembangkan kembali dengan mengaplikasikan penggunaan Bootstrap.</p>
        `,
        terestris: `
          <h5>KBK Terestris</h5>
          <p>KBK Terestris membahas tentang survei pemetaan darat, penggunaan Total Station, GNSS, dan metode pengukuran klasik lainnya.</p>
        `,
        sig: `
          <h5>KBK Sistem Informasi Geografis</h5>
          <p>KBK SIG fokus pada pembangunan sistem berbasis peta digital, analisis spasial, hingga pengembangan aplikasi GIS berbasis web.</p>
        `,
        fotogrametri: `
          <h5>KBK Fotogrametri</h5>
          <p>KBK Fotogrametri membahas teknik pemotretan udara menggunakan UAV, pengolahan citra udara, dan pembuatan model 3D permukaan.</p>
        `,
        pj: `
          <h5>KBK Penginderaan Jauh</h5>
          <p>KBK Penginderaan Jauh mempelajari citra satelit, interpretasi data multispektral, serta aplikasi remote sensing untuk lingkungan dan pertanian.</p>
        `,
        peta: `
          <h5>Jenis dan Contoh Peta</h5>
          <p>Berikut adalah contoh dua jenis peta:</p>
          <ul>
            <li><strong>Peta Statis:</strong> Peta cetak atau gambar yang tidak berubah, seperti yang digunakan dalam buku atau laporan.</li>
            <li><strong>Peta Dinamis:</strong> Peta yang dapat berubah atau memberikan animasi visual seperti peta GIF atau video singkat.</li>
          </ul>
          <div class="mb-3">
            <h6>Peta Statis:</h6>
            <img src="peta-statis.jpg" alt="Peta Statis" class="img-fluid rounded border">
          </div>
          <div>
            <h6>Peta Dinamis:</h6>
            <img src="peta-dinamis.gif" alt="Peta Dinamis" class="img-fluid rounded border">
          </div>
        `,
        petaInteractive: `
          <h5>Peta Interaktif</h5>
          <p>Berikut adalah contoh peta interaktif sederhana menggunakan Leaflet.js.</p>
          <div id="map" style="height: 400px; border: 1px solid #ccc;"></div>
        `
      };
      document.getElementById('mainContent').innerHTML = content[section] || '<p>Konten tidak ditemukan.</p>';

      if (section === 'petaInteractive') {
        setTimeout(initLeafletMap, 100);
      }
    }

    function initLeafletMap() {
      if (!document.getElementById('map')) return;

      if (window.leafletMap) {
        window.leafletMap.remove();
      }

      window.leafletMap = L.map('map').setView([-7.797068, 110.370529], 13);

      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 19,
        attribution: '© OpenStreetMap'
      }).addTo(window.leafletMap);

      L.marker([-7.797068, 110.370529]).addTo(window.leafletMap)
        .bindPopup('Lokasi UPN “Veteran” Yogyakarta')
        .openPopup();
    }
  </script>
</body>
</html>
