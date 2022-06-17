
<!-- README.md is generated from README.Rmd. Please edit that file -->

# rhud <img src='man/figures/logo.png' align="right" width="139"/>

<!-- badges: start -->

[![Project Status: Active – The project has reached a stable, usable
state and is being actively
developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![Lifecycle:
maturing](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://www.tidyverse.org/lifecycle/#maturing)
[![R-CMD-check](https://github.com/etam4260/rhud/workflows/R-CMD-check/badge.svg)](https://github.com/etam4260/rhud/actions)
[![Codecov test
coverage](https://codecov.io/gh/etam4260/rhud/branch/main/graph/badge.svg)](https://codecov.io/gh/etam4260/rhud?branch=main)
[![CodeFactor](https://www.codefactor.io/repository/github/etam4260/rhud/badge/main)](https://www.codefactor.io/repository/github/etam4260/rhud/overview/main)
[![Status at rOpenSci Software Peer
Review](https://badges.ropensci.org/524_status.svg)](https://github.com/ropensci/software-review/issues/524)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.6644503.svg)](https://doi.org/10.5281/zenodo.6644503)
<br/> <br/> [![devel
version](https://img.shields.io/badge/devel%20version-0.3.0.9000-yellow)]()

<!-- badges: end -->

Are you a python developer? Check out
[hudpy](https://github.com/etam4260/hudpy) instead.

## Installation

You can install the development version from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("etam4260/rhud")
```

For more details on how to setup and utilize this package. Please go to
<https://etam4260.github.io/rhud/>. Select \[Setup\] in the navigation
bar.

## Key Access

To use functions provided by this package, you need to get access HUD
USER via token. Go to <https://www.huduser.gov/hudapi/public/login> to
register for an account and then create a token with access to all
datasets provided by HUD. This will include selecting USPS Crosswalk,
Fair Markets Rent, Income Limits, and Comprehensive Housing
Affordability Strategy.

Now copy and paste that key into the hud_set_key() function to be used
throughout your R session.

``` r
hud_set_key("sample-key")
```

## Simplistic Example

This sample provided below shows how to query the USPS Crosswalk API

``` r
hud_cw_zip_tract(zip = '35213', year = c('2010'), quarter = c('1'))
```

## Tibbles vs Dataframes

To get tibbles instead of data frames, use
`options(rhud_use_tibble = TRUE)` or set it explicitly using the
`to_tibble` argument.

``` r
options(rhud_use_tibble = TRUE)

hud_cw_zip_tract(zip = '35213', year = c('2010'), quarter = c('1'),
                 to_tibble = TRUE)
```

## Housing and Urban Development in R

-   This interface uses the HUD User Data API but is not endorsed or
    certified by HUD User.

The goal of this project is to provide an easy-to-use interface to
access various open-source APIs provided by the U.S Department of
Housing and Urban Development. These include the USPS Crosswalk Files,
Fair Markets Rent, Income Limits, and Comprehensive Housing and
Affordability Strategy. Although HUD does provide datasets for other
programs, they are currently not supported by an API.

Please read
<https://www.huduser.gov/portal/dataset/api-terms-of-service.html> for
all terms of service.

According to HUD USER:

All services, which utilize or access the API, should display the
following notice prominently within the application: “This product uses
the HUD User Data API but is not endorsed or certified by HUD User.” You
may use the HUD User name in order to identify the source of API content
subject to these rules. You may not use the HUD User name, or the like
to imply endorsement of any product, service, or entity, not-for-profit,
commercial or otherwise.

## HUD User: <https://www.huduser.gov/portal/datasets>

According to (HUD User Home Page \| HUD USER), HUD User is a U.S.
Department of Housing and Urban Development information source that
includes reports and reference documents. HUD USER was founded in 1978
by the Department of Housing and Urban Development’s Office of Policy
Development and Research.

HUD User maintains an API to gain access to their data. However, their
API system can be confusing and provides their information in JSON
format rather than a data-frame like object. Although there exist file
downloadables, R users may want to be able to extract specific bits of
the data into memory.

## Available Data

The APIs and datasets which this library interfaces are listed below.
The HUD also provide miscellaneous supplemental APIs under them.

1.  HUD User

-   USPS Crosswalk
    (<https://www.huduser.gov/portal/dataset/uspszip-api.html>)

| USPS Crosswalk Files     | Years           |
|--------------------------|-----------------|
| `hud_cw_zip_tract()`     | 2010-2021       |
| `hud_cw_zip_county()`    | 2010-2021       |
| `hud_cw_zip_cbsa()`      | 2010-2021       |
| `hud_cw_zip_cbsadiv()`   | <b>2017-2021<b> |
| `hud_cw_zip_countysub()` | <b>2018-2021<b> |
| `hud_cw_zip_cd()`        | 2010-2021       |
| `hud_cw_tract_zip()`     | 2010-2021       |
| `hud_cw_county_zip()`    | 2010-2021       |
| `hud_cw_cbsa_zip()`      | 2010-2021       |
| `hud_cw_cbsadiv_zip()`   | <b>2017-2021<b> |
| `hud_cw_cd_zip()`        | 2010-2021       |
| `hud_cw_countysub_zip()` | <b>2018-2021<b> |
| `hud_cw()`               | 2010-2021       |
| `crosswalk()`            | 2010-2021       |
|                          |                 |
| `z_in_trt()`             | 2010-2021       |
| `z_in_cty()`             | 2010-2021       |
| `z_in_cbsa()`            | 2010-2021       |
| `z_in_cbsadiv()`         | <b>2017-2021<b> |
| `z_in_ctysb()`           | <b>2018-2021<b> |
| `z_in_cd()`              | 2010-2021       |
| `trt_in_z()`             | 2010-2021       |
| `cty_in_z()`             | 2010-2021       |
| `cbsa_in_z()`            | 2010-2021       |
| `cbsadiv_in_z()`         | <b>2017-2021<b> |
| `ctysb_in_z()`           | <b>2018-2021<b> |
| `cd_in_z()`              | 2010-2021       |
|                          |                 |
| `%z_in_trt%`             | 2021            |
| `%z_in_cty%`             | 2021            |
| `%z_in_cbsa%`            | 2021            |
| `%z_in_cbsadiv%`         | 2021            |
| `%z_in_ctysb%`           | 2021            |
| `%z_in_cd%`              | 2021            |
|                          |                 |
| `%trt_in_z%`             | 2021            |
| `%cty_in_z%`             | 2021            |
| `%cbsa_in_z%`            | 2021            |
| `%cbsadiv_in_z%`         | 2021            |
| `%ctysb_in_z%`           | 2021            |
| `%cd_in_z%`              | 2021            |

-   Fair Markets Rent
    (<https://www.huduser.gov/portal/dataset/fmr-api.html>)
    -   Small Areas Fair Markets Rent

| Fair Markets Rent            | Years     |
|------------------------------|-----------|
| `hud_fmr_state_counties()`   | 2017-2022 |
| `hud_fmr_state_metroareas()` | 2017-2022 |
| `hud_fmr_county_zip()`       | 2017-2022 |
| `hud_fmr_metroarea_zip()`    | 2017-2022 |
| `hud_fmr()`                  | 2017-2022 |

-   Income Limits
    (<https://www.huduser.gov/portal/dataset/fmr-api.html>)

| Income Limits | Years     |
|---------------|-----------|
| `hud_il()`    | 2017-2022 |

-   Comprehensive Housing and Affordability Strategy
    (<https://www.huduser.gov/portal/dataset/chas-api.html>)

| Comprehensive Housing and Affordability Strategy | Years                                                                                              |
|--------------------------------------------------|----------------------------------------------------------------------------------------------------|
| `hud_chas_nation()`                              | 2014-2018 , 2013-2017, 2012-2016, 2011-2015, 2010-2014, 2009-2013, 2008-2012, 2007-2011, 2006-2010 |
| `hud_chas_state()`                               | 2014-2018 , 2013-2017, 2012-2016, 2011-2015, 2010-2014, 2009-2013, 2008-2012, 2007-2011, 2006-2010 |
| `hud_chas_county()`                              | 2014-2018 , 2013-2017, 2012-2016, 2011-2015, 2010-2014, 2009-2013, 2008-2012, 2007-2011, 2006-2010 |
| `hud_chas_state_mcd()`                           | 2014-2018 , 2013-2017, 2012-2016, 2011-2015, 2010-2014, 2009-2013, 2008-2012, 2007-2011, 2006-2010 |
| `hud_chas_state_place()`                         | 2014-2018 , 2013-2017, 2012-2016, 2011-2015, 2010-2014, 2009-2013, 2008-2012, 2007-2011, 2006-2010 |
| `hud_chas()`                                     | 2014-2018 , 2013-2017, 2012-2016, 2011-2015, 2010-2014, 2009-2013, 2008-2012, 2007-2011, 2006-2010 |

-   US Geographic Entities

| US Geographies                      |
|-------------------------------------|
| `hud_nation_states_territories()`   |
| `hud_state_metropolitan()`          |
| `hud_state_counties()`              |
| `hud_state_places()`                |
| `hud_state_minor_civil_divisions()` |

-   Key access

| Management             |
|------------------------|
| `hud_set_key()`        |
| `hud_get_key()`        |
| `hud_set_user_agent()` |
| `hud_get_user_agent()` |

-   Caching

| Caching               |
|-----------------------|
| `hud_set_cache_dir()` |
| `hud_get_cache_dir()` |
| `hud_clear_cache()`   |

-   Utilities

| Utilities          |
|--------------------|
| `rhud_website()`   |
| `hud_rec_cw_yr()`  |
| `hud_rec_fmr_yr()` |
| `hud_rec_il_yr()`  |

## Contributors

-   Emmet Tam(<https://github.com/etam4260>)\[<emmet_tam@yahoo.com>\]
-   Allison Reilly()\[<areilly2@umd.edu>\]
-   Hamed Ghaedi()\[<hghaedi@terpmail.umd.edu>\]
-   Shuyu Jin(<https://github.com/geojsy>)\[<geojsy@umd.edu>\]

## Disclaimers

-   License: GPL >= 2

-   To get citation information for rhud in R, type citation(package =
    ‘rhud’)

-   This interface uses the HUD User Data API but is not endorsed or
    certified by HUD User.

-   The limit on the maximum number of API calls is 1200 queries a min.
    Each function call does not correspond to a single API call!

-   This is a WIP so please report any issues or bugs to:
    <https://github.com/etam4260/rhud/issues>

-   This is open source, so please fork and introduce some pull
    requests!

## Citation

Please cite this package using:

Tam E, Reilly A, Ghaedi H, Jin S (2022). rhud: A R Interface to the
HUD  
      (US Department of Housing and Urban Development) APIs.
0.3.0.9000,  
      <https://github.com/etam4260/rhud/>.

## References

HUD User Home Page: HUD USER. HUD User Home Page \| HUD USER. (n.d.).
Retrieved  
        February 24, 2022, from
<https://www.huduser.gov/portal/home.html>
