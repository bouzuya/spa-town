# spa-town

A simple router based on [bath][bouzuya/bath].

[bouzuya/bath]: https://github.com/bouzuya/bath

## Installation

```bash
$ npm install spa-town
```

## Usage

```ts
import * as assert from 'assert';
import { result, route, router } from 'spa-town';

const router1 = router([
  route('root#index', '/'),
  route('users#index', '/users'),
  route('users#index', '/users/'),
  route('users#show', '/users/{id}', { id: /^\w+$/ }),
  route('users#show', '/users/{id}/', { id: /^\w+$/ })
], result('root#notfound', {}));

assert.deepEqual(router1('/'), result('root#index', {}));
assert.deepEqual(router1('/users'), result('users#index', {}));
assert.deepEqual(router1('/users/'), result('users#index', {}));
assert.deepEqual(router1('/users/123'), result('users#show', { id: '123' }));
assert.deepEqual(router1('/users/123/'), result('users#show', { id: '123' }));
assert.deepEqual(router1('/no-match'), result('root#notfound', {}));
```

## Badges

[![npm version][npm-badge-url]][npm-url]
[![Travis CI][travisci-badge-url]][travisci-url]

[npm-badge-url]: https://badge.fury.io/js/spa-town.svg
[npm-url]: https://www.npmjs.com/package/spa-town
[travisci-badge-url]: https://travis-ci.org/bouzuya/spa-town.svg?branch=master
[travisci-url]: https://travis-ci.org/bouzuya/spa-town

## License

[MIT](LICENSE)

## Author

[bouzuya][user] &lt;[m@bouzuya.net][email]&gt; ([http://bouzuya.net][url])

[user]: https://github.com/bouzuya
[email]: mailto:m@bouzuya.net
[url]: http://bouzuya.net

