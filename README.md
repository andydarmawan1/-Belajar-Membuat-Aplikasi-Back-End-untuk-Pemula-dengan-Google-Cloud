Kriteria 1 : Aplikasi menggunakan port 9000
Aplikasi yang Anda buat harus menggunakan port 9000. Jika komputer yang Anda gunakan untuk membuat submission tidak bisa memakai port 9000,  buatlah submission dengan port lain, lalu ketika submission hendak dikirimkan silakan ganti portnya ke 9000.

Kriteria 2 : Aplikasi dijalankan dengan perintah npm run start.
Aplikasi yang Anda buat harus memiliki runner script start. Cara membuatnya, Anda tambahkan properti start ke dalam properti scripts pada package.json seperti berikut:

<img width="689" height="233" alt="image" src="https://github.com/user-attachments/assets/920f1964-19a1-4483-bbf5-67b1036df5b7" />

Pastikan aplikasi tidak dijalankan dengan menggunakan nodemon. Jika Anda ingin menggunakan nodemon dalam proses development, masukkan nodemon kedalam runner script lain, contohnya:

<img width="689" height="260" alt="image" src="https://github.com/user-attachments/assets/e262675b-03bc-4a1e-a344-2daa6a407346" />

Kriteria 3 : API dapat menyimpan buku
API yang Anda buat harus dapat menyimpan buku melalui route:

Method : POST
URL : /books
Body Request:

<img width="651" height="331" alt="image" src="https://github.com/user-attachments/assets/7630fe72-abf4-4ef3-b188-807d9028684b" />

Objek buku yang disimpan pada server harus memiliki struktur seperti contoh di bawah ini:

<img width="690" height="464" alt="image" src="https://github.com/user-attachments/assets/4b28bf16-9c50-4901-9d09-30798f91828f" />

Properti yang ditebalkan diolah dan didapatkan di sisi server. Berikut penjelasannya:

id : nilai id haruslah unik. Untuk membuat nilai unik, Anda bisa memanfaatkan nanoid.
finished : merupakan properti boolean yang menjelaskan apakah buku telah selesai dibaca atau belum. Nilai finished didapatkan dari observasi pageCount === readPage.
insertedAt : merupakan properti yang menampung tanggal dimasukkannya buku. Anda bisa gunakan new Date().toISOString() untuk menghasilkan nilainya.
updatedAt : merupakan properti yang menampung tanggal diperbarui buku. Ketika buku baru dimasukkan, berikan nilai properti ini sama dengan insertedAt.

Server harus merespons gagal bila:

Client tidak melampirkan properti name pada request body. Bila hal ini terjadi, maka server akan merespons dengan:
Status Code : 400
Response Body:

<img width="609" height="140" alt="image" src="https://github.com/user-attachments/assets/d6c4820a-562a-4ee9-839f-468925d9978e" />

Client melampirkan nilai properti readPage yang lebih besar dari nilai properti pageCount. Bila hal ini terjadi, maka server akan merespons dengan:
Status Code : 400
Response Body:

<img width="609" height="140" alt="image" src="https://github.com/user-attachments/assets/10eafaff-ffa8-49fc-b834-d08521287b75" />

Bila buku berhasil dimasukkan, server harus mengembalikan respons dengan:

Status Code : 201
Response Body:

<img width="623" height="232" alt="image" src="https://github.com/user-attachments/assets/28e1eaa7-50c7-4b33-82f8-1f7406df5b6b" />

Kriteria 4 : API dapat menampilkan seluruh buku
API yang Anda buat harus dapat menampilkan seluruh buku yang disimpan melalui route:

Method : GET
URL: /books

Server harus mengembalikan respons dengan:

Status Code : 200
Response Body:

<img width="623" height="494" alt="image" src="https://github.com/user-attachments/assets/2649ed5d-3dda-406c-9e1f-862dc428286b" />

Jika belum terdapat buku yang dimasukkan, server bisa merespons dengan array books kosong.

<img width="672" height="199" alt="image" src="https://github.com/user-attachments/assets/9ffb3ae0-73b2-4ab3-bab4-da5306c706cd" />

Kriteria 5 : API dapat menampilkan detail buku
API yang Anda buat harus dapat menampilkan seluruh buku yang disimpan melalui route:

Method : GET
URL: /books/{bookId}

Bila buku dengan id yang dilampirkan oleh client tidak ditemukan, maka server harus mengembalikan respons dengan:

Status Code : 404
Response Body:

<img width="635" height="130" alt="image" src="https://github.com/user-attachments/assets/6134a6ee-94b9-4695-8618-7f472ddb50ea" />

Bila buku dengan id yang dilampirkan ditemukan, maka server harus mengembalikan respons dengan:

Status Code : 200
Response Body:

<img width="635" height="485" alt="image" src="https://github.com/user-attachments/assets/db0c6dc6-9989-419b-85df-d885c28e963a" />

Kriteria 6 : API dapat mengubah data buku
API yang Anda buat harus dapat mengubah data buku berdasarkan id melalui route:

Method : PUT
URL : /books/{bookId}
Body Request:

<img width="635" height="315" alt="image" src="https://github.com/user-attachments/assets/96febce6-709c-4bc1-9a9c-a41afc11bfc4" />

Server harus merespons gagal bila:

Client tidak melampirkan properti name pada request body. Bila hal ini terjadi, maka server akan merespons dengan:
Status Code : 400
Response Body:

<img width="592" height="163" alt="image" src="https://github.com/user-attachments/assets/68fdc66b-58ce-4f37-b0fd-dfac6835e018" />

Client melampirkan nilai properti readPage yang lebih besar dari nilai properti pageCount. Bila hal ini terjadi, maka server akan merespons dengan:
Status Code : 400
Response Body:

<img width="592" height="163" alt="image" src="https://github.com/user-attachments/assets/10459fae-d90b-41f7-8fce-424390778257" />

Id yang dilampirkan oleh client tidak ditemukkan oleh server. Bila hal ini terjadi, maka server akan merespons dengan:
Status Code : 404
Response Body:

<img width="592" height="133" alt="image" src="https://github.com/user-attachments/assets/9091c7b9-ba7d-4dc0-93ee-5205403379b1" />

Bila buku berhasil diperbarui, server harus mengembalikan respons dengan:

Status Code : 200
Response Body:

<img width="592" height="133" alt="image" src="https://github.com/user-attachments/assets/e4d5e96e-7e53-42b1-94ca-5df9f345f14e" />

Kriteria 7 : API dapat menghapus buku
API yang Anda buat harus dapat menghapus buku berdasarkan id melalui route berikut:

Method : DELETE
URL: /books/{bookId}
Bila id yang dilampirkan tidak dimiliki oleh buku manapun, maka server harus mengembalikan respons berikut:

Status Code : 404
Response Body:

<img width="592" height="133" alt="image" src="https://github.com/user-attachments/assets/d4b2fb29-fb68-430b-9392-824ec39dbc26" />

Bila id dimiliki oleh salah satu buku, maka buku tersebut harus dihapus dan server mengembalikan respons berikut:

Status Code : 200
Response Body:

<img width="592" height="133" alt="image" src="https://github.com/user-attachments/assets/c53c7e97-5aa8-419e-95ed-2d0c125716f0" />

