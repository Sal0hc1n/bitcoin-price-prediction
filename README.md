# Bitcoin Price Predicion

This repo is a dockerized implementation of the code of [stavos0](https://github.com/stavros0/bitcoin-price-prediction) which is based on the [Bayesian Regression and Bitcoin](https://arxiv.org/pdf/1410.1231.pdf) paper.

## Structure

### Docker Compose

This project uses **Docker-compose** which is a tool for defining and running complex applications with Docker.
With Compose, you define a multi-container application in a single file, then spin your application up in a single command which does everything that needs to be done to get it running, including put them in the same network and make them communicate.

#### Usage

To make the project up and running go to the project main folder into the terminal and type:

 `$sudo docker-compose up`

**NOTE**: If you make changes to the code you have to use `$sudo docker-compose rebuild` and then `$sudo docker-compose up`

It will spin up 4 containers:

##### MongoDB

[MongoDB](https://www.mongodb.com/what-is-mongodb) is a document database that stores data in flexible JSON-like document, meaning fields can vary from document to document and data structure can be changed over time

##### Mongo Express

[Mongo Express](https://github.com/mongo-express/mongo-express) is a Web-based MongoDB admin interface written with Node.js, Express and Bootstrap3.

it can be accessed through <http://swarm-ip:8081>, <http://localhost:8081>, or <http://host-ip:8081> (as appropriate).

### Screenshots

| Home Page                                                      | Database View                                                                  | Collection View                                                     | Editing A Document                                   |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------- | ---------------------------------------------------- |
| ![Home Page showing databases](http://i.imgur.com/XiYhblA.png) | ![Viewing collections & buckets in a database](http://i.imgur.com/XWcIgY1.png) | ![Viewing documents in a collection](https://imgur.com/UmGSr3x.png) | ![Editing a document](https://imgur.com/lL38abn.png) |

##### OKcoin

Daemon that retrives **BTC Price**, **Ask** and **Bid** every 10 seconds from the [OKcoin](https://www.okcoin.com/) exchange.

##### Millionaire

Example container intended for tinkering and experimenting only, which will only display the ammount of bitcoin you will have in your bank account after trading with this way of thinkin.

**NOTE**: You should tinker with this script or write your own instead.

### Trading  Strategy
At  each  time,  we  either  maintain  position of  +1  Bitcoin,  0  Bitcoin  or − 1  Bitcoin.
At  each time instance, we predict the average price movement over the 10 seconds interval, say ∆p,
using Bayesian regression (precise details explained below) - if ∆p > t, a threshold, then we buy a bitcoin
if current bitcoin position is ≤ 0; if ∆p < −t, then we sell a bitcoin if current  position  is ≥ 0;  else  do  nothing.
The  choice of  time  steps  when  we  make  trading  decisions  as mentioned  above  are  chosen  carefully  by  looking  at
the recent trends. We skip details as they do not have first order effect on the performance.

**NOTE**: You need **at least** 721 data points so that `m = len(prices) - n > 0`, wich means at least 2163 DB entry.

## License

This project is licensed under the terms of the [MIT license](https://choosealicense.com/licenses/mit/). See [LICENSE](https://github.com/Sal0hc1n/bitcoin-price-prediction/blob/master/LICENSE) for more information.
