# A text object performance test for the Phaser Game Development Framework

## Why I've created this test
I've noticed that a Phaser project of mine performed worse once I switched from Phaser 2.6.2 to any PhaserCE release (CE = community edition).<br>
In order to study these differences more closely I've created this simple test which displays the frame rate in combination with a certain amount of text objects.<br>
I've released it here on Github so that it might help the Phaser developer community to find the cause of this problem.

You can use this test with any kind of HTML5-compatible-device by yourself if you like.

You just need to load the index-page inside the **phaser-perf-test**-folder that corresponds to the Phaser-version you want to test. 
The test has been configured to show 100 text objects at start and adds additional 50 when clicking/touching the canvas.
You can change the **number_of_text_objects** and the **number_of_additional_text_objects_on_click** in the source code in order to alter this setting.

I used the following device configurations for my tests:
- PC: Intel Core i5-6400 @ 2.7 GHz, nVidia GeForce GTX 650, Windows 10 / Google Chrome 58.0.3029.96 (64-bit)
- Apple iPad2: iOS 9.3.5 / Safari
- Google Nexus 7 (2013): Android 6.0.1 / Google Chrome 57.0.2987.132

## Results


**Phaser version 2.6.2**

| **Text objects** | **PC (FPS)** | **iPad2 (FPS)** | **Nexus 7 (FPS)** |
| ---------------- | ------------ | --------------- | ----------------- |
| 10               | 60           | 57              | 59				|
| 20               | 60           | 57              | 59                |
| 50               | 60           | 57              | 59                |
| 100              | 60           | 56              | 59                |
| 200              | 60           | 54              | 59                |
| 500              | 60           | 28              | 41                |
| 1000             | 60           | 18              | 19                |
| 2000             | 60           | 9               | 14                |
| 5000             | 42           | n/a             | 4                 |
| 10000            | 22           | n/a             | 2                 |


**PhaserCE version 2.7.x**

| **Text objects** | **PC (FPS)** | **iPad2 (FPS)** | **Nexus 7 (FPS)** |
| ---------------- | ------------ | --------------- | ----------------- |
| 10               | 60           | 29              | 57                |
| 20               | 60           | 19              | 46                |
| 50               | 60           | 10              | 20                |
| 100              | 60           | 6               | 11                |
| 200              | 60           | 3               | 6                 |
| 500              | 60           | 1               | 3                 |
| 1000             | 60           | <1              | 1                 |
| 2000             | 60           | <1              | <1                |
| 5000             | 35           | n/a             | <1                |
| 10000            | 16           | n/a             | <1                |

## Conclusion
According to this test PhaserCE 2.7.x seems to have a serious performance issue in comparison with Phaser 2.6.2 when using text objects (especially on tablets, mobile devices and old desktop devices).

While 200 text objects are still handled well by the iPad2 when using Phaser 2.6.2, it already has serious problems with only 10(!) text objects when using PhaserCE 2.7.x.
The situation is similar for the Nexus 7 although this device can handle a few more text objects before the FPS drop happens there too.

When increasing the amount of text objects such that only a modern desktop can still handle it well (>5000 text objects) the issue can also be noted on these devices.

## 3rd Party content
This project includes several minified builds of the Phaser Game Development Framework. For more information please checkout the following Github-repositories:
https://github.com/photonstorm/phaser
https://github.com/photonstorm/phaser-ce

Furthermore it includes an older minified version of the Stats-Benchmark that works well in combination with the Phaser framework. For more information please checkout the following Github-repository: http://github.com/mrdoob/stats.js

## Acknowledgements
to vpmedia for adding additional features to this test