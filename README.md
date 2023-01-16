# Arduino nano 33 ble sense (research notes)
Create Date: 2021/03/17
Board info: https://store.arduino.cc/usa/nano-33-ble-sense
Arduino On-chip AI: https://www.arduino.cc/en/AI/HomePage
###### tags: `Arduino On-chip AI`
## Getting started: installation 
* On Arduino app:
    * **下載程式褲**：Arduino>工具>管理程式庫>搜尋Arduino_TensorFlowLite & Arduino_LSM9DS1 & ArduinoBLE,etc>安裝
    * **下載開發版**：Arduino>開發版->開發版管理員>搜尋Arduino nRF528x Boards (Mbed OS)或Arduino Nano 33 bl>安裝
    * 燒錄器(programmer)記得設定為`AVRISP mkll`
* On Arduino web editor:
    * Sign in: https://create.arduino.cc/editor/chiahong95
    * Install **Arduino Create Agent**: https://create.arduino.cc/getting-started/plugin/install (So that web editor could detect your board which is connected to PC via USB port!)
     ![](https://i.imgur.com/fWfQ0LV.png)
    * Search for libraries you need!

## TensorFlow Lite for Microcontrollers examples
> Imfortant Ref: https://blog.arduino.cc/2019/10/15/get-started-with-machine-learning-on-arduino/ 
* Examples in **Arduino_TensorFlowLite** :micro_speech, person_detection, etc.
* Examples in **Arduino_LSM9DS1** helps to read accelerometer and gyroscope(陀螺儀) values 
* Examples in **ArduinoBLE** deal with BLE connection tasks
* 視所需下載程式庫，尚有溫濕度、壓力感測等等範例可使用... 
## Gesture Recognition Tutorial
<!-- > * Github: https://github.com/arduino/ArduinoTensorFlowLiteTutorials/tree/master/GestureToEmoji
> * Colab: https://colab.research.google.com/github/arduino/ArduinoTensorFlowLiteTutorials/blob/master/GestureToEmoji/arduino_tinyml_workshop.ipynb -->

* 在Arduino執行`IMU_Capture.ino`來搜集姿勢資料>複製序列埠data>將一種姿勢資料做成.csv檔案。<font color="red">記得將空白列利用excel刪除(否則訓練時會出現nan錯誤)。</font>
* 開啟`arduino_gesture_recog.ipynb`>匯入flex.csv與punch.csv檔案>進行訓練>匯出`model.h`
* 回到Arduino開啟`IMU_Classifier.ino`
* 在Arduino新增Tab>命名為model.h>將由colab匯出之model.h內容複製貼上。(或是直接將model.h放置於IMU_Classifier資料夾內)
* 最後編譯上傳IMU_Classifier.ino至開發版，開啟序列埠
![](https://i.imgur.com/ZNKg8yy.png =300x200)
* Future Attempt: 利用Emoji_Button.ino來輸出Gesture圖案
* Other pojects: https://create.arduino.cc/projecthub/dgiancono/nano33blesensor-getting-started-with-the-nano-33-ble-sense-8a7eba

<!-- # <font color="lighblue">To be Continued...</font> -->



