
# Values from Helicopter Tutorial
- Base Size = 0.09m
- Maximum Cell Size = 2500 %
- Maximum Core/Prism Transition Ratio -> Limit Cell Size by Prism Layer Thickness = Enable, then
- Size Thickness Ratio = 2
- Number of Prism Layers = 32
- Prism Layer Stretching = 1.25
- Prism Layer Thickness -> Size Type = Absolute
- Prism Layer Thickness -> Absolute Size = 3.83e-2 m
- Surface Curvature -> # Pts/circle = 36.0
- Surface Growth Rate = 1.1
- Surface Proximity = (do not change default values)
- Surface Size -> Relative Minimum Size -> Percentage of Base = 6.25 %
- Surface Size -> Relative Target Size -> Percentage of Base = 100 %
- Template Growth Rate -> Default Growth Rate = Custom, Custom Default Growth Rate = 3
- Template Growth Rate -> Boundary Growth Rate = Custom, Custom Boundary Growth Rate = 4
- Wrapper Scale Factor = 33 %

# Tips and tricks

- Generalized cylindrical meshing only works in serial. If run in parallel it crashes...