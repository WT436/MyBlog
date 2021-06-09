```c#

// string data = web1.DownloadString(item.Links[0].Uri.ToString());
var regex = "(?=<ul\\s+id=\"matchMe\"\\s+type=\"square\"\\s*>)(?><!--.*?-->|<[^>]*<opentag><(?!/)[^>]*[^/]>)|(?<-opentag></[^>]*[^/]>)|[^<>]*)*(?(opentag)(?!))";
var html = "<html><body><div><br /><ul id=\"matchMe\" type=\"square\"><li> stuffli><li> more stuff </li><li><div><span>still more </ span >< ul >< li > Another & gt& lt;, oh my!</ li >< li > ...</ li ></ ul ></ div ></ li ></ ul ></ div ></ bodyhtml > ";
var temp = Regex.Split(html, regex);
html = html.Replace(temp[0], "").Replace(temp[1], "");

```
