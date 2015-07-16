# preg

**preg** is a front-end that demonstrates different use-case for plaso. **preg** only purpose is Windows Registry parsing. The front-end uses the Windows Registry parser and plugins from plaso and prints out reports or allows you to interactively interact with the content of the Registry file using a console.

## Usage

Display the latest help message to get a full list of parameters and an explanation of each of them.

```
preg.py -h
```

## Example Usage

To get a list of all available plugins:
```
preg.py --info
```

### Plugin Mode

To run the tool against a specific plugin on an extracted Registry file use the ```-p``` parameter. Each Registry plugin contains a list of what Registry keys it needs to extract so there is no need to indicate key paths.

```
$ preg.py -q -p userassist test_data/NTUSER.DAT 

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx Registry File xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

  Registry File : /<PATH>test_data/NTUSER.DAT
  Registry Type : NTUSER
Registry Origin : OS


       Key Name : \Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{5E6AB780-7743-11CF-A12B-00AA004AE837}
        Subkeys : 1
         Values : 1

       Key Name : \Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{75048700-EF1F-11D0-9888-006097DEACF9}
        Subkeys : 1
         Values : 1


----------------------------------- Plugins ------------------------------------

****************************** Plugin: userassist ******************************
[NTUSER] Parser for User Assist Registry data.
Key information.
             Key Path : \Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{75048700-EF1F-11D0-9888-006097DEACF9}\Count

+++++++++++++++++++++++++++++++++++++ Data +++++++++++++++++++++++++++++++++++++

[1601-01-01T00:00:00+00:00]
	UEME_CTLCUACount:ctor : [Count: 2]

[2009-08-04T15:11:22.811067+00:00]
	UEME_RUNPIDL:%csidl2%\MSN.lnk : [Count: 14]
	UEME_RUNPIDL:%csidl2%\Windows Media Player.lnk : [Count: 13]
	UEME_RUNPIDL:%csidl2%\Windows Messenger.lnk : [Count: 12]
	UEME_RUNPIDL:%csidl2%\Accessories\Tour Windows XP.lnk : [Count: 11]
	UEME_RUNPIDL:%csidl2%\Accessories\System Tools\Files and Settings Transfer Wizard.lnk : [Count: 10]

[2009-08-04T15:13:42.607000+00:00]
	UEME_RUNPATH:C:\Program Files\Internet Explorer\iexplore.exe : [Count: 1]
	UEME_RUNPIDL:::{2559A1F4-21D7-11D4-BDAF-00C04F60B9F0} : [Count: 1]

...
```

The ```-q``` parameter is to indicate that the tool should not print out names of Registry keys it was unable to find and open.

The same applies when running the tool against a storage media file.

```
$ preg.py -q -p userassist -i test_data/registry_test.dd 
[INFO] [PreProcess] Set attribute: sysregistry to /Windows/System32/config
[INFO] [PreProcess] Set attribute: systemroot to /Windows
[INFO] [PreProcess] Set attribute: windir to /Windows
...
[INFO] [PreProcess] Set attribute: code_page to cp1252
[INFO] [PreProcess] Set attribute: hostname to WKS-WIN732BITA
[INFO] [PreProcess] Set attribute: time_zone_str to EST5EDT

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx Registry File xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

  Registry File : /Users/foobar/NTUSER.DAT
  Registry Type : NTUSER
Registry Origin : TSK


       Key Name : \Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{F4E57C4B-2036-45F0-A9AB-443BCFE33D9F}
        Subkeys : 1
         Values : 1


----------------------------------- Plugins ------------------------------------

****************************** Plugin: userassist ******************************
[NTUSER] Parser for User Assist Registry data.
Key information.
             Key Path : \Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{F4E57C4B-2036-45F0-A9AB-443BCFE33D9F}\Count

+++++++++++++++++++++++++++++++++++++ Data +++++++++++++++++++++++++++++++++++++

[1601-01-01T00:00:00+00:00]
	UEME_CTLCUACount:ctor : [UserAssist entry: 10, Count: 0, Application focus count: 0, Focus duration: 0]

[2010-11-10T07:49:37.078067+00:00]
	{0139D44E-6AFE-49F2-8690-3DAFCAE6FFB8}\Accessories\Welcome Center.lnk : [UserAssist entry: 1, Count: 14, Application focus count: 0, Focus duration: 14]
...
```

