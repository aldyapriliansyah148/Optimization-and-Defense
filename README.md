🛡️ Optimization and Defense: Perancangan Infrastruktur Zero-Trust Access Control dan VLAN Hardening pada Jaringan Multi-Department
🎯 Gambaran Proyek
Proyek ini merancang jaringan lokal multi-departemen dengan pendekatan Zero-Trust ("never trust, always verify"), artinya tidak ada perangkat atau trafik yang langsung dipercaya hanya karena terhubung ke kabel jaringan. Setiap segmen departemen (HR, Finance, IT, dan Guest) dipisahkan secara logis agar gangguan atau ancaman di satu bagian tidak merembet ke bagian lain, sementara perangkat tidak dikenal atau perilaku mencurigakan langsung diblokir otomatis oleh switch 💻🔒.

🧰 Perangkat Jaringan yang Digunakan
1 Unit Switch Layer 3 (3560-24PS): Berperan sebagai core/distribution switch yang mengurus routing antar-VLAN (SVI) serta penyaringan trafik lintas departemen menggunakan Extended ACL 🧠🔀.

1 Unit Switch Layer 2 (2960-24TT): Berperan sebagai access switch tempat perangkat pengguna terhubung sekaligus benteng pertama pertahanan port, DHCP Snooping, dan DAI 🖧🛡️.

1 Unit Router (Router1): Menangani jalur keluar/gateway eksternal serta koneksi jaringan luar atau layanan internet 🌐🚪.

Minimal 4 Unit PC / Laptop: Mewakili endpoint tiap departemen (misalnya HR, Finance, IT, dan Guest) untuk menguji isolasi trafik, akses layanan, dan respons keamanan 💻📱.

⚙️ Fitur, Teknologi & Penjelasan Keamanan
🔒 Network Hardening — Port Security (Sticky MAC & Violate Shutdown)

Membatasi jumlah MAC address yang diizinkan pada port akses dan merekamnya otomatis (sticky) agar port tidak mudah dibajak perangkat asing.

Jika ada MAC address tak berizin yang melewati batas, mode shutdown (atau drop/restrict sesuai kebijakan) langsung mengunci port (err-disabled) agar serangan MAC flooding atau colokan ilegal terhenti seketika 🚨🔌.

🔀 Traffic Isolation — VLAN & Inter-VLAN Routing

Memecah jaringan fisik menjadi beberapa broadcast domain terpisah (IT, HR, Finance, Guest, serta VLAN manajemen) sehingga lalu lintas antar-departemen tidak bercampur bebas.

Komunikasi antar-VLAN tetap bisa diatur secara terkontrol melalui Switch Layer 3 (SVI) atau Router-on-a-Stick sesuai desain jaringan 🗂️🔁.

🚧 Traffic Filtering — Extended ACL

Menyaring paket berdasarkan IP asal, IP tujuan, protokol, dan port untuk menerapkan least privilege antar-segmen.

Contoh skenario: departemen Guest diarahkan hanya ke akses internet/keluar tanpa leluasa masuk ke jaringan internal sensitif, dan trafik dari HR ke Finance diblokir agar data keuangan tetap terlindungi 🛑📊.

🕵️ Mitigasi Serangan — DHCP Snooping & Dynamic ARP Inspection (DAI)

DHCP Snooping memisahkan port trusted (arah DHCP server sah) dan untrusted (port klien) serta membatasi rate paket DHCP untuk mencegah rogue DHCP server dan DHCP starvation 📋⚡.

DAI memvalidasi paket ARP menggunakan database binding DHCP Snooping sehingga serangan ARP spoofing / man-in-the-middle antar-host di jaringan lokal dapat dicegah sebelum meracuni tabel ARP 🎯🛡️.

🧪 Ide Skenario Uji untuk Laporan / Presentasi
Uji Isolasi & ACL: Coba ping dari PC-HR ke PC-FINANCE untuk memastikan paket terblokir, lalu cek hit counter ACL di Switch L3 📊.

Uji Port Security: Sambungkan perangkat/MAC ketiga pada port yang dibatasi maksimal 2 MAC, lalu amati perubahan status port menjadi err-disabled 🔒.

Uji Keamanan L2: Simulasikan trafik DHCP berlebih atau paket ARP palsu pada port untrusted untuk menunjukkan bagaimana DHCP Snooping dan DAI melindungi klien 🌐🛡️.
