koa-knexjs
===================

[![NPM version][npm-image]][npm-url]


Knex.js Middleware for Koa. Package is versioned in step with <http://knexjs.org/#changelog>

Repository forked from [https://github.com/tjwebb/koa-knex-middleware](https://github.com/tjwebb/koa-knex-middleware)

### 0. Installation (via [npm](https://npmjs.org/package/koa-knexjs))

```bash
  $ npm install koa-knexjs --save
  
  # Then add one of the following (adding a --save) flag:
  $ npm install pg
  $ npm install sqlite3
  $ npm install mysql
  $ npm install mysql2
  $ npm install mariasql
  $ npm install strong-oracle
  $ npm install oracle
  $ npm install mssql
  $ npm install oracledb
```

### 1. Usage

```javascript

  var _ = require('koa-route');
  var knex = require('koa-knexjs');
  ...
  app.use(knex({
    client: 'pg', //or sqlite3, mysql, mysql2, mariasql, strong-oracle, oracle, mssql, oracledb
    connection: {
      /** typical knex connection object */
    }
  });

  app.use(_.get('/:userid', function *(userid) {
    this.body = {
      profile: yield this.knex('users').where('id', userid);
    };
  });

```

### 2. Options

The following environment variables will be automatically used for the Knex.js connection object if set:
```
  KOA_KNEX_HOST
  KOA_KNEX_PORT
  KOA_KNEX_USER
  KOA_KNEX_PASSWORD
  KOA_KNEX_DATABASE
  KOA_KNEX_CHARSET
  KOA_KNEX_SSL
  KOA_KNEX_DEBUG
```
### 3. Changes

Repository forked from [https://github.com/tjwebb/koa-knex-middleware](https://github.com/tjwebb/koa-knex-middleware)
The origial repository was forked for adding support to knex 0.12.x. 
As of now the following drivers are supported

- pg
- sqlite3
- mysql
- mysql2
- mariasql
- strong-oracle
- oracle
- oracledb
- mssql

### License

[MIT](http://www.opensource.org/licenses/mit-license.php)

[npm-image]: https://img.shields.io/npm/v/koa-knexjs.svg?style=flat-square
[npm-url]: https://npmjs.org/package/koa-knexjs

