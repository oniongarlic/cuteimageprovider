# Simple QtQuick image provider that can do basic image manipulation:

* Brightness
* Contrast
* Gamma
* Convert to grayscale
* Crop
* Rotate

Still WiP

# Usage

## Register with QQmlApplicationEngine:

```
QGuiApplication app(argc, argv);
QQmlApplicationEngine engine;
CuteImageProvider *cuteprovider=new CuteImageProvider(&app);
```

``` 
engine.rootContext()->setContextProperty("imp", cuteprovider);
engine.addImageProvider("cute", cuteprovider);
```

## Access from QtQuick

Load image, adjust contrast and brighness, flip it and commit changes:
```
imp.setImage("/path/to/image.jpg");
imp.adjustContrastBrightness(10, 1.2);
imp.mirror(true, false);
imp.commit();
im.updatePreview();
imp.save("/path/to/edited-image.jpg"); 
```

Display the image in Image component:
```
Image {
 id: im
 source: "image://cute/preview"
 cache: false
 function updatePreview() {
  im.source=""
  im.source="image://cute/preview"
 }

}
```
 
