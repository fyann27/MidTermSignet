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
  <link rel="stylesheet" href="https://unpkg.com/leaflet-routing-machine@latest/dist/leaflet-routing-machine.css" />

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
      </div>

      <!-- Konten Utama -->
      <div class="col-md-9 content" id="mainContent">
        <!-- Default HOME -->
        <h5>Selamat datang di Website Teknik Geomatika</h5>
        <p>Salah satu mata kuliah yang termasuk dalam KBK Sistem Informasi Geografis (SIG) adalah SIG Berbasis Internet. Pada mata kuliah ini mahasiswa mempelajari pengaplikasian SIG dengan berbasis pada platform internet.</p>
        <p>Memahami HTML dan CSS merupakan langkah awal, lalu Bootstrap digunakan untuk membangun tampilan yang lebih menarik dan responsif.</p>
      </div>
    </div>

    <!-- Footer -->
    <div class="row">
      <div class="col-12 footer">
        Copyright @Achmad Sofyan_117220058
      </div>
    </div>
  </div>

  <!-- JS Dependencies -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
  <script src="https://unpkg.com/leaflet-routing-machine@latest/dist/leaflet-routing-machine.js"></script>

  <script>
    let map, control;

    function showContent(section) {
      const content = {
        home: `
          <h5>Selamat datang di Website Teknik Geomatika</h5>
          <p>Salah satu mata kuliah yang termasuk dalam KBK Sistem Informasi Geografis (SIG) adalah SIG Berbasis Internet. Pada mata kuliah ini mahasiswa mempelajari pengaplikasian SIG dengan berbasis pada platform internet.</p>
          <p>Memahami HTML dan CSS merupakan langkah awal, lalu Bootstrap digunakan untuk membangun tampilan yang lebih menarik dan responsif.</p>6
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
          <ul>
            <p>Peta adalah gambaran permukaan bumi yang dibuat pada bidang datar dan diperkecil dengan skala tertentu, yang menunjukkan lokasi, bentuk, dan fenomena geografis yang ada di suatu wilayah. Peta digunakan untuk menyajikan informasi mengenai letak suatu tempat, kondisi fisik wilayah, atau data tematik tertentu, seperti kepadatan penduduk, iklim, atau penggunaan lahan.</p>
            <li><strong>Peta Statis:</strong> Peta yang bersifat tetap dan tidak berubah. Informasi yang ditampilkan pada peta ini sudah bersifat final dan tidak dapat diubah atau diperbarui oleh pengguna secara langsung. Contoh peta statis adalah peta cetak yang biasa ditemukan dalam buku atlas atau peta topografi yang dicetak.</li>
            <li><strong>Peta Dinamis:</strong> Peta yang bersifat interaktif dan dapat berubah sesuai dengan masukan atau data yang diperbarui secara real-time. Pengguna dapat berinteraksi dengan peta ini, misalnya dengan memperbesar, memperkecil, memilih lapisan informasi tertentu, atau melihat data yang terus diperbarui. Contoh dari peta dinamis adalah peta online seperti Google Maps atau peta cuaca yang selalu menampilkan informasi terkini.

</li>
          </ul>
          <img src="https://geohepi.wordpress.com/wp-content/uploads/2020/10/dfghsfg.jpg" class="img-fluid rounded mb-3" alt="Peta Statis">
          <img src="https://bloggeografi.id/wp-content/uploads/2010/06/penduduk_output.jpg" class="img-fluid rounded" alt="Peta Dinamis">
        `,
        petaInteractive: `
          <h5>Peta Interaktif</h5>
          <p>Masukkan lokasi berangkat dan tujuan, lalu klik "Tampilkan Rute"</p>
          <div class="mb-3 row">
            <div class="col-md-5">
              <input type="text" id="startLocation" class="form-control" placeholder="Lokasi Awal (misal: Tugu Jogja)">
            </div>
            <div class="col-md-5">
              <input type="text" id="endLocation" class="form-control" placeholder="Lokasi Tujuan (misal: UPN Yogyakarta)">
            </div>
            <div class="col-md-2">
              <button class="btn btn-warning w-100" onclick="showCustomRoute()">Tampilkan Rute</button>
            </div>
          </div>
          <div id="map" style="height: 400px; border: 1px solid #ccc;"></div>
        `
      };

      document.getElementById('mainContent').innerHTML = content[section] || '<p>Konten tidak ditemukan.</p>';

      if (section === 'petaInteractive') {
        setTimeout(initMap, 100);
      }
    }

    function initMap() {
      if (map) {
        map.remove();
      }
      map = L.map('map').setView([-7.797068, 110.370529], 13);

      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© OpenStreetMap contributors'
      }).addTo(map);
    }

    async function geocodeLocation(query) {
      const url = `https://nominatim.openstreetmap.org/search?format=json&q=${encodeURIComponent(query)}`;
      const res = await fetch(url);
      const data = await res.json();
      if (data && data[0]) {
        return [parseFloat(data[0].lat), parseFloat(data[0].lon)];
      } else {
        alert("Lokasi tidak ditemukan: " + query);
        return null;
      }
    }

    async function showCustomRoute() {
      const startText = document.getElementById('startLocation').value;
      const endText = document.getElementById('endLocation').value;

      if (!startText || !endText) {
        alert('Harap isi kedua lokasi.');
        return;
      }

      const startCoords = await geocodeLocation(startText);
      const endCoords = await geocodeLocation(endText);

      if (!startCoords || !endCoords) return;

      if (control) {
        map.removeControl(control);
      }

      control = L.Routing.control({
        waypoints: [L.latLng(...startCoords), L.latLng(...endCoords)],
        routeWhileDragging: true
      }).addTo(map);
    }
  </script>
</body>
</html>

