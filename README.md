
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Kuis Acak dengan Timer</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      padding: 20px;
    }
    #kuis-container {
      background: white;
      padding: 20px;
      max-width: 500px;
      margin: auto;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      border-radius: 12px;
    }
    h2, h3 {
      color: #333;
    }
    .pilihan, .kategori {
      margin: 10px 0;
    }
    button {
      margin-top: 15px;
      padding: 10px 20px;
      border: none;
      background-color: #4CAF50;
      color: white;
      cursor: pointer;
      border-radius: 8px;
    }
    #timer {
      font-size: 18px;
      font-weight: bold;
      color: dimgrey;
    }
  </style>
</head>
<body>

<div id="kuis-container">
  <h2 style="position: relative; left: 43%;">KUIS</h2>

  <div id="pilih-kategori">
    <h3 style="position: relative; top: -65%;">Pilih Jenis Kuis:</h3>
    <select id="kategori">
      <option value="matematika">Matematika</option>
      <option value="ipa">IPA</option>
      <option value="inggris">Bahasa Inggris</option>
    </select>
    <button onclick="mulaiKuis()">Mulai</button>
  </div>

  <div id="kuis" style="display:none;">
    <h3 id="pertanyaan" style="position: relative; top: 30px">Pertanyaan akan muncul di sini</h3>
    <div id="timer" style="font-size: 10px; position: relative; top: -46px;">Waktu: 15 detik</div>
    <div class="pilihan" id="pilihan-container" style="position: relative; top: 20px;"></div>
    <button onclick="nextQuestion()" style="position: relative; top: 10px;">Jawab</button>
    <p id="skor"></p>
  </div>
</div>

