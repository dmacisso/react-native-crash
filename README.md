# react-native-crash
React Native Crash Course+ presented by Travesey Media

[Youtube Link to Course](https://www.youtube.com/watch?v=bCpFbERgj7s)

[GitHub Link to course source code ](https://github.com/bradtraversy/notes-app/tree/main)

[GitHub Link to my note-app repository](https://github.com/dmacisso/notes-app)


### This repository README.md tracks my learning path for React Native. Below are slides and notes taken from the Travesy Media course.
<hr>

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


## Create an appwrite account on appwrite.io
I used my github account to login

Create a new project: Notes Project

Project ID dvm-notes-project

Pick a region: Only Frankfourt was availible.

Add a platform  => React Native

Package Name Registraion =>  for Android =>  Name: Notes App Android  Package Name: notes-app-android
Note: For android it is call 'package name'
  
    npx expo install react-native-appwrite react-native-url-polyfill

skip the initilize step for now, hit next..

Go to dashboard and repeat for iOS..
Note: for iOS it is called 'bundle'
  
    npx expo install react-native-appwrite react-native-url-polyfill


Create the databases

From the Dashboard => databases => create database Name: NotesDB DatabseID: notes-aap-db => Create

=> Create collection: Name: notes Collection ID:  notes => create.

Attributes tab 
Attribute is a field  => Create attribute

id is autogenerated.
for "text" filed choose String 
Attribute Key: text
Size: 255
check required
=> create

![image](https://github.com/user-attachments/assets/3fdd61dd-2433-4493-b4c2-951fa301011a)

The only other attribute is a createdAt filed, chose datetime field

![image](https://github.com/user-attachments/assets/2c243f62-8b1e-4335-864d-9f2170d5306a)

Now set the permission.
Go to collecion..  => settings. scroll to permissions.. click +   For now. select "any" select create, read, update, and delete.

![image](https://github.com/user-attachments/assets/89ef1044-acd8-42e6-b31a-263b5533d60b)

Later we can fix this.we will add a user, with less permissions. and remove the any.


You can add data to the collection by + create document

![image](https://github.com/user-attachments/assets/dd0cf098-05ca-4e9b-8ab2-58ce01feed8e)

Now integrate back end with React native app.


Install the SDK(software development kit) - allows us to communicate with Appwrite:

    npx expo install react-native-appwrite react-native-url-polyfill

Congfigure SDK (software development kit)
1. Create a folder called 'services' at root of project.
2. We'll have an appwrite config file and a db service to do CRUD with db. And a seperate notes service that uses the database service. (reusable, encapsulated code)
   <li>Database Service
   <li>Notes service
   <li>Authenticaion service.


![image](https://github.com/user-attachments/assets/e7914d07-6509-4cd6-b3a8-c56ea3c4d3ee)

Flow is database service, notes service, then component stuff..

useRef() Hook:
It is commonly used to access or hold a reference to a DOM element, store previous values, or manage any mutable value that needs to persist between renders.

after complete CRUD is acheived, authentication is next.

In the appwrite database. Go to the collection. In the settings tab. => then permssions. Delete the 'any' role. 
Next, Add an "users" role set to CRUD. Hit thr "Update" button. This means only an authenticated user can access the information.

### order of authentication configuration 
1. in the appwrite.js config a few lines
   ```
    //* initialize the account
    const account = new Account(client)
    export { database, config, client, account };
   ```

3. create an auth service will have functions to:
 1. Login
 2. Register
 3. Check the user
 4. Logout
    These will interact with appwrite through the account object.
3. Create an auth context using the react built in Context API to manage the auth state and  provide (send it down) it to the entire app
4. Auth screen with forms to register and login a user.  These forms will interact with the functions that are in the auth context and the auth context functions will interact with the auth service.
   App will be configured such that If user goes to notes page and you are not logged in, user gets redirect to the login page.

