Integrate angular 2+ app with interactive d3 charts e.g. **Doughnut, Pie, Single Bar chart, Multiple bar chart and Stacked bar chart**.

Beautiful charts for Angular2+ based on d3.js

**Last updated- 19th September 2017(Bar chart)**

**Important: Bar charts are under developement**.

## Getting Started
    npm install angular-d3-charts --save
    
**Notice**: The latest version on NPM may not reflect the branch `master`. Open an issue and tag me if you need it to be published.

## Configuration

Add d3 script to your index.html
```javascript
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.6/d3.min.js" charset="utf-8"></script>
```

Add these styles to your main stylesheet.
```css
   .tick text {
        font-size: 12px;
    }

    .axis path,
    .axis line {
        fill: none;
        stroke: #4C5554;
        stroke-width: 1;
    }

    .x.axis .tick line {
        display: none
    }

    .domain {
        display: block !important;
        stroke: #4C5554 !important;
        stroke-width: 2 !important;
    }
```

Ensure you import the module:

```javascript
import { DoughnutChartComponent, PieChartComponent, BarChartComponent } from 'angular-d3-charts'; // this is needed!

@NgModule({
   declarations: [ 
   DoughnutChartComponent, 
   PieChartComponent, 
   BarChartComponent,
   ...OtherModules 
   ] // along with your other modules
})
export class AppModule {}
```
## Usage
## Doughnut Chart: 
```ts
<angular-d3-donut [id]="donutChartId" [data]="donutChartData"></angular-d3-donut>   
<angular-d3-donut [data]="donutChartData"></angular-d3-donut>   
```
```ts
public donutChartData = [{
      id: 0, // number
      label: 'label name',  // string
      value: value,  // number
      color: 'color of slice',  // string,
      iconImage: 'path of image' // string
   },{
      id: 1, // number
      label: 'label name',  // string
      value: value,  // number
      color: 'color of slice',  // string,
      iconImage: 'path of image' // string
   }, ...
   ]
```

## Attributes

### Attributes of angular-d3-donut are

It can contain the following properties.
## Input
| Option        | Default       | Type   | Description  |
| :------------ | :------------ | :----- | :--------- |
| __id__    | donutChart | String | Unique Id of the bar chart. |
| __outerRadius__     | 150 | Number | Outer radius of the donut chart. (Recommended to not to larger than 150) |
| __innerRadius__   |  70 |  Number | Inner radius of the donut chart. |
| __data__    | Not set | Object | As above mentioned |
| __centerImage__   |  Not set |  String | Path of center image in donut. |
| __spreadSlice__    | False | Boolean | If you want to spread out the slide.
| __iconWidth__    | 40 | Number | Width of the icon images on slices.
| __iconHeight__    | 40 | Number | Height of the icon images on slices.

## Output
| Option |Description |
| :------------ |:--------- |
| __centerImageEvent__ | When cemter image is clicked, the centerImageEvent function triggers.  |


```ts
<angular-d3-donut [spreadSlice]=true [centerImage]='centerImage' [data]="donutChartData" (centerImageEvent)="centerImageEvent()"></angular-d3-donut>
```

```ts
<angular-d3-donut [outerRadius]=100 [innerRadius]=80 [spreadSlice]=true [data]="piedata" (centerImageEvent)="centerImageEvent()"></angular-d3-donut>
```

```ts
In your.component.ts file write
public centerImageEvent() {
 // Perform action here
}
```

## Pie Chart: 
```ts
<angular-d3-pie [id]="pieChartId" [data]="pieChartData"></angular-d3-pie>   
<angular-d3-pie [data]="pieChartData"></angular-d3-pie>   
```
```ts
public pieChartData = [{
      id: 0, // number
      label: 'label name',  // string
      value: value,  // number
      color: 'color of slice',  // string,
   },{
      id: 1, // number
      label: 'label name',  // string
      value: value,  // number
      color: 'color of slice',  // string,
   }, ... ]
```

## Attributes

### Attributes of angular-d3-pie are

It can contain the following properties.
## Input
| Option        | Default       | Type   | Description  |
| :------------ | :------------ | :----- | :--------- |
| __id__    | pieChart | String | Unique Id of the bar chart. |
| __outerRadius__     | 150 | Number | Outer radius of the donut chart. (Recommended to not to larger than 150) |
| __data__    | Not set | Object | As above mentioned |
| __spreadSlice__    | False | Boolean | If you want to spread out the slide.

```ts
<angular-d3-pie [spreadSlice]=true [data]="pieChartData" [outerRadius]=90></angular-d3-pie>
```

