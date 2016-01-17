# react-pinch-zoom-pan

A react component that lets you add pinch-zoom and pan sub components. 

## Install

`npm install react-pinch-zoom-pan`

## Usage

Take a look at lib/App.js for usage:

```
import React, {Component} from 'react';
import s from 'react-prefixr';
import PinchPanZoom from '..';

export default class App extends Component {
  
  getContainerStyle() {
    return {
      paddingTop: '100%',
      overflow: 'hidden',
      position: 'relative'
    }
  }

  getInnerStyle() {
    return {
      position: 'absolute',
      top: 0,
      left: 0,
      right: 0,
      bottom: 0
    }
  }

  render() {
    return (
      <PinchPanZoom maxScale={2} render={obj => {
        return (
          <div>
            <div style={this.getContainerStyle()}>
              <div style={this.getInnerStyle()}>
                <img 
                  src="http://lorempixel.com/300/300/nature/"
                  style={s({
                    width: '100%', 
                    height: 'auto', 
                    transform: `scale(${obj.scale}) translateY(${obj.y}px) translateX(${obj.x}px)`,
                    transition: '.3s ease'
                  })} />
              </div>
            </div>
            <p>scale: {obj.scale}, x: {obj.x}, y: {obj.y}</p>
          </div>
        );
      }} />
    );
  }
}
```