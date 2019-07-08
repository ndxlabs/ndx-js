<br/>
<p align="center">
  <img src="./images/ndx-logo.png" height="130" />
</p>  
<br/>
<p align="center">
  <img alt="NPM Version" src="https://img.shields.io/npm/v/@ndxlabs/ndx-js.svg" />
  <img alt="GitHub top language" src="https://img.shields.io/github/languages/top/ndxlabs/ndx-js.svg" />
  <img alt="GitHub License" src="https://img.shields.io/github/license/ndxlabs/ndx-js.svg" />
  <img alt="Dependencies" src="https://img.shields.io/david/peer/ndxlabs/ndx-js.svg" />
</p>
<br/>

<p>NDX is the industry's new standard for connecting information to movies and television. NDX improves the TV viewing experience by connecting audiences with more information about the actors and locations they see on screen.</p>

## Installation
Using either NPM or Yarn:

```bash
npm install @ndxlabs/ndx-js
```

```bash
yarn add @ndxlabs/ndx-js
```

## UMD

```html

  <div id="root"></div>

  <script crossorigin src="https://unpkg.com/@ndxlabs/ndx-js@2.0.0/dist/ndx.umd.min.js"></script>
  <script>

    ndx.configure({
      apiKey: '__NDX_API_KEY__'
    });

    var tech = ndx.Tech('#root', '__NDX_VIDEO_ID__', {
      list: {
        orientation: ndx.VERTICAL,
        style: {
          position: 'absolute',
          bottom: '2em',
          left: '0',
          padding: '0 2em',
        }
      }
    });
    
    tech.list.show();
    tech.list.updateTime(5);

  </script>

```

## React

```jsx
import React from 'react';
import { NDX, NDXTech } from '@ndxlabs/ndx-js';

import WatchPage from './containers/WatchPage';
import Player from './components/Player';
import Controls from './components/Controls';

function App(props) {
  return (
    <Provider>
      <NDX apiKey={'__NDX_API_KEY__'} config={{}} />
      <YourWatchPage { ...props }>
        <Player>
          <NDXTech videoId={'__NDX_VIDEO_ID__'} />
          <Controls />
        </Player>
      </YouWatchPage
    </Provider>
  )
}
```

