## How to create the automations for opening App using lldb, opening and closing camera preview

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
