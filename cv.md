# Summary

# Ilya Navumenka

## Contacts:
 >Mail: ilyanavumenka@icloud.com

 >Telegram: @ilyanavumenka

# Task

 >To acquire knowledge and experience in frontend/javascript development for making perspective carrier and be professional in this field.

# Skills

## Professional skills:
* Basic knowledge of languages: JS, Node.js
* HTML5/CSS3
* MongoDB, PostgreSQL

## Languages skills:
* Russian
* Belarusian
* English

## Example of latest code:

>Some part of my Telegram bot, which is written using the Node.js software platform

```js
const UUID_V4 = require('uuid/v4');

const WEEKDAYS = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
const GAMES = ["Football", "Volleyball", "Basketball", "Tennis", "Hockey"];
const EVENT_TIME_REGEXP = /^(0[0-9]|1[0-9]|2[0-3]|[0-9]):[0-5][0-9]$/g;

let eventParser = function (ctx) {
    console.log("TEXT", ctx.message.text);
    if (!ctx.message.text) {
        return false;
    }

    if(ctx.message.chat.type === "private") {
        ctx.message.text = ctx.message.text.replace("/addevent","").trimStart();
    }

    console.log("CTX", ctx);
    console.log("message", ctx.message);



    let eventDetails = ctx.message.text.split(' ');
    console.log("EVENT DETAILS", eventDetails);
    let eventType;
    let eventDay;
    let eventTime;

    eventDetails.forEach((value) => {
        if (WEEKDAYS.includes(value)) {
            eventDay = value;
        }
        if (GAMES.includes(value)) {
            eventType = value;
        }
        if (EVENT_TIME_REGEXP.test(value)) {
            eventTime = value;
        }
    });

    if(eventDay && eventTime && eventType) {
        let event = {
            _id: UUID_V4(),
            username: ctx.message.from.is_bot ? "BOT" : ctx.message.from.username,
            user_id: ctx.message.from.id,
            timestamp: new Date(ctx.message.date),
            details: {
                type: eventType,
                day: eventDay,
                time: eventTime
            }
        };
        return event;
    } else {
        return false;
    }

};

module.exports = eventParser; 
```
# Education
* International university "MITSO"