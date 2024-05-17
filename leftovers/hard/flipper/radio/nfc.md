# NFC - 13.56 MHz

NFC stands for Near Field Communication. It's a short-range (1-4 cm) wireless communication technology. NFC operates at frequencies of 13.56 MHz and allows for peer-to-peer communication, as well as communication between an NFC-enabled device and an NFC tag.
It is a subset of HF RFID technology but has its own standards and protocols tailored for short-range communication and peer-to-peer data exchange.

### Operating modes

- **Reader/Writer mode:** NFC-enabled devices can read data from and write data to NFC tags or other NFC-enabled devices.
- **Peer-to-Peer mode:** Two NFC-enabled devices can communicate with each other to exchange data. This mode is commonly used for tasks such as sharing files, contact information, or initiating wireless payments.
- **Card Emulation mode:** An NFC-enabled device can emulate an NFC card, allowing it to act as a contactless smart card for applications like mobile payments or ticketing.

### Data transfer

- **Text:** Sending and receiving plain text data.
- **URLs:** Opening URLs stored on NFC tags or shared between devices.
- **Contact Information:** Exchanging contact details such as names, phone numbers, and email addresses.
- **Files:** Sharing files such as photos, videos, or documents between NFC-enabled devices.

## NFC Card

An NFC card is a transponder that operates at 13.56 MHz and has a unique number (UID) as well as a part of rewritable memory for storing data. Depending on the card type, memory can be segmented into sectors, pages, applications, and more. When near a reader, NFC cards transmit the requested data.

### NFC cards type A

#### MIFARE Classic

MIFARE is a series of integrated circuit (IC) chips used in contactless smart cards and proximity cards. 

Flipper Zero can read 
- MIFARE Classic 1K
- MIFARE Classic 4K
- MIFARE Classic Mini
To read data stored in sectors, Flipper Zero has to find all 32 keys for 16 sectors (MIFARE Classic 1K), 80 keys for 40 sectors (MIFARE Classic 4K), and 10 keys for 5 sectors (MIFARE Classic Mini). For that, Flipper Zero uses keys from the **System dictionary**

