'use strict';

// Include the serverless-slack bot framework
const slack = require('serverless-slack');


// The function that AWS Lambda will call
exports.handler = slack.handler.bind(slack);


// Slash Command handler
slack.on('/cheat', (msg, bot) => {
  var answers = [8, 8, 9, 9, 10, 10, 11, 11, 12];
  var combinations = ["5 3", "2 6", "4 5", "6 3", "5 5", "4 6", "6 5", "5 6", "6 6"];
  var i = Math.floor(Math.random()*(8-0+1)+0)
  let message = {
    "text": "",
    "attachments": [
        {
            "text": "@david.kanwisher rolled *" + answers[i] + "*",
            "fields": [
                {
                    "title": "Dice",
                    "value": "2d6",
                    "short": true
                },
                {
                    "title": "Rolls",
                    "value": combinations[i],
                    "short": true
                }
            ],
            "color": "good",
            "mrkdwn_in": [
                "text"
            ]
        }
    ]
}

  // ephemeral reply
  bot.reply(message); 
});
