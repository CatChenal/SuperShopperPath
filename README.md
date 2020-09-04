# SuperShopperPath
Proof of concept for a real app I want to build
---

# Use case:
* Given a shopping list and a supermarket floor plan, obtain the shortest path to collect all items in the list.

# Details:
### Proof of concept:

* User generates a supermarket floor plan from memory on a canvas using labeled rectangles to represent locations.
  ** Save to json, example:
  ```
  # market_XYZ.json:
  [
    [{'floor':<int>,
   'layout':[<rectangles bbox>,]
   #bboxes need a name, e.g: 'entrance', 'exit', 'meats', 'frozen-fruits', etc.
   }]
  ]
  ```
  ** Need mapping btw product categories and floor and shelves  
  ** Need a product description (e.g. product.json):  
    - Name, units, quantity, [price]  
 * Graph creation:  
   ** Nodes are created by lookup of list items location  
   ** Edges are Manhattan distances (L1) from 'Entrance' rectangle  
 * Shopping path generation:  
   ** Calculate TSP path from graph  
 * Output sequence on layout [, or as text]  
 
 ### Implementation:
 * An initial products.json file can be generated (Faker?)  
 * The labelling of the rects on the canvas (Bokeh) can be simplified (& normalized!) using a product_categories.json; better: together with products.json.  
 * The file must be persistent to allow user's modifications.  
 ### Refinements:
 * Amend to use two shopping lists, A and B: you can shop for someone elese in a jiffy!
