# react-gesture-gallery

A simple image gallery built with react which works nicely on desktop and mobile devices.

## Install

Install `react-gesture-gallery` and its peer dependency, `react-gesture-responder` using yarn or npm.

```
yarn add react-gesture-gallery react-gesture-responder
```

## Basic usage

By default, the gallery will attempt to fit into its container using `height: 100%` and `width: 100%`, so you should generally provide a container with a set width and height. For a full-screen gallery, using `width: 100vw` and `height: 100vh`. Note that this library doesn't display in a modal by default, but it's easy enough to provide your own.

```jsx
import * as React from "react";
import { Gallery, GalleryImage } from "../src";

function Example() {
  const [index, setIndex] = React.useState(0);

  const images = [
    {
      src:
        "https://images.unsplash.com/photo-1557958114-3d2440207108?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1950&q=80"
    },
    {
      src:
        "https://images.unsplash.com/photo-1557939403-1760a0e47505?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1931&q=80"
    },
    {
      src:
        "https://images.unsplash.com/photo-1558029062-a37889b87526?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=975&q=80"
    },
    {
      src:
        "https://images.unsplash.com/photo-1558088458-b65180740294?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1579&q=80"
    },
    {
      src:
        "https://images.unsplash.com/photo-1558039719-79cb7b60d279?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1950&q=80"
    }
  ];

  return (
    <div style={{ width: "100vw", height: "100vh" }}>
      <Gallery
        index={index}
        onRequestChange={i => {
          setIndex(i);
        }}
      >
        {images.map(img => (
          <GalleryImage objectFit="contain" key={img.src} src={img.src} />
        ))}
      </Gallery>
    </div>
  );
}
```

## API

### Gallery

| Name               | Type                 | Default Value | Description                                   |
| ------------------ | -------------------- | ------------- | --------------------------------------------- |
| index \_           | number               |               | The index of gallery to show                  |
| onRequestChange \_ | (i: number) => void; |               | A callback requesting the active image change |
| enableKeyboard     | boolean              | true          | Enable keyboard controls                      |
| children \*        | GalleryImage[]       |               | A set of gallery images to diplay             |

### GalleryImage

| Name      | Type   | Default Value | Description           |
| --------- | ------ | ------------- | --------------------- |
| src \*    | string |               | The image source      |
| srcSet    | string |               | The image source set  |
| alt       | string |               | Alt tag for the image |
| objectFit | 'cover | contain'      | 'contain'             | How to display the image |

## License

MIT