When running the tool against a storage media file the tool will try to locate Windows partitions. If there is only one partition discovered the tool will be run against that. If more than a single one is discovered or if there are VSS snapshots on that volume the tool will start by asking clarifying information, such as which partition to parse, what VSS stores to include, etc.

Once that is done the tool will automatically discover where the Registry files are stored in the storage media file and determine based on the selected plugin which Registry file to open. In this case the *userassist* plugin was chosen, which works on NTUSER Registry files. Since there may be more than a single user on the system the tool parses each and every discovered user Registry file and displays the information from the selected plugin.

It is also possible to run the tool using more than a single plugin, eg:

```
$ preg.py -p userassist -p run test_data/NTUSER.DAT 
```

Just use the ```-p PLUGIN``` parameter multiple times to include more plugins.

### Key Mode

To run the tool against a specific Registry key, ignoring what plugins to use.

```
$ preg.py -q -k "\Software\Microsoft\Internet Explorer\TypedURLs" test_data/NTUSER.DAT 

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx Registry File xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

  Registry File : /<PATH>/test_data/NTUSER.DAT
  Registry Type : NTUSER
Registry Origin : OS


       Key Name : \Software\Microsoft\Internet Explorer\TypedURLs
        Subkeys : 0
         Values : 2


----------------------------------- Plugins ------------------------------------

************************** Plugin: windows_typed_urls **************************
[NTUSER] Parser for Explorer typed URLs Registry data.
Key information.
       Key Path : \Software\Microsoft\Internet Explorer\TypedURLs

+++++++++++++++++++++++++++++++++++++ Data +++++++++++++++++++++++++++++++++++++

[1970-01-01T00:00:00+00:00]
	           url2 : http://go.microsoft.com/fwlink/?LinkId=69157

[2009-08-04T15:14:42.357125+00:00]
	           url1 : http://firefox.com/

**************************** Plugin: winreg_default ****************************
[any] Parser for Registry data.
Key information.
Content Modification Time : 2009-08-04T15:14:42.357125+00:00
       Key Path : \Software\Microsoft\Internet Explorer\TypedURLs

+++++++++++++++++++++++++++++++++++++ Data +++++++++++++++++++++++++++++++++++++
	           url1 : [REG_SZ] http://firefox.com/
	           url2 : [REG_SZ] http://go.microsoft.com/fwlink/?LinkId=69157
--------------------------------------------------------------------------------


--------------------------------------------------------------------------------
```

The same applies when parsing a storage media file:
```
$ preg.py -q -k "\Software\Microsoft\Internet Explorer\TypedURLs" -i test_data/registry_test.dd NTUSER
```

The difference here is that you also need to specify which Registry file to parse. The options are:
 + NTUSER: Goes through all discovered NTUSER Registry files in the storage media file.
 + SOFTWARE:
 + SYSTEM:
 + SECURITY: 
 + USRCLASS: Goes through all discovered USRCLASS Registry files (one for each user) in the storage media file.
 + SAM: 

n.b. this will most likely be changed shortly for the proper Windows behavior, eg: "HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall" rather than the current approach of: "\Microsoft\Windows\CurrentVersion\Uninstall" and then specifically indicate the SOFTWARE Registry file.


### Registry File Mode

One way to parse a Registry file is to use all the available plugins for that particular Registry type. This is the Registry File Mode.

To run the tool in "Registry File Mode" simply provide no options:

```
$ preg.py -q test_data/NTUSER.DAT 

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx Registry File xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

  Registry File : /<PATH>/test_data/NTUSER.DAT
  Registry Type : NTUSER
Registry Origin : OS


--------------------------------------------------------------------------------

----------------------------------- Plugins ------------------------------------

****************************** Plugin: userassist ******************************
[NTUSER] Parser for User Assist Registry data.
Key information.
             Key Path : \Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{75048700-EF1F-11D0-9888-006097DEACF9}\Count

+++++++++++++++++++++++++++++++++++++ Data +++++++++++++++++++++++++++++++++++++

[1601-01-01T00:00:00+00:00]
	UEME_CTLCUACount:ctor : [Count: 2]

[2009-08-04T15:11:22.811067+00:00]
	UEME_RUNPIDL:%csidl2%\MSN.lnk : [Count: 14]
	UEME_RUNPIDL:%csidl2%\Windows Media Player.lnk : [Count: 13]
...
```


