# skyplot
Tools to visulaize the 2D sky projection of groups and associations discusses in Kourkchi and Tully (2017, ApJ, 843, 16), Galaxy Groups Within 3,500 km/s. 

Click here to see the paper: http://adsabs.harvard.edu/abs/2017ApJ...843...16K


 * Visulaizing galaxy groups: **skyplot_group.py**
   
   - How to run (example):
   
      Looking at the direction of the *Virgo* cluster, in *Supergalactic* coordinate
   
             $ python skyplot_group.py -f all.iter.2.v41.group -c supergalactic -a 102 -d -2 w 50
    
   - How to get help: 
   
   
             $ python skyplot_group.py -h 
    
   - Commnad line options:
   
   
                  -h, --help            show this help message and exit
                  -a ALPHA, --alpha=ALPHA
                                        right ascension of the coordinate system center
                                        [degree]
                  -d DELTA, --delta=DELTA
                                        declination of the coordinate system center [degree]
                  -f FILE, --file=FILE  The input file, e.g. 'north.iter.9.v23.group'
                  -c COORDINATE, --coordinate=COORDINATE
                                        Coordinate system (i.e. equatorial, galactic,
                                        supergalactic, cartesian)
                  -p PGC, --pgc=PGC     pgc number (optional, specify the plot center)
                  -w WIDTH, --width=WIDTH
                                        The width of the plot in degrees
                  -m VMIN, --Vmin=VMIN  The lower limit on radial velocity
                  -x VMAX, --Vmax=VMAX  The upper limit on radial velocity
                  -X SGX, --SGX=SGX     SGX center
                  -Y SGY, --SGY=SGY     SGY center
                  -Z SGZ, --SGZ=SGZ     SGZ center
                  -j PROJECTION, --projection=PROJECTION
                                        projection type
                                        1  - SGX-SGY                       2  - SGX-SGZ
                                        3  - SGY-SGZ                       10 - SGY-SGX
                                        20 - SGZ-SGX                       30 - SGZ-SGY
                  -u XT, --XT=XT        X-axis thickness (Mpc)
                  -v YT, --YT=YT        Y-axis thickness (Mpc)
                  -t ZT, --ZT=ZT        Z-axis thickness (Mpc)
                  -G                    Plot Virgo Border

![Virgo_group](https://user-images.githubusercontent.com/13570487/74584913-92827a00-4f94-11ea-8b6a-203f7587bb13.png)
 
 
