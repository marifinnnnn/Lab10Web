<table>
  <tr>
    <th colspan="2">DATA MAHASISWA</th>
  </tr>
  <tr>
    <td>Nama</td>
    <td>Muhammad Arifin</td>
  </tr>
  <tr>
    <td>NIM</td>
    <td>312210330</td>
  </tr>
  <tr>
    <td>Kelas</td>
    <td>TI.22.A3</td>
  </tr>
</table>

# <p align="center">Praktikum10 : PHP OOP</p>

# Instruksi Praktikum

1. Persiapkan text editor misalnya VSCode.
   
2. Buat folder baru dengan nama lab10_php_oop pada docroot webserver (htdocs)
  
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.

# Langkah-langkah praktikum

1. Buat file dengan pertama <b>mobile.php</b>
      
        <?php
        /**
        * Program sederhana pendefinisian class dan pemanggilan class.
        **/
        
        class Mobil
        {
            private $warna;
            private $merk;
            private $harga;
        
            public function __construct()
            {
                $this->warna = "Biru";
                $this->merk = "BMW";
                $this->harga = "10000000";
            }
            
            public function gantiWarna ($warnaBaru)
            {
                $this->warna = $warnaBaru;
            }
        
            public function tampilWarna ()
            {
                echo "Warna mobilnya : " . $this->warna; 
            }
        }
        
        // membuat objek mobil
        $a = new Mobil();
        $b = new Mobil();
        
        // memanggil objek
        echo "<b>Mobil pertama</b><br>";
        $a->tampilWarna();
        echo "<br>Mobil pertama ganti warna<br>";
        $a->gantiWarna("Merah");
        $a->tampilWarna();
        
        // memanggil objek
        echo "<br><b>Mobil kedua</b><br>";
        $b->gantiWarna("Hijau");
        $b->tampilWarna();
        
        ?>
   
  ### PENJELASAN
  
### 1. Class Mobil:
   
- Properti:

   - ```$warna``` : Menyimpan informasi warna mobil.

   - ```$merk```  : Menyimpan informasi merk mobil.

   - ```$harga``` : Menyimpan informasi harga mobil.

- Metode:

   - ```__construct()``` : Constructor yang dipanggil ketika objek diinisialisasi. Pada constructor, nilai default untuk warna, merk, dan harga diatur.

   - ```gantiWarna($warnaBaru)``` : Metode untuk mengganti warna mobil.

   - ```tampilWarna()``` : Metode untuk menampilkan informasi warna mobil.

### 2. Pembuatan Objek:

      $a = new Mobil();
      $b = new Mobil();

Dua objek, $a dan $b, dibuat dari class Mobil menggunakan operator new.

### 3. Pemanggilan Metode dan Output:

        // Memanggil objek $a
        echo "<b>Mobil pertama</b><br>";
        $a->tampilWarna();  // Menampilkan warna mobil pertama (default: Biru)
        echo "<br>Mobil pertama ganti warna<br>";
        $a->gantiWarna("Merah");  // Mengubah warna mobil pertama menjadi Merah
        $a->tampilWarna();  // Menampilkan warna mobil pertama setelah diubah
        
        // Memanggil objek $b
        echo "<br><b>Mobil kedua</b><br>";
        $b->gantiWarna("Hijau");  // Mengubah warna mobil kedua menjadi Hijau
        $b->tampilWarna();  // Menampilkan warna mobil kedua setelah diubah
        
### OUTPUT     
        
