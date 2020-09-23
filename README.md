<div align="center">

## Very Good Anti\-Leech Script


</div>

### Description

This is the best anti-leech script out there. There is now way at all to tell where a file is coming from. What it does is open the file, and streams it through the script. This example demonstrates various functions of PHP.
 
### More Info
 
$domain - your domain name.

$folder - folder that your files are in.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Steve Oliver](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/steve-oliver.md)
**Level**          |Intermediate
**User Rating**    |4.9 (34 globes from 7 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Internet/ Browsers/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-browsers-html__8-9.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/steve-oliver-very-good-anti-leech-script__8-286/archive/master.zip)





### Source Code

```
<?php
/*Anti-Leech script by Steve Oliver
 This is the best anti-leech out there.
 No way of telling where the file is coming from.
 Set the 2 variables below, $domain and $folder.
 You can replace the errors below where commented with html files if wanted.*/
//your domain
$domain="www.yourdomain.com";
//folder that the files are in, no lead or trailing slashes
$folder="filefolder";
$filename=stripslashes(urldecode($QUERY_STRING));
//this can be replaced with
//if ($filename==""){readfile("http://www.yourdomain.com/invalidfile.html");exit;}
if ($filename==""){die("<h1>Invalid File Request...</h1>");}
$refr=getenv("HTTP_REFERER");
list($remove,$stuff)=split('//',$refr,2);
list($home,$stuff)=split('/',$stuff,2);
//this can be replaced with
//if ($home!=$domain){readfile("http://www.yourdomain.com/leecher.html");exit;
if($home!=$domain){die("<h1>Leecher!</h1>This file is from $domain");
}else{
$fp=@fopen("http://".$domain."/".$folder."/".$filename,"r");
if($fp){
if (ereg(".mp3",$filename)){$xtype="audio/mpeg";}
elseif(ereg(".zip",$filename)){$xtype="application/x-zip-compressed";}
elseif(ereg(".exe",$filename)){$xtype="application/x-msdownload";}
else{$xtype="application/octet-stream";}
Header("Content-Type: $xtype");
Header("Accept-Ranges: bytes");
Header("Content-Disposition: ; Filename=$filename");
readfile("http://".$domain."/".$folder."/".$filename);
}else{
//this can be replaced with
//readfile("http://www.yourdomain.com/filenotfound.html");exit;
die("file not found");
}}
?>
```

