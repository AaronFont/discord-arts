
<div align='center'>
  <img src='https://i.imgur.com/NBpsl5W.png' alt='Discord Arts Banner' />
  <p align='center'>
  <a href='https://www.npmjs.com/package/discord-arts'>
    <img src='https://img.shields.io/npm/v/discord-arts?label=version&style=for-the-badge' alt='version' />
    <img src='https://img.shields.io/bundlephobia/min/discord-arts?label=size&style=for-the-badge' alt='size' />
    <img src='https://img.shields.io/npm/dt/discord-arts?style=for-the-badge' alt='downloads' />
  </a>
</p>
</div>

# 📦 Features
## 🤖 `profileImage(userId, imgOptions)`

*Generates the card of a user/bot, with its badges.*

PARAMETER | TYPE | REQUIRED | DESCRIPTION 
-------- | --------- | -------- | -------- 
userId| string | ✔️✔️✔️ | Discord User ID
imgOptions| object | ✖️✖️✖️ | Customize the card in multiple ways

#### imgOptions `NEW!!`
PARAMETER | TYPE | DEFAULT | DESCRIPTION 
-------- | --------- | -------- | -------- 
customTag| string | ✖️ | Text below the user
customBadges| string[] | ✖️ | Use your own png badges (path and URL)
customBackground| string | ✖️ | Change the background to any image (path and URL)
overwriteBadges| boolean | false | Merge your badges with the discord defaults
borderColor| string[] | ✖️ | Hex color of the border, can be gradient if 2 colors are used
borderAllign| string | 'horizontal' | Gradient alignment (if 2 colors are used)
presenceStatus| string | ✖️ | User status to be displayed below the avatar 

Returns: [**Promise**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)<**[Buffer](https://nodejs.org/api/buffer.html)**>

------------

### 📃 Discord.js Example
```javascript
const { AttachmentBuilder } = require('discord.js');
const { profileImage } = require('discord-arts');

const userId = interaction.options.getUser('user-option').id || interaction.user.id;
const bufferImg = await profileImage(userId);
const imgAttachment = new AttachmentBuilder(bufferImg, { name: 'profile.png' });

interaction.reply({ files: [imgAttachment] });
```


------------


### 🖼️Results 

#### - Default
```javascript
profileImage('ID')
```
![Default](https://i.imgur.com/HKumM3y.png)

------------

#### - Custom User 1
```javascript
profileImage('ID', {
	customTag: 'Programmer',
	customBadges: [  './skull.png', './letter.png', './rocket.png', './crown.png', './hearth.png'  ],
	customBackground: 'https://i.imgur.com/DGA63O0.jpg',
	overwriteBadges: true,
	borderColor: ['#841821', '#005b58'],
	presenceStatus: 'dnd'
});
```
![Default](https://i.imgur.com/qkT2DRk.png)

------------

#### - Custom User 2
```javascript
profileImage('ID', {
	customTag: 'Minecraft Modder',
	customBadges: [ './badges/booster.png','./badges/orange.png', './badges/giveaway.png' ],
	overwriteBadges: false,
	borderColor: ['#f90257', '#043a92'],
	presenceStatus: 'idle'
});
```
![Default](https://i.imgur.com/Tz4IgNH.png)

------------

#### - Custom Bot
```javascript
profileImage('ID', {
	customTag: 'Minecraft Bot',
	borderColor: ['#fe6a90'],
	presenceStatus: 'online'
});
```
![Default](https://i.imgur.com/Hw0SEtw.png)

------------

# 💥 Issues / Bugs
### Report [**here**](https://github.com/iAsure/discord-arts)

