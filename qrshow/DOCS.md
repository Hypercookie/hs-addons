# HS-qrcode.show
Display QR codes on your dashboard or elsewhere without an extra server.

## Usage

Start the addon. A new port will be opened (default is 9999)
If you now make a get request like
```
http://<homeassistant.ip>:9999/{qrcode content}
```

a qrcode will be displayed which contains everything you wrote instead of '{qrcode content}'


## More complicated data

If you want to encode something like Wi-Fi or contact infos or whatever which isn't simply text you can do that
too. Just create a correct QR code with the tool of you choice, read out the raw data of this code (many qr code readers
can do that) then use the data you get from this as content (most of these things have a specific format you can copy to
make more qrcodes without going through this process every time.)
Wi-Fi for example looks like this :

```
WIFI:S:{SSID};T:WPA;P:{PASSWORD};;
```
you can pass this as content.

I use this to display a qr code for many things on my dashboard tablet on request.