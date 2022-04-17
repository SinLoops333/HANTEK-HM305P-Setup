# HANTEK-HM305P/HM310P-USB

## Tools
- Windows Computer

- USB-A cord

## Download the repository 
- You can git clone or ZIP file

## Device Setup
- Plug in the USB-A cord into your computer and the power supply.

- Open ***Device Manager*** on your windows machine.

- Find ***Ports (COM & LPT)***

- Look for ***USB-SERIAL CH340 (COMX)***

- ***X*** Represents the COM port the device is on
   - The port number is subject to change after disconnecting the device
## Settings

- Navigate to and open the ```Settings/WSComSet.XML``` file
- Change the ***X*** to the port number from device manager ```<PortName>COMX</PortName>```

## Usage 
#### Simple Uses
- Open the ```PowerDC.exe``` file to launch the application
- Set the Voltage(V) and Current(A) to your desired values and click the designated ***Setting*** buttons to send the values to the power supply.

## Create Presets
- Navigate to and open the ```Settings/AutoControlValue.XML``` file 
- Copy and paste one of the preset blocks
  - Change the X to a different number```<PresetX>```
  - Change any other values you'd like inside each parameter
- ```<Sation WSname="DefaultDevice" ListCount="2" LoopCount="10">```
  - **WSname="DefaultDevice"** Text on the Preset Activation/Deactivation button
  - **ListCount="2"** Number of presets in the loop
  - **LoopCount="10"** Number of times to loop through the list of presets
- Example Parameters:
```<AutoControlValue>
  <Sation WSname="DefaultDevice" ListCount="2" LoopCount="10">

    <Preset0>
      <C1Mode>OnlyAdjustableVoltageType</C1Mode>
      <C1Voltage>5.0</C1Voltage>
      <C1Current>0.500</C1Current>
      <C1Power>0</C1Power>
      <C1ErrorDis>0</C1ErrorDis>
      <C1TimeAjust>0</C1TimeAjust>
      <C1TimeApans>6000</C1TimeApans>
      <C1Enable>True</C1Enable>
    </Preset0>

    <Preset1>
      <C1Mode>OnlyAdjustableVoltageType</C1Mode>
      <C1Voltage>3.0</C1Voltage>
      <C1Current>0.250</C1Current>
      <C1Power>0</C1Power>
      <C1ErrorDis>0</C1ErrorDis>
      <C1TimeAjust>0</C1TimeAjust>
      <C1TimeApans>9000</C1TimeApans>
      <C1Enable>True</C1Enable>
    </Preset1>

  </Sation>
</AutoControlValue> 
```

#### Presets
- Click on the ***Default Device Button***
- If there are any presets created, they will appear in the box below
- Each preset has a *(Model, Voltage, Current, Power, Duration(ms), Inaccuracy, GapOfAdjustment, and Enable)*
- To use the preset Double-Click on the ***Default Device Button***
- You will then be prompted to turn on the device if it is not turned on. Click on ***Yes*** to turn the device on or manually do it
- The software will then start looping between all of the presets that are currently ***Enabled***
- The duration each preset will be active is set by ***Duration(ms)***
- Example:
  -  Preset0 *( Duration = 6000ms ) (Voltage = 5V) (Current = 0.500A)*
  -  Preset1 *( Duration = 9000ms ) (Voltage = 3V) (Current = 0.250A)*
  -  The process will begin with ***Preset0*** and set the Voltage to ***5V*** and Current to ***0.5A*** for ***6 Seconds***
  -  Then it will change to ***Preset1*** and set the Voltage to ***3V*** and Current to ***0.25A*** for ***9 Seconds***
  -  Finally, after ***9 Seconds*** the device will restart the loop and set the device to ***Preset0*** 
- To stop the loop. Double-Click on the ***Default Device Button*** again. You will be prompted with "Device Control" Click ***Yes*** to turn everything off
- You will then be prompted with "Device is not shutdown" Click ***Yes*** again
## Data Visualization
- On the left the Application also Information Section and 3 graphs From top to bottom (Voltage, Current, Power)
- The Information Section has *(Device Information, Maximum (Voltage, Current, Power), Over(Voltage, Current, Power), NumberExecution, ExecutedToList, TimeToTheNext)*
- **NumberExecution:** The number of times the device has looped through all the enabled presets
- **ExecutedToList:** Number of presets in the loop
- **TimeToTheNext:** Time left until the next preset
- 
## Data Collection
- Navigate to and open the ```Log``` folder
- There you will find all the data visualized on the graphs with timestamps and device data collected
