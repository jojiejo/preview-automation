## How to create automations for opening App using lldb, opening and closing camera preview

1. Build the latest `master` Lumina Studio or you can run the installed App.
2. Open terminal -> cd to your app -> and try to `lldb LuminaStudio` -> `run`
<img width="682" alt="Screen Shot 2022-03-31 at 12 08 47" src="https://user-images.githubusercontent.com/36635194/160980779-4216dedc-628e-400e-9035-e5333cb37946.png">

3. If Lumina Studio runs smoothly, we can continue, otherwise there might be problem in the path.
4. Quit the `lldb` (I use ctrl + C -> type quit)
5. Open Automator (built-in macro app on mac)
<img width="1680" alt="Screen Shot 2022-03-31 at 12 11 35" src="https://user-images.githubusercontent.com/36635194/160981069-c0349163-d800-46b7-93f6-ab4fe86a833c.png">

6. Take a look at it and try some features
7. Now, create a `Run Shell Script` to open terminal and cd to our app. Here's a sample shell-script.
<img width="1112" alt="Screen Shot 2022-03-31 at 11 35 10" src="https://user-images.githubusercontent.com/36635194/160981246-78a18684-1892-4520-b888-7a9bae418468.png">

Here's a script you can use (You have to change the file path to the Lumina App bin directory)
```
osascript -e 'tell app "Terminal"
    do script "cd /Users/djodi/Lumina/build/main/LuminaStudio/LuminaStudio.app/Contents/MacOS"
end tell'
```

8. After that, create `Watch Me Do` on your automation
<img width="1112" alt="Screen Shot 2022-03-31 at 11 37 21" src="https://user-images.githubusercontent.com/36635194/160981428-40ba740f-fbb1-49d4-a701-9c33cae18b9f.png">

9. Click `Record` on the top left of the window. Basically, this will record pointer & keyboard moves.
Personally, i use this to reopen terminal window on the task bar -> type `lldb Lumina Studio` -> press return -> type `run` -> press return again -> and bring the Lumina Studio to the front 
<img width="1112" alt="Screen Shot 2022-03-31 at 11 41 49" src="https://user-images.githubusercontent.com/36635194/160981550-eba1977b-ca62-4a19-8836-d4e84f659546.png">

10. Test the automation before creating another automation. You can click `Run` on the top left of the window to test it.
11. Save that automation if you think it already meets the expectation
12. Create a new automation for the 2nd task (clicking & closing open preview) 
13. It will be simpler for the 2nd automation. You can create `Watch Me Do` again here. Now, we just need to record clicking `Show Control` on the Lumina App tray menu -> opening & closing the preview. You have to give 30s delay for this manually.
14. Create a `Loop` after watch me do, so that the task will be repeated automatically
15. Adjust the Loop function, personally i stop after 300 mins. Also select Loop automatically and Use the original input for the other dropdown list.
<img width="1112" alt="Screen Shot 2022-03-31 at 11 44 59" src="https://user-images.githubusercontent.com/36635194/160981882-a4839857-6b9c-4e3d-b136-8918034998d6.png">

16. Test the automation, but before that you have to run the app from lldb to see the actual result
17. Save that automation if you think it meets the requirement
18. Open Mac `System Preferences` -> `Security & Privacy` -> `Privacy tab` -> `Accessibility`
19. Allow the previosly created automation on this segment
<img width="780" alt="Screen Shot 2022-03-31 at 11 52 31" src="https://user-images.githubusercontent.com/36635194/160982064-a04a1bc7-def9-47c3-acdc-6219577fe467.png">

20. Open your Mac Calendar to create a new event for those automations
21. You will create 2 events for this (1 if you are going to open the app using lldb manually, not using automation)
22. Create an event on specific date -> adjust the starts & ends -> we will use alert to open the automation. 
23. To select the automations click the alerts dropdown -> choose Custom at the end of the options 
<img width="646" alt="Screen Shot 2022-03-31 at 11 55 54" src="https://user-images.githubusercontent.com/36635194/160982215-92736864-2f6e-4549-aa73-f3385c0b0252.png">

24. Choose open file, and select your automation, also select `at time of event` if you want that scheduler to run punctually
<img width="373" alt="Screen Shot 2022-03-31 at 11 56 12" src="https://user-images.githubusercontent.com/36635194/160982224-485f7d91-eac1-4098-887b-e45e324eef70.png">

25. Create another event for the opening & closing automation. Make sure the opening & closing preview events are after the initiating event one. So your Calendar might look like this (more or less)
<img width="1792" alt="Screen Shot 2022-03-31 at 12 24 39" src="https://user-images.githubusercontent.com/36635194/160982634-6c2583f9-8bf2-4886-a743-d41b3ed0b4e8.png">

26. Now we are ready, i would personally test that scheduler by changing the date time to the near future of current date time. And then change it again to the expected date, if the previous one runs smoothly.
