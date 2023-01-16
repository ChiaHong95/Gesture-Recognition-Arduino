# Gesture Recognition Arduino nano 33 ble sense (implementation notes)
<!-- Create Date: 2021/03/17 -->
> Board info: https://store.arduino.cc/usa/nano-33-ble-sense  
> Arduino On-chip AI: https://www.arduino.cc/en/AI/HomePage

## Getting started: installation 
* On Arduino app:
    * **下載程式褲**：Arduino :arrow_right: 工具 :arrow_right: 管理程式庫 :arrow_right: 搜尋Arduino_TensorFlowLite & Arduino_LSM9DS1 & ArduinoBLE,etc :arrow_right: Install
    * **下載開發版**：Arduino :arrow_right: 開發版 :arrow_right: 開發版管理員 :arrow_right: 搜尋Arduino nRF528x Boards (Mbed OS)或Arduino Nano 33 bl > install
    * 燒錄器(programmer)設定為`AVRISP mkll`
* On Arduino web editor:
    * Sign in: https://create.arduino.cc/editor/chiahong95
    * Install **Arduino Create Agent**: https://create.arduino.cc/getting-started/plugin/install (So that web editor could detect your board which is connected to PC via USB port!)<img src="https://i.imgur.com/fWfQ0LV.png" height="400" />
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

* 在Arduino執行`IMU_Capture.ino`來搜集姿勢資料(手握Arduino進行flex與punch兩種動作，或其他預進行辨識的動作) :arrow_right: 複製序列埠data :arrow_right: 將一種姿勢資料做成.csv檔案。記得將空白列刪除(可透過excel)，否則訓練時會出現nan錯誤。
* 開啟`arduino_gesture_recog.ipynb` :arrow_right: 匯入flex.csv與punch.csv檔案 :arrow_right: 進行訓練 :arrow_right: 匯出`model.h`
* 回到Arduino開啟`IMU_Classifier.ino`
* 在Arduino新增Tab :arrow_right: 命名為`model.h` :arrow_right: 將由colab匯出之`model.h`內容複製貼上。(或是直接將`model.h`放置於IMU_Classifier資料夾內)
* 最後編譯上傳`IMU_Classifier.ino`至開發版，開啟序列埠
   * 執行flex動作時，序列埠呈現：  
      <img src="https://i.imgur.com/u9mqD9H.png" height="100" />
   * 執行punch動作時，序列埠呈現：  
      <img src="https://i.imgur.com/c01DntD.png" height="100" />
* Future Attempt: 利用`Emoji_Button.ino`來輸出Gesture圖案
* Other pojects: https://create.arduino.cc/projecthub/dgiancono/nano33blesensor-getting-started-with-the-nano-33-ble-sense-8a7eba

<!-- # <font color="lighblue">To be Continued...</font> -->



