# iXperience - Full Stack

Welcome to iXperience Full Stack 2019!

[[toc]]

## ECharts Library Setup

### Installation

Enter in VS Code Terminal
```bash
npm install echarts -S
npm install ngx-echarts -S
npm install @types/echarts -D
```
## ECharts Library Usage

### Import into AppModule

Import ECharts as a service
```ts
import { NgxEchartsModule } from 'ngx-echarts';
 
@NgModule({
  imports: [
    ...,
    NgxEchartsModule
  ],
  ...
})
export class AppModule { }
```

### Import into Component.html

Import ECharts in HTML document
```html
<div echarts [options]="chartOption" class="demo-chart"></div>
```

### Import into Component.scss

Edit graph display details in scss
```css
.demo-chart {
  height: 400px;
}
```

### Import into Component.ts

Import in component.ts file, choose chart in load data
```ts
import { EChartOption } from 'echarts';
 
// ...
 
chartOption: EChartOption = {
  xAxis: {
    type: 'category',
    data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
  },
  yAxis: {
    type: 'value'
  },
  series: [{
    data: [820, 932, 901, 934, 1290, 1330, 1320],
    type: 'line'
  }]
}
```
### Create Admin Dashboard Graphs

## Create Service to Fetch Graph Data 

In file directory {project_name}\src\app\{project_name}\services\admin-panel\ create a service graph-data

```bash
ng generate service graph-data
```
Import graph-data service into AppModule

```ts
import { GraphDataService } from '../app/services/admin-panel/graph-data.service';
 
@NgModule({
  providers: [
    ...,
    GraphDataService
  ],
  ...
})
export class AppModule { }
```

Import graph-data service into Admin Dashboard component.ts and define a instance of service in the constructor

```ts
import { GraphDataService } from '../services/admin-panel/graph-data.service';
 
constructor(private graphDataService: GraphDataService) { }

```

### Setup Data for Total Monthly Rental Income 

In the graph data service create an object contain the data for total monthly rental income.