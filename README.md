# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
``` 
Program to QR decomposition using the Gram-Schmidt method
Developed by: Yuvethika v
RegisterNumber: 26016105
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
def QR_Decomposition(A):
  n,m = A.shape
  Q = np.empty((n,n))
  u = np.empty((n,n))
  u[:,0] = A[:,0]
  Q[:,0] = u[:,0]/np.linalg.norm(u[:,0])
  for i in range(1,n):
      u[:,i]=A[:,i]
      for j in range(i):
          u[:,i]-=(A[:,i]@ Q[:,j])*Q[:,j]
      Q[:,i]= u[:,i]/np.linalg.norm(u[:,i])
      R=np.zeros((n,m))
      for i in range(n):
          for j in range(i,n):
              R[i,j]=A[:,j]@ Q[:,i]
  print("The Q Matrix is\n",Q)
  print("The R Matrix is\n",R)
a = np.array(eval(input()))
QR_Decomposition(a)
```

## Output

<img width="870" height="382" alt="Screenshot 2026-11-11 120931" src="https://github.com/user-attachments/assets/d4a18757-149a-49c8-a3c4-bdf9ad133047" />
<img width="892" height="650" alt="Screenshot 2026-11-11 120942" src="https://github.com/user-attachments/assets/ad096468-4c82-4f12-b395-5278523716e7" />
<img width="1250" height="578" alt="Screenshot 2026-11-11 120954" src="https://github.com/user-attachments/assets/2ff7a8b2-f2b5-4af4-9728-ca4e76c32bb1" />

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
