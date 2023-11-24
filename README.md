# react-native-photo-cropper
React Native Image Cropper, inspired by Instagram
## Preview

<img src="https://github.com/thanhcuong1990/react-native-photo-cropper/blob/main/gifs/iphone.gif" alt="preview" width="300px" />

## Getting started
### First, install peer packages
- [react-native-gesture-handler@^2.12.1](https://docs.swmansion.com/react-native-gesture-handler/docs/)
- [react-native-reanimated@^3.4.2](https://docs.swmansion.com/react-native-reanimated/docs/fundamentals/getting-started/)
- [react-native-image-editor-next@^1.1.0](https://github.com/thanhcuong1990/react-native-image-editor)
### Second, install package
`npm install react-native-photo-cropper --save`
or
`yarn add react-native-photo-cropper`

### Thired, pod install
`cd ios && pod install && cd ..`

## Usage
```javascript
import React, {useState} from 'react';
import {Image, StyleSheet, Text, View} from 'react-native';
import PhotoCropper from 'react-native-photo-cropper';

const App = () => {
  const [croppedImage, setCroppedImage] = useState<string | null>(null);

  return (
    <View >
        <PhotoCropper
          onCropped={data => setCroppedImage(data.croppedUri)}
          image={{
            width: 1600,
            height: 700,
            uri: 'https://dummyimage.com/1600x700/b5b5b5/ffffff.png',
          }}
        />
        <Text>Cropped image</Text>
        {croppedImage && (
          <Image source={{uri: croppedImage}} style={styles.image} />
        )}
    </View>
  );
};
```

## Props
```ts
export interface PhotoCropperProps {
  image: { // required
    uri: string;
    width: number;
    height: number;
  };
  width?: number; // default Dimensions.get('window').width
  height?: number; // default Dimensions.get('window').width
  grid?: boolean; // default true
  gridVerticalNum?: number; // default 2
  gridHorizontalNum?: number; // default 2
  gridColor?: string; // default '#fff'
  onCropped?: (data: CroppedData) => void;
  maxScale?: number;  // default 2 / range 1 ~ ∞
  initialX?: number;
  initialY?: number;
  initialScale?: number; // default 1
  initialOpacity?: number; // default 1
}

export interface CroppedData {
  croppedUri: string;
  originalUri: string;
  croppedArea: {
    width: number;
    height: number;
    x: number;
    y: number;
  }
}
```
