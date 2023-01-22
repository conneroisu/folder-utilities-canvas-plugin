---
created: 2022-12-31T14:29:38-06:00
updated: 2023-01-22T13:26:32-06:00
---
# Work with files and folders in canvas mode!

Obsidian recently released a new core plugin called "canvas" which allows for the user to place Notes, Headers, and Media anywhere in a basically infinite, easily  location. Though a great update and addition I am sure will ignite numerous new plugins for the new mode, this plugin adds numerous canvas and folder commands and utilities to better take advantage of the canvas. 

Made with 🤍 by Conner Ohnesorge 

# Implementations 
**Unidirectional Folders**
**Localizing Canvases**

# Status 
- [ ] This plugin is not completed yet 

# Use
## Commands 

### Unidirectional Folders
| Command Name                                                 | Command id                     | Description                                                                                                                                                                                              |
| ------------------------------------------------------------ | ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Insert Unidirectional Folder into Canvas at selected element | insert-uni-folder-at-selection | This commands gets the currently selected canvas element's posiotion and removes said element, but then, inserts a group representing the folder selected in a modal into the removed elements position. |


### Localize Canvas Command
| Command Name           | Command id             | Description                                                                                                                  |
| ---------------------- | ---------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Localize Active Canvas | localize-active-canvas | This command localizes all files embedded into the canvas that you are presently viewing into the folder housing said canvas |

### Localize Canvas to Folder Command
| Command Name                     | Command id                         | Description                                                                |
| -------------------------------- | ---------------------------------- | -------------------------------------------------------------------------- |
| Localize Active Canvas to Folder | localize-activate-canvas-to-folder | This commmand moves all files embedded in a canvas into a selected folder. |

### Insert Canvas Elements from Vault into the active canvas
| Command Name                      | Command id                 | Description                                                                                                                 |
| --------------------------------- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Insert Canvas at Selected Element | insert-canvas-at-selection | This command inserts the elements in an external canvas into the active canvas through suggestions to the user with a modal |

### Link Group to Folder Using Modal 
| Command Name         | Command id           | Description                                                                                                                                           |
| -------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Link Group to Folder | link-group-to-folder | This command will rename and initialize a selected group with configurable syntax to allow for the organization of files into folders within a canvas |


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
