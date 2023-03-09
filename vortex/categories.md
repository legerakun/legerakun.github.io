# Creating new category

### Example of category

```
-- Table of category
categories.example                   = {}

-- Name of category
categories.example.name               = "Example"

-- Image of category
categories.example.image              = Material("vortex/gun.png", "vertexalpha vertexcolor")

-- There's a three options for this field
-- If it's "True" your itemTable should contain only images
-- If it's "False" your image field will apply to all items in itemTable
-- If it's "Model" all items will have WorldModel of item listed in itemTable
categories.example.bItemTableIsImages = "True"

-- Table of items of category
categories.example.itemTable          = {Material("vortex/cross.png", "vertexalpha vertexcolor"),
                                         Material("vortex/shield.png", "vertexalpha vertexcolor")
                                        }
                                        
-- Table of features of category                                        
categories.example.featureTable       = {"Add to library",
                                         "Do not add to library"
                                        }

```
