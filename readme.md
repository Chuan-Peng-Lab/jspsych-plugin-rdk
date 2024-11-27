# rdk plugin

## Overview

This plugin displays a Random Dot Kinematogram (RDK) and allows the subject to report the primary direction of motion by pressing a key on the keyboard. The stimulus can be displayed until a keyboard response is given or until a certain duration of time has passed. The RDK is fully customizable (see documentation below) and can display multiple apertures at the same time, each with its own parameters.

## Loading

### In browser

```js
<script src="https://unpkg.com/@panwanke/plugin-rdk@2.0.2"></script>
```

### Via NPM

```
npm install @panwanke/plugin-rdk
```

```js
import jsPsychRdk from '@panwanke/plugin-rdk';
```

## Development

1. Clone this repo and set as working path.
2. Run `npm install` to install required packages.
3. Run `npm run build:watch` to render the distribution.
4. Open one of the example html to show the basic function.

### Codespace dev

If you are in the codespace enviroment, please execute two additional processes: 
1. install live-server by `npm install -g live-server`. 
2. run `live-server`. 
3. Open the popup windows and open the example html.  

### Publish

Onece you have maken sure that all the code work out, you could publish your module in npm registry as 

```bash
npm publish --access=public
```

Or you could also use github action to help this process. 

## Compatibility

jsPsych v7.0.

## Documentation

See [documentation](docs/jspsych-rdk_revised.md)

## Author / Citation

Created by [Sivananda Rajananda](https://github.com/vrsivananda), Hakwan Lau, and Brian Odegaard. Modified by the jsPsych core team for 7.0 compatibility.

We would appreciate it if you cited this paper when you use the RDK plugin.

Rajananda, S., Lau, H. & Odegaard, B., (2018). A Random-Dot Kinematogram for Web-Based Vision Research. *Journal of Open Research Software. 6*(1), p.6. doi:[10.5334/jors.194](http://doi.org/10.5334/jors.194)

The plugin is revised by Siyu Wu and Wanke Pan in [Meta-Self Lab | Hu Chuan-Peng Lab](https://huchuanpeng.com/). 
