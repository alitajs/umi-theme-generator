# umi-theme-generator

This script generates color specific styles/less file which you can use to change theme dynamically in browser

## Example:

```
const { generateTheme } = require('umi-theme-generator');

const options = {
  antDir: path.join(__dirname, './node_modules/antd'),
  stylesDir: path.join(__dirname, './src'), // all files with .less extension will be processed
  varFile: path.join(__dirname, './src/styles/variables.less'), // default path is Ant Design default.less file
  themeVariables: ['@primary-color'],
}

generateTheme(options).then(less => {
  console.log('Theme generated successfully');
})
.catch(error => {
  console.log('Error', error);
})
```

| Property | Type | Default | Descript |
| --- | --- | --- | --- |
| antdDir | string | - | This is path to antd directory in your node_modules |
| stylesDir | string, [string] | - | Path/Paths to your custom styles directory containing .less files |
| varFile | string | - | Path to your theme related variables file |
| themeVariables | array | ['@primary-color'] | List of variables that you want to dynamically change |
| customCss | string | - | custom css,(like umi.css) |

Add following lines in your main html file

```
<link rel="stylesheet/less" type="text/css" href="/color.less" />
```

Now you can update colors by updating less variables like this

```
import less from 'less';

less.modifyVars({
  '@primary-color': '#0035ff'
})
```
