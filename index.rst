.. DO3SE documentation master file, created by
   sphinx-quickstart on Thu Feb 19 19:09:06 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. include:: _definitions.rst

|DO3SE| documentation
=====================

.. toctree::
   :maxdepth: 2

   irradiance
   zreferences


The |DO3SE| modules and parametrisations
----------------------------------------

.. list-table::
    :header-rows: 1

    * - DO3SE modules
      - Model variable
      - Unit
      - Key references
    * - Ozone dry deposition flux
      - `F_g`
      - |molO3_PLA_s|
      - :cite:`Simpson2012`
    * - Ozone dry deposition velocity
      - `V_g`
      - |sm_1|
      - :cite:`Simpson2012`
    * - Atmospheric resistance (for both stable and turbulent atmospheres)
      - `R_\text{a}`
      - |sm_1|
      - :cite:`Simpson2012`
    * - Boundary layer resistance (for canopy and leaf)
      - `R_\text{b}` (canopy), `r_\text{b}` (leaf)
      - |sm_1|
      - :cite:`Simpson2012,LRTAPMM`
    * - Surface resistance
      - `R_\text{sur}`
      - |sm_1|
      - :cite:`Simpson2012`
    * - In-canopy resistance
      - `R_\text{inc}`
      - |sm_1|
      - :cite:`Emberson2001`
    * - External plant resistance
      - `R_\text{ext}`
      - |sm_1|
      - :cite:`Emberson2001`
    * - Soil resistance
      - `R_\text{soil}`
      - |sm_1|
      - :cite:`Emberson2001`
    * - Stomatal conductance (multiplicative)
      - `g_\text{sto}`
      - |mmolO3_PLA_s|
      - :cite:`LRTAPMM`
    * - Stomatal conductance (photosynthesis-based)
      - `g_\text{sto}`
      - |mmolO3_PLA_s|
      - :cite:`Buker2007`
    * - Leaf Area Index
      - `\text{LAI}`
      - |m2m2|
      - :cite:`Simpson2012`
    * - Stand Area Index
      - `\text{SAI}`
      - |m2m2|
      - :cite:`Simpson2012`
    * - Latitude-derived growing season for forest trees
      - `\text{SGS}` (start of growing season), `\text{EGS}` (end of growing season)
      - Day of year
      - :cite:`LRTAPMM`
    * - Phenology (for leaf and canopy)
      - `f_\text{phen}`
      - fraction
      - :cite:`LRTAPMM`
    * - Irradiance
      - `F_\text{light}`
      - fraction
      - :ref:`Irradiance <f_light>`
    * - Leaf temperature
      - `T_\text{leaf}`
      - degrees C
      -
    * - Soil moisture content
      - `\text{SWC}` (soil water content), `\text{SWP}` (soil water potential)
      - |m3m3|, MPa
      - :cite:`Buker2012`
    * - Soil moisture
      - `f_\text{SWC}`, `f_\text{SWP}`
      - fraction
      - :cite:`Buker2012`
    * - Transfer functions for wind speed and ozone concentration
      -
      -
      - :ref:`transfer_funcs`
