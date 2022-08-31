# Home Assistant announces when the International Space Station (ISS) is overhead

<img src="https://github.com/enzymes/home_asssistant_node_red_iss/blob/main/iss.png">

- Notifies you when the International Space Station (ISS) is going to be overhead next for your location

- Gives you a forecast of the next viewable arrival of the International Space Station (valid until January 2031)

How does it work? It checks an RSS feed for your location to check for upcoming arrival times for the ISS.

There's an ISS card for Lovelace and you can set notifications on your mobile phone and Google / Nest smart speaker. Notifications are set  to be 10 minutes before the ISS is overhead and when it is overhead. 

The notification will tell you from what direction and angle above the horizon the ISS will arrive, how long it will be visible and it what direction and angle above the horizon it will disappear.

You can adjust the degrees above the horizon for getting notifications, from 0° to 50°. NASA's Spot the Station website suggests making the minimum rising angle of 40° above the horizon, but this depends on how much open sky you can see from your location.

Data is pulled from an RSS feed for your location, which you can get from https://spotthestation.nasa.gov/

For example, in Melbourne Australia where I am, the URL is https://spotthestation.nasa.gov/sightings/view.cfm?country=Australia&region=Victoria&city=Melbourne 

On that page, get the RSS feed URL and enter that into the Feedparser node in the top left.

In my example, the RSS feed is https://spotthestation.nasa.gov/sightings/indexrss.cfm?country=Australia&region=Victoria&city=Melbourne

## REQUIREMENTS

Needs “node-red-node-feedparser” and “node-red-contrib-string” added to the palette in Node RED. In Node Red, go to the menu, select Manage Palette and search for both of these nodes then install. You will need to add this if you don’t have it installed on Node RED already. Details on these are at:

https://flows.nodered.org/node/node-red-node-feedparser

https://flows.nodered.org/node/node-red-contrib-string 

https://flows.nodered.org/node/node-red-contrib-moment

You will also need to add the YAML to your existing Home Assistant YAML files. This are all listed in the yaml files that are part of this project.

## ADDITIONS YOU CAN ADD


Look in the comments for spots where you could add some additional checks to stop announcements when people are asleep or if who are home aren't interested in the ISS.


### MAKE ANNOUNCEMENTS ON SMART SPEAKER?

Listen to the example at https://github.com/enzymes/home_asssistant_node_red_iss/blob/main/iss_overhead_in_10_minutes_announcement.mp3

At our house, I have a sub-flow that checks to see if announcements on the speaker are allowed.

For example, if it is overnight, no announcements.

If I've set a "do not disturb" mode, then again no announcements.

### ARE PEOPLE HOME WHO ARE INTERESTED IN THE ISS?

If only certain people are interested in the ISS announcements on the speaker, you could add a check here to see if they are home. 

If they are home, there's an announcement.

If they aren't home, there's silence.

