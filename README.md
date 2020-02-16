# skyplot
Tools to visulaize the 2D sky projection of groups and associations discusses in Kourkchi and Tully (2017, ApJ, 843, 16), Galaxy Groups Within 3,500 km/s. 

Click here to see the paper: http://adsabs.harvard.edu/abs/2017ApJ...843...16K

## Table of contents
1. [Visulaizing Galaxy Groups (skyplot_group.py)](#skyplot_group)
2. [Demo (Virgo Cluster)](#demo)
3. [Features](#features)
4. [Visulaizing Galaxy Groups Associations (skyplot_supergroup.py)](#skyplot_supergroup)
5. [Dependencies](#dependencies)


## Visulaizing Galaxy Groups: **skyplot_group.py** <a name="skyplot_group"></a>
   
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


### Demo (Virgo cluster SGL=102 and SGB=-2) <a name="demo"></a>

The following diagrams is the output of the code for the Virgo cluster, using the following command:

             $ python skyplot_group.py -f all.iter.2.v41.group -c supergalactic -a 102 -d -2 w 50


Virgo is the largest group at the center and color coded in yellow. All groups are color coded based on their average radial velocities, i.e. V_ls. The legend on the right shows that color code. The box on the left shows the coordinate of the sky where the mosue pointer is. Each point is a galaxy and dashed circles represent the 2D projected border of groups. Clicking on each galaxy prints out information about the galaxy its associtaed galaxy in terminal.
 
![Virgo_group](https://user-images.githubusercontent.com/13570487/74584913-92827a00-4f94-11ea-8b6a-203f7587bb13.png)
 

#### Features: <a name="features"></a>

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
 
 9) If the chosen galaxy is in a group, a new window pops out and dispayes the radial velocity distribution of all group members. See the following example for the velocity distribution of galaxies in the group whose brightest galaxy is PGC 42734. Dashed black line is the average radial velocity and red otted lines denote the 1-sigma borders. *d* is the evaluated average distance of the group. 

![Velocity_Distribution](https://user-images.githubusercontent.com/13570487/74585332-be9ffa00-4f98-11ea-8fb6-11f79e8ef4d6.png)

 10) If you use the **-G** command flag, you would be able to overplot the 6.8 degree circle around Virgo and also the divider line. Using this flag for other regions dose not have any effect. See the following plot.
 
![Virgo1](https://user-images.githubusercontent.com/13570487/74585632-d9c03900-4f9b-11ea-9af6-5a53ad5e84c6.jpeg)

 11) Skyplot enables you to make plots in Cartesian coordinates. Skyplot needs to use distances to calculate SGX, SGY and SGZ, and for most cases it uses some sort of measured distances. Either galaxies have direct measured distances or they have some associated distances through the group they belong to. If there is no measured distance available, it uses Hubble distances. 
 
![skyplot_demo](https://user-images.githubusercontent.com/13570487/74585771-bac2a680-4f9d-11ea-87c8-ed7857f16474.png)

 You can run *skyplot_group* and *skyplot_supergroup* with approporiate flags to generate plots in SGX-SGY-SGZ coordinates. For example
 

               $ python skyplot_group.py -f all.iter.2.v41.group -c cartesian  -x 3500
               
plots everything up to Vls=3500 km/s in SGX-SGY system by default. Also, you can specify the center of plot and its size. In the folloing case case **-w 15** means 15 Mpc.
In this case the projection is automatically detected to be on a SGX-SGY plane.
   
   
               $ python skyplot_group.py -f all.iter.2.v41.group -c cartesian  --SGX=10 --SGY=15 -w 15
   
   If you specify all tree SGX, SGY and SGZ coordinates of the center, you need to use -j flag to specify your desired projection. This is explained below.
   
               $ python skyplot_group.py -f all.iter.2.v41.group -c cartesian  -m 1000 -x 2000 -j 3
                  
  The options you can use after -j are as follows:
  
                1  - SGX-SGY                      
                2  - SGX-SGZ
                3  - SGY-SGZ                      
              
                10 - SGY-SGX
                20 - SGZ-SGX                      
                30 - SGZ-SGY

  **Note**: You can set either the velocity range or the center of the coordinate system when working in Cartesian coordinates. Using a combination of both is also possible. See this example:
  
  
               $ python skyplot_group.py -f all.iter.2.v41.group -c cartesian  --SGX=10 --SGY=20 -w 15 -m 1000 -x 2000
               
   were, Vmin=1000 km/s and Vmax=2000 km/s, while the center of the coordinate system and its size were specified.
   
 12) You can also set the center and thickness in the line-of-sight of the view. So, for example, if you are looking at an SGX-SGY view with —SGX=0 —SGY=8 -w 16 then maybe you want to look in the SGZ direction centered at -8 and thickness 4. The following commands satify your conditions
 
               $ python skyplot_group.py -f all.iter.2.v41.group -c cartesian  --SGX=0 --SGY=8 -w 16 --SGZ=-8 --ZT=4

 When you specify the thickness parameter (**--ZT** above), you don't need to specify projection value. If you happen to specify the projection direction and it's incompatible with the specified projection, it ignores the thickness parameter. **Note:** Command line is NOT sensitive to the given order of parameters.

 This is the list all thickness parameters you can use.
 
 
                --XT=XT       X-axis thickness (Mpc)
                --YT=YT       Y-axis thickness (Mpc)
                --ZT=ZT       Z-axis thickness (Mpc)
                                
 **Useful feature:** When you are in Cartesian mode, you can see SGX-SGY-SGZ coordinates of the selected object on the left side on the plot in the coordinate box.
 
 
## Visulaizing Galaxy Groups Associations: **skyplot_supergroup.py** <a name="skyplot_supergroup"></a> 

Associations (supergroups) are enseble of galaxy groups that are within the first turnaround radius of the enclosed mass. For more details on the physical meanings and definitions perlse refer to Kourkchi and Tully (2017, ApJ, 843, 16): http://adsabs.harvard.edu/abs/2017ApJ...843...16K


   - How to run (example). The following diagrams is the output of the code for the Virgo cluster, using this command:

   
                $ python skyplot_supergroup.py -f all.iter.2.v41.supergroup -c supergalactic -a 102 -d -2 w 50

                
![Virgo_supergroup](https://user-images.githubusercontent.com/13570487/74596491-25f79180-500d-11ea-9c23-d1a81d743ebc.png)


In this plot, each point represents a group and the big circles are the halos of *galaxy group associations*. The radius of each circle is the projected first turnaround radius, of the corresponding halo.


Symbols are:

 1) Filled points: groups in super-groups
 2) Open point: groups not in any super-group
 3) filled boxes: single galaxies associated to a super groups
 4) crosses (x) : single galaxies not associated to anything

By clicking on each point you can see the group projected radius resented by R2t. For example, in the above plot, the red star shows the center of the Virgo cluster and dhashed red circle is its projected second turnaround radius. 

The code uses the following formulation to calculate first turnaround radii, r1t. It uses the Hubble distance for those groups with no available distance information. 

                r2t = sqrt(1.5)*R_2t
                r1t = 3.5*r2t

All other features of **skyplot_supergroup.py** are very similar to those of **skyplot_group.py**.

By clicking on each point, you can get some relevant information in the terminal.

![selected_suergroup](https://user-images.githubusercontent.com/13570487/74596689-d5356800-500f-11ea-8085-27d4a1f24fef.png)


Here is the meaning of the numeric flags:

 1) flag = 5: Super-group head
 2) flag = 4: group in a supergroup
 3) flag = 3: single galaxy in a supergroup
 4) flag = 2: single group NOT in any supergroup
 5) flag = 0: single galaxy NOT in any group or super-group

 
