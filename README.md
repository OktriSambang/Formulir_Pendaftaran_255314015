# Formulir_Pendaftaran_255314015
## Jawaban Latihan Soal Evaluasi Mandiri (Modul 6)
1. Mengapa validasi client-side tidak boleh menjadi satu-satunya lapisan validasi pada aplikasi web?
   jawab : Validasi client-side berjalan di sisi browser pengguna sehingga sangat mudah untuk dilewati, dimodifikasi, atau dinonaktifkan (misalnya dengan mematikan eksekusi JavaScript atau mengirim payload langsung menggunakan perangkat seperti Postman).Oleh karena itu, validasi server-side wajib diterapkan sebagai benteng keamanan utama untuk menjamin integritas, keamanan, dan kevalidan data sebelum disimpan ke dalam basis data.
2. Sebutkan minimal tiga atribut validasi bawaan HTML5 beserta fungsinya masing-masing.
   jawab : required: Menandakan bahwa suatu elemen input wajib diisi sebelum form dapat dikirimkan.
   minlength / maxlength: Menentukan batas minimum dan maksimum jumlah karakter yang diizinkan pada input teks.
   pattern: Mencocokkan nilai input dengan pola ekspresi reguler (regular expression) tertentu.
3. Jelaskan perbedaan antara input.checkValidity() dan input.reportValidity().
   jawab : input.checkValidity(): Mengembalikan nilai boolean (true atau false) yang menyatakan apakah nilai pada elemen   input memenuhi seluruh batasan validasinya tanpa memicu tampilan visual apapun di browser.
   input.reportValidity(): Selain mengembalikan nilai boolean, fungsi ini juga secara otomatis memerintahkan browser untuk menampilkan gelembung pesan validasi bawaan (validation message bubble) pada elemen yang tidak valid kepada pengguna.
4. Apa fungsi setCustomValidity("") (string kosong), dan mengapa penting memanggilnya kembali setelah error diperbaiki?jawab : Fungsi: setCustomValidity("") dengan argumen string kosong digunakan untuk menghapus pesan kesalahan kustom yang sebelumnya disetel, yang menandakan bahwa elemen input tersebut kini berstatus valid.  Jika pesan kustom tidak dihapus (dikosongkan) saat data sudah benar, browser akan terus menganggap elemen tersebut berada dalam status invalid secara permanen meskipun nilai yang diketik pengguna sudah sesuai.
5. Rancang aturan validasi (beserta pseudocode) agar field “Tanggal Lahir” tidak boleh berada di masa depan.Aturan: Tanggal yang dipilih oleh pengguna tidak boleh lebih besar dari tanggal hari ini (current date).Contoh Pseudocode / Implementasi JavaScript:JavaScriptconst inputTglLahir = document.querySelector("#tanggalLahir");

inputTglLahir.addEventListener("input", () => {
  const tanggalPilihan = new Date(inputTglLahir.value);
  const hariIni = new Date();

  // Hilangkan jam/menit untuk perbandingan tanggal yang akurat
  hariIni.setHours(0, 0, 0, 0);

  if (tanggalPilihan > hariIni) {
    inputTglLahir.setCustomValidity("Tanggal lahir tidak boleh berada di masa depan.");
  } else {
    inputTglLahir.setCustomValidity(""); // Reset validitas kustom
  }
});