### Console Mode

The final mode of operation is using an interactive console that can be used to browse the content of the Registry file and parse individual keys. The console is based on IPython shell that comes pre-loaded with  few magic functions and exposed methods to make things easier. Since this is an IPython shell it can be used to write or load Python code to write one-off scripts to interact with the data or automate tasks.

Some of the commands available in the console are:
 + **cd key** : Navigate the Registry like a directory structure.
 + **ls [-v]** : List all subkeys and values of a Registry key. If called as ls True then values of keys will be included in the output.
 + **parse -[v]** : Parse the current key using all plugins.
 + **plugin [-h] plugin_name** : Run a particular key-based plugin on the loaded hive. The correct Registry key will be loaded, opened and then parsed.
 + **get_value value_name** : Get a value from the currently loaded Registry key.
 + **get_value_data value_name** : Get a value data from a value stored in the currently loaded Registry key.
 + **get_key** : Return the currently loaded Registry key.
 + **hive** [list|open] : List available Registry files and open for interacting with.

To run the tool in console mode against a Registry file:

```
preg.py -c test_data/NTUSER.DAT
```

Since the tool is run against a single Registry file it will be automatically open and ready for interacting with. To list the subkeys under the base key.

```
[16:03:32] NTUSER.DAT
[1] $ ls
dr-xr-xr-x 2009-08-04 15:12:23           [KEY]  AppEvents
dr-xr-xr-x 2009-08-04 15:12:23           [KEY]  Console
dr-xr-xr-x 2009-08-04 15:12:23           [KEY]  Environment
dr-xr-xr-x 2009-08-04 15:12:23           [KEY]  Keyboard Layout
dr-xr-xr-x 2009-08-04 15:12:23           [KEY]  Printers
dr-xr-xr-x 2009-08-04 15:12:23           [KEY]  UNICODE Program Groups
dr-xr-xr-x 2009-08-04 15:12:26           [KEY]  Windows 3.1 Migration Status
dr-xr-xr-x 2009-08-04 15:12:45           [KEY]  Identities
dr-xr-xr-x 2009-08-04 15:13:18           [KEY]  Control Panel
dr-xr-xr-x 2009-08-04 15:21:33           [KEY]  Software

```

The command "ls" lists up all the available subkeys and values for each registry key. The way records are represented is using the standard UNIX folder layout where:

```
dr-xr-xr-x
```

Represents a "directory", which in this case is a Registry key, and:

```
-r-xr-xr-x
```

Represents a "file", which in this case is a Registry value. If the listing is of a Registry key (sub directory) then a timestamp is displayed next to the mode string. The timestamp is the Registry key's last modification time in UTC.

Additionally before the name of the file/directory there is an additional type inside brackets. This would be something like:

 + "[KEY]" for a directory entry or a subkey, 
 + "[REG_SZ]" for a regular string value, 
 + "[REG_MULTI_SZ]" for a multi string value, etc.

To navigate the Registry the command ```cd``` can be used. One thing to note is that directory entries are divided by a backslash and there is no need to escape the backslash, that is to get into the directory or the Registry key "Microsoft\Windows" there is no need to escape the backslash as
normally would be required, that is "Microsoft\\Windows".

To open up the "*Software*" key:

```
[16:03:34] NTUSER.DAT
[2] $ cd Software
```

After navigating to a new key it is always possible to see in which key you are located by the path that is included in each line or by typing ```pwd```. And to see subkeys or subkeys alongside their values, use the "ls" command. With the verbose settings values are included (if possible).

