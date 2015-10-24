# entitas-ts

Entitas ECS
Typescript implementation ported from https://github.com/sschmid/Entitas-CSharp

    +------------------+
    |       Pool       |
    |------------------|
    |    e       e     |      +-----------+
    |        e     e---|----> |  Entity   |
    |  e        e      |      |-----------|
    |     e  e       e |      | Component |
    | e            e   |      |           |      +-----------+
    |    e     e       |      | Component-|----> | Component |
    |  e    e     e    |      |           |      |-----------|
    |    e      e    e |      | Component |      |   Data    |
    +------------------+      +-----------+      +-----------+
      |
      |
      |     +-------------+  Groups:
      |     |      e      |  Subsets of entities in the pool
      |     |   e     e   |  for blazing fast querying
      +---> |        +------------+
            |     e  |    |       |
            |  e     | e  |  e    |
            +--------|----+    e  |
                     |     e      |
                     |  e     e   |
                     +------------+
    
### Live Demo
https://darkoverlordofdata.com/entitas-ts-example/

### Visual Debugging
Include dat.gui, and entitas-ts will display live stats for entities, pools, and systems.
 * http://code.google.com/p/dat-gui

### Entitas cli
use entitas cli to generate empty components & extensions:


    Usage:
      entitas init namespace 
      entitas create -c name field:type... 
      entitas create -s name path interface...
      entitas create -e name 
      entitas generate
    
    Options:
      -c  [--component] # create a component
      -s  [--system]    # create a system
      -e  [--entity]    # create entity
      -x  [--extension] # create an extension
    
Components classes are generated from json configuration, enforcing data oriented design.

Default template is equivalent to:

      entitas create -c Player
      entitas create -c Position x:number y:number
      entitas create -c View sprite:Object
      entitas create -c Velocity x:number y:number
      entitas create -c Movable
      entitas create -c Destroy
      entitas create -c Input x:number y:number
      entitas create -c Interactive
      entitas create -c Resource name:string
      entitas create -c Score value:number
      entitas create -s DestroySystem IReactiveSystem ISetPool
      entitas create -s ProcessInputSystem IReactiveSystem ISetPool
      entitas create -s RenderPositionSystem IReactiveSystem
      entitas create -s AddViewSystem IReactiveSystem
      entitas create -s RemoveViewSystem IReactiveSystem ISetPool IEnsureComponents
      entitas create -s ScoreSystem IInitializeSystem IReactiveSystem ISetPool


# MIT License

Copyright (c) 2015 Bruce Davidson &lt;darkoverlordofdata@gmail.com&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
