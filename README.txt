OVERLAY SETUP GUIDE
===================

ADDING OVERLAY TO OBS:
----------------------
1. In OBS Studio, click the "+" button in Sources
2. Select "Browser Source"
3. Name it whatever will help you identify this source the best, and click OK
4. In the Browser Source settings:
   - Check "Local File" checkbox
   - Click "Browse" and select: index.html
   - Set Width: 1920 (or whatever your canvas width is)
   - Set Height: 1080 (or whatever your canvas height is)
5. Click OK

STREAMER.BOT SETUP:
------------------
1. Open Streamer.bot application
2. Go to "Servers/Clients" tab
3. Make sure "Websocket Server" is enabled (should be running on port 8080)
4. The overlay will automatically connect when loaded

SENDING EVENTS TO OVERLAY:
-------------------------
In Streamer.bot, create actions that send websocket messages:

Available Arguments (make sure you set them BEFORE calling the Custom Event Trigger):
- overlay_source    (REQUIRED) - Path to image/video/gif/html file to display
- overlay_text      (Optional) - Text content to show with the overlay  
- source_width      (Optional) - Custom width for the media in pixels
- source_height     (Optional) - Custom height for the media in pixels
- source_duration   (Optional) - How long to show overlay in milliseconds
- source_muted      (Optional) - If the source should be muted (videos only)

Adding Arguments:
- Add "Core > Arguments > Set Argument"
- Input the name of the Argument (see above for list of valid arguments)
- Input the value you want (if it's a file on your computer, put the full path like C:\stream\assets\gifs\michael-scott.gif)

Sending to the Overlay:
- Add "Core > Triggers > Custom Event Trigger" sub-action
- Set "Event Name" to "SquidCustomOverlay"
- Turn on "Use Args"

TESTING THE CONNECTION:
----------------------
1. Load the overlay in OBS (should show "Connected" in green)
2. In Streamer.bot, trigger one of your actions
3. The overlay should display your content

TROUBLESHOOTING:
---------------
- If overlay shows "Disconnected": Check Streamer.bot websocket server is running
- If no events received: Verify your action has correct websocket broadcast format
- If overlay not visible: Check OBS source is enabled and on active scene
- For local file issues: Make sure index.html path is correct in OBS

FILE STRUCTURE:
--------------
index.html         - Main overlay file (load this in OBS)
script.js          - JavaScript functionality
style.css          - Overlay styling
simple-test.html   - Basic test overlay html file

For more advanced customization, edit index.html, script.js and style.css files.
