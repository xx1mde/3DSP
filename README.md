# 3DSP
3 Diffie-Hellman with signed prekey (X3DH strict modification)


Bob и Alice имеют долгосрочную пару x448 ключей. На сервере у каждого пользователя хранятся 100 prekey. Основное отличие от X3DH - нет SPK и каждый prekey подписывается приватным ключом из долгосрочной пары.

Создание root_key сессии:

Сервер отдает публичный долгосрочный ключ Bob и один signed prekey. Alice создает свою ephemeral x448 пару, проверяет подпись Bob prekey и начинает тройную волну Diffie-Hellman.

1. DH(Alice_private_long-term_key, Bob_public_long-term_key)
2. DH(Alice_private_ephemeral_key, Bob_public_prekey)
3. DH(Alice_private_ephemeral_key, Bob_public_long-term_key)

Далее по алгоритму X3DH + Double Ratchet.
