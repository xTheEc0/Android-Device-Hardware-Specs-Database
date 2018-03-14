# Android Device Hardware Specs (CPU SoC) Database

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