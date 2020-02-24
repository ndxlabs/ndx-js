<br/>
<p align="center">
  <img src="./images/ndx-logo.png" height="130" />
</p>
<br/>
<p align="center">
  <img alt="NPM Version" src="https://img.shields.io/npm/v/@ndxlabs/ndx-js.svg?style=for-the-badge" />
  <img alt="GitHub top language" src="https://img.shields.io/github/languages/top/ndxlabs/ndx-js.svg?style=for-the-badge" />
  <img alt="Bundlephobia" src="https://img.shields.io/bundlephobia/minzip/@ndxlabs/ndx-js?style=for-the-badge" />
  <br/>
  <img alt="Dependencies" src="https://img.shields.io/david/peer/ndxlabs/ndx-js.svg?style=for-the-badge" />
  <img alt="GitHub License" src="https://img.shields.io/github/license/ndxlabs/ndx-js.svg?style=for-the-badge" />
</p>
<br/>
<p>NDX is the industry's new standard for connecting information to movies and television. NDX improves the TV viewing experience by connecting audiences with more information about the actors and locations they see on screen.</p>

## Installation

```bash
npm install @ndxlabs/ndx-js
```

## Usage

### Javascript

```html

<div class="ndx-embed"></div>

<script src="https://unpkg.com/@ndxlabs/ndx-js"></script>
<script>

  ndx.configure({
    apiKey: 'ab3rGRg4iwC5Qy...'
  });

  const tech = ndx.Tech('.ndx-embed', '1234567...', {
    list: {
      orientation: ndx.HORIZONTAL,
      style: {
        position: 'absolute',
        bottom: '2em',
        left: '0'
      }
    }
  });

  tech.list.show().updateTime(5);

</script>

```

### React

```jsx

import React from 'react';
import { withRouter } from 'react-router';
import { NDX, Tech } from '@ndxlabs/ndx-js';

import Controls from '../../components/Controls';
import Player from '../../components/Player';

function Watch({ match, store }) {
  const { videoId } = match.params;
  const { playing, currentTime } = store.getState().player;

  return (
    <div className="watch-page">
      <NDX apiKey={process.env.REACT_APP_NDX_API_KEY} />
      <Player>
        <Tech
          videoId={videoId}
          show={!playing}
          currentTime={currentTime}
        />
        <Controls />
      </Player>
    </div>
  );
});

export default withRouter(Watch);

```