```
[16:04:42] /PATH/test_data/NTUSER.DAT
\Software [3] $ pwd
\Software

[16:04:44] /PATH/test_data/NTUSER.DAT
\Software [4] $ ls
dr-xr-xr-x 2009-08-04 15:12:23           [KEY]  Intel
dr-xr-xr-x 2009-08-04 15:12:23           [KEY]  Netscape
dr-xr-xr-x 2009-08-04 15:12:24           [KEY]  Policies
dr-xr-xr-x 2009-08-04 15:16:34           [KEY]  Clients
dr-xr-xr-x 2009-08-04 15:18:34           [KEY]  JavaSoft
dr-xr-xr-x 2009-08-04 15:19:21           [KEY]  Microsoft
dr-xr-xr-x 2009-08-04 15:21:33           [KEY]  Jetico

[16:08:47] /PATH/test_data/NTUSER.DAT
\Software [3] $ cd \Software\Microsoft\Windows NT\CurrentVersion\Winlogon

[16:08:56] /PATH/test_data/NTUSER.DAT
\Software\Microsoft\Windows NT\CurrentVersion\Winlogon [4] $ ls -v
-r-xr-xr-x                            [REG_SZ]  ExcludeProfileDirs         Local Settings;Temporary Internet Files;History;Temp
-r-xr-xr-x                            [REG_SZ]  ParseAutoexec              1
-r-xr-xr-x                      [REG_DWORD_LE]  BuildNumber                2600

```

One thing to note is that tab completion is available. If you press "<TAB>" after the command ```cd``` it will try to auto-complete all values of subkeys.

There is also the verbose settings of both the ```ls``` and ```parse``` command. What the verbose settings does is to add additional information to the dataset:

 + ls -v prints out value data as well as the value names.
 + parse -v includes hexadecimal representation of binary values from the extracted event as well as including a full hexadecimal representation of the key itself.

To parse a registry key, navigate to it and use the command ```parse```.

```
[16:09:00] /PATH/test_data/NTUSER.DAT
\Software\Microsoft\Windows NT\CurrentVersion\Winlogon [5] $ parse

----------------------------------- Plugins ------------------------------------

**************************** Plugin: winreg_default ****************************
[any] Parser for Registry data.
Key information.
Content Modification Time : 2009-08-04T15:12:26.794625+00:00
          Key Path : \Software\Microsoft\Windows NT\CurrentVersion\Winlogon

+++++++++++++++++++++++++++++++++++++ Data +++++++++++++++++++++++++++++++++++++
	       BuildNumber : [REG_DWORD_LE] 2600
	     ParseAutoexec : [REG_SZ] 1
	ExcludeProfileDirs : [REG_SZ] Local Settings;Temporary Internet Files;History;Temp
--------------------------------------------------------------------------------
```

And to display the hexadecimal representation:

```
[16:17:38] /PATH/test_data/NTUSER.DAT
\Software\Microsoft\Windows NT\CurrentVersion\Winlogon [3] $ parse -v

----------------------------------- Plugins ------------------------------------

**************************** Plugin: winreg_default ****************************
[any] Parser for Registry data.
Key information.
Content Modification Time : 2009-08-04T15:12:26.794625+00:00
          Key Path : \Software\Microsoft\Windows NT\CurrentVersion\Winlogon

+++++++++++++++++++++++++++++++++++++ Data +++++++++++++++++++++++++++++++++++++
	       BuildNumber : [REG_DWORD_LE] 2600
	     ParseAutoexec : [REG_SZ] 1
	ExcludeProfileDirs : [REG_SZ] Local Settings;Temporary Internet Files;History;Temp

------------------------ Hexadecimal output from event. ------------------------
0000000: 6e6b 2000 0a69 19fa 1515 ca01 0000 0000  nk ..i..........
0000010: 3826 0300 0000 0000 0000 0000 ffff ffff  8&..............
0000020: ffff ffff 0300 0000 e834 0300 8000 0000  .........4......
0000030: ffff ffff 0000 0000 0000 0000 2400 0000  ............$...
0000040: 6a00 0000 0000 0000 0800 0000 5769 6e6c  j...........Winl
0000050: 6f67 6f6e d8ff ffff 766b 0d00 0400 0080  ogon....vk......
0000060: 3100 0000 0100 0000 0100 08ea 5061 7273  1...........Pars
0000070: 6541 7574 6f65 7865 63b3 7700 d0ff ffff  eAutoexec.w.....
0000080: 766b 1200 6a00 0000 7834 0300 0100 0000  vk..j...x4......
0000090: 0100 0000 4578 636c 7564 6550 726f 6669  ....ExcludeProfi
00000a0: 6c65 4469 7273 0000 0000 0000 90ff ffff  leDirs..........
00000b0: 4c00 6f00 6300 6100 6c00 2000 5300 6500  L.o.c.a.l. .S.e.
00000c0: 7400 7400 6900 6e00 6700 7300 3b00 5400  t.t.i.n.g.s.;.T.
00000d0: 6500 6d00 7000 6f00 7200 6100 7200 7900  e.m.p.o.r.a.r.y.
00000e0: 2000 4900 6e00 7400 6500 7200 6e00 6500   .I.n.t.e.r.n.e.
00000f0: 7400 2000 4600 6900 6c00 6500 7300 3b00  t. .F.i.l.e.s.;.
0000100: 4800 6900 7300 7400 6f00 7200 7900 3b00  H.i.s.t.o.r.y.;.
0000110: 5400 6500 6d00 7000 0000 0000 f0ff ffff  T.e.m.p.........
0000120: 2034 0300 4834 0300 f834 0300 d8ff ffff   4..H4...4......
0000130: 766b 0b00 0400 0080 280a 0000 0400 0000  vk......(.......
--------------------------------------------------------------------------------
```

