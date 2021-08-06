# Clockwork Card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg?style=for-the-badge)](https://github.com/custom-components/hacs)

**Current Version:** 0.2.0

This is a simple little custom lovelace element that shows a clock and some extra timezones for Home Assistant.

It may break, it may work. For now, it works.

Anyone who wants to fork it and make it better, by all means PLEASE go for it. Will also accept pull requests.

I pretty much stole the idea from [Mikael T](https://community.home-assistant.io/t/palm-springs-theme/103533) and then hacked it up to do what I wanted.

If by some miracle it works it should look like this:![Sample Image](sample.jpg)

## DISCLAIMER

*This was never intended for external use, but was asked a couple times to release it so I did.
Use at own risk, absolutely minimal testing has been completed. Milage may very.*

## INSTALL WITH HACS

To install via [HACS](https://hacs.xyz/) select the "Custom repositories" button add in the link in this format ***user* + *repository name***  (You can find this information at the top of the repository.  For category select  **Lovelace** then click "ADD".

After this navigate to "Frontend" click the plus symbol and enter "Clockwork Card" into the search bar. Then click on the first result. ![Description](search_bar.png) and select "Install this repository in HACS" and you are done!

## MANUAL INSTALLATION

To install add it to your custom lovelace folder and then reference it accordingly

```yaml
resource:
  - url: /local/custom-lovelace/clockwork-card.js
    type: js
```

## CONFIGURATION

Then in your lovelace configuration edit accordingly.
Will use browser's date/time if entity is not specified. Otherwise, entity should be an existing [date_time_iso](https://www.home-assistant.io/integrations/time_date/) sensor.

The other_clocks section can contain zero or more (probably no more than 3) other clocks to display. Each clock can simply be a timezone name or an object with a tz property and optional name and weekday format (short or long). If unspecified, the name defaults to the timezone and the weekday format defaults to short.

The Rest should be pretty self explanatory.

```Yaml
  - type: 'custom:clockwork-card'
    #title: "My Time"
    locale: en-AU
    entity: sensor.date_time_iso
    other_clocks:
      - tz: "America/New_York"
        name: "Big Apple"
      - tz: "Australia/Sydney"
        weekday: long
      - "America/Los_Angeles"
```


### iPhone/Safari
 So safari (i.e. mac and ios) has a quirky *feature* where it imports date/time as UTC time even when not specifically expressed. So on your iPhone or on a Mac, everything will be out by exactly your timezone.

So in this case, dont use an entity. However the time shown will be LOCAL for your device. In other words, if your phone is in a different timezone, it will show that time, and not the time wherever your HomeAssistant instance is.

Will try to fix this.

## TODO LIST
    [ ] Fix iPhone issue.
    [✔️] Integrate with HACS.
    [ ] Clean up README and more detailed install 
    [ ] Have ability to choose whether to show local device time or HomeAssistant time.
