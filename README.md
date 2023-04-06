# Fitting Poisson  distribution
# Aim : 

To fit poisson distribution for the arrival of objects per minute from the feeder

# Software required :  

Python and Visual component tool

# Theory:

The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.

![image](https://user-images.githubusercontent.com/104613195/166248326-fd042076-8b0b-40c4-8b11-1d8e8fcb74db.png)

 Conditions for Poisson Distribution:

1. An event can occur any number of times during a time period.
2. Events occur independently. I
3. The rate of occurrence is constant.
4. The probability of an event occurring is proportional to the length of the time period. 
 
# Procedure :

![image](https://user-images.githubusercontent.com/104613195/166251988-d0c53205-6080-4f7b-ae4c-398178586637.png)

# Experiment :
![192953068-30698907-c247-4c44-aa52-b176153e6626](https://user-images.githubusercontent.com/118889143/230278986-3d151149-df03-43b3-b054-42662e4bb494.png)

![192953094-118925ff-ee7a-469d-912b-3f7e1082e2d2](https://user-images.githubusercontent.com/118889143/230278943-62b7926d-f703-48b6-bacb-152c304004ed.png)

# Program :
```
import numpy as np
import math
import scipy.stats
L=[int(i) for i in input().split()]
N=len(L);M=max(L)
X=list();f=list()
for i in range(M+1):
    c=0
    for j in range (N):
        if L[j]==i:
            c=c+1
    f.append(c)
    X.append(i)
sf=np.sum(f)
p=list()
for i in range(M+1):
    p.append(f[i]/sf)
mean=np.inner(X,p)
pr=list();E=list();xi=list()
print(" X P(X=x) Obs.Fr Exp.Fr xi")
print("------------------------")
for x in range(M+1):
    pr.append(math.exp(-mean)*mean**x/math.factorial(x))
    E.append(pr[x]*sf)
    xi.append((f[x]-E[x])**2/E[x])
    print("%2.2f %2.2f %4.2f %3.2f %3.2f"%(x,pr[x],f[x],E[x],xi[x]))
print("------------------")
cal_chi2_sq=np.sum(xi)
print("Calculated value of Chi square is %4.2f"%cal_chi2_sq)
table_chi2=scipy.stats.chi2.ppf(1-.01,df=M)
print("Table value of Chi square at 1 level is %4.2f"%table_chi2)
if cal_chi2_sq<table_chi2:
    print("The given data can be fitted in poisson distribution at 1% LOS ")
else:
     print(("The given data cannot be fitted in poisson distribution at 1% LOS "))
 
```
#output :
![195506884-60443103-3d9e-4631-b2e1-4a2fe10ac765](https://user-images.githubusercontent.com/118889143/230282408-92d29d53-18c3-4b52-aa86-f4bd511a833c.png)


# Results : 
 Thus the poisson distribution for the arrival of objects per minute from the feeder is fitted.
