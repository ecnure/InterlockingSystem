# step 1: problem description of InterlockingSystem


# step 2: description of Interlocking system in PF-CCSL

Problem InterlockingSystem
beginP
endP
M: "Interlocking system” {}
C:"Onboard system" {
    responseOfTrain = enter + wait,
    request ~ enter + wait,
responseOfLight = showRed + showGreen,
showRed < wait,
showGreen < enter,
enter < leave,
request- responseOfTrain <= 50}
C: "Signal Light" {
greenPulse <= showGreen,
redPulse <= showRed,
greenPulse - showGreen <= 30,
redPulse - showRed <= 30 }
C: "Track" {
inquiry < responseOfTrack
responseOfTrack = checkSuccess + checkFail
inquiry - responseOfTrack <= 30
enter = startOccupied 
leave = startUnoccupied
}
ST: Track + Signal{
checkFail < redPulse
checkSucc < greenPulse
checkFail - showRed < 40
checkSucc - showGreen < 40
}
TOS: Track + Onboard System +Signal Light
{checkSucc < greenPulse
checkFail < redPulse  
request < inquiry
request < response
showGreen < enter
showRed < wait
}

# Step 3: change

# step 4: consistency checking

# step 5: Specification derivation 

