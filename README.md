# HANTEK-HM305P/HM310P-USB



## Tools
- Windows Computer

- USB-A cord

## Download the repository 
- You can git clone or ZIP file

## Device Setup
- Plug in the USB-A cord into your computer and the power supply.

- Open ***Device Manager*** on your windows machine.
- 
![Screenshot 2022-04-17 050209](https://user-images.githubusercontent.com/83417785/163708110-de8bfc37-fa26-49dc-9735-021e51673911.jpg)

- Find ***Ports (COM & LPT)***

- Look for ***USB-SERIAL CH340 (COMX)***

- ***X*** Represents the COM port the device is on
   - The port number is subject to change after disconnecting the device

## Settings

- Navigate to and open the ```Settings/WSComSet.XML``` file

![Screenshot 2022-04-17 050941](https://user-images.githubusercontent.com/83417785/163708112-171870e4-35c0-4884-99c1-6a547dcacd1b.jpg)

- Change the ***X*** to the port number from device manager ```<PortName>COMX</PortName>```

- Navigate to and open the ```Settings/DevicesClassInfo.XML``` file

- Make sure ***Line 153*** looks like this ```<PowerSwitchAddr>0x0001</PowerSwitchAddr>```

- Make sure the device is off 
- Then hold down the power output button and at the same time power the unit on

![Screenshot 2022-04-17 054309](https://user-images.githubusercontent.com/83417785/163709147-29a78237-17d2-458b-b75e-80d1ec2d32e3.jpg)
![Screenshot 2022-04-17 054251](https://user-images.githubusercontent.com/83417785/163709148-7c6d7eab-ea7f-47c5-96e5-547b09bd559b.jpg)

- This opens the device in hidden menu mode
- Make sure is looks like the image below 
- If it doesn't show  ```Addr 001``` Use ```M3``` to Increase the value and ```M4``` to Decrease it

![Screenshot 2022-04-17 054341](https://user-images.githubusercontent.com/83417785/163709149-aaa36771-4cc6-47e4-a463-ef582d6f63cf.jpg)


## Usage 
#### Simple Uses
- Open the ```PowerDC.exe``` file to launch the application
- Set the Voltage(V) and Current(A) to your desired values and click the designated ***Setting*** buttons to send the values to the power supply.

![Screenshot 2022-04-17 051248](https://user-images.githubusercontent.com/83417785/163708243-14c13993-5dc5-4ae7-ab3a-14ab0b65ac06.jpg)

- If everything worked properly, you will get a ***Setting success!*** pop-up

![Screenshot 2022-04-17 154725](https://user-images.githubusercontent.com/83417785/163828289-44ce7c77-3515-4790-8bca-cf817967db55.jpg)

## Create Presets
- Navigate to and open the ```Settings/AutoControlValue.XML``` file 
- Copy and paste one of the preset blocks
  - Change the X to a different number```<ListX>```
  - Change any other values you'd like inside each parameter
- ```<Sation WSname="DefaultDevice" ListCount="2" LoopCount="10">```
  - **WSname="DefaultDevice"** Text on the Preset Activation/Deactivation button
  - **ListCount="2"** Number of presets in the loop
  - **LoopCount="10"** Number of times to loop through the list of presets
- Example Parameters:
```
<AutoControlValue> 
  <Sation WSname="DefaultDevice" ListCount="2" LoopCount="10">
    <List0>
      <ClMode>OnlyAdjustableVoltageType</ClMode>
      <ClVoltage>12</ClVoltage>
      <ClCurrent>3.2</ClCurrent>
      <ClPower>0</ClPower>
      <ClErrorDis>0</ClErrorDis>
      <ClTimeAjust>0</ClTimeAjust>
      <ClTimeSpans>10000</ClTimeSpans>
      <ClEnble>True</ClEnble>

      <ClMode>OnlyAdjustableVoltageType</ClMode>
      <ClVoltage>6</ClVoltage>
      <ClCurrent>1.5</ClCurrent>
      <ClPower>0</ClPower>
      <ClErrorDis>0</ClErrorDis>
      <ClTimeAjust>0</ClTimeAjust>
      <ClTimeSpans>10000</ClTimeSpans>
      <ClEnble>True</ClEnble>

    </List0>
  </Sation>
</AutoControlValue> 
 
```

#### Presets
- Click on the ***Default Device Button***

![Screenshot 2022-04-17 175323](https://user-images.githubusercontent.com/83417785/163828288-bb45029f-2a91-4eb9-ab99-569b4d2d4af7.jpg)

- If there are any presets created, they will appear in the box below
- Each preset has a *(Model, Voltage, Current, Power, Duration(ms), Inaccuracy, GapOfAdjustment, and Enable)*
- To use the preset Double-Click on the ***Default Device Button***
- You will then be prompted to turn on the device if it is not turned on. Click on ***Yes*** to turn the device on or manually do it

![Screenshot 2022-04-17 174914](https://user-images.githubusercontent.com/83417785/163828293-373b822d-80a3-4895-9fe0-b6a5dd8e495e.jpg)

- The software will then start looping between all of the presets that are currently ***Enabled***
- The duration each preset will be active is set by ***Duration(ms)***
- Example:
  -  Preset0 *( Duration = 6000ms ) (Voltage = 5V) (Current = 0.500A)*
  -  Preset1 *( Duration = 9000ms ) (Voltage = 3V) (Current = 0.250A)*
  -  The process will begin with ***Preset0*** and set the Voltage to ***5V*** and Current to ***0.5A*** for ***6 Seconds***
  -  Then it will change to ***Preset1*** and set the Voltage to ***3V*** and Current to ***0.25A*** for ***9 Seconds***
  -  Finally, after ***9 Seconds*** the device will restart the loop and set the device to ***Preset0*** 
- To stop the loop. Double-Click on the ***Default Device Button*** again. You will be prompted with "Device Control" Click ***Yes*** to turn everything off

![Screenshot 2022-04-17 174953](https://user-images.githubusercontent.com/83417785/163828284-11a21bf5-eb15-4b16-82b2-4f590ca8b961.jpg)

- You will then be prompted with "Device is not shutdown" Click ***Yes*** again

![Screenshot 2022-04-17 175141](https://user-images.githubusercontent.com/83417785/163828286-1fcd57d8-7998-40c6-a7d8-ae8a3b5ab813.jpg)


## Data Visualization
- On the left the Application also Information Section and 3 graphs From top to bottom (Voltage, Current, Power)
- The Information Section has *(Device Information, Maximum (Voltage, Current, Power), Over(Voltage, Current, Power), NumberExecution, ExecutedToList, TimeToTheNext)*
- **NumberExecution:** The number of times the device has looped through all the enabled presets
- **ExecutedToList:** Number of presets in the loop
- **TimeToTheNext:** Time left until the next preset

![Screenshot 2022-04-17 174841](https://user-images.githubusercontent.com/83417785/163828291-67bd1589-86e2-4bcf-8241-66e3152e1096.jpg)

## Data Collection
- Navigate to and open the ```Log``` folder
- There you will find all the data visualized on the graphs with timestamps and device data collected
