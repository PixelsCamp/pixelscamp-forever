# Pixels Camp Forever!
_Or... been there, done that, got the t-shirt!_

After being [postponed](https://blog.pixels.camp/pixels-camp-postponed-fddece7ccc4c) three weeks before it was due to happen in March, Pixels Camp v4.0 was [cancelled](https://blog.pixels.camp/) in September due to the still ongoing COVID-19 pandemic and the uncertainty around it for the forseeable future. 😔

But the pixels community is still out there, and lacking a place to gather this year doesn't mean we don't yearn for ways to pick each other out of the crowd (metaphorically speaking, of course). **Fancy a free t-shirt?** 🙂

## What?

We have special **_Pixels Camp Forever_** t-shirts ready to be printed and shipped to the first **100** campers that meet the following criteria:

  1. Was **approved** for Pixels Camp v4.0 or any of the previous editions;
  2. Shows some **public proof** that they're a proud member of the pixels community.

## How?

You're probably thinking what we mean by "public proof"...

It means posting a **photo or video** with the hashtags `#pixelscamp` and `#forever` **on social media**. The photo (or video) needs to show you're proud to be part of this community. You can use your imagination or pick one example from this list:

  * A photo of yourself wearing some item of Pixels Camp swag in public;
  * A photo of yourself with a Pixels Camp venue visible in the background (LX Factory warehouse or Carlos Lopes pavillion);
  * A photo from any Pixels Camp edition where you happen to appear (identifying yourself in the photo if not alone);
  * A photo of some item or location related with one of the Pixels Camp v4.0 sponsors, thanking them for supporting us (they deserve it).
  * A nostalgic recollection of having participated in a challenge (must be illustrated in some way, _pics or it didn't happen_);

## What social media?

Well, [Twitter](https://twitter.com/pixelscamp) is our primary social network for event updates, but we understand you may not be active on Twitter and may prefer to post somewhere else and that's fine. You may have to attach a screenshot to the GitHub issue though. 🤔

Don't forget the `#pixelscamp` `#forever` hashtags!

## GitHub issue?

Glad you asked...

After posting on social media, open a new [issue](https://github.com/PixelsCamp/pixelscamp-forever/issues/new/choose) in this repository using the **same GitHub account** as you used for Pixels Camp. This is how we will keep track of shipping, and also the final proof that you're `#oneofus`.

The issue template is pretty straightforward except for the shipping address part. The world doesn't need to know your real name and address, and we're a bunch of nerds, so you'll have to encrypt it in a way only we can decrypt it, which means **asymmetric cryptography** is involved: 💥🤓

  1. Paste this certificate (our public key) into a file called `public.crt`:
```
-----BEGIN CERTIFICATE-----
MIIDBzCCAe+gAwIBAgIJANaoAW/x51PhMA0GCSqGSIb3DQEBCwUAMBoxGDAWBgNV
BAMMD29yZ0BwaXhlbHMuY2FtcDAeFw0yMDA5MTAwODU0MjFaFw0zMDA5MDgwODU0
MjFaMBoxGDAWBgNVBAMMD29yZ0BwaXhlbHMuY2FtcDCCASIwDQYJKoZIhvcNAQEB
BQADggEPADCCAQoCggEBANWNaLI2jtGMszaVJlFsk9NlxXJ6r7F8t1LNLjJyyKLO
OcP4ygIE4YHZkLEQBPKLzRrxRF3gzmyJtXmBfCMo2pJvyz7KRu+MkTuDz8J/VN56
tUyqSAo3Sn8rr2OThyESXP8dQXwoadqzChP20bgk5DEyI0IyZLAt3DW1XCZxFVaw
UquMQhEykzmnFnRu5nJmZMZ9VbEdbvTnnU6RzU6eJe7Yy8niFa/VLBjHXKHQq2cU
WHUvm2hVYMcz2KU/ieV6RFGlY7lwCHmAAG3R7nvxUHfQ+sIZeA9oQbWrit4wBZeH
TjxrpZcmqkR5WOPWw/UnIiGg7Pu8+5AJHLKwTR11ws0CAwEAAaNQME4wHQYDVR0O
BBYEFBcoa0PcxG7wA/dZJ/zGwT4YhmTbMB8GA1UdIwQYMBaAFBcoa0PcxG7wA/dZ
J/zGwT4YhmTbMAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQELBQADggEBAGFUFzId
4uGYRcU2BNt1CMqj5jdJT715jH5J8mb8P12qmFd3S000Lxq0E2XECV9YmAB4dJco
89hcvscGZi+n+WPJaNckB4w/iBPIuPc83rQoPk6OxhmBM+COUdC/TdMc9S2I5Cxs
ayM8N1NQoApj7RQQMf8+BsqLeA/vSLskxzvhiZaE5Etp36S0B/q4gbL216OLx1Fl
0fDhdePlEdifpiA8Dw3qGoCNOoS9G/I4KVlKhtUpBTiUgxetOoo5gvuo8XiFT26n
vQWnNDATAjVDCUjocVvOKsr+w5JGvlxPBUgD4+To2Ugc22doo8nwOjKwtZQPfVC6
fzvGXCdMeQqNMAM=
-----END CERTIFICATE-----
```
  2. Write your name and shipping address in a file called `file.txt`;
  3. Encrypt `file.txt` with a random 256-bit key unique to you:
```
openssl rand -out random.key 32
openssl aes-256-cbc -e -in file.txt -pass file:random.key | base64 > file.enc
```
  4. Encrypt the random 256-bit key with our public key:
```
openssl rsautl -encrypt -inkey public.crt -certin -in random.key | base64 > random.enc
rm -f random.key
```
  5. Place the contents of `file.enc` and `random.enc` in the _shipping information_ and _shared key_ sections of the GitHub issue.

**Note:** The shipping address you give us will only be used to send you the t-shirt, we won't store it in our database.

On our side we'll use our private key (which only a couple of people have access to) with the following commands to see your address:
```
base64 -d random.enc | openssl rsautl -decrypt -inkey private.key -out decryption.key
base64 -d file.enc | openssl aes-256-cbc -d -pass file:decryption.key
```

## How do I know I've won?

When we accept your submission we'll let you know in the GitHub issue itself.

## Important note!

Due to logistics constraints, we're only able to ship to within the portuguese territory (mainland and islands). 📦 🚐 🇵🇹

--<br>
The Pixels Camp Organization, 2020
