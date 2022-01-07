# qrshow

_qrcode.show for homeassistant_

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armhf Architecture][armhf-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports i386 Architecture][i386-shield]

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg

This is a custom docker container wrapping around a modified version of qrcode.show. 
It can be used to show qr codes in various ways. I ported this to Docker/Hs to display qr codes on my dashboard or tablet

NOTE : All work except the port to docker/hs was done by the maintainers of qrcode.show (check it out here [qrcode.show](https://github.com/sayanarijit/qrcode.show))
I will try to stay up with their branch/repo. But since this seems to work (open an issue if not).I see no need to make any big changes except for security reasons.
(Of course you are still free to open a feature request or something)
## Usage

Start the addon. A new port will be opened (default is 9999)
If you now make a get request like
```
http://<homeassistant.ip>:9999/{qrcode content}
```

a qrcode will be displayed which contains everything you wrote instead of '{qrcode content}'

If you look at the documentation in the original repo you see that there are many ways to use this to generate qr codes. 
While this add-on only focuses on the web generation the other ways _should_ work. Also i modified this fork to remove all 
infos on the webpage itself and only display the qr code. This makes the interface a lot cleaner and prohibits users to mess 
with the webpage if it is displayed on one of your displays for example.

## More complicated data

If you want to encode something like Wi-Fi or contact infos or whatever which isn't simply text you can do that
too. Just create a correct QR code with the tool of you choice, read out the raw data of this code (many qr code readers
can do that) then use the data you get from this as content (most of these things have a specific format you can copy to
make more qrcodes without going through this process every time.)
Wi-Fi for example looks like this :

```
WIFI:S:{SSID};T:WPA;P:{PASSWORD};;
```
you can pass this as content. If you now scan the displayed QR-Code you will see that your device detects it as a WIFI 
QR code and asks you if you want to connect to this network (if supported by your device).