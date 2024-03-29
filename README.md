
# Promodeler ERCF Servo Upgrade
#### Using the ProModeler DS105CLHV Servo  
##### Disclaimer: I am not an affiliate of ProModeler and I don't get any sort of compensation from ProModeler for this. I just like their stuff. It's some of the best on the market and far more reasonably priced than servos of competing quality.
### [Click here for more info on the servo or to buy](https://www.promodeler.com/DS105CLHV)

## Pictures
![In the box.jpg](https://github.com/IRTrail/ERCF_Servo_Upgrade/blob/main/images/In%20the%20box.jpg?raw=true)
![Open Box.jpg](https://github.com/IRTrail/ERCF_Servo_Upgrade/blob/main/images/Open%20Box.jpg?raw=true)
## Why do you *need* it?  
- Well, because it is a high quality servo that pretty much blows others out of the water...at a reasonable price.  
-- Most other high-end servos like this are double (or more) cost. Others aren't made by a guy who answers emails.  
-- Others aren't made by a guy that actually does RC and knows how much quality matters.  
-- Others aren't made by John Beech, engineer, electronics guru, and all-around good guy.  
- The specs are listed under the `Specifications` tab on the link above. You'll notice, that for the input voltage, the ProModeler servo has **46%** more torque at 4.8V than the paltry Savox offering. The MG90S is simply a wet tissue in comparison.  
- This servo has a CNC aluminum housing. How cool is that?  
- This servo has a 25T spline, which is compatible with most servo arms, not that the ERCF uses standard servo arms, but standardization is good for the end user.  
- It uses a...wait for it...M3 servo screw. No more hunting for a M2.5, M2, M-whatever that only fits your specific servo because you dropped the only one in existence into the ethereal plane which swallows important screws, 10MM sockets, and single socks for all eternity. Just grab another M3 button head from your stash and laugh at the infernal depths of screw stealing madness.  
- It is **quiet**. Seriously, compared to a MG90s, this thing whispers instead of coughs like your old crazy uncle that smokes too much.
- ProModeler servos are used by the military. [They're also used to aim high precision lasers.](https://www.promodeler.com/profiles/NPL-ProModeler-and-steering-lasers)  
- ![](https://i.makeagif.com/media/8-09-2015/4F7n75.gif) 
## Important notes:
##### Don't back drive your servo.
Seriously just don't. Back driving is moving the servo arm by hand. It's not good for the servo. This servo has a 480:1 gear ratio and back driving can impart huge stresses on the gear train, not to mention spinning the servo motor at insane speeds. Back EMF could be a thing if you have it plugged into the MMU board already, just like moving the stepper motors for the X, Y, and Z axes will eventually fry your MCU.
The ProModeler website is full of warnings about it. It can **VOID YOUR WARRANTY**. So just don't. It's not a great idea for any servo, if we're honest. So don't. Have I mentioned...don't back drive your servo?
## Great. What other stuff do I need?
Good question. You'll need the following:
1) [A servo arm](STL/Servo%20Arm%20ProModeler.STL). This servo has 25T splines and neither of the other available servo arms work. So, I made one for you. Depending on your printer tolerances, it will be from a perfect fit to impossible to install. Tweak your extrusion modifier and print another if the fit isn't correct.
-- **Print the servo arm with very thin layers**. I usually print mine with 0.12mm layers and shoot for 0.18mm first layer. This helps define the spline better and get a more perfect fit.
2) A servo extension. ProModeler has several lengths [here](https://www.promodeler.com/extensions) and guess what. They have a locking tab. How cool is that? Order one when you order your servo. Yes, you can craft your own, but why crimp another connection when you can let someone else?
-- A good approximation of the extension length needed is (315 + (number of gates * 23.05)) * 1mm and round to the nearest 10mm.  
(I currently have a 6 gate ERCF in V2 spec. The numbers below are for reference only and not tested)

| Gates | Length (mm) | Length (in) |
|-------|-------------|-------------|
| 4     | 410         | 16.14       |
| 6     | 450         | 17.72       |
| 8     | 500         | 19.69       |
| 12    | 590         | 23.23       |

3) [A servo mount](STL/Servo%20Mount%20Promodeler.STL). This servo has slightly different geometry from either the MG90S or the Savox SH-0225MG, and thus needs a new mount.
4) [A new idler block](STL/Linear%20Axis%20Idler%20Block%20ProModeler.STL). The pocket for the servo has been deepened by 2.2mm to accommodate the extra badassitude of the ProModeler.
5) The wire bracket for the selector cart. You really don't want to snip the wire on such a nice servo do you? I didn't either. Use a different selector bracket so your servo wire doesn't need snipped. [The one from GNeu42 looks promising.](https://github.com/Enraged-Rabbit-Community/ERCF_v2/tree/master/User_Mods/Gneu42/Selector_Drag_chain_Anchor_with_servo_connectors) 
6) A couple 2mm self tappers or 2mm socket head cap screws. The important thing here is they can't be longer than 5mm or they'll poke through and prevent the springiness of the Springy servo mount from springing. If you don't have something 5mm or shorter, file them down, or hit them with a Dremel. Just don't do it with the servo in place and screw up the finish on your new blingified servo.
## So, how do I install it?
Well, pretty much like you installed the other servo options. Although, you'll need to replace the idler block as well. Make sure you don't put the servo arm on before powering up the servo. You'll want to leave it off. FIrst, put the servo in the UP position. **Only after the servo is in the up position should you install the arm** with the leg as close to the servo housing as possible. But **make sure it isn't installed on initial power up** so the servo doesn't stall before it's set up in Happy Hare.

Note: It's ok to pre-install the servo arm on the servo to make it fit well before the initial power up, just remember to remove it before power up.  

According to the specs, this servo has a 150° range based on 800-200 microsecond pulsewidth. So, you'll want to adjust those in `mmu_hardware.cfg`.
![image](https://github.com/IRTrail/ERCF_Servo_Upgrade/assets/53546870/0aa39d75-b85b-4ac4-a3d6-adae336fc721)  

Calibrate the servo as normal and set the springy bolt to suit. You don't want it so tight it stalls the servo. Just enough to engage the gears firmly. For servo calibration routine, see [Page 127 in the ERCF V2 build manual](https://github.com/IRTrail/ERCF_v2/blob/master/Documentation/ERCF_v2_Manual.pdf)  and [Happy Hare servo calibration](https://github.com/moggieuk/Happy-Hare/blob/main/doc/calibration.md#step-2-calibrate-your-servo).  

For reference only, my numbers are 30 for the up position and 90 for the down position using Thumper Blocks and the pulsewidths above.  
![image](https://github.com/IRTrail/ERCF_Servo_Upgrade/assets/53546870/e148c905-e77a-435a-b3e0-d8381d9c84d0)  

One person said their servo worked backward from the Savox, which makes sense when looking at the suggested values for the Savox vs. the MG90s. If yours seems reversed, just reverse the numbers in the config, then tune from there.
I haven't had the Triple Decky blocks with this servo, so I don't have an example for those.

##### Here's a picture of it all nestled into place making the ERCF happy:
![Installed.jpg](https://github.com/IRTrail/ERCF_Servo_Upgrade/blob/main/images/Installed.jpg?raw=true)  
Yeah, it's really hard to get a nice picture of it installed.
## Ok. What else have you got for me?
Well, since you asked...[there's a total bling version made from solid brass](https://www.promodeler.com/DS125CLHV-BM).

#### Hit me up on discord if you have any questions or suggestions @Silverback_Attack.

![](https://c.tenor.com/TrLN3mH8oAkAAAAd/tenor.gif)
