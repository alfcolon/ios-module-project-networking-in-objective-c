<<<<<<< HEAD
# Today's Weather - Part 2 (Networking in Objective-C)
=======
# Today's Weather (2 day project)
>>>>>>> origin/master

Using the data that you parsed in the first part of the project. Today's first goal is to add networking to get the current weather for your devices GPS coordinate. With that fresh weather information you can update your app's UI to display the hourly forecast and daily forecast.

![Apple Weather app](https://tk-assets.lambdaschool.com/b75cb0a8-0706-4a47-81ab-6450283fedba_Apple-Weather.jpg)


## Instructions

1. Please continue from your previous fork. Create a new branch for `NetworkingUI`. 
2. Make a change, commit, and create your new Pull Request for today's assignment. 
3. Push your local changes regularly to Github so they appear on your Pull Request.
4. Submit your Pull Request along with your Module Project submission.

<<<<<<< HEAD
## Design Requirements

Your designer would like the app to show the daily weather and the weekly weather. It can be all on one screen, or you can use the Tab Bar to separate the screens (If you use a tab bar, use appropriate icons from SF Symbols). 

* Daily Weather View
	* Show the daily weather vertically (rows of data)
	* Display the following for each day of the week (including today):
		* Day of the week (i.e.: Monday)
			* Font: Title 3
			* Color: White
			* Left aligned
		* Weather icon
			* 40x40 points
		* Group Temperature
			* Spacing: 16 points
			* High temperature (i.e. 50)
				* Font: Title 3
				* Color: White
				* Separation: 16 point
			* Low temperature (i.e.: 30)
				* Font: Title 3
				* Color: 80% White (gray)
		* Row Height: ~62.5 points tall
		* Weather icon
* Hourly Weather View
	* Show the Hourly Forecast in a horizontal direction
	* Each "weather hour" should be vertical with the horizontal centers aligned
		* Time
			* Display the current hour (5PM) in the top of the cell ("Now" for the current)
			* Use the users current locale and timezone
		* Icon
			* 40x40 points
		* High temperature (i.e.: 30º)

## Technical Requirements 

* ~[Register and create a Dark Sky API account](https://darksky.net/dev)~ for access to the current weather. (Apple bought Dark Sky ... so you can't make a new account–talk to your instructor).
* Read the [Dark Sky documentation](https://darksky.net/dev/docs) and request the current weather based on your devices current location.
* Since requests are limited to 1,000/day you need to make your app work in both an offline/online mode. Use a Boolean value or a button to disable/enable actual API requests (so that during development you don't exhaust the daily API limit).
* For your custom Table View Cell, use pin your view contents to the margins so that you get the correct spacing on the top, bottom, and sides.
* Use Equal Spacing for the primary Stack View for the layout in the Table View (if there's 3 elements it'll center your icon)
* Make sure you constrain the icon to 40x40, so it doesn't expand to it's intrinsic size of 130x130.
* For your custom Collection View Cell, make sure you add a subview for the "Content View" as the top most view, and then add your contents inside it. You'll need to pin this view to the edges with a constraint constant of 0 on all side
* Use container views if you are using a single screen to show the weather (embed your current weather and collection view controllers)

## Hints

* Use the `NSDateFormatter` to convert the date into a [day of the week (i.e.: Thursday)](https://nsdateformatter.com) for the devices current locale. 
* If you create a `UICollectionView` subclass using Xcode's template, **don't register a blank cell** in your `viewDidLoad` method (the default), it'll replace your design from your storyboard on start, leaving a blank collection view cell.


## Dark Sky API Requirements

* You must include a button that can display the text "Powered by Dark Sky", and it must be take users to the Dark Sky website: <https://darksky.net/poweredby/>
=======
## Part 1: Design Today's Weather

![Today's Weather](https://tk-assets.lambdaschool.com/19e93a70-2966-471a-9183-326aab2d97b9_WeatherApp-Objective-C.png)

1. You will be making an app that looks like the Today's Weather screenshot. 
2. Included in the project is an Asset Catalog with all the weather images you will need for this project.

## Design Hints

Your designer sketched out the requirements for the fonts, colors, and spacing on a notepad. They want you to try and match the screenshot as much as possible.

![Designer UI Hints](https://tk-assets.lambdaschool.com/6746bb60-c92c-46d2-ae7d-928a40e13099_Todays-Weather-UI-markup.JPG)


### Customer Requirements

Design Requirements are as follows:

#### Quick Look: Top View

* "Top View" is 40% height of iPhone screen (Use equal height to superview with 0.4 multiplier)
	* No white bars on iPhone X style devices
	* Edge to edge color (0 point margins)
	* Color: System Blue
* "Quick Look" view content inside "Top View"
	* Centered vertically and horizontally in "Top View"
	* Icon: 64x64 point size
	* "City, State" label
		* Font: Title 1
		* Color: White
	* "Summary" label
		* Font: Body
		* Color: White
	* "Temperature" label
		* System Light, 60 points
		* Color: White
	* Icon, "City, State", and "Summary" views should be 0 points vertical spacing
	* "Temperature" should be 16 points away from "Summary" 

#### Detailed Conditions: Bottom View

* 60% height of the iPhone screen (fill remaining space below top view)
	* Edge to edge color (0 point margins)
	* Color: HEX: `0057B6`
	* Light style Home indicator
* Weather "Details Views"
	* Title
		* ALL CAPS
		* Font: System Footnote
		* Color: 80% white (gray)
	* Value
		* Include appropriate units (mph, º, %, and inHg)
		* Font: Title 1
		* Color: White
	* Spacing
		* Inset 20 points horizontally on left/right margins
		* Inset 20 points vertically from top of "Bottom View"
		* Both Title and Value are leading text layout (left edge)
		* Detail Views are 50% screen width (minus the 40 constant from left/right margins)
		* Detail Views are equal width

#### Toolbar and Settings View Controller

1. You must include a info button (SF Symbol: "info.circle.fill") that can display a Settings Table View Controller in the bottom right corner
	2. The "Settings Table View Controller" must have a navigation title: "Settings" (Embed it in a navigation controller)
	3. The first cell must display "Today's Weather v.1.0"
	4. The second cell must display "Powered by Dark Sky", and it must be take users to the Dark Sky website: <https://darksky.net/poweredby/>
2. The toolbar must be transparent along the bottom of the screen. (See [this developer hint](https://stackoverflow.com/a/18969325/276626))

## Part 2: Data Modeling in Objective-C

Parse the data for the weather from a JSON file.

### Technical Requirements

Create model objects to parse the data into the following model objects.

NOTE: Make sure you choose a location for your Simulator if you don't test this on a device, since you won't get a location until you do.

#### Starter Project

Your team lead created a starter project with the icons, helper files, and location services so that you can focus on the weather.

Review the provided files before you begin.

#### Current Weather

1. [Review the APIs value types](https://darksky.net/dev/docs#data-point) (and if they are optional) for the required fields.

2. Parse the "CurrentWeather.json" file and verify it works in your Unit Test.

	Create a model object: `LSIWeatherForcast` with a child CurrentForecast object 
	
	**Required Fields**
	
	* `time` (unix time)
	* `summary`
	* `icon`
	* `precipProbability`
	* `precipIntensity`
	* `temperature`
	* `apparentTemperature` (Feels like)
	* `humidity`
	* `pressure`
	* `windSpeed`
	* `windBearing`
	* `uvIndex`

3. After parsing the "CurrentWeather.json", update the UI using the model object.
	1. Use the LSIWeatherIcons.h to load the correct icon (? if missing)
	2. Use LSICardinalDirections.h to convert wind direction (bearing) from 30º to NE.
	3. Parse the model in the LSIWeatherViewController.m when you "fetch the weather" (Look for the `TODO:`), tomorrow you'll update this to do the actual weather requests.

#### Daily Weather

1. Parse the "DailyWeather.json" file and verify it works in your Unit Test.

2. Parse each day as an: `LSIDailyForecast`

	* `time` (unix time)
	* `summary`
	* `icon`
	* `sunriseTime`
	* `sunsetTime`
	* `precipProbability`
	* `precipIntensity`
	* `precipType` ("rain", "snow", or "sleet", or nil)
	* `temperatureLow`
	* `temperatureHigh`
	* `apparentTemperature` (Feels like)
	* `humidity`
	* `pressure`
	* `windSpeed`
	* `windBearing`
	* `uvIndex`

#### Hourly Weather

1. Parse the "HourlyWeather.json" file and verify it works in your Unit Test
2. Parse each object in the array as an `LSIHourlyForecast` object

	**Required Fields**
	* `time` (unix time)
	* `summary`
	* `icon`
	* `precipProbability`
	* `precipIntensity`
	* `precipType` ("rain", "snow", or "sleet", or null)
	* `temperatureLow`
	* `temperatureHigh`
	* `apparentTemperature` (Feels like)
	* `humidity`
	* `pressure`
	* `windSpeed`
	* `windBearing`
	* `uvIndex`

3. Some fields are optional and are dependent on values in other fields. Make sure you [read the documentation](https://darksky.net/dev/docs#data-point).

### Weather 

1. Parse the "Weather.json" and store the properties

	* `currently`
	* `daily`
	* `hourly`

2. Refactor your logic to update Today's Weather using the "Weather.json" 

### Use Helper Functions


>>>>>>> origin/master


## Going Further

* Parse todays sunset and sunrise and display that in the hourly view content. (You may want another data structure to store the information as a single array). The data should be sorted based on the time.
* Add a toggle for military time and create a toggle in your settings app.
* Add a toggle for Fº or Cº in your settings app.
* Allow the user to add multiple locations (use reverse geocode lookup to search for a place), then make appropriate API calls.