![288366561](https://github.com/marifinnnnn/Lab10Web/assets/115518274/be6d24f2-584d-4460-875a-e19e2172cd98)

        
## Class Library
  
Class library merupakan pustaka kode program yang dapat digunakan bersama pada beberapa file yang berbeda (konsep modularisasi). Class library menyimpan fungsi-fungsi atau class object komponen untuk memudahkan dalam proses development aplikasi.

### Contoh class library untuk membuat form.

2. Buat file baru dengan nama <b>form.php</b>

        <?php
        /**
        * Nama Class: Form
        * Deskripsi: CLass untuk membuat form inputan text sederhan
        **/
        class Form
        {
        private $fields = array();
        private $action;
        private $submit = "Submit Form";
        private $jumField = 0;
        public function __construct($action, $submit)
        {
        $this->action = $action;
        $this->submit = $submit;
        }
        public function displayForm()
        {
        echo "<form action='".$this->action."' method='POST'>";
        echo '<table width="100%" border="0">';
        for ($j=0; $j<count($this->fields); $j++) {
        echo "<tr><td
        
        align='right'>".$this->fields[$j]['label']."</td>";
        echo "<td><input type='text'
        name='".$this->fields[$j]['name']."'></td></tr>";
        }
        echo "<tr><td colspan='2'>";
        echo "<input type='submit' value='".$this->submit."'></td></tr>";
        echo "</table>";
        }
        public function addField($name, $label)
        {
        $this->fields [$this->jumField]['name'] = $name;
        $this->fields [$this->jumField]['label'] = $label;
        $this->jumField ++;
        }
        }
        ?>

Class adalah prototype, atau blueprint, atau rancangan yang mendefinisikan variable dan method-methode pada seluruh objek tertentu. Class berfungsi untuk menampung isi dari program yang akan di jalankan, di dalamnya berisi atribut / type data dan method untuk menjalankan suatu program.

File tersebut tidak dapat dieksekusi langsung, karena hanya berisi deklarasi class. Untuk menggunakannya perlu dilakukan include pada file lain yang akan menjalankan dan harus dibuat instance object terlebih dulu.

  ### PENJELASAN
  
### 1. Class Form:

- Properti:

   - ```$fields```: Sebuah array yang menyimpan informasi tentang setiap field pada formulir. Setiap field memiliki nama (name) dan label (label).

   - ```$action```: Menyimpan URL yang akan dijadikan nilai atribut action pada tag.

   - ```$submit```: Menyimpan teks yang akan dijadikan nilai atribut value pada tombol submit formulir.

   - ```$jumField```: Menyimpan jumlah field pada formulir.

- Metode:

   - ```__construct($action, $submit)```: Constructor yang digunakan untuk menginisialisasi properti $action dan $submit saat objek diinstansiasi.

   - ```displayForm()```: Metode untuk menampilkan formulir HTML ke layar. Formulir ini memiliki field input teks untuk setiap field yang ditambahkan menggunakan metode addField().

   - ```addField($name, $label)```: Metode untuk menambahkan field baru ke dalam formulir. Setiap field memiliki nama dan label.

### 2. Pembuatan Objek dan Penggunaan:

      $myForm = new Form("process.php", "Submit Form");
      $myForm->addField("name", "Name");
      $myForm->addField("email", "Email");
      $myForm->addField("phone", "Phone Number");
      $myForm->displayForm();

Objek $myForm dibuat dari class Form. Kemudian, tiga field (Name, Email, dan Phone Number) ditambahkan ke dalam formulir menggunakan metode addField(). Terakhir, formulir ditampilkan ke layar menggunakan metode displayForm().

### Contoh implementasi pemanggilan class library form.php

3. Buat file baru dengan nama <b>form_input.php</b>

        <?php
        /**
        * Program memanfaatkan Program 10.2 untuk membuat form inputan sederhana.
        **/
        include "form.php";
        echo "<html><head><title>Mahasiswa</title></head><body>";
        $form = new Form("","Input Form");
        $form->addField("txtnim", "Nim");
        $form->addField("txtnama", "Nama");
        $form->addField("txtalamat", "Alamat");
        echo "<h3>Silahkan isi form berikut ini :</h3>";
        $form->displayForm();
        echo "</body></html>";
        ?>
   
Fungsi PHP include() dan require() merupakan fungsi yang digunakan untuk menyertakan file php lain ke dalam suatu program PHP. Hal sangat yang sangat membantu proses pemrograman karena tidak perlu menulis program PHP secara berulang-ulang, cukup dalam satu file saja.

### OUTPUT

<img width="683" alt="288378571" src="https://github.com/marifinnnnn/Lab10Web/assets/115518274/643c0d4d-78c2-40f3-96cf-1a404fb0a791">


### Contoh lainnya untuk database connection dan query.

4. Buat file dengan nama <b>database.php</b>

        <?php
        class Database
        {
            protected $host;
            protected $user;
            protected $password;
            protected $db_name;
            protected $conn;
            public function __construct()
            {
                $this->getConfig();
                $this->conn = new mysqli(
                    $this->host,
                    $this->user,
                    $this->password,
                    $this->db_name
                );
                if ($this->conn->connect_error) {
                    die("Connection failed: " . $this->conn->connect_error);
                }
            }
            private function getConfig()
            {
                include_once("config.php");
                $this->host = $config['host'];
                $this->user = $config['username'];
                $this->password = $config['password'];
                $this->db_name = $config['db_name'];
            }
            public function query($sql)
            {
                return $this->conn->query($sql);
            }
            public function get($table, $where = null)
            {
                if ($where) {
                    $where = " WHERE " . $where;
                }
                $sql = "SELECT * FROM " . $table . $where;
                $sql = $this->conn->query($sql);
                $sql = $sql->fetch_assoc();
                return $sql;
            }
            public function insert($table, $data)
            {
                if (is_array($data)) {
                    foreach ($data as $key => $val) {
                        $column[] = $key;
                        $value[] = "'{$val}'";
                    }
                    $columns = implode(",", $column);
                    $values = implode(",", $value);
                }
                $sql = "INSERT INTO " . $table . " (" . $columns . ") VALUES (" . $values . ")";
                $sql = $this->conn->query($sql);
                if ($sql == true) {
                    return $sql;
                } else {
                    return false;
                }
            }
            public function update($table, $data, $where)
            {
                $update_value = array(); // Inisialisasi sebagai array kosong
        
                if (is_array($data)) {
                    foreach ($data as $key => $val) {
                        $update_value[] = "$key='{$val}'";
                    }
                }
        
                $update_value = implode(",", $update_value); // Konversi menjadi string
        
                $sql = "UPDATE " . $table . " SET " . $update_value . " WHERE " . $where;
                $result = $this->conn->query($sql);
                return ($result) ? true : false;
            }
        
        
            public function delete($table, $filter)
            {
                $sql = "DELETE FROM " . $table . " " . $filter;
                $sql = $this->conn->query($sql);
                if ($sql == true) {
                    return true;
                } else {
                    return false;
                }
            }
        }

  ### PENJELASAN

### 1. Properti:

      protected $host;
      protected $user;
      protected $password;
      protected $db_name;
      protected $conn;

- Properti-properti ini menyimpan informasi terkait dengan koneksi database, seperti alamat host, username, password, nama database, dan objek koneksi MySQLi.

### 2. Constructor (__construct):

      public function __construct()
      {
          $this->getConfig();
          $this->conn = new mysqli(
              $this->host,
              $this->user,
              $this->password,
              $this->db_name
          );
          if ($this->conn->connect_error) {
              die("Connection failed: " . $this->conn->connect_error);
          }
      }

   - Constructor ini dipanggil ketika objek dari class Database dibuat.

   - Memanggil metode getConfig() untuk mendapatkan konfigurasi koneksi dari file "config.php".

   - Membuat objek koneksi MySQLi menggunakan informasi yang telah diambil.

   - Jika koneksi gagal, program akan berhenti dan menampilkan pesan kesalahan.

### 3. Metode getConfig():

      private function getConfig()
      {
          include_once("config.php");
          $this->host = $config['host'];
          $this->user = $config['username'];
          $this->password = $config['password'];
          $this->db_name = $config['db_name'];
      }

   - Metode ini digunakan untuk mengambil konfigurasi koneksi dari file "config.php".

   - File "config.php" seharusnya berisi definisi variabel $config yang menyimpan informasi koneksi.

### 4. Metode query($sql):

      public function query($sql)
      {
          return $this->conn->query($sql);
      }

- Metode ini digunakan untuk mengeksekusi query SQL pada database.

### 5. Metode get($table, $where = null):

      public function get($table, $where = null)
      {
          // ... (mendapatkan data dari tabel dengan atau tanpa kondisi)
      }

   - Metode ini digunakan untuk mengambil data dari tabel.

   - Jika $where diberikan, akan ditambahkan ke dalam query sebagai kondisi WHERE.

### 6. Metode insert($table, $data):

      public function insert($table, $data)
      {
          // ... (menyisipkan data ke dalam tabel)
      }

- Metode ini digunakan untuk menyisipkan data baru ke dalam tabel.

### 7. Metode update($table, $data, $where):

      public function update($table, $data, $where)
      {
          // ... (mengupdate data di dalam tabel berdasarkan kondisi WHERE)
      }

- Metode ini digunakan untuk memperbarui data di dalam tabel berdasarkan kondisi WHERE.

### 8. Metode delete($table, $filter):

      public function delete($table, $filter)
      {
          // ... (menghapus data dari tabel berdasarkan kondisi WHERE)
      }

- Metode ini digunakan untuk menghapus data dari tabel berdasarkan kondisi WHERE.

# Pertanyaan dan Tugas

Implementasikan konsep modularisasi pada kode program pada praktikum sebelumnya dengan menggunakan class library untuk form dan database connection.