## Dependencies: <a name="dependencies"></a> 

This code has been tested using **Python 3.7.6**. For any later python versions, you may need to modify/adjust a few syntaxes to get all the GUI features to work. 

This is the list of the python packages you need. 

 1) Python main packages:
   - matplotlib
   - numpy
   - optparse
   - astropy


             sudo apt-get install python3-tk
             
 2) Python external packages. These are not available in the *PyPi* repository and therefore you need to install them manually. 
   - **kapteyn** (get it here: https://www.astro.rug.nl/software/kapteyn/). The latest version for Python 3.x can be installed using *pip* as follow
   
   
                
                pip install https://www.astro.rug.nl/software/kapteyn/kapteyn-3.0.tar.gz
                
                
   - **tkinter**: This is the heart of the visualization engine.
   Find more about it here: https://docs.python.org/3/library/tkinter.html
   
**Note:** *tkinter* might not be installed using *pip*. So, you need to install it on your system separately. On *Ubuntu*, you can use the following command:


                sudo apt-get install python3-tk

   - - - -
 * Credit: Kourkchi and Tully (2017, ApJ, 843, 16), Galaxy Groups Within 3,500 km/s
 * Author: Ehsan Kourkchi <ekourkchi@gmail.com>
 * Feel free to distribute and modify for a better performance
 
 
 
 
 
