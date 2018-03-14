# Android Device Hardware Specs (CPU SoC) Database

Disclaimer: This is probably very incomplete and very wrong in a lot of places as I assume consistency (which Android usually doesn't have...) in board names.  
For example Exynos: all new(-ish, S6+?) boards are 'universalXXXX'. But connecting old devices I found that board could be named 'smdk4x12' ¯\\_(ツ)_/¯

So if you find any mistakes or want to add information PLEASE DO. (But please try keeping alphabetical order for keys : ))

Database containing information about Android 4.1+ device CPU and SoC specs

Using 

	adb shell cat /proc/cpuinfo  

OR  

	adb shell getprop ro.product.board  

(because different devices give different results etc)
we get proper motherboard number.  
Using that as key we can get CPU specs


Ex:

Samsung Galaxy S9 (Europe)  

	adb shell getprop ro.product.board -> universal9810

	database.json[universal9810] ->  
    
	"CPU":"4x Cortex-A55 @ 1.7GHz 4x Samsung Exynos M3 @ 2.8GHz",	
   	"SoC":"Exynos 9 Series 9810"