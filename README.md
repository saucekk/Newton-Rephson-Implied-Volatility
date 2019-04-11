# Newton-Rephson-Implied-Volatility

import scipy as si
from scipy.stats import norm

def f(sigma,S,K,r,T,c):
    d1=(si.log(S/K)+(r+sigma**2/2)*T)/(sigma*si.sqrt(T))
    d2=d1-sigma*si.sqrt(T)
    f=S*norm.cdf(d1)-norm.cdf(d2)*K*si.exp(-r*T)
    return f-c

def fprime(sigma,S,K,r,T,c):
    d1=(si.log(S/K)+(r+sigma**2/2)*T)/(sigma*si.sqrt(T))
    fprime=S*si.sqrt(T)*norm.pdf(d1)
    return fprime

S=
K=
T=
r=
c=

sigma1=0.20
epsilon=10**(-10)

while(True):
    sigma0=sigma1
    sigma1=sigma0-f(sigma0,S,K,r,T,c)/fprime(sigma0,S,K,r,T,c)
    if(si.absolute(sigma1-sigma0)<epsilon):
        break

print(sigma1)
