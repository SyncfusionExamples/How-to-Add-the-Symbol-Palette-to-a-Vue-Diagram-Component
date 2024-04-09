<template>
  <div class="container">
    <div>
      <ejs-symbolpalette :width="paletteWidth" :height="paletteHeight"
      :palettes="palettes"
      :symbolHeight="symbolHeight"
      :symbolWidth="symbolWidth"
      :paletteExpanding="paletteExpanding"
      :enableSearch="true"
      :symbolPreview="symbolPreview"></ejs-symbolpalette>
    </div>
    <div>
      <ejs-diagram :width="width" :height="height"></ejs-diagram>
    </div>
  </div>
</template>
<script>

import {
  DiagramComponent,
  SymbolPaletteComponent
} from '@syncfusion/ej2-vue-diagrams';

let flowShapes = [
  { id: 'Terminator', shape: { type: 'Flow', shape: 'Terminator' }},
  { id: 'Process', shape: { type: 'Flow', shape: 'Process' } },
  { id: 'Data', shape: { type: 'Flow', shape: 'Data' } },
  { id: 'Document', shape: { type: 'Flow', shape: 'Document' } }
];

let basicShapes = [
  { id: 'Rectangle', shape: { type: 'Basic', shape: 'Rectangle' } },
  { id: 'Ellipse', shape: { type: 'Basic', shape: 'Ellipse' } },
  { id: 'Hexagon', shape: { type: 'Basic', shape: 'Hexagon' } },
  { id: 'Star', shape: { type: 'Basic', shape: 'Star' } }
];

let connectorSymbols = [
  {
    id: 'Directional-Connector',
    type: 'Straight',
    sourcePoint: { x:0, y:0},
    targetPoint: { x:0, y:60},
    targetDecorator: {shape: 'Arrow'}
  },
  {
    id: 'Line',
    type: 'Straight',
    sourcePoint: { x: 0, y: 0 },
    targetPoint: { x: 60, y: 60 },
    targetDecorator: { shape: 'None' }
  },
  {
    id: 'Elbow-Directional',
    type: 'Orthogonal',
    sourcePoint: { x: 0, y: 0 },
    targetPoint: { x: 60, y: 60 },
    targetDecorator: { shape: 'Arrow' }
  },
  {
    id: 'Elbow',
    type: 'Orthogonal',
    sourcePoint: { x: 0, y: 0 },
    targetPoint: { x: 60, y: 60 },
    targetDecorator: { shape: 'None' }
  }
];

export default {
  components: {
    'ejs-diagram': DiagramComponent,
    'ejs-symbolpalette': SymbolPaletteComponent
  },
  data: function () {
    return {
      width: '1102px',
      height: '702px',
      paletteWidth: '300px',
      paletteHeight: '700px',
      symbolHeight: 60,
      symbolWidth: 60,
      symbolPreview: {
        height: 150,
        width: 150,
        offset: {
          x:15,
          y:10
        }
      },
      palettes: [
        {
          id: 'flow',
          title: 'Flow Shapes',
          symbols: flowShapes
        },
        {
          id: 'basic',
          title: 'Basic Shapes',
          symbols: basicShapes,
          expanded: false
        },
        {
          id: 'connectors',
          title: 'Connectors',
          symbols: connectorSymbols,
        }
      ],
      paletteExpanding: (args)=>{
        if(args.palette.id == 'flow'){
          args.cancel = true;
        }
      }
    };
  }
};
</script>

<style>
@import "../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";

.container {
  display: flex;
  margin-left: 10px;
}
</style>