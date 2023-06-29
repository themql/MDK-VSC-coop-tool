# MDK-VSC-coop-tool

## Introduction

A script for pytrhon 3.x parse the keil project `.uvproj` and create c configuation  `.vscode/c_cpp_properties.json` in vscode  , which can also generate a batch file to be integrated into the keil compilation process to automatically update the c config file. 

## How to use

1. check the python ,vscode and the plugin C/C++ for Visual Studio Code is running on your compute correstly;

2. copy the Scripts folder to workspace, and the file hierarchy should be like following;
   
   ```
   .
   ├── Core
   ├── Drivers
   ├── MDK-ARM
   │   ├── other files
   │   └── prjName.uvprojx
   ├── Scripts
   │   ├── uvproj_ccppProperties_conv.bat(will be generate later)
   │   └── uvproj_ccppProperties_conv.py
   ├── .mxproject
   └── prjName.ioc
   ```

3. run the python script in the root of workspace for the first time, and remember to fulfill the `keil_project_file_path`; 
   
   if you want to see the parsing result, using the `--verbose` flag
   
   if you dont't install keil in the default place, attaching the `-i COMPILER_INCLUDE_PATH` to indicate the complier lib path
   
   if you want to generate the batch file in another place, using `--bat_file_path BAT_FILE_PATH`

```
python .\Scripts\uvproj_ccppProperties_conv.py .\MDK-ARM\*.uvprojx --genbat
```

4. add the batch file to keil's `Options for Target - User -  Before Build/Rebuild`, and dont't forget to enable the checkbox;

5. run build in keil, and you will see the infomation displayed in Build Output panel



## Thanks to

[Daniel "Thready" Nitecki / Keil_integration_into_VSCode_and_STM32CubeIDE · GitLab](https://gitlab.com/niciki/keil_integration_with_vscode)


