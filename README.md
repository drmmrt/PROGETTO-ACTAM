# URJ-3000 - ACTAM PROJECT

## INTRODUCTION
The main goal of our project is to implement a multifunctional system wich is able to give to the executor a creative tool for music production and live sessions, just using his laptop.

The project is a web application developed using HTML, JS and CSS. We used HTML in order to define the static interface and structure of the page, CSS to apply some style attributes to the page components and JS to render the dynamic components of the page and manage all the user interactions with the page.

![image](https://user-images.githubusercontent.com/99413338/153466062-5cc4423d-43fd-4890-80d6-a4aeb47b87f2.png)

## USER INTERFACE
Our system is carachterised by three main sections:

## Recorder
This sort of "Talkbox" allows the executor to record his voice or an instrument through the mic input.
![image](https://user-images.githubusercontent.com/99413338/153432794-0ae2fb83-6d11-425a-a3ce-8d7c38b9004a.png)

Starting from the lower buttons, the ON/OFF switcher activate the recorder, and the REC button allows you to start and stop the recording whenever you want.

![image](https://user-images.githubusercontent.com/99413338/153433034-aab30257-6e64-4cb9-aae1-751ccfc7cbb6.png)

It is possible can select a sample of the recording trough the two knobs implemented in the middle section: 
with the upper one you can choose where the sample starts, and with the lower one where the sample ends.

![image](https://user-images.githubusercontent.com/99413338/153433138-886f48d0-3493-4c97-8722-b658699dc605.png)

If you  want to hear and check what you have selected trough the knobs, there is a button TEST that allows you to do that.

![image](https://user-images.githubusercontent.com/99413338/153433223-6e29ee1a-083f-4da1-8dd5-3413734c352c.png)

On the upper section there is the "Randomizer",a granular tool which takes random particles of the recorded signal and is activated by pressing the RND button. In this section you can also select the random speed with a slider that goes from 0.1 to 3.0: the system starts playing some random particles of the recording, that have the same length of the main section and change with the selected velocity. 

![image](https://user-images.githubusercontent.com/99413338/153433303-526d4a5e-42eb-457a-86a7-2c3c974d6be0.png)

![image](https://user-images.githubusercontent.com/99413338/153433352-55bc4eff-e172-469f-9b08-b8227ce1db3f.png)![image](https://user-images.githubusercontent.com/99413338/153433369-01852615-c73b-4ca8-91f1-381efa337969.png)
    Fig.1 : selected section and random function OFF                                
    Fig.2 : selected section and random function ON
    
## Synth
In this section a polyphonic synth is implemented. 

![image](https://user-images.githubusercontent.com/99413338/153464379-2acbafb0-bef0-49e9-8529-d063989ce5c8.png)

In the lower section, there is a 2-octave keyboard and some buttons: 

the ON/OFF, the octave selector, where pressing + or – you can go up or down by an octave, and the switcher TALK/PLAY:  when the switcher is set on PLAY, the keyboard works for the synth section, but when is set to TALK, the keyboard becomes a pitch modulator for the recorder explained before. 

![image](https://user-images.githubusercontent.com/99413338/153434291-389e52cb-223f-4bc0-bb53-c7f2f1fede18.png)![image](https://user-images.githubusercontent.com/99413338/153434325-1bfb048d-f53f-403c-b10c-28db4d815aa8.png)

In the middle section there are two different tools: 
On the left, there is a waveshape selector, where you can choose the shape of your soundwave between: sine, triangular, square or sawtooth. 

![image](https://user-images.githubusercontent.com/99413338/153434422-5343a02f-76f0-4e7b-9eee-7e47e5ee4203.png)

On the right side there is the envelopes secition, where you can set the attack, sustain, decay, release and the main gain of the notes. There is also a canvas where you can directly visualize the final result.

![image](https://user-images.githubusercontent.com/99413338/153465328-3a4dde02-4fa7-4e36-9923-ade36f92f57a.png)

On the upper section there is a canvas where you can see the final wave emitted by the synth. 
![image](https://user-images.githubusercontent.com/99413338/153434588-c0cf5a3d-7dad-4618-85b8-952ba4181a8c.png)


## Effect Rack

![image](https://user-images.githubusercontent.com/99413338/153434708-3bf57136-1232-46c8-80e1-a008fd583f21.png)

In this section some effects for the synth are implemented: starting from the left, there is a filters section, divided in low-pass and high-pass,  an echo section, where you can set the delay and the gain, and a frequency difference section, where you can set the detune value.
All these function are implemented with some sliders. 
There is also a window on the left where you can select some presets for the envelopes and  the effects. For this last feature 


## Some peculiar functions 

### Random

First of all we defined a function setIntervalX, that can call a function for a certain number of time ("repetitions" input) after a delay
Then we implemented the PlayRandom function: we compare the length of the selected section(in seconds) with the updating random speed. In the case that the section is longer, the function plays a shorter section with duration equal to the random speed. On the other hand, if the section is shorter, the function plays the section X times, where X = DecNumber + IntNumber.

![image](https://user-images.githubusercontent.com/99413338/153580590-40913452-f748-4e76-a212-1667e7577f56.png)

In order to update the random sections, we implemented the updateRandom function: we set a random value for the start of the section, and then we set the end at the same distance of the main section's length (choosed with the two knobs of the recorder). The CheckOutOfBondsRandom function allows us to check that the random bounds do not exceed the canvas size.

![image](https://user-images.githubusercontent.com/99413338/153580200-3d2fbe34-a256-488b-a466-9f7765dd07e6.png)

### playNote

This function assigns 3 oscillator to each note. With this arrrangement a superposition of 3 oscillators is implemented, where the central takes the frequency from nFreq and is matched with the other two, which are positively/negatively shifted in frequency by a delta value w.r.t the central one. 

Moreover it defines the low-pass/hi-pass filters and the echo with all their parameters. All of them are after connected to a gain, which is linked with the Envelope parameters.

![playnote](https://user-images.githubusercontent.com/82934687/153707871-a9445e68-474f-48e6-93a2-3dba8dbf4867.png)
![playnote1](https://user-images.githubusercontent.com/82934687/153707881-0897e309-3817-4fd9-8842-5368021dd0d3.png)
![platnote2](https://user-images.githubusercontent.com/82934687/153707892-1a1b99a7-f197-4df8-bd39-cdc650e78d56.png)


### stopNote

This function basically set the time values of when the gain needs to be active using a setValue for the amplitude behaviour and a linearRamp to establish the time starting point (currentTime) and the ending point ('release' from the envelope).

Furthermore a 'stop' is imposed for the 3 oscillators giving as time duration the same release value as before. A little time shift is added on each oscillator to avoid "click" sound when the sound stops. (?)
![stopnote](https://user-images.githubusercontent.com/82934687/153707901-22833387-4683-4df2-8986-ac3c5c741c3a.png)


# Firebase Part

We thaught that the possibility to safe a proper set of values by the user could be a very useful feature. In order to to that we used the serverless platform Firebase as a database where to put the list of values of the settings choosen by the user.

![firebase1](https://user-images.githubusercontent.com/82934687/153708750-0495ba47-0cf3-4bd2-8588-3638cb8c02fb.png)

This function allows you through a dropdown window to select the proper preset of values that you want to use. A simple pop-up reminds you to the firebase folder where you can complete the personalization. 

![firebase2](https://user-images.githubusercontent.com/82934687/153708759-d2558912-2726-4ba8-9aeb-6706c1d1a230.png)

This function has the task to upload and save the set of choosen values of all the features in the firebase database. 





# Group Components

- Umberto Derme
- Riccardo Di Palma
- Jacopo Caucig



