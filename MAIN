from mnemonic import Mnemonic
from web3 import Web3
from bip32utils import BIP32Key

def generate_mnemonic():
    mnemo = Mnemonic("english")
    mnemonic_words = mnemo.generate(strength=128)
    return mnemonic_words

def derive_ethereum_address(mnemonic_phrase):
    # Derive the Ethereum address from the mnemonic phrase
    w3 = Web3()
    seed = Mnemonic.to_seed(mnemonic_phrase)
    root_key = BIP32Key.fromEntropy(seed)
    path = "m/44'/60'/0'/0/0"  # Ethereum derivation path
    child_key = root_key.ChildKey(path)
    eth_address = w3.toChecksumAddress(child_key.Address())
    return eth_address

def derive_bitcoin_address(mnemonic_phrase):
    # Derive the Bitcoin address from the mnemonic phrase
    seed = Mnemonic.to_seed(mnemonic_phrase)
    root_key = BIP32Key.fromEntropy(seed)
    path = "m/44'/0'/0'/0/0"  # Bitcoin derivation path
    child_key = root_key.ChildKey(path)
    btc_address = child_key.Address()
    return btc_address

if __name__ == "__main__":
    mnemonic_phrase = generate_mnemonic()
    print("Generated 12-word mnemonic phrase:")
    print(mnemonic_phrase)

    eth_address = derive_ethereum_address(mnemonic_phrase)
    btc_address = derive_bitcoin_address(mnemonic_phrase)

    print(f"Ethereum Address: {eth_address}")
    print(f"Bitcoin Address: {btc_address}")
