# Reflection

Nama: Emir Mohamad Fathan <br>
NPM: 2206081982 <br>

<hr>

1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?

Pada unary RPC, client mengirimkan single request ke server lalu server mengembalikan single reponse juga. Pada server streaming RPC, client mengirimkan single request ke server lalu server mengembalikan stream response yang berarti bisa banyak response sampai berhenti. Sedangkan bi-directional streaming RPC, client mengirimkan stream request ke server lalu server juga mengembalikan stream response. Pemakaian dari ketiga jenis RPC tersebut tergantung dari komunikasi antara client dan server pada aplikasi yang dibuat. Apakah komunikasinya membutuhkan response dan request yang serentak dan berkelanjutan atau tidak.

2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?

Untuk keamanan authentication, bisa menggunakan Token untuk memverifikasi client yang melakukan request ke server. Server side sudah menyimpan indentitas token dari client. Contoh strategi token yang biasanya digunakan adalah JWT. Untuk keamanan authorization, contohnya menggunakan role access control, yang mana tiap user memiliki permission yang berbeda dan aplikasi akan mengotorisasi sesuai permission tersebut. Untuk data encryption menggunakan End-to-End encryption.

3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?

Client dan server saling mengirimkan request dan response secara streaming pada bidirectional streaming di gRPC. Maka tantangannya adalah bagaimana mengatur streaming tersebut berjalan, selain itu juga bagaimana mengatur thread safety-nya karena paralel.

4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?

- Advantages: RecieverStream membuat implementasi streaming response menjadi lebih simple dan sederhana.
- Disadvantages: RecieverStream me-limit fleksibilitas dari kode atau program rust.

5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?

Beberapa contoh cara yang bisa diterapkan ke kode agar lebih terstruktur untuk Rust gRPC adalah: Memisah codebase menjadi beberapa komponen standar berdasarkan kegunaan dari kode tersebut (mirip seperti SRP pada SOLID principle), menggunakan implementation class agar reusable, dan menggunakan beberapa library yang sudah ada untuk meningkatkan maintainability.

6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?

Agar MyPaymentService dapat meng-handle proses payment yang lebih kompleks, kita dapat menambahkan logic baru seperti validation sebagai error handling.

7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?

Penggunaan gRPC memberikan dampak yaitu membuat sederhana interaksi antar sistem tanpa menggunakan HTTP method secara manual. Selain itu juga, gRCP mendukung salah satu software architechture yaitu microservice.

8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?

HTTP/2 memungkinkan untuk menerima dari satu request ke server mengembalikan banyak response data sekaligus. Namun, implementasinya menjadi kompleks tidak seperti HTTP/1.

9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?

Pada REST API, client mengirimkan request ke server dan client menunggu response dari server. Hal ini menggambarkan bahwa REST API adalah sinkronus, karena harus menunggu. Sedangkan gRPC menerapkan bidirectional streaming dimana antara client dan server berkomunikasi secara streaming asinkronus.

10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?

Schema-based approach dari gRPC, yaitu menggunakan protocol buffers, dapat menguntungkan program karena memberikan data serialization yang lebih efisien, interoperability, dan versioning support.