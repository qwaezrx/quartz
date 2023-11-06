
To access the entire file structure of a project including all files hidden within folders from the XCode view, select Project from the tab at the top of the Project window.

![The Project View in xCode with 'Main' selected](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/lGroQ1azR2Cq6ENWszdghA_ba5d8097bb634caab737140c0e7ac7e1_xcode_project_files.png?expiry=1694908800000&hmac=XgRE2fZPCJG9ZQtLxBTEtAG3ymhVMw4dkYEGQU_Eai0)

Choosing Project View allows you to see a lot more files and directories. The most important of these are:

## **module-name/**

### **AppDelegate**

The app delegate is effectively the root object of your app, and it works in collaboration with UIApplication to manage some user interactions with the system.

### **SceneDelegate**

What is displayed on the screen is the responsibility of SceneDelegate.

### **ViewController**

[[iOS App Cheat Sheet#ViewControllers]]

The View Controller is the parent of all the views present on a storyboard. Each application has at least one ViewController. It facilitates the transition between various parts of the user interface.

### **Main**

With the Main.storyboard file you can lay out and design the user interface of your application by adding views such as buttons, table views, and text views onto the editor.

### **Assets**

This can be used to organize your app's images, icons, colors, and more

### **LaunchScreen**

Launch screens appear when your app starts up and give the user the impression that your app is fast and responsive.

### **Info.plist**

Xcode supplies an information property list file when you create a project from a template, as described in "create a project." By default, Xcode names this file Info.plist and adds it to your project as a source file that you can edit.

## **module-nameTests/**

This folder is responsible for managing code required to test functions within the application.

## **module-nameUITests/**

This folder keeps test files required for testing user interactions with the app user interface.