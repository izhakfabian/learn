# learn
__author__ = 'Fabian'
from sklearn import tree
import numpy as np
x=[]
def GetInput():
    """get values for the ML module, T= type, S= status, R= range in percantage A =angle"""
    T=int(raw_input("enter type"))
    S=int(raw_input("enter statuse s=0 l=1"))
    R=int(raw_input("enter range in percantage"))
    A=int(raw_input("enter angle"))
    I =[T, S, R, A]
    print I
    return I

def DescisionMaking(x,y,I):
    """ decide what is the right action based on the input"""
    clf = tree.DecisionTreeClassifier()
    clf = clf.fit(x, y)
    d= clf.predict([I])
    print d
    return d

def Learn():
    I=GetInput()
    x=np.load('x_file.npy')
    y=np.load('y_file.npy')
    recommendation = DescisionMaking(x,y,I)
    print "The recommendation is",  recommendation
    a = raw_input('is the descision correct? yes =1 no =0')
    if int(a)== 1:
        x= np.append(x, I)
        y=np.append(y, recommendation)
    elif a== "n":
        recommendation= int(raw_input("please correct 1= ,2=3=4-"))
        x =x.appnd(I)
        y=y.appnd(recommendation)
    else:
        print "wrong value"
    print x, y

Learn()
