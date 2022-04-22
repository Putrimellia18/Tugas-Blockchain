Tugas 4
Analisis Consensus.go
=======================================================================================================================================================================
Consensus.go merupakan consensus etherium yang dibuat dengan bahasa go language.
Pada file Consensus.go terdapat 4 interface yaitu ChainHeaderReader, ChainReader, Engine, dan PoW.

Interface ChainHeaderReader ini merupakan metode yang digunakan untuk melakukan verifikasi header.
Hal pertama yang dilakukan saat melakukan verifikasi header adalah config mengambil header saat ini dari rantai lokal, lalu mengambil header blok dari database dengan hash dan nomor, mengambil header blok dari data base dengan nomor, lalu mengambil header blok dari database dengan hashnya, dan terakhir mengambil total kesulitan dari database dengan hash dan nomor.

Interface ChainReader berfungsi untuk mengakses lokal blockchain selama verifikasi header dan/atau uncle. 
Dalam interface ChainReader terdapat fungsi GetBlock yang berfungsi untuk mengambil blok dari database dengan hash dan nomor. 

Interface Engine merupakan interface untuk melakukan consensus agnostic algoritma.
Terdapat beberapa tahapan untuk melakukan consensus agnostic yaitu mengambil alamat Ethereum, dari akun yang mencetak yang di berikan blok yang mungkin berbeda dari basis koin header jika konsensus mesin di dasarkan pada tanda tangan penulis, lalu memeriksa apakah header sesuai dengan aturan konsensus mesin yang di berikan, memverifikasi segel (optional atau secara eksplisit), memverifikasi bahwa uncle block yang diberikan sesuai dengan konsensus aturan dari mesin tertentu, menginisialisasi bidang konsensus dari header block sesuai dengan aturan mesin tertentu, memodifikasi status pasca transaksi tetapi tidak merakit blok. menjalankan modifikasi status pasca transaksi dan menggabungkan final blok, menghasilkan permintaan penyegelan baru untuk blok input yang diberikan dan mendorong hasilnya ke channel yang diberikan, mengembalikan hash dari sebuah block sebelum disgel, melakukan penyesuaian tingkat kesulitan, terakhir mengembalikan API RPC yang disediakan mesin consensus.

Interface yang terakhir adalah PoW. Interface PoW merupakan interface untuk melakukan consensus engine berdasarkan Proof-Of-Work yang mengartikan berdasarkan bukti kerja. 
Interface PoW ini memanggil interface engine serta mengembalikan hashrate penambangan saat ini dari mesin konsensus PoW.

Proof-of-work adalah mekanisme yang memungkinkan jaringan Ethereum yang terdesentralisasi untuk mencapai konsensus, atau menyetujui hal-hal seperti saldo akun dan urutan transaksi. 
Algoritma PoW yang berdasarkan penetapkan kesulitan dan aturan untuk pekerjaan yang dilakukan penambang. PoW merupakan tindakan menambahkan blok yang valid ke rantai. 
Semakin banyak pekerja/penambang yang dilakukan, semakin panjang rantainya, dan semakin tinggi nomor bloknya, semakin yakin jaringan tersebut tentang keadaan saat ini.
