# scatterpie-over-map
help with distorted scatterpies with scatterpie package over a map. Basically, I am trying to plot three pies over a stadiamap of Italy. Depending on the use of the coord_equal() option, I get either: a) a correct Italy with distorted pies; or b) correct pies over a distorted Italy.  A simple example follows. If your email server does not allow email messages that contain code, I can share the file.

# need to register for maps using register_stadiamaps()
library(ggmap)
library(scatterpie)

# a small dataframe with data for pies
data <- data.frame(long = c(15,13,10), lat = c(38,43,46), region = factor(c('sud', 'centro', 'nord')), A = c(1,3,4), B = c(2,2,2), C = c(1,1,5), radius = c(0.2,0.3,0.4))

# plot, example 1
# pies are circular as expected, but Italy is abnormally rendered (too wide)
ggmap(basemap) + # the map
geom_scatterpie(aes(x=long, y=lat, group=region, r=radius), data=data, cols=LETTERS[1:3], color=NA, alpha=.8) + # the pies
coord_equal()

# plot, example 2
# Italy is rendered as expected, but pies are not circular (too narrow)
ggmap(basemap) + # the map
geom_scatterpie(aes(x=long, y=lat, group=region, r=radius), data=data, cols=LETTERS[1:3], color=NA, alpha=.8) # the pies