At any time if you want to get back to the base key type the ```cd``` command without parameters.

```
[16:17:38] /PATH/test_data/NTUSER.DAT
\Software\Microsoft\Windows NT\CurrentVersion\Winlogon [4] $ cd

[16:18:37] /PATH/test_data/NTUSER.DAT
\ [5] $ 
```

The same applies when using the console mode against a storage media file. Except that it is possible to have more than a single Registry file available.

```
$ preg.py -c -i test_data/registry_test.dd
...
More than one Registry file ready for use.

Index Hive [collector]
0     /Users/smith/NTUSER.DAT [TSK]
1     /Windows/System32/config/SAM [TSK]
2     /Users/foobar/NTUSER.DAT [TSK]
3     /Users/Default/NTUSER.DAT [TSK]
4     /Windows/System32/config/SYSTEM [TSK]

Use "hive open INDEX" to load a Registry file and "hive list" to see a list of available Registry files.

Happy command line console fu-ing.
[08:34:18] NO HIVE LOADED
[1] $ 

```

At this point no Registry file is loaded in and thus none of the commands work until one file is opened using the ```hive open``` command.

```
[1] $ hive list
Index Hive [collector]
0     /Users/smith/NTUSER.DAT [TSK]
1     /Windows/System32/config/SAM [TSK]
2     /Users/foobar/NTUSER.DAT [TSK]
3     /Users/Default/NTUSER.DAT [TSK]
4     /Windows/System32/config/SYSTEM [TSK]

To open a Registry file, use: hive open INDEX
```

At any time you can use the ```hive list``` to see a list of available Registry files to open.

```
[2] $ hive open 2
Opening hive: /Users/foobar/NTUSER.DAT [TSK]

[08:36:02] /Users/foobar/NTUSER.DAT
[3] $ ls
dr-xr-xr-x 2010-11-10 07:50:39           [KEY]  AppEvents
dr-xr-xr-x 2010-11-10 07:50:39           [KEY]  Console
dr-xr-xr-x 2010-11-10 07:50:39           [KEY]  EUDC
dr-xr-xr-x 2010-11-10 07:50:39           [KEY]  Environment
dr-xr-xr-x 2010-11-10 07:50:39           [KEY]  Printers
dr-xr-xr-x 2010-11-10 07:50:39           [KEY]  System
dr-xr-xr-x 2010-11-10 07:50:45           [KEY]  Keyboard Layout
dr-xr-xr-x 2010-11-10 10:17:48           [KEY]  Control Panel
dr-xr-xr-x 2010-11-10 10:40:50           [KEY]  Identities
dr-xr-xr-x 2012-04-06 14:09:23           [KEY]  Software
dr-xr-xr-x 2012-04-06 14:09:25           [KEY]  Network

[08:36:04] /Users/foobar/NTUSER.DAT
[4] $ 
```

To open up a particular Registry file use the ```hive open INDEX``` command, which loads the Registry file, at which point you'll see the prompt changing from ```NO HIVE LOADED``` to the path of the loaded Registry file. Now all the same commands can be used as before.