This is a work-in-progress [website](https://fanwangecon.github.io/M4Econ/) of support files for using matlab, produced by [Fan](https://fanwangecon.github.io/). Materials gathered from various [projects](https://fanwangecon.github.io/research) in which matlab codes are used. Matlab files are linked below by section with livescript files.

Please contact [FanWangEcon](https://fanwangecon.github.io/) for issues or problems.
<!-- 1. [Linspace + Logspace Asset Grid](asset/grid/ff_grid_loglin.html): [**mlx**](https://github.com/FanWangEcon/R4Econ/blob/master/asset/grid/ff_grid_loglin.mlx) \| [**M**](https://github.com/FanWangEcon/R4Econ/blob/master/asset/grid/ff_grid_loglin.m) \|  [**html**](asset/grid/ff_grid_loglin.html) \| [**pdf**](asset/grid/ff_grid_loglin.pdf) -->

# Asset Grids

1. [Linspace + Logspace Asset Grid](asset/grid/ff_grid_loglin.m): ipynb \| mlx \| [**M**](https://github.com/FanWangEcon/R4Econ/blob/master/asset/grid/ff_grid_loglin.m) \|  html \| pdf
    + *call*: ff_grid_loglin(it_a_vec_n, fl_amax, fl_amin, fl_loglin_threshold)
    + **core**: *while + logspace + start:gap:fin + unique*

# Table and Figure

1. [Add Columns to Table](table/ff_mat2tab.m): ipynb \| mlx \| [**M**](https://github.com/FanWangEcon/R4Econ/blob/master/table/ff_mat2tab.m) \|  html \| pdf
    + *call*: ff_mat2tab(mt_data, ar_st_colnames)
    + **core**: *array2table, table.Properties.VariableNames*
2. [Export Table or Mat](table/ff_sup_save_prep.m): ipynb \| mlx \| [**M**](https://github.com/FanWangEcon/R4Econ/blob/master/table/ff_sup_save_prep.m) \|  html \| pdf
    + *call*: ff_sup_save_prep(st_path_folder, st_file_name, bl_exp_csv, mt_data, ar_st_colnames); *dependency*: ff_mat2tab
    + **core**: *mkdir, csvwrite, save*


# Matlab Functionalities

1. **Default parameters**: Matlab does not have standard default parameters like most modern languages. The hacks below allow for maintaining code testability. The varargin structure could lead to excessive code preambles. Container Map works well.
    + [Multi-type Varargin Structure](https://github.com/FanWangEcon/M4Econ/blob/master/support/funcdefine/ff_varargin.m)
        - use for functions with limited parameters
        - *function [out_put] = func_name(varargin), cell2mat*
    + [Container Map Structure](https://github.com/FanWangEcon/M4Econ/blob/master/support/funcdefine/ff_defaultmap_test.html): ipynb \| [**mlx**](https://github.com/FanWangEcon/M4Econ/blob/master/support/funcdefine/ff_defaultmap_test.mlx) \| [**M**](https://github.com/FanWangEcon/M4Econ/blob/master/support/funcdefine/ff_defaultmap.m) \|  [**html**](https://github.com/FanWangEcon/M4Econ/blob/master/support/funcdefine/ff_defaultmap_test.html) \| [**pdf**](https://github.com/FanWangEcon/M4Econ/blob/master/support/funcdefine/ff_defaultmap_test.pdf)
        - core model functions with potentially many parameters
        - *function [out_put] = func_name(varargin); cm_defaults = {cm_a, cm_b}; [cm_defaults{1:optional_params_len}] = varargin{:}; cm_c = [cm_a;cm_b]*
2. **Container Maps**: Use this structure for carrying parameters and input arrays. By using container maps, if parameters are added to model, code editing is limited to actual location where parameter is used and initial location of definition.
    + [Any Type Container Maps](support/dtype/map_anytype.m):
        - *containers.Map('KeyType','char', 'ValueType','any')*
    + [Combining Container Maps](support/dtype/map_override.m)
        - *cm_c = [cm_a;cm_b]*
