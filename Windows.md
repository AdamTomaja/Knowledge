# Which app listening on given port ? #
Sometimes some app is blocking the port and we want to know which. To check this: 
* run **resmon.exe**
* open **Network** tab
* Click on **Listening ports**
* Now You can see the list of apps and ports they listen

# Process management #
* Kill app by process ID - **taskkill /PID 1234**
* If the application don`t want to be killed You can add **/F** parameter to force kill - **taskkill /PID 1234 /F**
