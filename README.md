# Scalable Moodle on Azure
*This repository is forked from [https://github.com/Azure/Moodle](https://github.com/Azure/Moodle)*

## Stack Architecture
![network_diagram](images/custom-stack.png "Diagram of deployed stack")

Resource yang digunakan pada template ini antara lain:
- [Virtual Network](https://azure.microsoft.com/en-us/services/virtual-network).
- Controller [Virtual Machine](https://azure.microsoft.com/en-us/services/virtual-machines), VM utama, untuk menjalankan cron dan menghandle log.
- [Virtual Machine Scale Sets](https://azure.microsoft.com/en-us/services/virtual-machine-scale-sets), set Virtual Machine yang dapat diskalakan otomatis saat traffic tinggi, tempat nginx web server berjalan dan diakses pengguna.
- [Load Balancer](https://azure.microsoft.com/en-us/services/load-balancer), menyeimbangkan traffic pada VMSS.
- [Azure File Storage](https://azure.microsoft.com/en-us/services/storage/files), tempat penyimpanan file aplikasi moodle (scripts, config, dll) yang akan dishare ke VMSS dan Controller VM.
- [Azure Database for MySQL](https://azure.microsoft.com/en-us/services/mysql).
- [Azure Blob Storage](https://azure.microsoft.com/en-us/services/storage/blobs), untuk plugin moodle ObjectFS, untuk menyimpan file site data (gambar, dokumen, dll) pada blob storage.

## Deployment Prerequisites
- Siapkan SSH protocol 2 (SSH-2) RSA public-private key pairs dengan panjang minimum 2048 bits, public key diperlukan pada parameter template.

- (Opsional) SSL (TLS) certificate dapat digunakan jika ingin menggunakan HTTPS server, informasi lebih lanjut pada [instruksi ssl](https://github.com/kmhalpin/Moodle/blob/master/docs/SslCert.md).

## Deployment
Sebagian besar konfigurasi sudah ditentukan untuk mencapai biaya dan sumber daya yang cukup. Klik tombol dibawah untuk mulai mendeploy dan mengisi parameter.

[![Deploy to Azure](https://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fkmhalpin%2FMoodle%2Fmaster%2Fazuredeploy-custom.json)