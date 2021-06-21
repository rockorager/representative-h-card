# representative-h-card

A node implementation of the [representative h-card parsing algorithm](https://microformats.org/wiki/representative-h-card-parsing), using [this repo](https://github.com/indieweb/representative-h-card-php) as a basis

## Installation

Using npm:

```js
npm install representative-h-card
```

## Usage

representative-h-card.js parses a microformats2 object and returns the representative h-card for that page. It accepts a valid microformats2 object (parsed from [microformat-node](https://www.npmjs.com/package/microformat-node), for example) and a URL, as a string. The URL should be the URL of the the mf2 object was parsed from.

```js
const rhc = require('@rockorager/representative-h-card');

const url = 'https://www.timculverhouse.com';
const mf2 = {
  items: [
    {
      type: ["h-entry"],
      properties: {
        url: [
          "https://www.timculverhouse.com",
        ],
        author: [
          {
            value: "Tim Culverhouse",
            type: ["h-card"],
            properties: {
              name: ["Tim Culverhouse"],
              photo: [
                "https://www.timculverhouse.com/assets/img/tim-avatar.jpeg",
              ],
              url: ["https://www.timculverhouse.com"],
              uid: ["https://www.timculverhouse.com"],
            },
          },
        ],
        name: ["Home"],
        content: [
          {
            value: "Website of Tim Culverhouse",
            html: "<h1>Website of Tim Culverhouse</h1>",
          },
        ],
      },
    },
  ],
  rels: {},
  "rel-urls": {},
};

// Call the function
const hcard = rhc(mf2, url);

if(hcard) {
  // do something with the h-card
}
```
## Output

If a representative h-card is found, the object is returned, otherwise `false` is returned.

```js
{
  value: "Tim Culverhouse",
  type: ["h-card"],
  properties: {
    name: ["Tim Culverhouse"],
    photo: [
      "https://www.timculverhouse.com/assets/img/tim-avatar.jpeg",
    ],
    url: ["https://www.timculverhouse.com"],
    uid: ["https://www.timculverhouse.com"],
  },
}
```

## License
MIT