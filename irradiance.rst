.. include:: _definitions.rst

.. _f_light:
.. index::
    single: multiplicative; F_light

Irradiance and `F_\text{light}`
-------------------------------

The "big leaf" |DO3SE| model uses a one-layer "two big-leaf" approach to calculate the stomatal conductance. This assumes that the canopy can be represented as a single "big-leaf" leaf split into shaded and sun lit fractions. This model follows the accepted principle that radiation attenuation through canopies follows Beer’s law and that such radiation penetration must separately consider direct and diffuse radiation, due to their different attenuation through canopies, and visible and near infra-red wavelengths due to differential absorptance by leaves :cite:`Goudriaan1977`. The DO3SE model uses the radiation attenuation method of :cite:`WeissNorman1985` to estimate the quantity and quality of radiation distribution through the canopy. Application of this model requires that the Photosynthetically Active Radiation (PAR), which has a wavelength of 400 to 700 nm, reaching the top of the canopy has to be differentiated into direct and diffuse irradiance. This is dependent upon transmission through the atmosphere which is a function of optical air mass (`om`), atmospheric pressure, (`P`) and hence altitude. If atmospheric pressure is not recorded, it can be estimated according to :eq:`altitude_pressure`.

.. math:: P = P_0 \cdot \exp\left(-g \cdot \frac{h_\text{site}}{H_\text{atm}}\right)
    :label: altitude_pressure

where `P_0` is the atmospheric pressure at sea level (101.325 kPa), `g` is the acceleration due to gravity (9.81 m s\ :sup:`-2`), `h_\text{site}` is the site altitude in m and `H_\text{atm}` is the atmospheric scale height (7400 m).

The value of `om` can be calculated according to :cite:`WeissNorman1985` as in :eq:`om`.

.. math:: om = \left(\sin\beta\right)^{-1}
    :label: om

where `\sin\beta` is the solar elevation.  This parameter varies over the course of the day as a function of latitude and day length as described in :eq:`sinB`.  This equations and the other solar geometry equations required for it's calculation are taken from :cite:`CampbellNorman1998`.

.. math:: \sin\beta = \sin\lambda \cdot \sin\delta + \cos\lambda \cdot \cos\delta \cdot \cos{hr}
    :label: sinB

where `\beta` is the solar elevation above the horizontal, `\lambda` is the latitude, `\delta` is the angle between the sun's rays and the equatorial plane (solar declination), `hr` is the hour angle of the sun and is given by `[15(t - t_0)]` where `t` is time and `t_0` is the time at solar noon.

The solar declination (`\delta`) is calculated according to :eq:`solar_dec`.

.. math:: \delta = -23.4 \cos\left[\frac{360(t_d + 10)}{365}\right]
    :label: solar_dec

where `t_d` is the year day.

The time, `t` is in hours (standard local time), ranging from 0 to 23.  Solar noon (`t_0`) varies during the year by an amount that is given by the equation of time (`e`, in min) and calculated by:

.. math:: t_0 = 12 - LC - e
    :label: solar_noon

where `LC` is the longitude correction.  `LC` is +4 or -4 minutes for each degree east or west of the standard meridian.  `e` is a 15 to 20 minute correction which depends on year day according to :eq:`equation_of_time`.

.. math:: e = \frac{-104.7 \sin f + 596.2 \sin^2 f + 4.3 \sin^3 f - 12.7 \sin^4 f - 429.3 \cos f - 2.0 \cos^2 f + 19.3 \cos^3 f}{3600}
    :label: equation_of_time

where `f = 279.575 + 0.9856 t_d`, in degrees.

It is also necessary to calculate the day length so that the hour angle of the sun can be calculated throughout the day. Day length is defined as the number of hours that the sun is above the horizon and requires the hour angle of the sun, `hr`, at sunrise or sunset to be calculated with :eq:`hour_angle`.

.. math:: \cos{hr} = -\tan\lambda \cdot \tan\delta
    :label: hour_angle

so that day length in hours equals `2 \cdot hr / 15`.

The formulations of :cite:`WeissNorman1985` can then be used to estimate the potential direct (`pPAR_\text{dir}`) :eq:`pPARdir` and diffuse (`pPAR_\text{diff}`) :eq:`pPARdiff` irradiances in |Wm2| which are necessary to estimate irradiance penetration and quality (whether direct or diffuse) into the canopy.

.. math:: p\text{PAR}_\text{dir} = 600 \cdot \exp\left( -0.185 \cdot \frac{P}{P_0} \cdot om \right) \cdot \sin\beta
    :label: pPARdir

where the 600 (|Wm2|) represents the average amount of PAR radiation available at the top of the atmosphere, estimated according to the solar constant (1320 |Wm2|), of which 0.45 is the PAR fraction :cite:`Jones1992` and 0.185 represents the extinction coefficient.

.. math:: p\text{PAR}_\text{diff} = 0.4 \cdot (600 - p\text{PAR}_\text{dir}) \cdot \sin\beta
    :label: pPARdiff

where the term in brackets represents the total available PAR diffuse radiation. 0.4 is the fraction of intercepted PAR beam radiation that is converted to downward diffuse radiation at the surface. The potential total PAR beam radiation (`p\text{PAR}_\text{total}`) is then the sum of `p\text{PAR}_\text{dir}` and `p\text{PAR}_\text{diff}`. The actual total PAR (`\text{PAR}_\text{total}`) is measured at each site (or provided as modelled values). To allow for variability in the calibration of the measurement apparatus or modelled data we estimate the sky transmissivity (`ST`) during the daylight period as in :eq:`ST` where the `p\text{PAR}_\text{total}` is not allowed to exceed the `\text{PAR}_\text{total}`.

.. math:: ST = \min \left\{ 0.9, \max \left\{ 0.21, p\text{PAR}_\text{total} / \max \left\{ p\text{PAR}_\text{total}, \text{PAR}_\text{total} \right\} \right\} \right\}
    :label: ST
