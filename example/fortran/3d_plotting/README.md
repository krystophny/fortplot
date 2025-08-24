# 3D Plotting Examples

This comprehensive example demonstrates all 3D plotting capabilities in fortplot, consolidating features from multiple examples.

## Features Demonstrated

- **3D Line Plots**: Helices and parametric curves
- **3D Scatter Plots**: Multiple patterns and marker types
- **3D Surface Plots**: Mathematical functions and meshes
- **Mixed Plots**: Combining 2D and 3D in single figures
- **Plot Combinations**: Multiple 3D plot types together

## Running

```bash
make example ARGS="3d_plotting"
```

## Output Files Generated

### PNG Visualization
- `3d_helix.png` - Basic 3D helix line plot
- `parametric_curve.png` - Parametric spiral curve
- `scatter_sphere.png` - 3D scatter in sphere pattern
- `scatter_multiple.png` - Multiple scatter patterns with legend
- `surface_paraboloid.png` - Paraboloid surface plot
- `surface_gaussian.png` - Gaussian surface plot
- `mixed_plots.png` - Combined 2D and 3D plots
- `scatter_line_combo.png` - 3D scatter + line combination


## API Usage Examples

### Basic 3D Line Plot
```fortran
call fig%add_3d_plot(x, y, z, label="3D Line")
```

### 3D Scatter Plot
```fortran
call fig%add_scatter_3d(x, y, z, label="Scatter", marker='o')
```

### 3D Surface Plot
```fortran
call fig%add_surface(x_grid, y_grid, z_grid, label="Surface")
```

## Technical Notes

- **Automatic 3D Detection**: fortplot automatically detects 3D data
- **No Special Initialization**: Same `fig%initialize()` for 2D and 3D
- **Mixed Dimensionality**: Can combine 2D and 3D plots in same figure
- **Surface Grid Requirements**: `size(z_grid,1) == size(x_grid)` and `size(z_grid,2) == size(y_grid)`
- **Memory Management**: Uses allocatable arrays for efficient memory usage