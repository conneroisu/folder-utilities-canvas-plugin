---
created: 2022-12-31T14:29:38-06:00
updated: 2023-01-14T20:51:47-06:00
---

Obsidian recently released a new core plugin called "canvas" which allows for the user to place Notes, Headers, and Media anywhere in a basically infinite, easily  location. Though a great update and addition I am sure will ignite numerous new plugins for the new mode, this plugin adds numerous canvas and folder commands and utilities to better take advantage of the canvas. 

Made with 🤍 by Conner Ohnesorge 

## Commands 
### Localize Canvas Command
Localize all files embededed the directory that the canvas you are presently viewing into the folder which contains the aformentioned active canvas. 
### Localize Canvas to Folder Command
Make sure that all files present in the canvas are inside of a housing folder. 
### Insert Canvas Elements from Vault into the active canvas
Insert the elements present in a canvas within your vault and insert the canvas into your active canvas. 

### Link Group to Folder Using Modal 
WIll rename the selected group with syntax to allow for the organization of files into folders within the core plugin of canvas. 

### Convert Canvas To Folder and move Contents to it 

### Convert Canvas to Folder and copy Contents to it 


# Usage 
While this plugin adds numerous commands and utilities, they all revolve around operations applied to the currently active canvas in your interface. So, if you encounter problems with commands not appearing, make sure that you are currently editing a canvas file in canvas view. 

# Installation 
## Community Plugins 
Currently unavaliable through community plugins inside of obsidian 
## Manual Install 
You can manually install folder utilities canvas plugin using github: 
1. Go to the GitHub page for folder utilities canvas plugin: https://github.com/conneroisu/folder-utilities-canvas-plugin 

2. Click the "Clone or Download" button and then select "Download ZIP" 
3. Move the folder into your plugin inside of your `.obsidian` folder for your vault you want to add this plugin to 
4. Inside of the folder you have just added to your plugins folder, you can run `npm i` and `npm run dev` to build it. 
5. You now should be able to access the plugin! 

## (Obsidian Canvas Constants Resource for Developers)[ https://github.com/obsidianmd/obsidian-api/blob/master/canvas.d.ts] 

```typescript
// A color used to encode color data for nodes and edges
// can be a number (like "1") representing one of the (currently 6) supported colors.
// or can be a custom color using the hex format "#FFFFFFF".
export type CanvasColor = string;

// The overall canvas file's JSON
export interface CanvasData {
    nodes: AllCanvasNodeData[];
    edges: CanvasEdgeData[];
}

// A node
export interface CanvasNodeData {
    // The unique ID for this node
    id: string;
    // The positional data
    x: number;
    y: number;
    width: number;
    height: number;
    // The color of this node
    color?: CanvasColor;
}

export type AllCanvasNodeData = CanvasFileData | CanvasTextData | CanvasLinkData | CanvasGroupData;

// A node that is a file, where the file is located somewhere in the vault.
export interface CanvasFileData extends CanvasNodeData {
    type: 'file';
    file: string;
    // An optional subpath which links to a heading or a block. Always starts with a `#`.
    subpath?: string;
}

// A node that is plaintext.
export interface CanvasTextData extends CanvasNodeData {
    type: 'text';
    text: string;
}

// A node that is an external resource.
export interface CanvasLinkData extends CanvasNodeData {
    type: 'link';
    url: string;
}

// A node that represents a group.
export interface CanvasGroupData extends CanvasNodeData {
    type: 'group';
    label?: string;
}

// The side of the node that a connection is connected to
export type NodeSide = 'top' | 'right' | 'bottom' | 'left';

// An edge
export interface CanvasEdgeData {
    // The unique ID for this edge
    id: string;
    // The node ID and side where this edge starts
    fromNode: string;
    fromSide: NodeSide;
    // The node ID and side where this edge ends
    toNode: string;
    toSide: NodeSide;
    // The color of this edge
    color?: CanvasColor;
    // The text label of this edge, if available
    label?: string;
}
```
