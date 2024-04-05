### Scan Surprise
* ssh -p 49849 ctf-player@atlas.picoctf.net
* 83dcefb7
* Sau khi vào được máy chủ của bên pico thì mình thấy ngay một hình ảnh mã qr, sau khi ls thì có một file là flag.png nên mình đoán ảnh QR ở đầu chính là file này

![Screenshot 2024-04-05 121331](https://github.com/LDV-SpaceK/picoCTF2024/assets/151914246/3ebfad66-5996-4938-86c9-763e73d9c3fb)

* Quét QR và mình tìm được flag, flag được encode trong ảnh QR

![ảnh](https://github.com/LDV-SpaceK/picoCTF2024/assets/151914246/57eed1b2-6287-4ef7-98cb-8202fae3e2c5)

`Flag: picoCTF{p33k_@_b00_3f7cf1ae}`

### Verify
* ssh -p 51194 ctf-player@rhea.picoctf.net
* 83dcefb7
* mình tải file challenge.zip đề bài cho thì có file checksum.txt là chứa một mã băm, một file decrypt.sh và một folder chứa các file có nội dung

![Screenshot 2024-04-05 125658](https://github.com/LDV-SpaceK/picoCTF2024/assets/151914246/ac93a485-0699-4ff6-bf30-1cea1e2892cf)

* file decrypt.sh này chứa lệnh ``openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in "/home/ctf-player/drop-in/$file_name" -k picoCTF`` sử dụng để decrypt bằng aes với độ rộng bit là 256 mode CBC với một file truyền vào
* ssh vào máy chủ bên đó, mình đoán là checksum.txt sẽ chứa mã băm của một file nào đó trong folder file nên mình đã sử dụng lệnh ``sha256sum files/* | grep $(cat checksum.txt)`` để băm các file trong folder file và so sánh với checksum.txt

![Screenshot 2024-04-05 131324](https://github.com/LDV-SpaceK/picoCTF2024/assets/151914246/57089a58-d54a-474c-b35d-28f9dc943e8c)

* sau khi tìm được file chứa nội dung giống checksum.txt thì mình sử dụng decypt.sh để decrypt file này thì mình được flag

`Flag: picoCTF{trust_but_verify_c6c8b911}`

### 
