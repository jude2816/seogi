# seogi

This library improved use way console api so you will able to use them more better and more simplity and you can use similarly like existing console api.

# Install

```javascript
npm i seogi
```

# Support Platforms

IE9 later, All modern browsers(Chrome, Safari, Edge ...), NodeJS(`12.0.0` version later).

## Normal API

```javascript
log('Hello World');
log(['Hello', 'World']);
log('Hello World', { color: 'red', backgroundColor: 'cyan', fontWeight: 'bold', fontSize: '10px' });
log(['Hello', 'World'], { color: 'cyan', backgroundColor: 'yellow' });
log(['Hello', 'World'], [{ color: 'magenta', backgroundColor: 'blue' }]);
log(['Hello', 'World'], [{ color: 'blue', backgroundColor: 'magenta' }, { color: 'cyan' }]);

error('Hello World', { color: 'cyan', backgroundColor: 'yellow', textDecoration: 'underline', fontSize: '20px' });
warn('Hello World', { color: 'magenta', backgroundColor: 'blue', textDecoration: 'line-through', fontSize: '30px' });
info('Hello World', { color: 'blue', backgroundColor: 'magenta', fontStyle: 'italic', fontSize: '40px' });
debug('Hello World', { color: 'yellow', backgroundColor: 'cyan', fontSize: '50px' });
assert(() => true /* or false */, 'Hello World', {
  color: 'green',
  fontSize: '50px',
});
```

