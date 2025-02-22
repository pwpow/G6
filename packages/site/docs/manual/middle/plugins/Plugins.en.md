---
title: Plugins
order: 0
---

There are several plugins in G6 which can be used for G6's graph or other applications.

- [Legend](#legend) *supported by v4.3.0 and later versions*
- [SnapLine](#snapline) *supported by v4.3.0 and later versions*
- [Grid](#grid)
- [Minimap](#minimap)
- [Edge Bundling](#edge-bundling)
- [Menu](#menu)
- [ToolBar](#toolbar)
- [TimeBar](#timebar)
- [Tooltip](#tooltip)
- [Fisheye](#fisheye-lens)
- [EdgeFilterLens](#edge-filter-lens)

## Configure to Graph

Instantiate the plugin and configure the minimap onto the instance of Graph:

```javascript
// Instantialize the Grid plugin
const grid = new G6.Grid();
// Instantialize the Minimap plugin
const minimap = new G6.Minimap();
const graph = new G6.Graph({
  //... Other configurations
  plugins: [grid, minimap], // Configure Grid and Minimap to the graph
});
```

## Legend

Legend is a built-in legend plugin for G6. It is useful for npde/edge type demonstration, and the end-users are able to interact with the legend to highlight and filter the items on the graph. *supported by v4.3.0 and later versions*.

<img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*UmXzQLG65vYAAAAAAAAAAAAAARQnAQ' alt="img" width='500px'>

### Configuration

| Name | Type  | Description                                |
| --- | --- | --- |
| data | GraphData | The data for the legend, not related to the data of the graph. The legend for nodes currently supports `'circle'`, `'rect'`, and `'ellipse'`. The legend for edges currently supports `'line'`, `'cubic'`, and `'quadratic'`. `type` for each data means the type of the legend item, and the `order` could be assigned to each node/edge data for ordering in a legend group |
| position | 'top' / 'top-left' / 'top-right' / 'right' / 'right-top' / 'right-bottom' / 'left' / 'left-top' / 'left-bottom' / 'bottom' / 'bottom-left' / 'bottom-right' | The relative of the position to the canvas. `'top'` by default, which means the legend area is on the top of the canvas |
| padding | number / number[] | The inner distance between the content of the legend to the border of the legend area. Array with four numbers means the padding to the top, right, bottom, and left responsively |
| margin | number / number[] | The outer distance between the legend area to the border of the canvas. Array with four numbers means the distance to the top, right, bottom, and left responsively. Only the top distance takes effect when  `position:'top'`, situations for other `position` configurations are similar to it |
| offsetX | number | The x-axis offset for the legend area, it is useful when you want to adjust the position of the lenged slightly |
| offsetY | number | The y-axis offset for the legend area, it is useful when you want to adjust the position of the lenged slightly |
| containerStyle | ShapeStyle | The style for the background rect, the format is similar as [rect shape style](/en/docs/api/shapeProperties#rect) |
| horiSep | number | The horizontal seperation of the legend items |
| vertiSep | number | The vertical seperation of the legend items |
| layout | 'vertical' / 'horizontal' | The layout of the legend items. `'horizontal'` by default |
| align | 'center' / 'right' / 'left' | The alignment of the legend items.  `'center'` by default |
| title | string | The title string for the legend, the style of the title could be configured by `titleConfig` |
| titleConfig | object | The style of the legend title, detail configurations are shown in following lines |
| titleConfig.position | 'center' / 'right' / 'left' | The alignment of the title to the legend content. `'center'` by default |
| titleConfig.offsetX | number | The x-axis offset for the legend title, it is useful when you want to adjust the position of the title slightly |
| titleConfig.offsetY | number | The y-axis offset for the legend title, it is useful when you want to adjust the position of the title slightly |
| titleConfig[key] | ShapeStyle | Other styles for the text, configurations are same as [text shape style](/en/docs/api/shapeProperties#text) |
| filter | object | Configurations for the graph item filtering while the end-user interacting with the legend items. Detials are shown in the following lines |
| filter.enable | boolean | Whether allow filtering the items in the main graph while the end-user interaction with the legend items. `false` by default |
| filter.multiple | boolean | Whether support active multiple types of legend items, `false` by default, which means only one type of legend item will be activated in the same time. If it is `true`, multiple items could be activated only when the `filter.trigger` is `'click'` |
| filter.trigger | 'click' / 'mouseenter' | The interaction way to the legend items. `click` by default, which means while the end-user clicking a legend item, the legend item and corresponding filtered items on the main graph will be activated |
| filter.legendStateStyles | { active?: ShapeStyle, inactive?: ShapeStyle  | The state styles for the legend items while filtering, inluding `filter.legendStateStyles.active` and `filter.legendStateStyles.inactive`. The type of each one is `ShapeStyle`. Similar to the `nodeStateStyles` of Graph |
| filter.graphActiveState | string | The activate state name for the items on the main graph. When a lenged item is activated, the corresponding items of the main graph will be set to `filter.graphActiveState`, `'active'` by default. And you should assign the state style for this state name on Graph |
| filter.graphInactiveState | string | The inactivate state name for the items on the main graph. When a lenged item is inactivated, the corresponding items of the main graph will be set to `filter.graphInactiveState`, `'inactive'` by default. And you should assign the state style for this state name on Graph |
| filter.filterFunctions | { [key: string]: (d) => boolean; } | Since the data of the legend is not related to the main graph, you should configure filtering functions for each legend item type. The `key` is corresponding to the `type` of the legend item, and the value is a function. For the function, the parameter is the item data of the main graph, and the return value is a boolean which means whether the item of the main graph should be activated |


## SnapLine

SnapLine is a built-in components in G6. *supported by v4.3.0 and later versions*.

### Configuration

| Name | Type   | Required | Description                                |
| ------------- | --------------------------------------------- | -------- | --------------------- |
| line          | ShapeStyle                                    | false    | the style of SnapLine |
| itemAlignType | boolean、'horizontal' 、'vertical'、'center'; | false    | the type of SnapLine  |

## Grid

Grid plugin draws grids on the canvas.

<img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*y8u6Rrc78uIAAAAAAAAAAABkARQnAQ' width=300 alt='img'/>

Use the code in [Configure to Graph](#configure-to-graph) to instantiate grid plugin with the following configurations.

### Configuration

| Name | Type   | Required | Description                                |
| ---- | ------ | -------- | ------------------------------------------ |
| img  | Srting | false    | base64 formatted string for the grid image |

## Minimap

Minimap is a tool for quick preview and exploration on large graph.

<img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*v1svQLkEPrUAAAAAAAAAAABkARQnAQ' width=300 alt='img'/>

It can be configured to adjust the styles and functions.

### Configuration

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| container | Object | false | The DOM container of Minimap. The plugin will generate a new one if `container` is not defined |
| className | String | false | The className of the DOM element of the Minimap |
| viewportClassName | String | false | The className of the DOM element of the view port on the Minimap |
| type | String | false | Render type. Options: `'default'`: Render all the graphics shapes on the graph; `'keyShape'`: Only render the keyShape of the items on the graph to reach better performance; `'delegate'`: Only render the delegate of the items on the graph to reach better performance. Performance: `'default'` < `'keyShape'` < `'delegate'`. `'default'` by default |
| size | Array | false | The size of the Minimap |
| delegateStyle | Object | false | Takes effect when `type` is `'delegate'`. The style of the delegate of the items on the graph |

The `delegateStyle` has the properties:

| Name        | Type   | Required | Description             |
| ----------- | ------ | -------- | ----------------------- |
| fill        | String | false    | Filling color           |
| stroke      | String | false    | Stroke color            |
| lineWidth   | Number | false    | The width of the stroke |
| opacity     | Number | false    | Opacity                 |
| fillOpacity | Number | false    | Filling opacity         |

## Edge Bundling

In complex graph with large number of edges, edge bundling can help you to improve the visual clutter.

<img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*z9iXQq_kcrYAAAAAAAAAAABkARQnAQ' width=600 alt='img'/>

> Edge bundling on American airline graph. <a href='/en/examples/case/graphDemos#edgeBundling' target='_blank'>Demo Link</a>. <a href='/en/docs/manual/cases/edgeBundling' target='_blank'>Demo Document</a>.

The edge bundling plugin can be configured to adjust the styles and functions.

### Configuration

| Name | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| K | Number | false | 0.1 | The strength of the bundling |
| lambda | Number | false | 0.1 | The initial step length |
| divisions | Number | false | 1 | The initial number of division on each edge. It will be multipled by `divRate` in each cycle |
| divRate | Number | false | 2 | The rate of the divisions increasement. Large number means smoother result, but the performance will be worse when the number is too large |
| cycles | Number | false | 6 | The number of outer interations |
| iterations | Number | false | 90 | The initial number of inner interations. It will be multiplied by `iterRate` in each cycle |
| iterRate | Number | false | 0.6666667 | The rate of the iterations decreasement |
| bundleThreshold | Number | false | 0.6 | The edge similarity threshold for bundling. Large number means the edges in one bundle have smaller similarity, in other words, more edges in one bundle |

## Menu

Menu is used to configure the right-click menu on the node.

### Configuration

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| className | string | null | the class name of the menu dom |
| getContent | (evt?: IG6GraphEvent, graph?: IGraph) => HTMLDivElement / string | <img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*OtOkS4g-vrkAAAAAAAAAAABkARQnAQ' width=60 alt='img'/> | the menu content，supports DOM or string |
| handleMenuClick | (target: HTMLElement, item: Item, graph?: IGraph) => void | undefined | the callback function when click the menu |
| shouldBegin | (evt: G6Event) => boolean | undefined | Whether allow the tooltip show up. You can return true or false according to the content of the `evt.item` (current item of the event) or `evt.target` (current shape of the event) |
| offsetX | number | 6 | the offset of tooltip along x axis, the padding of the parent container should be take into consider |
| offsetY | number | 6 | the offset of tooltip along y axis, the padding of the parent container should be take into consider |
| itemTypes | string[] | ['node', 'edge', 'combo'] | the item types that allow the tooltip show up. e.g. if you only want the node tooltip, set the `itemTypes` to be ['node'] |
| trigger | 'click' / 'contextmenu' | 'contextmenu' | the trigger for the menu, `'contextmenu'` by default, which means the menu will show up when the end user right click on some item. `'click'` means left click. *'click' is supported by v4.3.2 and later versions* |

### Usage

Use G6 build-in menu by default.

```
// Instantiate Menu plugin
const menu = new G6.Menu();
const graph = new G6.Graph({
  //... other Configuration
  plugins: [menu],
});
```

#### DOM Menu

```
const menu = new G6.Menu({
  offsetX: 10,
  offsetY: 20,
  itemTypes: ['node'],
  getContent(e, graph) {
    const outDiv = document.createElement('div');
    outDiv.style.width = '180px';
    outDiv.innerHTML = `<ul>
        <li>menu01</li>
        <li>menu01</li>
        <li>menu01</li>
        <li>menu01</li>
        <li>menu01</li>
      </ul>`
    return outDiv
  },
  handleMenuClick(target, item, graph) {
    console.log(target, item, graph)
  },
});

const graph = new G6.Graph({
  //... other Configuration
  plugins: [menu], // the Menu plugin
});
```

#### String Menu

```
const menu = new G6.Menu({
  getContent(e) {
    return `<ul>
      <li title='1'>menu02</li>
      <li title='2'>menu02</li>
      <li>menu02</li>
      <li>menu02</li>
      <li>menu02</li>
    </ul>`;
  },
  handleMenuClick(target, item) {
    console.log(target, item)
  },
});

const graph = new G6.Graph({
  //... other Configuration
  plugins: [menu], // The Menu plugin
});
```

## ToolBar

ToolBar has the following operations by default:

- Undo;
- Redo;
- Zoom-in;
- Zoom-out;
- Fit the View;
- Actual Size.

### Configuration

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| container | HTMLDivElement | null | The container of the ToolBar. It will take use the DOM of the canvas by default |
| className | string | null | The class name of the sub DOM nodes of the ToolBar |
| getContent | (graph?: IGraph) => HTMLDivElement / string | <img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*7QSRRJwAWxQAAAAAAAAAAABkARQnAQ' width=80 alt='img'/> | The content of the ToolBar |
| handleClick | (code: string, graph: IGraph) => void | undefined | The callback functions for the icons of the ToolBar |
| position | Point | null | The position of the ToolBar |

### Usage

#### Default Usage

ToolBar provides some default operations above.

```
const toolbar = new G6.ToolBar();

const graph = new G6.Graph({
  //... Other configurations
  plugins: [toolbar], // Use the ToolBar plugin
});
```

#### Custom ToolBar by String

```
const tc = document.createElement('div');
tc.id = 'toolbarContainer';
document.body.appendChild(tc);

const toolbar = new G6.ToolBar({
  container: tc,
  getContent: () => {
    return `
      <ul>
        <li code='add'>Add Node</li>
        <li code='undo'>Undo</li>
      </ul>
    `
  },
  handleClick: (code, graph) => {
    if (code === 'add') {
      graph.addItem('node', {
        id: 'node2',
        label: 'node2',
        x: 300,
        y: 150
      })
    } else if (code === 'undo') {
      toolbar.undo()
    }
  }
});

const graph = new G6.Graph({
  //... Other configurations
  plugins: [toolbar], // Use the ToolBar plugin
});
```

#### Custom ToolBar by DOM

```
const toolbar = new G6.ToolBar({
  getContent: () => {
    const outDiv = document.createElement('div');
    outDiv.style.width = '180px';
    outDiv.innerHTML = `<ul>
        <li>example 01</li>
        <li>example 02</li>
        <li>example 03</li>
        <li>example 04</li>
        <li>example 05</li>
      </ul>`
    return outDiv
  },
  handleClick: (code, graph) => {

  }
});

const graph = new G6.Graph({
  //... Other configurations
  plugins: [toolbar], // Use the ToolBar plugin
});
```

## TimeBar

The built-in TimeBar plugin has the following abilities:

- Filtering the data of the graph by changing the time range;
- Demonstrating the trending of the data by an attribute on the TimeBar.

<img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*HJjmT7uQwjAAAAAAAAAAAABkARQnAQ' width=700 alt='img'/>

**Description:** It is a beta version of TimeBar, which will support complex time series graph and analysis in the future.

### Configuration

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| container | HTMLDivElement | null | The container of the TimeBar. A DOM container with className 'g6-component-timebar' will be used by default |
| width | number | 400 | The width of the TimeBar's container |
| height | number | 400 | The height of the TimeBar's container |
| timebar | TimeBarOption | {} | The style configurations for TimeBar |
| rangeChange | (graph: IGraph, min: number, max: number) => void | null | The callback function after changing the time range |

**TimeBarOption for timebar**

```
interface HandleStyle {
  width: number;
  height: number;
  style: ShapeStyle;
}
```

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| x | number | 0 | The begining x of the TimeBar |
| y | number | 0 | The begining y of the TimeBar |
| width | number | 400 | The width of the TimeBar |
| height | number | 400 | The height of the TimeBar |
| backgroundStyle | ShapeStyle | {} | The background style of the TimeBar |
| foregroundStyle | ShapeStyle | {} | The foreground style of the TimeBar, which indicates the selected area |
| handlerStyle | HandleStyle | null | The style of the slider handler |
| textStyle | ShapeStyle | null | The style of the texts |
| minLimit | number | 0 | The minimum position for the slider on the left, range from 0 to 1 |
| maxLimit | number | 1 | The maximum position for the slider on the right, range from 0 to 1 |
| start | number | 0 | The initial start position of the slider |
| end | number | 1 | The initial end position of the slider |
| minText | string | null | The text for the minimum value |
| maxText | string | null | The text for the maximum value |
| trend | TrendConfig | null | The configuration of the trend chart on the TimeBar |

**TrendConfig for trend**

```
interface Data {
  date: string;
  value: number;
}
```

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| data | Data[] | [] | The data of the TimeBar |
| smooth | boolean | false | Whether use the smooth curve instead of polylines for the trend chart |
| isArea | boolean | false | Whether use the area chart instead of line chart |
| lineStyle | ShapeStyle | null | The style of the line for line chart, takes effect when `isArea` is `false` |
| areaStyle | ShapeStyle | null | The style of the area for area chart, takes effect when `isArea` is `true` |

### Usage

#### Default Usage

```
const timebar = new G6.TimeBar();

const graph = new G6.Graph({
  //... Other configurations
  plugins: [timebar], // Use timebar plugin
});
```

##### Style Configuration

It is free to configure the style for the TimeBar, and listen to the value changing to do some response.

```
const timebar = new G6.TimeBar({
  width: 600,
  timebar: {
    width: 600,
    backgroundStyle: {
      fill: '#08979c',
      opacity: 0.3
    },
    foregroundStyle: {
      fill: '#40a9ff',
      opacity: 0.4
    },
    trend: {
      data: timeBarData,
      isArea: false,
      smooth: true,
      lineStyle: {
        stroke: '#9254de'
      }
    }
  },
  rangeChange: (graph, min, max) => {
    // Get the instance of the graph and the range of the timebar, you can control the rendering of the graph by yourself here
    console.log(graph, min, max)
  }
});

const graph = new G6.Graph({
  //... Other configurations
  plugins: [timebar], // Use timebar plugin
});
```

## ToolTip

ToolTip helps user to explore detail infomations on the node and edge. Do note that, This Tooltip Plugins will replace the tooltip in the built-in behavior after G6 4.0.

### Configuration

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| className | string | null | Tge class name of the tooltip's container |
| container | HTMLDivElement | null | The container of the Tooltip. The canvas DOM will be used by default |
| getContent | (evt?: IG6GraphEvent) => HTMLDivElement / string | <img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*aPPuQquN5Q0AAAAAAAAAAABkARQnAQ' width=80 alt='img'/> | The content of the Tooltip |
| shouldBegin | (evt: G6Event) => boolean | undefined | Whether allow the tooltip show up. You can return true or false according to the content of the `evt.item` (current item of the event) or `evt.target` (current shape of the event) |
| offsetX | number | 6 | the offset of tooltip along x axis, the padding of the parent container should be take into consider |
| offsetY | number | 6 | the offset of tooltip along y axis, the padding of the parent container should be take into consider |
| itemTypes | string[] | ['node', 'edge', 'combo'] | the item types that allow the tooltip show up. e.g. if you only want the node tooltip, set the `itemTypes` to be ['node'] |

### Usage

The content of the Tooltip is the type and id of the item by default. Users are free to custom the content of the Tooltip by configuring `getContent`:

#### Dom Tooltip

```
const tooltip = new G6.Tooltip({
  offsetX: 10,
  offsetY: 20,
  getContent(e) {
    const outDiv = document.createElement('div');
    outDiv.style.width = '180px';
    outDiv.innerHTML = `
      <h4>自定义tooltip</h4>
      <ul>
        <li>Label: ${e.item.getModel().label || e.item.getModel().id}</li>
      </ul>`
    return outDiv
  },
  itemTypes: ['node']
});


const graph = new G6.Graph({
  //... Other configurations
  plugins: [tooltip], // Use Tooltip plugin
});
```

#### String Tooltip

```
const tooltip = new G6.Tooltip({
  getContent(e) {
    return `<div style='width: 180px;'>
      <ul id='menu'>
        <li title='1'>example 01</li>
        <li title='2'>example 02</li>
        <li>example 03</li>
        <li>example 04</li>
        <li>example 05</li>
      </ul>
    </div>`;
  },
});

const graph = new G6.Graph({
  //... Other configurations
  plugins: [tooltip], // Use Tooltip plugin
});
```

## Fisheye Lens

Fisheye is designed for focus_context exploration, it keeps the context and the relationships between context and the focus while magnifing the focus area.

### Configuration

| Name | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| trigger | 'drag' / 'mousemove' / 'click' | false | 'mousemove' | The trigger for the lens |
| d | Number | false | 1.5 | Magnify coefficient. Larger the value, larger the focus area will be magnified |
| r | Number | false | 300 | The radius of the focus area |
| delegateStyle | Object | false | { stroke: '#000', strokeOpacity: 0.8, lineWidth: 2, fillOpacity: 0.1, fill: '#ccc' } | The style of the lens's delegate |
| showLabel | Boolean | false | false | If the label is hidden, whether to show the label of nodes inside the focus area |
| maxR | Number | The height of the graph | The maximum radius scaled by the wheel |
| minR | Number | 0.05 \* The height of the graph | The minimum radius scaled by the wheel |
| maxD | Number | 5 | when `trigger` is `'mousemove'` or `'click'`, minimap allow users to adjust the magnifying coefficient `d` by dragging left / right on the lens. `maxD` is the maximum magnifying coefficient that limits this interaction. The suggested range for `maxD` is [0, 5]. Note that updating the configurations by `minimap.updateParam` will not be limited by `maxD` |
| minD | Number | 0 | when `trigger` is `'mousemove'` or `'click'`, minimap allow users to adjust the magnifying coefficient `d` by dragging left / right on the lens. `minD` is the minimum magnifying coefficient that limits this interaction. The suggested range for `minD` is [0, 5]. Note that updating the configurations by `fisheye.updateParams` will not be limited by `minD` |
| scaleRBy | 'wheel'/'drag'/'unset'/undefined | false | 'unset' | The trigger for end users to scale the range of the lens |
| scaleDBy | 'wheel'/'drag'/'unset'/undefined | false | 'unset' | The trigger for end users to scale the magnification factor of the lens |
| showDPercent | Boolean | false | true | Whether show the percent of current magnification factor on the bottom of the lens, where the percent is about the D, minD, and maxD |

### Member Function

#### updateParams(cfg)

Update partial of the configurations of the fisheye instance, including `trigger`, `d`, `r`, `maxR`, `minR`, `maxD`, `minD`, `scaleDBy`, and `scaleRBy`. E.g.

```
const fisheye = new G6.Fisheye({
  trigger: 'mousemove'
});

... // Other operations

fisheye.updateParams({
  d: 2,
  r: 500,
  // ...
})
```

### Usage

```
const fisheye = new G6.Fisheye({
  trigger: 'mousemove',
  d: 1.5,
  r: 300,
  delegateStyle: clone(lensDelegateStyle),
  showLabel: false
});

const graph = new G6.Graph({
  //... Other graph configurations
  plugins: [fisheye], // configuring fisheye plugin
});
```

## Edge Filter Lens

Edge Filter Lens is designed for edge filtering, the desired edges will be kept inside the lens while the others will be hidden.

### Configuration

| Name | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| trigger | 'drag' / 'mousemove' / 'click' | false | 'mousemove' | The trigger for the lens |
| type | 'one' / 'both' / 'only-source' / 'only-target' | false | 'both' | Simple filtering conditions related to the end nodes. `'one'`: show the edge whose one or more end nodes are inside the filter lens; `'both'`: show the edge whose both end nodes are inside the lens; `'only-source'`: show the edge whose source node is inside the lens and target node is not; `'only-target'`: show the edge whose target node is inside the lens and source node is not. More complicated conditions can be defined by the `shouldShow` |
| shouldShow | (d?: unknown) => boolean | false | undefined | The custom conditions for filtering. The parameter `d` is the data of each edge, you can return boolean value according to the data, where `true` means show. |
| r | Number | false | 60 | The radius of the filter area |
| delegateStyle | Object | false | { stroke: '#000', strokeOpacity: 0.8, lineWidth: 2, fillOpacity: 0.1, fill: '#ccc' } | The style of the lens's delegate |
| showLabel | 'edge' / 'node' / 'both' | false | 'edge' | If the label is hidden, whether to show the label of nodes inside the focus area |
| maxR | Number | The height of the graph | The maximum radius scaled by the wheel |
| minR | Number | 0.05 \* The height of the graph | The minimum radius scaled by the wheel |
| scaleRBy | 'wheel'/'drag'/'unset'/undefined | false | 'unset' | The trigger for end users to scale the range of the lens |

### Member Function

#### updateParams(cfg)

Update partial of the configurations of the filter lens instance, including `trigger`, `type`, `r`, `maxR`, `minR`, `shouldShow`, `showLabel`, and `scaleRBy`. E.g.

```
const filterLens = new G6.EdgeFilterLens({
  trigger: 'drag'
});

... // Other operations

filterLens.updateParams({
  r: 500,
  // ...
})
```

### Usage

```
const filterLens = new G6.EdgeFilterLens({
  trigger: 'mousemove',
  r: 300,
  shouldShow: d => {
    return d.size > 10;
  }
});

const graph = new G6.Graph({
  //... Other graph configurations
  plugins: [filterLens], // configuring edge filter lens plugin
});
```
