#RequireAdmin ;Requires admin to run.
#include <MsgBoxConstants.au3>
#include <Array.au3>
#include <Chrome.au3>
#include <AutoItConstants.au3>


MsgBox(0, "Title Of Box", "A message for telling the user about input of mouse/keyboard.") ;Melding til brukeren om hva som skjer framover.

BlockInput($BI_DISABLE) ; Blocks any input from keyboard/mouse.
_ChromeShutdown() ; Shutdown Chrome.exe

ChromeStartAnd()
Func ChromeStartAnd()
	Local $folder64 = "C:\Program Files\Google\Chrome\Application\chrome.exe" ; Where the x64 install is.
	If FileExists($folder64) Then _ChromeStartup("www.google.no", "C:\Program Files\Google\Chrome\Application\chrome.exe") ; Start chrome with this page if x64.

	Local $folder32 = "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe"
	If FileExists($folder32) Then _ChromeStartup("https://google.no", "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe") ; Start Chrome with this page if x32.


	; Wait for the page with the document title of "_IE_Example('form')"
	_ChromeDocWaitForExistenceByTitle("This text must match the Chrome Tab-name", 6)

	Send("{CTRLDOWN}") ; Holds down CTRL.
	Send("{SHIFTDOWN}") ;Holds down SHIFT
	Send("{J}")        ;Press J !NOTE This might be different depending on locale, find your shortcut in Console>Settings.
	Send("{CTRLUP}") ;Release CTRL
	Send("{SHIFTUP}") ;Release SHIFT

	Sleep(2000) ; Wait 2 sec.
	Send("{ENTER}") ; Press ENTER once, to exec.
	Sleep(1000) ; Wait 1 sec.
	ClipPut("localStorage.setItem('rulesets', JSON.stringify ([  {    ") ; This copies a line to the console. 1/3
	Send("^v") ; Paste the line 1/3.
	Sleep(200) ; Wait 0.2 Sec.
	ClipPut('"enabled": true,    "description": "Hello,    "url": ".*\\google\\.no",    "filename": "PDF-name1\\.(epub|mobi|pdf)$",    "pattern": "ThisFolder/"  }') ; This is just an example. 2/3
	Send("^v") ; Paste the line 2/3.
	Sleep(200) ; Wait 0.2 Sec
	ClipPut(' ,{    "enabled": true,    "description": "Goodbye",    "url": ".*\\google\\.no",    "filename": "PDF-name2\\.(epub|mobi|pdf)$",    "pattern": "NotThisFolder/"  }]));') ; This is just an example. 3/3.
	Send("^v") ; Paste the line 3/3.
	Sleep(500) ; Wait 0.5 sec.
	Send("{ENTER}") ; Press ENTER once, to execute
	Sleep(500) ; Wait 0.5 sec.
	Send("{F5}") ; Press F5 once, to refresh
	; Close any existing Chrome browser
	_ChromeShutdown()
	BlockInput($BI_ENABLE) ; Opens for input..

	MsgBox(0, "OK", "This should represent some info to the user.") ; Message to the user.
EndFunc   ;==>ChromeStartAnd
