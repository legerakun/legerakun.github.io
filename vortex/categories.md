## Creating new category

#### Item categories needs to be added in *vortex.loadCategories* hook

#### Example:

```
hook.Add("vortex.loadCategories", "VortexLoadCategoriesExample", function()
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
  -- Can be a function that returns table, for example weapons.GetList()
  categories.example.itemTable          = {Material("vortex/cross.png", "vertexalpha vertexcolor"),
                                           Material("vortex/shield.png", "vertexalpha vertexcolor")
                                          }
                                          
  -- Table of features of category
  categories.example.featureTable       = {"Add to library",
                                           "Do not add to library"
                                          }
end)                                        

```
