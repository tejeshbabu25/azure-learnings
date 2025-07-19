# Encryption in Storage account

1. Encryption in Transit: 

    What it is: Encryption applied to data as it moves between systems or networks. 

    Why it's important: Protects data from interception or modification during transmission, especially over public networks. 

    Examples:
        TLS/SSL (HTTPS): Encrypts communication between web browsers and servers. 
        IPsec: Encrypts network traffic at the IP layer. 
        SSH: Encrypts remote access to servers. 

    How it works: Uses encryption protocols (like TLS/SSL) to encrypt data before transmission and decrypt it upon arrival. 
    
    Benefits: Ensures data confidentiality and integrity during transmission. 

2. Encryption at Rest 

    What it is:
    Encryption applied to data stored on physical or digital media like hard drives, databases, or cloud storage. 

    Why it's important:
    Protects data from unauthorized access if storage devices are lost, stolen, or compromised. 

    Examples:
        Full disk encryption on a laptop. 
        Database encryption. 
        Cloud storage encryption. 

    How it works:
    Uses cryptographic algorithms (like AES) to convert data into an unreadable format, requiring a key to decrypt. 

    Key Management:
    Securely managing encryption keys is vital for effective at-rest encryption. 

    2 options on portal :
        a. Microsoft-managed keys (MMK) - deafult and handled by Microsoft
        b. Customer-managed keys (CMK) - depending on Org this is used
            - To use this option we have to create a key valut/ managed HSM

Key Differences:
    Data State: At rest, data is stored. In transit, it's actively moving. 
    Focus: At-rest encryption protects stored data, while in-transit encryption protects data during transmission. 
    Implementation: At-rest encryption involves encrypting storage media, while in-transit encryption involves encrypting network traffic. 
    In summary, both encryption at rest and in transit are essential for comprehensive data security. At-rest encryption safeguards stored data, while in-transit encryption protects data as it travels across networks. 