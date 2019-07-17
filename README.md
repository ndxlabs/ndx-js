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

## Usage

### Javascript

```html

<div class="ndx-embed"></div>

<script src="https://unpkg.com/@ndxlabs/ndx-js"></script>
<script>

  ndx.configure({
    apiKey: 'ab3rGRg4iwC5Qy...',
    analytics: true
  });

  var tech = ndx.Tech('.ndx-embed', '1234567...', {
    list: {
      orientation: ndx.HORIZONTAL,
      view: ndx.LIST,
      timeBased: true,
      style: {
        position: 'absolute',
        bottom: '2em',
        left: '0',
        padding: '0 2em'
      },
      onItemSelected: function(content) {
        // doSomethingWithSelectedContent(content);
      }
    },
    detail: {
      relatedContent: true,
      useTMDb: true,
      onClose: function() {
        // doSomethingAfterClose();
      }
    }
  });

  tech.list.show().updateTime(5);

</script>

```

### React

```JSX

import React from 'react';
import { NDX, NDXTech } from '@ndxlabs/ndx-js';
import { withRouter } from 'react-router';

import Controls from '../../components/Controls';
import Player from '../../components/Player';
import Provider from '../../context/Provider';

function Watch({ match, store }) {
  const { videoId } = match.params;
  const { playing, currentTime } = store.getState();

  return (
    <Provider>
      <NDX apiKey={process.env.REACT_APP_NDX_API_KEY} config={{ analytics: true }} />
      <Player>
        <NDXTech videoId={videoId} config={{
          list: {
            orientation: ndx.VERTICAL,
            showing: !playing,
            currentTime,
            style: {
              position: 'absolute',
              top: '2em',
              left: '2em',
            },
          }
        }} />
        <Controls />
      </Player>
    </Provider>
  );
}

export default withRouter(Watch);

```