<script>
  const bankSoal = {
    matematika: [
      { pertanyaan: "18 + 24 ÷ 6 = ?", pilihan: ["7", "22", "26", "42"], benar: "26" },
      { pertanyaan: "Jika x = 3, maka 2x² - x = ?", pilihan: ["15", "18", "21", "27"], benar: "15" },
      { pertanyaan: "20% dari 250 adalah …", pilihan: ["25", "40", "50", "60"], benar: "50" },
      { pertanyaan: "√81 + 2³ = ?", pilihan: ["11", "17", "27", "35"], benar: "17" },
      { pertanyaan: "Jika x + y = 10 dan x - y = 2, maka x = ?", pilihan: ["4", "5", "6", "8"], benar: "6" },
      { pertanyaan: "Hasil dari (5² × 2) - 3 adalah …", pilihan: ["47", "50", "52", "55"], benar: "47" },
      { pertanyaan: "Luas persegi panjang dengan panjang 8 dan lebar 5 adalah …", pilihan: ["13", "30", "40", "48"], benar: "40" },
      { pertanyaan: "Nilai dari 3² + 4² adalah …", pilihan: ["12", "25", "16", "20"], benar: "25" },
      { pertanyaan: "Hasil dari 2(3x - 4) jika x = 5 adalah …", pilihan: ["16", "20", "22", "26"], benar: "22" },
      { pertanyaan: "Jika 5x = 40, maka x = ?", pilihan: ["6", "7", "8", "9"], benar: "8" }
    ],
    ipa: [
      { pertanyaan: "Alat untuk mengukur suhu adalah ...", pilihan: ["Barometer", "Termometer", "Higrometer", "Anemometer"], benar: "Termometer" },
      { pertanyaan: "Proses perubahan air menjadi uap disebut ...", pilihan: ["Menguap", "Membeku", "Mencair", "Mengembun"], benar: "Menguap" },
      { pertanyaan: "Bagian tumbuhan yang berfungsi menyerap air adalah ...", pilihan: ["Daun", "Batang", "Akar", "Bunga"], benar: "Akar" },
      { pertanyaan: "Planet terdekat dengan Matahari adalah ...", pilihan: ["Venus", "Merkurius", "Mars", "Bumi"], benar: "Merkurius" },
      { pertanyaan: "Benda yang dapat menarik logam disebut ...", pilihan: ["Termometer", "Mesin", "Magnet", "Kipas"], benar: "Magnet" },
      { pertanyaan: "Contoh perubahan kimia adalah ...", pilihan: ["Air membeku", "Kertas dibakar", "Es mencair", "Air menguap"], benar: "Kertas dibakar" },
      { pertanyaan: "Gaya yang menyebabkan benda jatuh ke bawah adalah ...", pilihan: ["Gaya otot", "Gaya gesek", "Gaya gravitasi", "Gaya dorong"], benar: "Gaya gravitasi" },
      { pertanyaan: "Zat yang memiliki volume tetap tapi bentuk tidak tetap adalah ...", pilihan: ["Padat", "Cair", "Gas", "Uap"], benar: "Cair" },
      { pertanyaan: "Contoh energi terbarukan adalah ...", pilihan: ["Batu bara", "Minyak bumi", "Angin", "Gas alam"], benar: "Angin" },
      { pertanyaan: "Organ utama dalam sistem pernapasan manusia adalah ...", pilihan: ["Hati", "Jantung", "Paru-paru", "Lambung"], benar: "Paru-paru" }
    ],
    inggris: [
      { pertanyaan: "Choose the correct sentence:", pilihan: ["She don't like coffee.", "She doesn't likes coffee.", "She don't likes coffee.", "She doesn't like coffee."], benar: "She doesn't like coffee." },
      { pertanyaan: "You _____ speak loudly here. It’s a library.", pilihan: ["Can", "Must", "Should", "Must not"], benar: "Must not" },
      { pertanyaan: "If she studies hard, she _____ pass the exam.", pilihan: ["Would", "Will", "Is", "Can't"], benar: "Will" },
      { pertanyaan: "The letter _____ by the secretary yesterday.", pilihan: ["Is typed", "was typed", "were typed", "typing"], benar: "was typed" },
      { pertanyaan: "The cat is hiding_____ the table.", pilihan: ["In", "On", "Under", "At"], benar: "Under" },
      { pertanyaan: "This road is _____ than the one we took yesterday.", pilihan: ["Wide", "Wider", "Widest", "More wide"], benar: "Wider" },
      { pertanyaan: "The opposite of difficult is _____.", pilihan: ["Complex", "Confusing", "Easy", "Hard"], benar: "Easy" },
      { pertanyaan: "My sister and I _____ going to the market.", pilihan: ["Is", "Was", "Are", "Am"], benar: "Are" },
      { pertanyaan: "She _____ her homework before dinner.", pilihan: ["Finish", "Finishes", "Finished", "Finishing"], benar: "Finished" },
      { pertanyaan: "Look! The children _____ in the garden.", pilihan: ["Play", "Played", "Are playing", "Plays"], benar: "Are playing" }
    ]
  };

  let soal = [];
  let index = 0;
  let score = 0;
  let waktu = 15;
  let timerInterval;
  let pilihanBenarSekarang = "";

  function acakArray(array) {
    return array.sort(() => Math.random() - 0.5);
  }

  function mulaiKuis() {
    const kategori = document.getElementById("kategori").value;
    soal = acakArray([...bankSoal[kategori]]); // acak urutan soal
    index = 0;
    score = 0;
    document.getElementById("pilih-kategori").style.display = "none";
    document.getElementById("kuis").style.display = "block";
    tampilkanPertanyaan();
  }

  function tampilkanPertanyaan() {
    const q = soal[index];
    document.getElementById("pertanyaan").textContent = q.pertanyaan;

    const pilihanContainer = document.getElementById("pilihan-container");
    pilihanContainer.innerHTML = "";

    const pilihanAcak = acakArray([...q.pilihan]); // acak pilihan
    pilihanAcak.forEach((text, i) => {
      const id = "pilihan" + i;
      const radio = `<input type="radio" name="jawaban" id="${id}" value="${text}">
                     <label for="${id}">${text}</label><br>`;
      pilihanContainer.innerHTML += radio;
    });

    pilihanBenarSekarang = q.benar;
    waktu = 600;
    document.getElementById("timer").textContent = `Waktu: ${waktu} detik`;
    clearInterval(timerInterval);
    timerInterval = setInterval(updateTimer, 1000);
  }

  function updateTimer() {
    waktu--;
    document.getElementById("timer").textContent = `Waktu: ${waktu} detik`;
    if (waktu <= 0) {
      clearInterval(timerInterval);
      alert("Waktu habis!");
      nextQuestion(true);
    }
  }

  function nextQuestion(auto = false) {
    clearInterval(timerInterval);

    if (!auto) {
      const pilihan = document.querySelector("input[name='jawaban']:checked");
      if (!pilihan) {
        alert("Pilih salah satu jawaban!");
        return tampilkanPertanyaan();
      }
      if (pilihan.value === pilihanBenarSekarang) {
        score++;
      }
    }

    index++;
    if (index < soal.length) {
      tampilkanPertanyaan();
    } else {
      document.getElementById("kuis").innerHTML = `<h2>Benar = ${score} dari ${soal.length} soal</h2>`;
    }
  }
</script>

</body>
</html>
