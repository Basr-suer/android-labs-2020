# 实验七
## 一、实验目标
1. 理解Android相机、蓝牙、传感器等设备编程方法。
2. 理解Android设备编程与前面所学组件、存储、网络及界面开发的知识点关系。

## 二、实验内容
1. 修改xml配置文件的内容添加相机权限；
2. 在ReadActivity.java中编程实现相机设备使用；

## 三、实验步骤
1. 在manifests下的配置文件AndroidManifest.xml加入一条权限标签;
```xml
<uses-feature android:name="android.hardware.camera"
        android:required="true" />
```
2. 在界面Java文件ReadActivity.java中请求拍照；
```java
Intent takePictureIntent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
        if (takePictureIntent.resolveActivity(getPackageManager()) != null) {
            startActivityForResult(takePictureIntent, REQUEST_IMAGE_CAPTURE);
        }
```
3. 在界面Java文件ReadActivity.java中获取缩略图；
```java
if (requestCode == REQUEST_IMAGE_CAPTURE && resultCode == RESULT_OK) {
            Bundle extras = data.getExtras();
            Bitmap imageBitmap = (Bitmap) extras.get("data");
            ImageView imageView = new ImageView(this);
            imageView.setImageBitmap(imageBitmap);
            linearLayout.addView(imageView);
        }
```

## 四、实验结果
![拍照显示截图](https://raw.githubusercontent.com/Basr-suer/android-labs-2020/master/students/net1814080903319/lab7.jpg)

## 五、实验心得
实验加了请求使用相机权限，进而使用相机应用程序进行拍照获取缩略图，不过在缩略图这里出现了空指针问题
