

# Identity Manager - Keyrock

[![FIWARE Security](https://img.shields.io/badge/FIWARE-Security-ff7059.svg?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABsAAAAVCAYAAAC33pUlAAAABHNCSVQICAgIfAhkiAAAA8NJREFUSEuVlUtIFlEUx+eO+j3Uz8wSLLJ3pBiBUljRu1WLCAKXbXpQEUFERSQF0aKVFAUVrSJalNXGgmphFEhQiZEIPQwKLbEUK7VvZrRvbr8zzjfNl4/swplz7rn/8z/33HtmRhn/MWzbXmloHVeG0a+VSmAXorXS+oehVD9+0zDN9mgk8n0sWtYnHo5tT9daH4BsM+THQC8naK02jCZ83/HlKaVSzBey1sm8BP9nnUpdjOfl/Qyzj5ust6cnO5FItJLoJqB6yJ4QuNcjVOohegpihshS4F6S7DTVVlNtFFxzNBa7kcaEwUGcbVnH8xOJD67WG9n1NILuKtOsQG9FngOc+lciic1iQ8uQGhJ1kVAKKXUs60RoQ5km93IfaREvuoFj7PZsy9rGXE9G/NhBsDOJ63Acp1J82eFU7OIVO1OxWGwpSU5hb0GqfMydMHYSdiMVnncNY5Vy3VbwRUEydvEaRxmAOSSqJMlJISTxS9YWTYLcg3B253xsPkc5lXk3XLlwrPLuDPKDqDIutzYaj3eweMkPeCCahO3+fEIF8SfLtg/5oI3Mh0ylKM4YRBaYzuBgPuRnBYD3mmhA1X5Aka8NKl4nNz7BaKTzSgsLCzWbvyo4eK9r15WwLKRAmmCXXDoA1kaG2F4jWFbgkxUnlcrB/xj5iHxFPiBN4JekY4nZ6ccOiQ87hgwhe+TOdogT1nfpgEDTvYAucIwHxBfNyhpGrR+F8x00WD33VCNTOr/Wd+9C51Ben7S0ZJUq3qZJ2OkZz+cL87ZfWuePlwRcHZjeUMxFwTrJZAJfSvyWZc1VgORTY8rBcubetdiOk+CO+jPOcCRTF+oZ0okUIyuQeSNL/lPrulg8flhmJHmE2gBpE9xrJNkwpN4rQIIyujGoELCQz8ggG38iGzjKkXufJ2Klun1iu65bnJub2yut3xbEK3UvsDEInCmvA6YjMeE1bCn8F9JBe1eAnS2JksmkIlEDfi8R46kkEkMWdqOv+AvS9rcp2bvk8OAESvgox7h4aWNMLd32jSMLvuwDAwORSE7Oe3ZRKrFwvYGrPOBJ2nZ20Op/mqKNzgraOTPt6Bnx5citUINIczX/jUw3xGL2+ia8KAvsvp0ePoL5hXkXO5YvQYSFAiqcJX8E/gyX8QUvv8eh9XUq3h7mE9tLJoNKqnhHXmCO+dtJ4ybSkH1jc9XRaHTMz1tATBe2UEkeAdKu/zWIkUbZxD+veLxEQhhUFmbnvOezsJrk+zmqMo6vIL2OXzPvQ8v7dgtpoQnkF/LP8Ruu9zXdJHg4igAAAABJRU5ErkJgggA=)](https://www.fiware.org/developers/catalogue/)
[![License: MIT](https://img.shields.io/github/license/ging/fiware-idm.svg)](https://opensource.org/licenses/MIT)
[![Documentation](https://img.shields.io/readthedocs/fiware-idm.svg)](https://fiware-idm.readthedocs.io/en/latest/)
[![Docker badge](https://img.shields.io/docker/pulls/fiware/idm.svg)](https://hub.docker.com/r/fiware/idm/)
[![Support badge]( https://img.shields.io/badge/support-sof-yellowgreen.svg)](http://stackoverflow.com/questions/tagged/fiware)

* [Introduction](#introduction)
    + [Software requirements](#software-requirements)
* [How to Build & Install](#how-to-build--install)
    + [Docker](#docker)
* [Changes Introduced in 7.x](#changes-introduced-in-7x)
* [API Overview](#api-overview)
* [Advanced Documentation](#advanced-documentation)
* [License](#license)

---



## Introduction

This project is part of [FIWARE](http://fiware.org). You will find more information about this FIWARE GE [here](https://catalogue-server.fiware.org/enablers/identity-management-keyrock).

- You will find the source code of this project in GitHub [here](https://github.com/ging/fiware-idm)
- You will find the documentation of this project in Read the Docs [here](https://fiware-idm.readthedocs.io/en/latest/)

Welcome to the main repository for the UPM's implementation of the FIWARE Identity Management Generic Enabler. Thanks to this component and together with PEP Proxy and Authorization PDP GEs, you will add authentication and authorization security to your services and applications.


### Software requirements
This GE is based on a javascript environment and SQL databases. In order to run the identity manager the following requirements must be installed:

 - node.js
 - npm
 - mysql-server (^5.7)
 - build-essential


## How to Build & Install

 1. Clone Proxy repository:

```console
git clone https://github.com/ging/fiware-idm.git
```

 2. Install the dependencies:

```console
cd fiware-idm/
npm install
```

 3. Duplicate config.template in config.js:

```console
cp config.js.template config.js
```

 4. Configure data base access credentials:

```javascript
config.database = {
    host: 'localhost',           // default: 'localhost'
    password: 'idm',             // default: 'idm'
    username: 'root',            // default: 'root'
    database: 'idm',             // default: 'idm'
    dialect: 'mysql'             // default: 'mysql'
}
```

 5. To configure the server to listen HTTPs requests, generate certificates OpenSSL and configure config.js:

```console
./generate_openssl_keys.sh
```

```javascript
config.https = {
    enabled: true, 		//default: 'false'
    cert_file: 'certs/idm-2018-cert.pem',
    key_file: 'certs/idm-2018-key.pem',
    port: 443
}
```

 6. Create database, run migrations and seeders:

```console
npm run-script create_db
npm run-script migrate_db
npm run-script seed_db
```

 7. Start server with admin rights (server listens in 3000 port by
    default or in 443 if HTTPs is enabled).

```console
sudo npm start
```

You can test the Identity manager using the default user:
 - Email: `admin@test.com`
 - Password: `1234`


### Docker

We also provide a Docker image to facilitate you the building of this GE.

- [Here](https://github.com/ging/fiware-idm/tree/master/extras/docker) you will find the Dockerfile and the documentation explaining how to use it.
- In [Docker Hub](https://hub.docker.com/r/fiware/idm/) you will find the public image.


## Changes Introduced in 7.x
They biggest change introduced in 7.x is that the identity manager no longer depends on Openstack components Keystone and Horizon. Now is fully implemented in Node JS. Another remarkable changes have been made:

 1. A driver has been implemented in order to make authentication against another database different from the default one.+
 2. The appearance of the web portal can be easily modified though configurable themes.
 3. Now users don't need to switch session in order to create an application that will belong to an organization.
 4. Permissions of an application can be edited or deleted.


## API Overview
Several resources could be managed through the API like users, applications or organizations. Further information could be found in the [API section](http://fiware-idm.readthedocs.org/en/latest/api/#def-apiIdm).

Finally, one of the main uses of this Generic Enabler is to allow developers to add identity management (authentication and authorization) to their applications based on FIWARE identity. This is posible thanks to [OAuth2](https://oauth.net/2/) protocol. For more information check the [OAuth2 API](http://fiware-idm.readthedocs.org/en/latest/api/#def-apiOAuth).


## Advanced Documentation

- [How to run tests](http://fiware-idm.readthedocs.org/en/latest/admin_guide#end-to-end-testing)
- [User & Programmers Manual](http://fiware-idm.readthedocs.org/en/latest/user_guide/)
- [Installation & Administration Guide](http://fiware-idm.readthedocs.org/en/latest/admin_guide/)

---

## License

[MIT](LICENSE) © 2018 Universidad Politécnica de Madrid.

