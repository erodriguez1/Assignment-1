# Assignment-1
Converting from Decimal to Binary Representation and the Altitude of a Satellite 


#Elizabeth Rodriguez
#Phys 50733: Computational Physics
#Assignment 1


#1: Converting from decimal to binary representation
# Set up an algorithm which converts a integer number given in the
#base-10 representation to the binary representation. You may or may not
#use a scientific representation. Write thereafter a program which
#implements this algorithm.

print 'Decimal to Binary and Binary to Decimal conversion'
print 'Enter 1 if you want to convert dec to bin'
print 'Enter 2 if you want to convert bin to dec'
x=input('Enter either 1 or 2 to start:') #In order to determine which set of equations you will be using
if x==1: #If you input 1 
    i=1
    s=0
    dec=input('Enter decimal to be converted:') #Input decimal number
    while dec>0: #Process in order to convert from decimal to binary
        rem=dec%2
        s=s+(i*rem)
        dec=dec/2
        i=i*10
    print 'The binary of the given number is', s, '.'
else: #If you input 2
        bin=raw_input('Enter binary to be converted:') #Input binary number
        n=len(bin) # Returns the number of elements associated with binary 
        res=0
        for i in range(1,n+1):
            res=res+int(bin[i-1])*2**(n-i)
        print 'The decimal of the given binary is',res,'.'
        

#2: Altitude of a satellite
# A satellite is to be launched into a circular orbit around the Earth so
#that it orbits the planet once every T seconds.

#A) Show that the altitude h above the Earths surface that the satellite
#must have is,h=((GMT^2)/(4*PI^2))^(1/3)-R, where
#G=6.67e(-11)m^3kg^-1s^-2 (Newton's Gravitational Constant),
#M=5.97e(24)kg (Mass of Earth), R=6371 km (Radius)

# In order to obtain an equation for the altitude of a satellite, h, one
#must use the Law of Gravitation. Which states, (m*v^2)/r = (G*m*M)/r^2
#where v = sqrt((GM)/r)).
# In addition one must obtain the orbital radius, but we must obtain an
#equation for the period of a satellite first. Which states,
#T = (2*PI*r)/v =(2*PI)*sqrt(r^3/(GM))
# Once you rearrange for r you'll have the orbital radius. But, not the
#altitude. Altitude (h) has the following equation, h = r-R, where R is
#the radius of Earth that you must account for due to escape velocity
#that a satellite must overcome. 
# As a result, you'll have h=((GMT^2)/(4*PI^2))^(1/3)-R = r-R

#B) Write a program that asks the user to enter the desired value of T
#and then calculates and prints out the correct altitude in meters

from __future__ import division
G=6.67e-11 #Newton's Gravitational Constant
M=5.97e24 #Mass of Earth
r1=6371 #units is km
r2=r1*1000 #converts km to m
R=r2 #Radius of Earth in units m
T=float(input('Enter time (seconds):'))
import math
h=round(float(((G*M*T**2)/(4*math.pi**2))**(1.0/3.0)-R),3) #Calculation of altitude
print 'T (sec):',T,'Altitude (m) {0:.3f}. :',h

#C) Use your program to calculate the altitude of satellites that orbit
#the Earth once a day (so-called geosynchronous orbit), once every 90
#minutes, and once every 45 minutes. What do you conclude from the last
#of these calculations?

from __future__ import division
G=6.67e-11 #Newton's Gravitational Constant
M=5.97e24 #Mass of Earth
r1=6371 #units is km
r2=r1*1000 #converts km to m
R=r2 #Radius of Earth in units m
t=float(input('Enter time (min):'))
T=t*60 #Obtain time in sec
import math
h=round(float(((G*M*T**2)/(4*math.pi**2))**(1.0/3.0)-R),3) #Calculation of altitude
print 't (min):',t,'Altitude (m):',h

# When T=90 min,h=279321.625373 m
# When T=45 min, h=-2181559.89781 m
# In conclusion, the longer the orbital period is then the satellite will
#have a higher altitude. So moving high enough will make its orbit match
#Earth's rotation rate which is clearly shown between the +- sign
#difference

#D) Technically a geosynchronous satellite is one that orbits the Earth
#once persidereal day, which is 23.93 hours, not 24 hours. Why is this?
#And how much difference will it make to the altitude of the satellite?

from __future__ import division
G=6.67e-11 #Newton's Gravitational Constant
M=5.97e24 #Mass of Earth
r1=6371 #units is km
r2=r1*1000 #converts km to m
R=r2 #Radius of Earth in units m
t=float(input('Enter time (hr):'))
T=t*3600 #Obtain time in sec
import math
h=round(float(((G*M*T**2)/(4*math.pi**2))**(1.0/3.0)-R),3) #Calculation of altitude
print 't (hr):',t,'Altitude (m):',h

# When T=23.93 hr, h=35773762.3299 m
# When T=24 hr, h=35855910.1762 m
# Difference = 82147.84630000591 m
# There are two ways to measure the amount of time that it takes a planet
# to rotate; the time it takes the Earth to rotate compared to the stars
#(23.93 hr) and the time it takes the Earth to rotate compared to the
#Sun (24 hr). Common time on a typical clock measures a slightly longer
#cycle, accounting not only for the Earth's axial rotation but also Earth's
#annual revolution around the sun. The difference is not significant to
#make any changes due to the altitude of the satellite but if there was a
#higher difference then there would be significant changes. 
