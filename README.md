# ColorGeneratorPlugin

A Swift Package Plugin which generates semantically named colours based off of a palette of your choice. 

The package takes two JSON input files, a `Palette.json` and a `Semantic.json`. The package will then use these JSON files to produce two outputs, a `GeneratedColors.xcassets` and a `Colors.swift`. 

* The `GeneratedColors.xcassets` catalogue will contain all of the colours referenced in the Semantic.json. 

* The `Colors.swift` is a file with a `Colors` enum which you can use to access the colours in code, like so: `Colors.Namespace.colourName`

## Installation 

### Xcode Project

You can integrate ColorGeneratorPlugin into your Xcode project as an Xcode Build Tool Plug-in if you're working with a project in Xcode. 

Add ColorGeneratorPlugin as a package dependency to your project. 
<img width="540" alt="Screenshot 2022-11-18 at 16 11 27" src="https://user-images.githubusercontent.com/53755195/202750271-29e8395f-1ae2-496d-aff3-c15a1d90510c.png">

Select the target you want to add the colour generation to and open and open the `Build Phases` inspector. 
Open `Run Build Tool Plug-ins` and select the `+` button. Select `ColorGeneratorPlugin` from the list and add it to the project. 
<img width="540" alt="Screenshot 2022-11-18 at 16 11 40" src="https://user-images.githubusercontent.com/53755195/202750299-5ec29d4a-b758-4aa9-a8b4-d3fec01db2b6.png">


### Swift Package 

You can integrate ColorGeneratorPlugin as a Swift Package Manager Plug-in if you're working with a Swift Package with a `Package.swift` manifest. 

Add ColorGeneratorPlugin as a package dependency to your `Package.swift` file. 
Add ColorGeneratorPlugin to a target using the `plugins` parameter. 

<img width="865" alt="Screenshot 2022-11-18 at 16 38 31" src="https://user-images.githubusercontent.com/53755195/202756040-1d4258c9-ee88-499a-bbce-a42c256871bc.png">

## Usage 

### Requirements 

This ColorGeneratorPlugin requires that the target you are using it with contains two JSON files. 
1. **Palette.json**
```
[
    {
        "name": "paletteRed",
        "hex": "ff0000"
    },
    {
        "name": "paletteBlue",
        "hex": "0000ff"
    },
]

```


2. **Semantic.json** 

Each color is semantically named and references a color defined in Palette.json
 ```
 [
    {
        "namespace": "TestView",
        "colors": [{
            "name": "borderColor",
            "universal": {
                "paletteColor": "paletteRed"
            },
            "dark": {
                "paletteColor": "paletteBlue"
            }
        }]
    }
]
 ```


