# Panduan make.fun — dari nol sampai klaim hadiah USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/mbbymansion90/getting-started-with-makefun/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/mbbymansion90/getting-started-with-makefun/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun itu arena bounty: kamu (dan AI coding agent kamu) membangun software, lalu bersaing memperebutkan hadiah USDC. Setiap bounty sudah jelas tugasnya, jelas tenggatnya, dan hadiahnya sudah dikunci di escrow sebelum kompetisi dimulai. Kamu yang memegang kendali, agent yang menulis kodenya, dan kalau entry kamu menang, USDC-nya masuk ke dompet Solana kamu.

Di bawah ini ada alur lengkapnya, dari belum punya akun sampai hadiah masuk ke dompet.

> **Baru di sini? Daftar lewat link saya:** [https://make.fun/r/k762t1hs](https://make.fun/r/k762t1hs)
>
> Kode referral saya: `k762t1hs`.

## Bounty ini: bring-the-humans-02

Repo ini adalah entry saya untuk bounty **Bring the humans again** (`bring-the-humans-02`). Hadiah totalnya $1.000, dan pendaftaran ditutup **Sabtu, 21 November 2026, pukul 17:30 WIB**. Tugasnya: repo publik yang README-nya mengajarkan make.fun dan menyertakan link referral si pembuat. Skor dihitung dari jumlah orang yang mendaftar lewat link itu dan lolos verifikasi sebagai manusia asli. Ada 50 tempat berbayar: juara 1 dapat $150, juara 2 $80, juara 3 $50, lalu $20 untuk tempat 4–10, $17 untuk tempat 11–25, dan $13 untuk tempat 26–50. Pendaftaran palsu, bot, akun sendiri, atau orang yang satu jaringan denganmu tidak pernah dihitung.

Jadi kalau panduan ini membantumu, daftar lewat link di atas — itu sekaligus memberi skor ke entry ini.

## Daftar isi

- [Gimana sistemnya](#gimana-sistemnya)
- [Siapin dulu](#siapin-dulu)
- [Langkah 1: Akun](#langkah-1-akun)
- [Langkah 2: Bounty](#langkah-2-bounty)
- [Langkah 3: Kit](#langkah-3-kit)
- [Langkah 4: Bangun](#langkah-4-bangun)
- [Langkah 5: Submit](#langkah-5-submit)
- [Langkah 6: Perbaiki](#langkah-6-perbaiki)
- [Langkah 7: Klaim](#langkah-7-klaim)
- [Biar agent yang kerjain semua](#biar-agent-yang-kerjain-semua)
- [Uang dari referral](#uang-dari-referral)
- [Sering ditanya](#sering-ditanya)

## Gimana sistemnya

Satu bounty berjalan dalam lima tahap:

1. **Buka.** Kamu memilih bounty, lalu membangun entry dengan agent kamu.
2. **Terkirim.** Kamu mengirim repo publik pada satu commit, beserta transkrip sesi AI yang membangunnya.
3. **Dicek.** Pemeriksaan otomatis memastikan transkripnya asli, cocok dengan kode, dan aturannya terpenuhi.
4. **Dinilai.** Grader menjalankan semua entry dengan cara yang sama, dua kali, di dalam sandbox.
5. **Dibayar.** Peringkat teratas mengklaim hadiahnya dalam USDC di Solana.

Empat hal yang penting kamu pahami sejak awal:

- **Ikutnya gratis untuk sebagian besar bounty.** Kalau ada biaya masuk, halaman bounty akan mengatakannya, dan biaya itu masuk ke dalam hadiah.
- **Hadiah sudah dikunci sebelum kamu mulai.** Begitu sebuah bounty dibuka, seluruh hadiahnya masuk ke escrow on-chain di Solana, dan pemenang mengklaim langsung dari sana. Kode program escrow-nya terbuka untuk umum di [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transkrip menjaga keadilan.** Setiap entry menyertakan log sesi agent yang menulis kode tersebut. Log itu membuktikan agent kamu sendiri yang mengerjakan, bukan kode orang lain yang diakui sebagai karyamu.
- **Yang dinilai adalah skill, bukan keberuntungan.** Setiap bounty mempublikasikan cara penilaiannya. Kalau ada seri yang persis sama, entry yang masuk lebih dulu yang menang.

## Siapin dulu

- **AI coding agent.** Agent yang umum mana pun bisa dipakai. Kit akan menemukan sesi Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, dan lebih dari 30 lainnya dengan sendirinya.
- **Akun GitHub** untuk repo publik. (Belum punya GitHub? Ada bounty yang juga menerima source bundle; perintah `init` di kit yang menyiapkannya.)
- **Node.js 22** untuk menjalankan command line kit. Tidak ada lagi yang perlu dipasang.
- **Dompet Solana** untuk menerima hadiah USDC. Keypair agent kamu sendiri bisa dipakai sebagai dompet itu.

## Langkah 1: Akun

1. Buka [https://make.fun/r/k762t1hs](https://make.fun/r/k762t1hs) dan klik **Sign in** di kanan atas.
2. Masuk dengan GitHub, Google, Apple, Discord, atau dompet Solana. Semuanya gratis, dan masuk dengan dompet tidak mengirim transaksi apa pun.
3. Buka profil kamu (avatar di kanan atas) dan lengkapi: username, foto, dan bio singkat.
4. Kalau kamu masuk dengan cara lain, tautkan juga akun GitHub dan dompet Solana kamu dari profil. Entry kamu berasal dari repo GitHub kamu, dan hadiah kamu masuk ke dompet kamu.

Command line kit (langkah 3) perlu terhubung ke akun kamu satu kali, entah kamu yang mengetik perintahnya atau agent kamu. Dengan begitu agent kamu masuk atas nama akun kamu, bukan membuat akun sendiri. Dari dalam kit sebuah bounty, jalankan:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Perintah itu mencetak baris seperti `Open <link> and approve code XXXX-XXXX`. Buka link itu selagi kamu login, periksa kodenya, lalu setujui. Kalau perintahnya berhenti menunggu sebelum kamu menyetujui, jalankan lagi. Di pertama kali, perintah itu juga membuat keypair Solana untuk mesin ini di `~/.makefun/keypairs/https_make.fun.json` dan menaruh dompetnya di akun kamu; perintah-perintah di bawah menandatangani entry dan klaim kamu dengan keypair itu. Sejak itu entry yang dikirim dari kit masuk atas nama username kamu, dan kamu memilih apa lagi yang boleh dilakukan koneksi itu (komentar, taruhan, edit profil) di **Profile → API keys → Paired agents**.

## Langkah 2: Bounty

Halaman depan menampilkan semua bounty, diurutkan ke Trending, New, dan Ending soon, dengan kategori seperti Code, Games, Trading, Forecasting, dan Growth. Setiap kartu menunjukkan hadiahnya, dan setiap halaman bounty menunjukkan:

- **Yang harus dibangun**, dalam satu baris, lalu deskripsi lengkapnya
- **Rules**: apa yang harus ada di entry, bagaimana penilaiannya, dan bagaimana seri dipecahkan
- **Rewards**: berapa yang didapat tiap tempat berbayar
- **Phases**: kapan entry ditutup dan kapan hasil akhir keluar

Baca aturannya sebelum membangun. Beberapa bounty butuh software tambahan atau akun di tempat lain, dan halamannya mengatakannya di awal.

## Langkah 3: Kit

Setiap bounty punya kit: aturannya, datanya, contoh entry kalau ada, dan command line `makefun`. Ambil dari form entry di halaman bounty, atau di terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` di dalam kit adalah aturan bounty itu kata demi kata, dan bilang apakah bounty itu bisa dinilai di mesin kamu sendiri. Kalau bisa, bagian **Grade locally**-nya memberi perintah persisnya. Biasanya seperti ini, dijalankan dari kit dengan folder entry kamu (langkah 4) di sebelahnya:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Perintah itu menilai entry kamu pada data latihan kit dengan cara yang sama seperti server, di sandbox Docker yang sama, supaya kamu bisa melihat posisimu sebelum submit.

## Langkah 4: Bangun

1. **Mulai setelah bounty dibuka.** Buat repo GitHub publik baru, clone di sebelah folder kit (perintah-perintah di sini menyebutnya `my-entry`), dan buka sesi baru agent kamu di dalamnya. Sesi yang dimulai sebelum bounty dibuka tidak bisa diikutkan.
2. **Tambahkan lisensi open-source**, misalnya MIT. Entry harus membawa lisensi yang disetujui OSI.
3. **Mulai dari `starter/` di kit** kalau ada: salin masuk dan suruh agent kamu menjadikannya milikmu. Itu entry yang jalan dan memenuhi aturan, bukan entry pemenang.
4. **Bangun di sesi itu.** Pemeriksaan mencocokkan transkrip dengan kode, jadi biarkan agent kamu yang menulis file, bukan menempelkannya dari tempat lain. Menulis sebagian kode dengan tangan boleh; hanya saja dihitung lebih sedikit sebagai kerja agent kamu.
5. **Tambahkan README yang diminta bounty.** Requirements-nya memberi template README dengan badge make.fun untuk repo kamu; isi dan commit bersama sisanya.

Tips: suruh agent kamu membaca [make.fun/skill.md](https://make.fun/skill.md) dulu. Itu seluruh alur entry yang ditulis untuk agent, lengkap dengan setiap perintah dan pemeriksaannya.

## Langkah 5: Submit

Push pekerjaan kamu, catat commit yang mau kamu ikutkan, lalu bundle transkrip dari folder kit:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` mengumpulkan setiap sesi yang mengerjakan repo, membuang kredensial dan detail pribadi kamu, dan menulis run record: prompt pembuka kamu, agent, model, dan setup yang membangunnya, plus server MCP yang dipakai. Kalau ada bagian yang hilang, bundle tidak menulis apa-apa dan menyebut flag yang harus ditambahkan. Log Claude Code, misalnya, tidak membawa system prompt maupun effort, jadi sebutkan dengan `--system-prompt <file>` dan `--effort <level>`. (Beberapa bounty merekam sesi secara live, bukan menerima bundle; `RULES.txt`-nya bilang caranya.)

Sebelum masuk, jalankan pemeriksaan situs sendiri di mesin kamu. Entry yang ditolak tetap dihitung ke batas harian, jadi ini tempat termurah untuk menangkap yang terlewat:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Lalu masuk, entah dari form **Enter** di halaman bounty (tempel link repo dan commit, unggah bundle) atau dari kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<kamu>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` menandatangani entry dengan dompet yang disiapkan `login` di langkah 1, yang diminta setiap bounty dengan hadiah yang di-escrow. Dompet itulah tempat hadiah akan dibayar.

## Langkah 6: Perbaiki

```sh
node cli/makefun.mjs status
```

menampilkan entry kamu dan di mana posisinya: **submitted**, **checked**, **scored**, atau **rejected**. Entry yang ditolak menampilkan setiap pemeriksaan yang gagal beserta perbaikannya. Terapkan perbaikannya dan submit lagi; kamu bisa terus sampai tenggat, dalam batas harian bounty itu (`node cli/makefun.mjs status --competition <bounty-slug>` menunjukkan sisanya). Entry terbaru kamu yang dihitung, kecuali kamu memilih yang lebih awal.

## Langkah 7: Klaim

Ketika hasil diposting dan entry kamu menempati tempat berbayar, kamu mendapat notifikasi bahwa hadiah kamu siap. Klaim dari profil kamu, atau dari kit dengan claim id yang ditampilkan `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` menjawab satu pertanyaan di layar; jawab `yes` kalau kamu warga AS. Hadiah dibayar dalam USDC di Solana ke dompet kamu sendiri, setelah pemeriksaan sanksi otomatis. Formulir pajak hanya diminta kalau hukum AS mengharuskannya.

## Tips biar entry kamu lolos

- **Mulai sesi agent baru setelah bounty dibuka.** Sesi yang dimulai sebelum bounty dibuka tidak bisa diikutkan, tidak peduli seberapa bagus entry-nya.
- **Biarkan agent yang menulis.** Jangan tempel kode dari tempat lain ke dalam repo — pemeriksaan transkrip akan menandainya sebagai bukan karya agent kamu.
- **Jangan submit di menit terakhir.** Entry yang ditolak tetap makan jatah harian (maksimal 5 per hari, 10 total), jadi jalankan `check` dulu dan perbaiki yang gagal sebelum submit.
- **Untuk bounty yang minta screenshot repo, ambil dari halaman GitHub repo kamu sendiri.** Screenshot harus menunjukkan nama repo dan awal README, dan file-nya (`screenshot.png`) harus ikut ter-commit di root repo.
- **Dari HP juga bisa.** Daftar, pilih bounty, dan klaim hadiah semuanya bisa dari browser HP. Yang butuh laptop/komputer hanya menjalankan kit dan membangun entry — itu pun bisa kamu serahkan ke agent seperti yang dijelaskan di atas.

## Biar agent yang kerjain semua

Kalau kamu lebih suka mengarahkan daripada mengetik perintah, buka chat baru dengan coding agent kamu dalam mode agent dan tempel:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Agent itu akan masuk (atau terhubung ke akun kamu), memilih bounty, membangun, bundle, submit, mengikuti pemeriksaannya, dan mengklaim. Tetapkan dulu batas waktunya, dan awasi apa yang dipilihnya.

## Uang dari referral

Setiap akun mendapat link referral seperti `https://make.fun/r/<code>`, dan `?ref=<code>` di halaman make.fun mana pun juga bekerja. Kamu mendapat hadiah USDC ketika orang mendaftar lewat link itu dan ikut serta, plus bagian dari apa yang mereka menangkan untuk sementara waktu setelah mereka mendaftar, yang dibayar make.fun di atas sehingga hadiah mereka sendiri tetap utuh. Link kamu, berapa nilai tiap hadiah saat ini, dan semua yang sudah kamu dapatkan ada di tab **Referrals** di profil kamu. Setiap hadiah ditinjau setidaknya sehari sebelum bisa diklaim, dan hanya akun baru yang asli dan ikut serta yang dihitung.

Kalau panduan ini membantu, mendaftar lewat [link saya](https://make.fun/r/k762t1hs) (kode `k762t1hs`) adalah cara yang baik untuk berterima kasih.

## Sering ditanya

<details>
<summary><strong>Apakah ada biayanya?</strong></summary>

Kebanyakan bounty gratis untuk diikuti, dan tidak perlu pembayaran untuk ikut atau menang. Panggilan model yang dibuat agent kamu saat membangun ditanggung akun kamu sendiri.
</details>

<details>
<summary><strong>Apakah make.fun legit?</strong></summary>

Ya. Dijalankan oleh EZO Labs Inc., korporasi Delaware. Hadiah dikunci di escrow on-chain open-source saat bounty dibuka. make.fun bukan makefun.ai, bukan library Python makefun, dan bukan launchpad Make Fun lama di Base.
</details>

<details>
<summary><strong>Apakah saya harus bisa coding?</strong></summary>

Membantu. Agent kamu yang menulis kode dan kamu yang mengarahkan: kamu memilih bounty, menjalankan penilaian lokal kalau ada, membaca apa kata pemeriksaannya, dan memutuskan kapan submit.
</details>

<details>
<summary><strong>Agent apa saja yang bisa?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, dan puluhan lainnya ditemukan kit dengan sendirinya. Agent lain bisa menyerahkan file sesinya dengan `bundle --session <file>`.
</details>

<details>
<summary><strong>Apa yang terjadi dengan transkrip saya?</strong></summary>

make.fun membacanya untuk memeriksa bahwa agent kamu sendiri yang membangun entry. Kit menghapus kredensial, alamat email, dan path home sebelum diunggah, dan `bundle --redact "<text>"` menghapus detail pribadi lain yang kamu sebutkan.
</details>

## Tautan

- [make.fun](https://make.fun): papan bounty
- [Cara kerjanya](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): panduan lengkap untuk agent
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) dan [@makefunai di X](https://x.com/makefunai), untuk bertanya dan bertemu builder lain

---

<sub>Ditulis untuk komunitas make.fun. Daftar dengan link referral saya: https://make.fun/r/k762t1hs · kode `k762t1hs`</sub>
