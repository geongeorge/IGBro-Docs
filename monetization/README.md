# Monetization

For facebook instant games the only monetization option is to enable **Facebook Audience Network**

IGBro supports facebook audience network out of the box.
This tutorial will guide you how to setup audience network for your app.

## Facebook Audience Network(FAN)

We need to first signup for FAN. It's pretty straiht forward process.

- Goto developers.facebook.com and choose your app
- Go to the products section and add **Audience network**
- Now open the **Audience Network** tab and continue to account setup
- The process is pretty straight forward and facebook guides you through the process. You might have to add a payout method so you can get paid.
- Make sure your Ad Space is of Instant games (Don't bother it's default this way. But do not change this)
- After the setup, Facebook will prompt you to create your first placement.
>   A Placement is an ad. You'll get a placement id which you enter in igbro app to show the ad
- Create a placement of type - **Interstitial** , choosing all properties to default. Give it any name.
- After the Interstitial, create another placement of the type **Reward Video**
- You have successfully created 2 placements. You'll be able to copy the placement ids from there

### Game setup

In the front end game you have to paste the placement ids.

- Open `data/ads.js`
```js
window.INTERSTITIAL_PLACEMENT_ID = "2172689262970942_217xxxxx";
window.REWARDED_PLACEMENT_ID = "2172689262970942_123xxxx";
/*
AD_RATIO
The following ratio is used to represent ad ratio
o - none, 1- interstitial, 2- video ad
if you want no ads just put
ratio = [0]
if you want to show an interstitial every second play then 
ratio = [0,1]
if you want every first in every 5 plays to be an intestitial then 
ratio = [1,0,0,0,0]
if you want to shuffle this ratio every instance
add AD_SHUFFLE=1;
Ads may not always appear. Try to space ads atleast one empty slot
I myself use the ratio: [1,0,0,2,0,0]
*/
window.AD_RATIO = [0];
window.AD_SHUFFLE = 0;
```
- Paste the placement ids corresponding to the ad type

### Ad Ratio

Ad ratio is an array that you can edit to show different patterns of ads in the game.

**Ads are loaded before game result loads**

The below table will help you understand what is ad ratio. Please read and try to understand this rather than contacting us to explain this

| Ad Ratio        | Meaning     |
| ------------- |:-------------:| 
| [0]           | no ads        | 
| [1]           | Interstitial everytime        | 
| [2]           | Reward video everytime        | 
| [0,1]           | Interstitial every 2nd gameplay.        | 
| [0,2]           | Reward every 2nd gameplay.        | 
| [0,1,0,2]           | no ads, interstitial, no ads, reward video, repeat| 


### Ad Shuffle

Ad shuffle shuffles ad ratio every time the user opens the game.
So if the ad ratio is: `[0,1,0,2]`
If ad shuffle is set to `1` 
then the ratio could be any combination like:
- `[0,1,2,0]`
- `[1,0,2,0]`
- `[2,0,0,1]`
- ...
 