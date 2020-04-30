## hyperapp-styled-components

<div>
  <!-- NPM Version -->
  <a href="https://www.npmjs.org/package/hyperapp-styled-components">
    <img src="http://img.shields.io/npm/v/hyperapp-styled-components.svg"
    alt="NPM version" />
  </a>
</div>

<br />

A super tiny Hyperapp equivalent of [`styled-components`](https://github.com/styled-components/styled-components).

## Install

```
npm install --save hyperapp-styled-components
```

## Usage

First add this to your HTML file in the <head> tag: `<style type="text/css" id="styles"></style>` than..

```js
import { h, app } from "hyperapp";
import styled from 'hyperapp-styled-components';

const Header = styled.h2`
  color: #333;
`;

const MyButton = styled.button`
  padding: 10px;
  border-radius: ${0}px;
  background: #F1F1F1;

  &:hover {
    background: ${props => props.color};
  }
`;

const Wrapper = styled.div`
  width: 500px;
  border: 1px solid #aaa;

  @media (min-width: 400px) {
    width: 100%;
    background: #F1F1F1;
  }
`;

app({
  init: 0,
  view: state => (
    <Wrapper>
      <Header>Welcome to Styled Hyperapp {state ? 'Yay!' : ''}</Header>

      <MyButton onclick={state => 1}>Go</MyButton>
    </Wrapper>
  ),
  node: document.getElementById("app")
});
```

## Features

  - Super tiny **2.1kb** gzipped
  - Completely DOM based
  - Supports `@media`
  - Supports `@keyframes` (via `keyframes` method)
  - Supports pseudo CSS (i.e. `&:hover`)
  - State can be fed in through primitive methods (i.e `props => ...`)
  - No dependencies
  - Uses template literals and real CSS
  - Supports all DOM elements
  - Auto CSS class injection/management
  - Works with `hyperapp`

## About

I love `styled-components` and needed a HyperApp equivalent for a project. This is the result. It functions almost the same with pseudo and media queries supported. Dynamic props can be fed in through primitive functions; the output of each is a function where props can be fed in, which then returns another function where child elements and strings can be fed in.

A special thanks to [Max Stoiber](https://twitter.com/mxstbr) and the `styled-components` team for coming up with a great component API for mixing CSS and JS.

## Usage with Props

```js
import styled from 'hyperapp-styled-components';

const Header = styled.h2`
  color: #${props => props.status === 'success' ? '000' : '333'};
`;

const View = () => () => (
  <div>
    <Header status="success"></Header>
  </div>
);
```

## With Keyframes

```js
import styled, { keyframes } from 'hyperapp-styled-components';

const boxmove = keyframes`
  0%   {top: 0px;}
  25%  {top: 200px;}
  75%  {top: 50px}
  100% {top: 100px;}
`;

const Box = styled.div`
  background-color: lightcoral;
  width: 100px;
  height: 100px;
  display: block;
  position :relative;
  animation: ${boxmove} 5s infinite;
`;

```

## Important documents

- [Changelog](CHANGELOG.md)
- [Code of Conduct](CODE_OF_CONDUCT.md)
- [License](https://raw.githubusercontent.com/SilentCicero/hyperapp-styled-components/master/LICENSE)

## Todo

- Testing
- Coverage
- Documentation

## Licence

This project is licensed under the MIT license, Copyright (c) 2016 Nick Dodson. For more information see LICENSE.md.

```
The MIT License

Copyright (c) 2016 Nick Dodson. nickdodson.com <thenickdodson@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
