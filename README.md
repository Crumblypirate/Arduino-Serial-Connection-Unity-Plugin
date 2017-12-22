
Arduino-Serial-Connection-Unity-Plugin


-----------------------------------------------------------------------------------
DESCRIPTION
------------------------------------------------------------------------------------
An open source plugin for connecting an Arduino to Unity through a serial connection.
This plugin provides an easy way to connect and interact with an Arduino from the Unity game engine.

------------------------------------------------------------------------------------
IMPORTANAT NOTES
------------------------------------------------------------------------------------

The connect function may only work if you hold a genuine Arduino board, In order to check this:

1. Connect yoru Arduino to your computer
2. Open device manager
3. Expand "Ports (COM & LPT)"
4. Select your arduino device from the list
5. Right click on the device and select properties
6. Click the "Details" tab
7. Check the value when the "Device description" is selected

If the Vlaue field does not contain the word Arduino, you will have to open the included dll source and find the 
"SearchForArduino()" function and add the device description of your device in the following code:

//search description for arduino name or CH340 (Arduino NANO) **Add to when more descriptions can be identified**
if ((portDesc.find("Arduino") != std::string::npos) || (portDesc.find("CH340") != std::string::npos))
  
Simply add the following before the last ).

|| (portDesc.find("NAME FROM YOUR DEVICE DESCRIPTION") != std::string::npos)

REBUILD THE SOLUTION AND CONTINUE TO THE INSTALLATION.

Detailed instructions with images can be found in the "Adding a Third party Arduino device to work with the plugin" section of the wiki.

-----------------------------------------------------------------------------------
INSTALLATION
------------------------------------------------------------------------------------
To install the plugin to a unity project simply create a new folder in the unity assets folder
called "Plugins". Then import the "Unity Arduino Plugin.ddl" into the plugins folder.

In order to use the plugin in a unity script place the following code at the start of the script.
The included example unity project can also be used for installation guidance.

[DllImport("Unity Arduino Plugin")]
private static extern IntPtr Create ();

[DllImport("Unity Arduino Plugin")]
private static extern void Connectf (IntPtr pClassName, int i);

[DllImport("Unity Arduino Plugin")]
private static extern bool ConTest (IntPtr pClassName);

[DllImport("Unity Arduino Plugin")]
private static extern void TerminateConnection(IntPtr pClassName);

[DllImport("Unity Arduino Plugin")]
private static extern void WriteToSerial(IntPtr pClassName, string send);

[DllImport("Unity Arduino Plugin", CharSet = CharSet.Ansi, CallingConvention = CallingConvention.StdCall)]
[return: MarshalAs(UnmanagedType.BStr)]
private static extern string ReadSerial(IntPtr pClassName);

[DllImport("Unity Arduino Plugin")]
private static extern void Identify(IntPtr pClassName);

[DllImport("Unity Arduino Plugin")]
private static extern void SetPin(IntPtr pObject, int pin, string inorout);

[DllImport("Unity Arduino Plugin")]
private static extern void ControlPin(IntPtr pObject, int pin, int level);

[DllImport("Unity Arduino Plugin")]
private static extern bool GetPinState(IntPtr pObject, int pin);


---------------------------------------------------------------------
USAGE
----------------------------------------------------------------------
For detailed documentation on the functions please see the Wiki on the Github page.
Alternatively each of the functions are used and commented in the included example unity project.


----------------------------------------------------------------------
ADDITIONAL CREDITS
----------------------------------------------------------------------

Thank you to Jaeka2 for the testing of the plugin.
https://github.com/Jaeka2


----------------------------------------------------------------------
LICENSE
----------------------------------------------------------------------
MIT License

Copyright (c) 2017 Alex Chapman

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.




