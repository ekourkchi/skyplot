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


### Demo (Virgo cluster SGL=102 and SGB=-2)

The following diagrams is the output of the code for the Virgo cluster, which is the largest group at the center and color coded in yellow. All groups are color coded based on their average radial velocities, i.e. V_ls. The legend on the right shows that color code. The box on the left shows the coordinate of the sky where the mosue pointer is. Each point is a galaxy and dashed circles represent the 2D projected border of groups. Clicking on each galaxy prints out information about the galaxy its associtaed galaxy in terminal.
 
![Virgo_group](https://user-images.githubusercontent.com/13570487/74584913-92827a00-4f94-11ea-8b6a-203f7587bb13.png)
 

#### Features:

 1) If you click on the color bars on the left, you can turn on/off the colors.
 
 2) On the horizontal bar above the plot, you can interactively manually enter your desired velocity limits. This feature can also be used with the color bar feature to even have more flexibility. After entering your values, press the **set** botton to see the effect. Press *Clear* to clear the text cells and enter new values. Press *Show all* to reset the values (i.e. showing all galaxies, groups).
 
 3) **show all** and **set** buttons can be used alternatively to either display all the objects or to go back to the initial velocity setup.
 
 4) You can also enter radial velocity limits on the command line using **-m** and **-x** flags. See the following examples to only display galaxy with radial velocities between 1,000 and 2,000 km/s:
 
              $ python skyplot_group.py -f all.iter.2.v41.group -c supergalactic -a 102 -d -2 w 50 -m 1000 -x 2000

              
 5) Use the yellow button in the left box **(Reset View)** to go back the view that was originally set in the command line
 
 6) Use the middle mouse scroll wheel on the plot for zooming in/out.
 
 7) Use the yes/no box in the buttom right corner to change the color scheme. 
 
 8) Click on each point (galaxy) to chose it and get some relevant information in the terminal. *pgc* is the galaxy ID. *flag* equals 1 for galaxies in a group and 0 for a single galaxy. *ra*, *dec* *SGL* and *SGB* are the Equatorial and Supergalactic coordinates of the chosen galaxy. *Ks* is the magnitude, *Vls* is the radial velicity in km/s, *dcf2* is the distance in Mpc, *mDist* is the average group distance and *mDistErr* is the uncertainty of the average group distance. *nest* is the pgc ID of the most luminous galaxy in the group. *objname* is the galaxy other name.
 
![terminal](https://user-images.githubusercontent.com/13570487/74585318-a9c36680-4f98-11ea-8bae-ec92acc95da5.png)
 
 9) If the chosen galaxy is in a group, a new window pops out and dispayes the radial velocity distribution of all group members. 

![Velocity_Distribution](https://user-images.githubusercontent.com/13570487/74585332-be9ffa00-4f98-11ea-8fb6-11f79e8ef4d6.png)
