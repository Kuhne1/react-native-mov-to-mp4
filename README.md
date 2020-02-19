# react-native-mov-to-mp4

Convert mov file to mp4 for cross-platform playback compatibility.

## About this Fork

The original repo is no longer maintained and has a few issues. This one adds a podspec and fixes android import issues. You'll still likely want to check the platform when calling the convert function, e.g.:

```
import MovToMp4 from 'react-native-mov-to-mp4';

if (Platform.OS === 'ios') {
  const filename = Date.now().toString();
  MovToMp4.convertMovToMp4(data.path, filename + ".mp4")
    .then(function (results) {
      //here you can upload the video...
      console.log(results);
    });
}
```

## Installation

link react-native-mov-to-mp4:
```ruby
react-native link react-native-mov-to-mp4
```

and import :
```javascript
import MovToMp4 from 'react-native-mov-to-mp4';
```

#### convertMovToMp4(videoFilePath,newFilenameMp4,callback)

## Usage:
```javascript
const filename = Date.now().toString();
MovToMp4.convertMovToMp4(data.path, filename + ".mp4")
  .then(function (results) {
    //here you can upload the video...
    console.log(results);
  });
          
  ```
## Example
this example use react-native-camera
```javascript
render() {
    return (
      <View style={styles.container}>
        <Camera
            ref={(cam) => {
            this.camera = cam;
          }}
            captureTarget={Camera.constants.CaptureTarget.disk}
            captureMode={Camera.constants.CaptureMode.video}
            style={styles.preview}
            aspect={Camera.constants.Aspect.fill}>
          <Text style={styles.capture} onPress={this.takeVideo.bind(this)}>[CAPTURE]</Text>
        </Camera>
      </View>
    );
  }
  takeVideo() {
    if(this.isRec){
      this.isRec = false;
      this.camera.stopCapture();
    }else {
      this.isRec = true;
      this.camera.capture()
          .then((data) => {
            const filename = Date.now().toString();
            MovToMp4.convertMovToMp4(data.path, filename + ".mp4")
              .then(function (results) {
              //here you can upload the video...
              console.log(results);
            });
          })
          .catch(err => console.error(err));
    }
  }
  ```

## License

MIT
