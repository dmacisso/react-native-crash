# react-native-crash
React Native Crash Course+ presented by Travesey Media

The repository is setup to track my learning path for React Native.

![image](https://github.com/user-attachments/assets/97ed8aaa-74dd-4106-ba82-78b72924d8c4)

Runs on Ios and Android using a single code base.

![image](https://github.com/user-attachments/assets/4af2bf80-748f-4ea9-af6b-d5040bf43069)

It dosn't need react-dom, because it does't render to a browser. Use components like View and Text
which map to Native components.
![image](https://github.com/user-attachments/assets/2df3d090-2379-427a-a212-0bd9c11c6f9c)

You also get access to the native API's like the camerea, the photos, location services, push notifications.
Does this by "The Bridge"

![image](https://github.com/user-attachments/assets/e5a742fc-fb09-4a61-a42c-f9178fba8d98)

![image](https://github.com/user-attachments/assets/73ed2543-a60c-42e5-906d-b81eb3c66d6c)



## Setup using Expo 
You can use a dev server, simulator, or expp Go app. 
 You can view:
1.  In browser (uses react native web)
2.  Using a iOS simulator on a Mac and have to have xcode installed
3.  Using an Android simultator, install android studio,
4.  On a mobile device, install Expo Go. Scan a QR code.

   
https://reactnative.dev/
Need to run:

    npx create-expo-app@latest notes=app

To clean up and reset the project, and remove the original boiler plate run:
        
        npm run reset-project

        Do you want to move existing files to /app-example instead of deleting them? 
     (Y/n): n
     ❌ /app deleted.       
     ❌ /components deleted.
     ❌ /hooks deleted.
     ❌ /constants deleted.
     ❌ /scripts deleted.
     
     📁 New /app directory created.
     📄 app/index.tsx created.
     📄 app/_layout.tsx created.
     
     ✅ Project reset complete. Next steps:
     1. Run `npx expo start` to start a development server.
     2. Edit app/index.tsx to edit the main screen.

  ### Common Components:
  ![image](https://github.com/user-attachments/assets/93e8c65e-4af7-4751-83fe-66cf447a00b2)

## Stack:
A stack of screens or pages. Used when you want multiple pages.. FIFO on top. Manipulted by:
1. Push (redirect to another page)

## Slot:
If you want just one screen. There is not header to see what page you are on and there is no back button.


