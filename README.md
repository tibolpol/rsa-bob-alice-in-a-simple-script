# RSA Bob + Alice dans un simple script
```
bob_xirap(1)                                            bob_xirap(1)

NOM
        bob_xirap -  Échange de messages chiffrés basé sur RSA.

SYNOPSIS
        alice_xirap -h | -c | -d | -n | -l | -b | -p | -a [command args ... ]
        bob_xirap   -h | -c | -d | -n | -l

DESCRIPTION
        Échange de messages chiffrés basé sur RSA.

        Le présent script se nomme bob_xirap formé du radical "bob"
        et de "xirap" distinctif de la clé.

        Alice peut signer et déchiffrer, Bob peut vérifier et chiffrer.

        Si le message est inférieur à 49 octets, le chiffré est du
        texte manipulable, sinon le chiffré est binaire.

OPTIONS
        -h
            Aide

        -b
            Générer Bob

        -c
            Chiffrer ou signer l'entrée standard.

        -d
            Déchiffrer ou vérifier l'entrée standard.

            Exemples :

            Signer un message avec Alice et le vérifier avec Bob :

            [message] | alice_xirap -c | bob_xirap -d

            Chiffrer un message avec Bob et le déchiffrer avec Alice :

            [message] | bob_xirap -c | alice_xirap -d

        -a  [command args ...]
            Ouvrir la clé privée Alice et l'utiliser dans un sous-shell
            sans devoir saisir à nouveau la passphrase.

            Exemple :

            alice_xirap -a # passphrase demandée
            alice_xirap -d # passphrase non demandée
            logout # Sortie du sous-shell
            alice_xirap -d # passphrase demandée

        -l
            Empreinte de la clé

        -p
            Changer la passphrase de Alice

        -n
            Générer Alice et Bob avec une nouvelle clé privée et le
            distinctif formé du premier mot du digest.


STATUT FINAL
        0 SUCCESS
            Succès.

        4 ERROR
            Une erreur est signalée.

VOIR AUSSI
        ssh-keygen(1) openssl-pkeyutl(1) mcrypt(1)

  https://github.com/tibolpol/rsa-bob-alice-in-a-simple-script

bob_xirap(1)                                            bob_xirap(1)
```
# Mode d'emploi

Télécharger le script et lancer `bob_xirap -n` pour créer `alice` avec sa propre clé privée.

Selon ses préférences, renommer les scripts obtenus, par exemple `alice_myname` et `bob_myname` en respectant la nomenclature : `bob` implémente la clé publique, `alice` implémente la clé privée, suivi du caractère `_` et d'un nom significatif de la clé privée.

Il est aussi suggéré d'éditer le script `alice` et d'y insérer une clé privée existante de son choix, puis de regénérer `bob`.

Les interlocuteurs ayant reçu une copie de `bob` peuvent déchiffrer/vérifier les messages de `alice`, et chiffrer des messages exclusivement destinés à `alice`.

Ils peuvent également générer leur propre `alice` et distribuer à leur tour une copie de `bob`.