![seogi_1](https://user-images.githubusercontent.com/11391606/97726770-f1802300-1b12-11eb-969b-67b0d79fc10e.png)

## Object Type API

This api include argument of object type and it same to console api.

- `table` API will be unable to using at IE browser and instead will be using `log` API.

```javascript
dir({ x: 1 });
table({ x: 1, y: 2 });
```

![seogi_2](https://user-images.githubusercontent.com/11391606/94977014-de992380-0551-11eb-8c33-7818ffab8431.png)

## Group Type API

`Group Type API` will be unable to using at the IE9 and IE10 browser because browser compatibility issues.

```javascript
group(
  [
    1,
    2,
    () => group([3, 4, 5], 'GROUP 2'),
    '6',
    () => log('log'),
    7,
    () => table({ x: 1, y: 2 }),
    () => groupTable({ x: 1, y: 2 }, 'GROUP 3'),
    8,
    () => group([9, 10], 'GROUP 4'),
    () => groupDir({ x: 1, y: 2 }, 'GROUP 5'),
  ],
  'GROUP 1'
);

groupLog(1, null, 'GROUP LOG', { color: 'white' });
groupDir({ x: 1, y: 2 }, 'GROUP DIR', { color: 'cyan' });
groupTable({ x: 1, y: 2 }, 'GROUP TABLE', { color: 'magenta' });
```

![seogi_3](https://user-images.githubusercontent.com/11391606/94977015-df31ba00-0551-11eb-9a9f-c411ab91dd09.png)

## Group Collapsed Type API

`Group Collapsed Type API` will be unable to using at the IE9 and IE10 browser because browser compatibility issues.

```javascript
groupCollapsed(
  [
    () => error('error'),
    1,
    2,
    () =>
      groupCollapsed(
        [
          3,
          () => info('Hello World', { color: 'green', backgroundColor: 'yellow' }),
          () => warn('Hello World', { color: 'yellow', backgroundColor: 'white' }),
          4,
        ],
        'GROUP COLLAPSED 2'
      ),
  ],
  'GROUP COLLAPSED 1'
);

groupCollapsedLog('test', null, 'GROUP COLLAPSED LOG', { color: 'green' });
groupCollapsedDir({ x: 1, y: 2 }, 'GROUP COLLAPSED DIR', { color: 'yellow' });
groupCollapsedTable({ x: 1, y: 2 }, 'GROUP COLLAPSED TABLE', { color: 'blue' });
```

![seogi_4](https://user-images.githubusercontent.com/11391606/94977017-e062e700-0551-11eb-8143-c5d622d3dce7.png)

## On NodeJS Environment

<s>This library used [chalk library](https://github.com/chalk/chalk) that expression color on the NodeJS.

You can check color list that you can use in [this link](<(https://github.com/chalk/chalk)>) and you can use like following codes all feature of the chalk library.</s>

This library used [colors.js library](https://github.com/Marak/colors.js) that expression color on the NodeJS.

You can check color list that you can use in [this link](<(https://github.com/Marak/colors.js)>) and you can use like following codes all feature of the colors.js library.

- I changed chalk library to colors.js library because [polyfill issue](https://github.com/jaredpalmer/razzle/issues/998) happened at `0.0.15` version.

## Normal API

```javascript
log('Hello World');
log(['Hello', 'World']);
log('Hello World', { color: 'red', backgroundColor: 'cyan', fontWeight: 'bold', fontSize: '10px' });
log(['Hello', 'World'], { color: 'cyan', backgroundColor: 'yellow' });
log(['Hello', 'World'], [{ color: 'magenta', backgroundColor: 'blue' }]);
log(['Hello', 'World'], [{ color: 'blue', backgroundColor: 'magenta' }, { color: 'cyan' }]);

error('Hello World', { color: 'cyan', backgroundColor: 'yellow', textDecoration: 'underline' });
warn('Hello World', { color: 'magenta', backgroundColor: 'blue' });
info('Hello World', { color: 'blue', backgroundColor: 'magenta', fontStyle: 'italic', backgroundColorBright: true });
debug('Hello World', { color: 'yellow', backgroundColor: 'cyan', colorBright: true });
assert(() => true /* or false */, 'Hello World', {
  color: 'green',
});
```

<img width="154" alt="seogi_5" src="https://user-images.githubusercontent.com/11391606/97727008-36a45500-1b13-11eb-8644-fd1fbd08e7d4.png">

## Object Type API

This api include argument of object type and it same to console api

```javascript
dir({ x: 1 });
table({ x: 1, y: 2 });
```

<img width="203" alt="seogi_6" src="https://user-images.githubusercontent.com/11391606/94977019-e0fb7d80-0551-11eb-82f8-60736c60bb30.png">

## Group Type API

```javascript
group(
  [
    1,
    2,
    () => group([3, 4, 5], 'GROUP 2'),
    '6',
    () => log('log', { color: 'magenta' }),
    7,
    () => table({ x: 1, y: 2 }),
    () => groupTable({ x: 1, y: 2 }, 'GROUP 3'),
    8,
    () => group([9, 10], 'GROUP 4'),
    () => groupDir({ x: 1, y: 2 }, 'GROUP 5'),
  ],
  'GROUP 1'
);

groupLog(1, null, 'GROUP LOG', { color: 'white' });
groupDir({ x: 1, y: 2 }, 'GROUP DIR', { color: 'cyan' });
groupTable({ x: 1, y: 2 }, 'GROUP TABLE', { color: 'magenta' });
```

<img width="259" alt="seogi_7" src="https://user-images.githubusercontent.com/11391606/94977020-e1941400-0551-11eb-9549-dc7fab2afb64.png">

## Group Collapsed Type API

```javascript
groupCollapsed(
  [
    () => error('error'),
    1,
    2,
    () =>
      groupCollapsed(
        [
          3,
          () => info('Hello World', { color: 'green', backgroundColor: 'yellow' }),
          () => warn('Hello World', { color: 'yellow', backgroundColor: 'white' }),
          4,
        ],
        'GROUP COLLAPSED 2'
      ),
  ],
  'GROUP COLLAPSED 1'
);

groupCollapsedLog('test', null, 'GROUP COLLAPSED LOG', { color: 'green' });
groupCollapsedDir({ x: 1, y: 2 }, 'GROUP COLLAPSED DIR', { color: 'yellow' });
groupCollapsedTable({ x: 1, y: 2 }, 'GROUP COLLAPSED TABLE', { color: 'blue' });
```

<img width="250" alt="seogi_8" src="https://user-images.githubusercontent.com/11391606/94977021-e22caa80-0551-11eb-9ee7-b35e4a0dbc84.png">

## getStyleMsg API

If you will make an arguments that will send to the native api, you can use a `getStyleMsg API`

```javascript
console.log(...getStyleMsg('Hello World'));
console.log(...getStyleMsg(['Hello', 'World']));
console.log(
  ...getStyleMsg('Hello World', { color: 'red', backgroundColor: 'cyan', fontWeight: 'bold', fontSize: '10px' })
);
console.log(...getStyleMsg(['Hello', 'World'], { color: 'cyan', backgroundColor: 'yellow' }));
console.log(...getStyleMsg(['Hello', 'World'], [{ color: 'magenta', backgroundColor: 'blue' }]));
console.log(...getStyleMsg(['Hello', 'World'], [{ color: 'blue', backgroundColor: 'magenta' }, { color: 'cyan' }]));
```

![seogi_1](https://user-images.githubusercontent.com/11391606/97726770-f1802300-1b12-11eb-969b-67b0d79fc10e.png)