## Bar Chart: 
```ts
<angular-d3-bar [id]="barChartId" [data]="barChartData"></angular-d3-bar>   
```
```ts
public barChartData = [{
<angular-d3-bar [data]="barChartData"></angular-d3-bar>   
```
```ts
barChartData = [{
      id: 0, // number
      label: 'label name',  // string
      value1: value,  // number
      value2: value,  // number
      value3: value,  // number
      ... ,
      valuen: value // number
   },{
      id: 1, // number
      label: 'label name',  // string
      value1: value,  // number
   },
      id: 1, // number
      label: 'label name',  // string
       value1: value,  // number
      value2: value,  // number
      value3: value,  // number
      ... ,
      valuen: value // number
   }, ... ]
```

## Attributes

### Attributes of angular-d3-bar are

It can contain the following properties.
## Input
| Option        | Default       | Type   | Description  |
| :------------ | :------------ | :----- | :--------- |
| __id__    | barChart | String | Unique Id of the bar chart. |
| __width__     | 700 | Number | Width of the bar chart. |
| __height__     | 400 | Number | Height of the bar chart. |
| __transitionDuration__ | 1000 | Number | The duration of the bar's transition (bar comes from x- axis). |
| __transitionDelay__     | 100 | Number | The delay of the bar's transition.  |
| __barWidth__     | '11px' | String | Width of the bars. |
| __yAxisd3Format__     | '.1S' | String | d3Format of Y axis, Refer to the d3 documentation. |
| __data__    | Not set | Object | As above mentioned |
| __colors__    | Not set  | Array | Color of the bars. |
| __dataGroup__    | 1 | Number | Number of data. (dataGroup > 1 for stacked bar chart.) |
| __yAxisTicks__    | 10 | Number | Ticks on Y axis. |
| __alphaDistance__    | 0.6 | Number | Distance between 2 bars, when chart is multi bar chart. |
| __dataColumns__    | [1] | Array | Length of array = Number of columns ,Value on index = number of stacked bars on particular column.|

### Single Bar Chart

```ts
--- Single Bar Chart --- // dataColumns = [1];
<angular-d3-bar [id]="test2" [data]="barChartData" [dataColumns]="dataColumns" [colors]="colors" [yAxisTicks]=10 [width]=400 [height]=200 [transitionDuration]=1000 [transitionDelay]=30
[barWidth]="'16px'"></angular-d3-bar>
```
### Stacked Bar Chart 

```ts
--- Stacked Bar Chart --- // dataColumns = [3];
<angular-d3-bar [id]="test1" [alphaDistance]="0.3" [data]="barChartData" [dataColumns]="dataColumns1" [colors]="colors" [yAxisTicks]=10 [width]=400 [height]=200 [transitionDuration]=1000 [transitionDelay]=30
[barWidth]="'16px'"></angular-d3-bar>
```

### Multi Bar Chart 

```ts
--- Multi Stacked Bar Chart --- // dataColumns = [3, 2];
<angular-d3-bar [id]="test1" [alphaDistance]="0.3" [data]="barChartData" [dataColumns]="dataColumns1" [colors]="colors" [yAxisTicks]=10 [width]=400 [height]=200 [transitionDuration]=1000 [transitionDelay]=30
[barWidth]="'16px'"></angular-d3-bar>
| __color__    | ['blue'] | Array | Color of the bars. |
| __dataGroup__    | 1 | Number | Number of data. |
| __yAxisTicks__    | 10 | Number | Ticks on Y axis. |

```ts
<angular-d3-bar [data]="bardata" [color]="colors" [width]=400 [height]=200 [transitionDuration]=1000 [transitionDelay]=30 [barWidth]="'16px'"></angular-d3-bar>
```

```ts
<angular-d3-bar [data]="bardata" [color]="colors" [dataGroup]="3" [width]=400 [height]=200 [transitionDuration]=1000 [transitionDelay]=30
  [barWidth]="'16px'"></angular-d3-bar>
```

```ts
colors = ['red', 'blue', 'green']
```

Examples: 
```ts
public colors = ['red', 'green', 'blue']
public  dataColumns = [1]; // Single Bar Chart
// public  dataColumns = [3]; // Stacked Bar Chart
// public  dataColumns = [2, 1]; // Multi Stacked Bar Chart
public  barChartData = [{
    id: 0,
    label: 'label1',
    value1: 10,
    value2: 10,
    value3: 10,
 },{
    id: 1,
    label: 'label2',
    value1: 10,
    value2: 10,
    value3: 10,
 }]
 
 <angular-d3-bar [id]="test2" [data]="barChartData" [dataColumns]="dataColumns" [colors]="colors" [yAxisTicks]=10 [width]=400
    [height]=200 [transitionDuration]=1000 [transitionDelay]=30 [barWidth]="'16px'"></angular-d3-bar>
```
