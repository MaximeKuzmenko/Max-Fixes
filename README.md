# Max-Fixes
Max Fixes is a project aimed at cryptocurrency enthusiasts, particularly those focused on recording trades and maximizing profits. This repository provides resources, tools, and scripts tailored for individuals engaged in managing and optimizing their cryptocurrency trading activities.
from solana.rpc.api import Client
from solana.transaction import Transaction
from solders.keypair import Keypair
import base64
import time

# Підключення до Solana Mainnet
solana_client = Client("https://api.mainnet-beta.solana.com")

# Ваш приватний ключ (експортований з Phantom)
PRIVATE_KEY = "ВСТАВТЕ_ВАШ_ПРИВАТНИЙ_КЛЮЧ"

# Завантаження ключа
def load_keypair(private_key: str):
    keypair = Keypair.from_bytes(base64.b64decode(private_key))
    return keypair

wallet = load_keypair(PRIVATE_KEY)

# Адреса контракту для мінту NFT (від колекції)
NFT_CONTRACT_ADDRESS = "АДРЕСА_КОНТРАКТУ"

# Функція для мінту NFT
def mint_nft(count: int):
    for i in range(count):  # Повторюємо стільки разів, скільки потрібно
        try:
            print(f"Мінт NFT #{i+1}")
            transaction = Transaction()
            transaction.add(
                # Тут ваша інструкція для мінту
                ("<INSTRUCTION>")
            )
            # Відправка транзакції
            tx = solana_client.send_transaction(transaction, wallet)
            print(f"Transaction {i+1} success: {tx}")
            time.sleep(1)  # Затримка між мінтами, щоб не перевантажити мережу
        except Exception as e:
            print(f"Error at mint {i+1}: {e}")

# Виконання мінту
NUMBER_OF_NFTS = 5  # Скільки NFT замінтити
mint_nft(NUMBER_OF_NFTS)
