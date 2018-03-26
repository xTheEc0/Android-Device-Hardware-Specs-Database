# Android Device Hardware Specs (CPU SoC) Database
Database containing information about Android 4.1+ device CPU and SoC specs

Disclaimer: This is probably very incomplete and very wrong in a lot of places as I assume consistency (which Android usually doesn't have...) in board names.  
For example Exynos: all new(-ish, S6+?) boards are 'universalXXXX'.  
But connecting old devices I found that board could be named 'smdk4x12' ¯\\\_(ツ)\_/¯

So if you find any mistakes or want to add information PLEASE DO. (But please try keeping alphabetical order for keys : ))


Checking logic:

	adb shell getprop ro.product.board  
	// then
	adb shell cat /proc/cpuinfo //with regex: Hardware.+ ([\w\-]+)
	
	// if cpuinfo contains board => use Hardware,
	// else use board

Because different devices give different results etc  
Ex: board => MSM8996, but Hardware => MSM8996pro, which is a (little bit) different CPU, in which case we should use Hardware.  
And don't get me started on google 'boards'.. Tuna? WHAT?! sigh..
 
Using that as key we can get CPU specs
Ex:

Samsung Galaxy S9 (Europe)  

	adb shell getprop ro.product.board => universal9810
	adb shell cat /proc/cpuinfo => universal9810
	// we can safely use cpuinfo.  
	database.json[universal9810] => 
    
	"CPU":"4x Cortex-A55 @ 1.7GHz 4x Samsung Exynos M3 @ 2.8GHz",	
   	"SoC":"Exynos 9 Series 9810"

Google Pixel

	adb shell getprop ro.product.board => walleye
	adb shell cat /proc/cpuinfo => MSM8998
	// cpuinfo does not contain board, but this device has a unique entry in the database, so we can use the board as key  
	database.json[walleye] => 
    
	"CPU":"2x Kryo HP @ 2.15GHz 2x Kryo @ 1.6GHz",
    "SoC":"Snapdragon 821 MSM8996 Pro"