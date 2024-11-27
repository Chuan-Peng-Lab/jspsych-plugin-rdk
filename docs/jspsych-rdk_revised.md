# Revised version of the jspsych-rdk plugin

We have added the motion delay, the functions of setting different colors, color proportions and color delay in this version to meet the requirements of changes in both motion and color dimensions.

## New parameters

this revised version accepts the following parameters. Parameters with a default value of *undefined* must be specified. Parameters can be left unspecified if the default value is acceptable.

| Parameter          | Type                      | Default Value | Descripton                               |
| ------------------ | ------------------------- | ------------- | ---------------------------------------- |
| motion_change_delay|numeric                    | 0             | The time point of motion delay, in frames. Before this time point, all dots move according to the specified noise type. After this time point, the signal dots move in the specified direction while the noise dots continue to move randomly.|
| dot_color          | string or array of string | ["white"]     | When only one color is needed, the color of the dots can be defined with a single string; it can also be defined with an array. If there are two elements in the array, the proportion is 5:5. If you do not need the `color_change_delay`, please use this parameter to define the color.|
|color_change_delay | numeric                    | 0             | The time point of color change delay, in frames. After this time point, a certain proportion of dots will change to the value of `dot_color_final`.|
| dot_color_final    | string or array of string | ["white"]     | The color of the dots after the color delay time point. When only one color is needed, the color of the dots can be defined with a single string; it can also be defined with an array. If there are two elements in the array, the first element is the target dots color and the second element is the distractor dots color. When aperture >= 2, pay attention to the input format, like `[["blue", "red"], ["blue", "red"]]`.|
| target_color_proportion | numeric              | 0             | The proportion of the target dots color. |


## New data Generated

The new parameter data for each trial.

| Name                   | Type                      | Value                                          |
| ---------------------- | ------------------------- | ---------------------------------------------- |
| motion_change_delay    | numeric                   | The time (in frames) before the motion changes.|
| dot_color              | string or array of string | The color of the dots.                         |
| color_change_delay     | numeric                   | The time (in frames) before the color changes. |
| dot_color_final        | string or array of string | The final changed color of the dots.           |
| target_color_proportion| numeric                   | The proportion of the target dot color.        |

## Example

### Motion delay display

```js
var RDK_trial = {
  type: jsPsychRdk,
  number_of_dots: 100, // Total number of dots in each aperture
  RDK_type: 3, // The type of RDK used
  choices: " ", // Choices available to be keyed in by participant
  trial_duration: 5000, // Duration of each trial in ms
  coherence: 0.8,
  background_color: "black",
  number_of_apertures: 2,
  motion_change_delay: [0, 200], // Note that it's the number of frames here, not milliseconds
  aperture_width: 400, 
  aperture_center_x: [(window.innerWidth/2)-250, window.innerWidth/2+250] //Separate the apertures on the screen (window.innerWidth/2 is the middle of the screen)
}
```
See `examples/example5.html` for a demo.

### "Defining the color of the dots and setting it to blue."

```js
var RDK_trial = {
  type: jsPsychRdk,
  number_of_dots: 100, // Total number of dots in each aperture
  RDK_type: 3, // The type of RDK used
  choices: " ", // Choices available to be keyed in by participant
  trial_duration: 5000, // Duration of each trial in ms
  background_color: "white",
  dot_color: "blue", // or dot_color: ["blue"]
  number_of_apertures: 1,
  aperture_width: 400, 
}
```
See `examples/example6.html` for a demo.

### "Setting two colors, and the default proportion is 0.5." 

```js
var RDK_trial = {
  type: jsPsychRdk,
  number_of_dots: 100, // Total number of dots in each aperture
  RDK_type: 3, // The type of RDK used
  choices: " ", // Choices available to be keyed in by participant
  trial_duration: 5000, // Duration of each trial in ms
  background_color: "white",
  dot_color: ["blue", "red"],
  number_of_apertures: 1,
  aperture_width: 400
}
```
See `examples/example7.html` for a demo.

### "Setting color change (single color) and the delay time of the change."

```js
var RDK_trial = {
  type: jsPsychRdk,
  number_of_dots: 100, // Total number of dots in each aperture
  RDK_type: 3, // The type of RDK used
  choices: " ", // Choices available to be keyed in by participant
  trial_duration: 5000, // Duration of earedch trial in ms
  background_color: "grey",
  dot_color_final: "blue", // or dot_color_final: ["blue"]
  number_of_apertures: 2, // Use two apertures to display, one without color change and one with color change
  color_change_delay: [0, 100], // The left one doesn't change, and the right one turns blue after 100 frames (approximately 1.7 seconds)
  aperture_width: 400, 
  aperture_center_x: [(window.innerWidth/2)-250, window.innerWidth/2+250] //Separate the apertures on the screen (window.innerWidth/2 is the middle of the screen)
}
```
See `examples/example8.html` for a demo.

### "Setting color change (two colors), the delay time of the change and the proportion of different colors."

```js
var RDK_trial = {
  type: jsPsychRdk,
  number_of_dots: 100, // Total number of dots in each aperture
  RDK_type: 3, // The type of RDK used
  choices: " ", // Choices available to be keyed in by participant
  trial_duration: 5000, // Duration of each trial in ms
  background_color: "grey",
  dot_color_final:[["blue", "red"], ["blue", "red"]], //// This is the input format
  target_color_proportion: 0.8, // The proportion of target color is 0.8, corresponding to the first color, that is, blue
  color_change_delay: [0, 100], // The left one doesn't change, and the right one turns into blue and red after 100 frames (approximately 1.7 seconds)
  number_of_apertures: 2,
  aperture_width: 400, 
  aperture_center_x: [(window.innerWidth/2)-250, window.innerWidth/2+250] //Separate the apertures on the screen (window.innerWidth/2 is the middle of the screen)
}
```
See `examples/example9.html` for a demo.

### "Examples contain various incorrect input formats."

See `examples/example10_bugTest.html` for a demo.